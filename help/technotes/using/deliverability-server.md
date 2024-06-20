---
product: campaign
title: Uppdatera till den nya leveransservern
description: Lär dig hur du uppdaterar till den nya servern för kampanjleverans
feature: Technote, Deliverability
hide: true
hidefromtoc: true
exl-id: bc62ddb9-beff-4861-91ab-dcd0fa1ed199
source-git-commit: 19b40f0b827c4b5b7b6484fe4953aebe61d00d1d
workflow-type: tm+mt
source-wordcount: '991'
ht-degree: 1%

---

# Uppdatera till den nya leveransservern {#acc-deliverability}

Startar [Version v7.2.2](../../rn/using/latest-release.md#release-7-2-2), förlitar sig Adobe Campaign på en ny server för leverans med hög tillgänglighet och som åtgärdar problem med säkerhetsefterlevnad. Campaign Classic synkroniserar nu leveransregler, utsändningsloggar och undertryckningsadress från och till en ny leveransserver. Den gamla leveransservern kommer att avvecklas den 31 augusti 2022.

Som Campaign Classic måste ni implementera den nya leveransservern **före 31 augusti 2022**.

>[!NOTE]
>
>Mer information om dessa ändringar finns i [Vanliga frågor](#faq)eller kontakta [Adobe kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){_blank}.
>

## Vad har ändrats?{#acc-deliverability-changes}

Adobe tar äldre datacenter ur drift på grund av säkerhetsskäl. Adobe Campaign Classic-klienter måste migrera till den nya slutprodukten, som ligger hos Amazon webbtjänst (AWS).

Den nya servern garanterar hög tillgänglighet (99.9) &#x200B; och tillhandahåller säkra och autentiserade slutpunkter så att kampanjservrar kan hämta nödvändiga data: i stället för att ansluta till databasen för varje begäran, cachelagrar den nya leveransservern data för att hantera förfrågningarna där det är möjligt. Den här funktionen förbättrar svarstiden. &#x200B;

## Påverkas du?{#acc-deliverability-impacts}

Alla kunder påverkas och måste uppgradera till [Campaign v7.2.2](../../rn/using/latest-release.md#release-7-2-2) (eller mer) och implementera deras miljö för att dra nytta av den nya leveransservern.

## Hur uppdaterar jag?{#acc-deliverability-update}

Som en **värdbaserad kund** kommer Adobe att arbeta med dig för att uppgradera dina instanser till den nyare versionen och skapa projektet i Adobe Developer Console.

Som en **lokal/hybridkund** måste du uppgradera till [Campaign v7.2.2](../../rn/using/latest-release.md#release-7-2-2) (eller mer) om du vill dra nytta av den nya leveransservern. När alla instanser har uppgraderats måste du [implementera den nya integreringen](#implementation-steps) till Adobe-server och säkerställa en smidig övergång.

## Implementeringssteg {#implementation-steps}

>[!WARNING]
>
>Dessa åtgärder bör endast utföras för hybridimplementeringar och lokala implementeringar.

Campaign måste kommunicera med Adobe Shared Services via en IMS-baserad autentisering, vilket ingår i den nya integreringen av leveransservern. Det bästa sättet är att använda den Adobe Developer-baserade gatewaytoken (kallas även Token för tekniskt konto eller Adobe IO JWT).

>[!AVAILABILITY]
>
> JWT-autentiseringsuppgifterna (Service Account) har tagits bort av Adobe, och Campaign-integreringar med Adobe-lösningar och appar måste nu förlita sig på autentiseringsuppgifter för OAuth Server-till-Server. </br>
>
> * Om du har implementerat inkommande integreringar med Campaign måste du migrera ditt tekniska konto enligt informationen i [den här dokumentationen](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#_blank). Befintliga JWT-referenser (Service Account) kommer att fortsätta att fungera fram till 27 januari 2025. </br>
>
> * Om ni har implementerat utgående integreringar, som integrering med Campaign-Analytics eller integrering med Experience Cloud-utlösare, fortsätter de att fungera fram till 27 januari 2025. Innan detta datum måste ni dock uppgradera er Campaign-miljö till v7.4.1 och migrera ert tekniska konto till Autentisering.

### Förhandskrav{#prerequisites}

Kontrollera instanskonfigurationen innan du startar implementeringen.

1. Öppna Campaign-klientkonsolen och logga in på Adobe Campaign som administratör.
1. Bläddra till **Administration > Plattform > Alternativ**.
1. Kontrollera att `DmRendering_cuid` alternativvärdet är ifyllt.

   * Om alternativet är ifyllt kan du starta implementeringen.
   * Om inget värde är ifyllt kontaktar du [Adobe kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){_blank} för att få ditt CUID.

   Det här alternativet måste fyllas i för alla Campaign-instanser (MKT, MID, RT, EXEC) med rätt värde. Som hybridkund kan du kontakta Adobe om du vill att alternativet ska vara inställt på MID-, RT- och EXEC-instanserna.

Som lokal kund måste ni också kontrollera att en kampanj **[!UICONTROL Product profile]** finns för din organisation. Gör så här:

1. Som administratör ansluter du till [Adobe Admin Console](https://adminconsole.adobe.com/){_blank}.
1. Öppna **Produkt och tjänster** sektion och kontroll **Adobe Campaign** visas.
Om du inte ser **Adobe Campaign** kontakta [Adobe kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){_blank} för att få det tillagt.
1. Klicka **Adobe Campaign** och väljer organisation.
   **Varning**: Om du har fler än en organisation måste du välja rätt organisation. Läs mer om organisationer [på den här sidan](https://experienceleague.adobe.com/docs/control-panel/using/faq.html#ims-org-id){_blank}.

1. Kontrollera att **[!UICONTROL Product profile]** finns. Om inte, skapar du den. Ingen behörighet krävs för detta **[!UICONTROL Product profile]**.


>[!CAUTION]
>
>Om en brandvägg implementeras på din sida måste du som lokal kund lägga till den här URL:en `https://deliverability-service.adobe.io` till tillåtelselista. [Läs mer](../../installation/using/url-permissions.md).


### Steg 1: Skapa/uppdatera ditt Adobe Developer-projekt {#adobe-io-project}

Om du vill fortsätta konfigurera din Adobe Analytics-anslutning öppnar du Adobe Developer-konsolen och skapar ett OAuth Server-till-Server-projekt.

Se [den här sidan](../../integrations/using/oauth-technical-account.md#oauth-service) för detaljerad dokumentation.

### Steg 2: Lägg till projektautentiseringsuppgifterna i Adobe Campaign {#add-credentials-campaign}

Följ stegen i [den här sidan](../../integrations/using/oauth-technical-account.md#add-credentials) för att lägga till dina OAuth-projektbehörigheter i Adobe Campaign.

### Steg 3: Validera konfigurationen

Följ stegen nedan för att kontrollera att integreringen lyckas:

1. Öppna klientkonsolen och logga in på Adobe Campaign.
1. Bläddra till **Administration > Produktion > Tekniska arbetsflöden**.
1. Starta om **Uppdatera för leverans** arbetsflöde (deliverabilityUpdate). Detta bör utföras på alla era Campaign-instanser (MKT, MID, RT, EXEC). Som hybrikund kan du kontakta Adobe för att få arbetsflödet startat om på MID-, RT- och EXEC-instanserna.
1. Kontrollera loggar: arbetsflödet ska köras utan fel.

>[!CAUTION]
>
>Efter uppdateringen **Uppdatera startnätverk för Inbox Rendering (updateRenderingSeeds)** arbetsflödet måste stoppas eftersom det inte längre gäller och kommer att misslyckas.

## Vanliga frågor och svar {#faq}

### Vad är tidslinjen för uppdateringen?

Övergången till den nya leveransservern, som gör det möjligt att lägga till dessa förbättrade funktioner och ökad säkerhet, börjar den 22 juli för värdkunder (Campaign Managed Services). Alla värdkunder kommer att uppdateras före augusti.

Lokala kunder och hybridkunder måste gå över under samma tidsram.

### Vad händer om jag inte uppgraderar min miljö?

Alla Campaign-instanser som inte har uppgraderats senast den 31 augusti kommer inte längre att kunna ansluta till Campaign Deliverability-servern. Som en följd av detta **Uppdatera för leverans** (deliverabilityUpdate)-arbetsflödet kommer att misslyckas och detta påverkar leveransmöjligheterna.

Om du inte uppgraderar din miljö kommer e-postinställningarna inte längre att synkroniseras (MX-hanteringsregler, regler för inkommande e-post, regler för domänhantering och studsregler). Detta kan påverka leveransmöjligheterna. Om dessa regler ändras avsevärt måste de tillämpas manuellt från och med nu.

Endast för MKT-instanser [Global Suppression List](../../campaign-opt/using/filtering-rules.md#default-deliverability-exclusion-rules) påverkas.
