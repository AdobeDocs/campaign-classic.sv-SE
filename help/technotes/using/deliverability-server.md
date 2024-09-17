---
product: campaign
title: Uppdatera till den nya leveransservern
description: Lär dig hur du uppdaterar till den nya servern för kampanjleverans
feature: Technote, Deliverability
hide: true
hidefromtoc: true
exl-id: bc62ddb9-beff-4861-91ab-dcd0fa1ed199
source-git-commit: c42d4022587846081442a39d03546c0ef335c7a0
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Uppdatera till den nya leveransservern {#acc-deliverability}

Från och med [v7.2.2-utgåvan](../../rn/using/latest-release.md#release-7-2-2) förlitar sig Adobe Campaign på en ny leveransserver som erbjuder hög tillgänglighet och åtgärdar problem med säkerhetsefterlevnad. Campaign Classic synkroniserar nu leveransregler, utsändningsloggar och undertryckningsadress från och till en ny leveransserver. Den gamla leveransservern kommer att avvecklas den 31 augusti 2022.

Som Campaign Classic-kund måste du implementera den nya leveransservern **före den 31 augusti 2022**.

>[!NOTE]
>
>Mer information om de här ändringarna finns i [Vanliga frågor](#faq) eller kontakta [Adobe kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){_blank}.
>

## Vad har ändrats?{#acc-deliverability-changes}

Adobe tar äldre datacenter ur drift på grund av säkerhetsskäl. Adobe Campaign Classic-klienter måste migrera till den nya slutprodukten, som ligger hos Amazon webbtjänst (AWS).

Den nya servern garanterar hög tillgänglighet (99.9) &#x200B; och tillhandahåller säkra och autentiserade slutpunkter så att kampanjservrar kan hämta nödvändiga data: i stället för att ansluta till databasen för varje begäran, cachelagrar den nya leveransservern data för att hantera förfrågningarna där det är möjligt. Den här funktionen förbättrar svarstiden. &#x200B;

## Påverkas du?{#acc-deliverability-impacts}

Alla kunder påverkas och måste uppgradera till [Campaign v7.2.2](../../rn/using/latest-release.md#release-7-2-2) (eller mer) och implementera sin miljö för att kunna utnyttja den nya leveransservern.

## Hur uppdaterar jag?{#acc-deliverability-update}

Som **värdkund** arbetar Adobe med dig för att uppgradera dina instanser till den nyare versionen och skapa projektet i Adobe Developer Console.

Som **lokal/hybridkund** måste du uppgradera till [Campaign v7.2.2](../../rn/using/latest-release.md#release-7-2-2) (eller mer) för att kunna utnyttja den nya leveransservern. När alla instanser har uppgraderats måste du [implementera den nya integreringen](#implementation-steps) till leveransservern Adobe och säkerställa en sömlös övergång.

## Implementeringssteg {#implementation-steps}

>[!WARNING]
>
>Dessa åtgärder bör endast utföras för hybridimplementeringar och lokala implementeringar.

Campaign måste kommunicera med Adobe Shared Services via en IMS-baserad autentisering, vilket ingår i den nya integreringen av leveransservern. Det bästa sättet är att använda den Adobe Developer-baserade gatewaytoken (kallas även Token för tekniskt konto eller Adobe IO JWT).

>[!AVAILABILITY]
>
> JWT-autentiseringsuppgifterna (Service Account) har tagits bort av Adobe, och Campaign-integreringar med Adobe-lösningar och appar måste nu förlita sig på autentiseringsuppgifter för OAuth Server-till-Server. </br>
>
> * Om du har implementerat inkommande integreringar med Campaign måste du migrera ditt tekniska konto enligt beskrivningen i [den här dokumentationen](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#_blank). Befintliga [JWT-autentiseringsuppgifter ](../../integrations/using/oauth-technical-account.md) fortsätter att fungera till 27 januari 2025. </br>
>
> * Om ni har implementerat utgående integreringar, som integrering med Campaign-Analytics eller integrering med Experience Cloud-utlösare, fortsätter de att fungera fram till 27 januari 2025. Innan detta datum måste ni dock uppgradera er Campaign-miljö till v7.4.1 och migrera ert tekniska konto till Autentisering.

### Förhandskrav{#prerequisites}

Kontrollera instanskonfigurationen innan du startar implementeringen.

1. Öppna Campaign-klientkonsolen och logga in på Adobe Campaign som administratör.
1. Gå till **Administration > Plattform > Alternativ**.
1. Kontrollera att alternativvärdet `DmRendering_cuid` är ifyllt.

   * Om alternativet är ifyllt kan du starta implementeringen.
   * Om inget värde har fyllts i kontaktar du [Adobe kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){_blank} för att få ditt CUID.

   Det här alternativet måste fyllas i för alla Campaign-instanser (MKT, MID, RT, EXEC) med rätt värde. Som hybridkund kan du kontakta Adobe om du vill att alternativet ska vara inställt på MID-, RT- och EXEC-instanserna.

Som lokal kund måste du även kontrollera att det finns en kampanj **[!UICONTROL Product profile]** tillgänglig för din organisation. Gör så här:

1. Som administratör ansluter du till [Adobe Admin Console](https://adminconsole.adobe.com/){_blank}.
1. Gå till avsnittet **Produkt och tjänster** och kontrollera att **Adobe Campaign** visas.
Om du inte kan se **Adobe Campaign** kontaktar du [Adobe kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){_blank} för att få det tillagt.
1. Klicka på **Adobe Campaign** och välj din organisation.
   **Varning**: Om du har fler än en organisation måste du välja rätt. Läs mer om organisationer [på den här sidan](https://experienceleague.adobe.com/docs/control-panel/using/faq.html#ims-org-id){_blank}.

1. Kontrollera att **[!UICONTROL Product profile]** finns. Om inte, skapar du den. Ingen behörighet krävs för denna **[!UICONTROL Product profile]**.


>[!CAUTION]
>
>Om en brandvägg implementeras på din sida måste du som lokal kund lägga till den här URL:en `https://deliverability-service.adobe.io` på tillåtelselista. [Läs mer](../../installation/using/url-permissions.md).


### Steg 1: Skapa/uppdatera ditt Adobe Developer-projekt {#adobe-io-project}

Om du vill fortsätta konfigurera din Adobe Analytics-anslutning öppnar du Adobe Developer-konsolen och skapar ett OAuth Server-till-Server-projekt.

Mer information finns på [den här sidan](../../integrations/using/oauth-technical-account.md#oauth-service).

### Steg 2: Lägg till projektautentiseringsuppgifterna i Adobe Campaign {#add-credentials-campaign}

Följ stegen som beskrivs på [den här sidan](../../integrations/using/oauth-technical-account.md#add-credentials) för att lägga till dina OAuth-projektautentiseringsuppgifter i Adobe Campaign.

### Steg 3: Validera konfigurationen

Följ stegen nedan för att kontrollera att integreringen lyckas:

1. Öppna klientkonsolen och logga in på Adobe Campaign.
1. Bläddra till **Administration > Produktion > Tekniska arbetsflöden**.
1. Starta om arbetsflödet **Uppdatera för leverans** (deliverabilityUpdate). Detta bör utföras på alla era Campaign-instanser (MKT, MID, RT, EXEC). Som hybrikund kan du kontakta Adobe för att få arbetsflödet startat om på MID-, RT- och EXEC-instanserna.
1. Kontrollera loggar: arbetsflödet ska köras utan fel.

>[!CAUTION]
>
>Efter uppdateringen måste arbetsflödet **Uppdatera startnätverk för Inbox Rendering (updateRenderingSeeds)** stoppas eftersom det inte längre gäller och kommer att misslyckas.

## Vanliga frågor och svar {#faq}

### Vad är tidslinjen för uppdateringen?

Övergången till den nya leveransservern, som gör det möjligt att lägga till dessa förbättrade funktioner och ökad säkerhet, börjar den 22 juli för värdkunder (Campaign Managed Services). Alla värdkunder kommer att uppdateras före augusti.

Lokala kunder och hybridkunder måste gå över under samma tidsram.

### Vad händer om jag inte uppgraderar min miljö?

Alla Campaign-instanser som inte har uppgraderats senast den 31 augusti kommer inte längre att kunna ansluta till Campaign Deliverability-servern. Därför kommer arbetsflödet **Uppdatera för levererbarhet** (deliverabilityUpdate) att misslyckas, vilket påverkar leveransmöjligheterna.

Om du inte uppgraderar din miljö kommer e-postinställningarna inte längre att synkroniseras (MX-hanteringsregler, regler för inkommande e-post, regler för domänhantering och studsregler). Detta kan påverka leveransmöjligheterna. Om dessa regler ändras avsevärt måste de tillämpas manuellt från och med nu.

Endast [Global Suppression List](../../campaign-opt/using/filtering-rules.md#default-deliverability-exclusion-rules) påverkas för MKT-instanser.
