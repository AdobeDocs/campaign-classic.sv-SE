---
product: campaign
title: Uppdatera till den nya leveransservern
description: Lär dig hur du uppdaterar till den nya servern för kampanjleverans
feature: Technote, Deliverability
exl-id: bc62ddb9-beff-4861-91ab-dcd0fa1ed199
source-git-commit: eea3657f1cffa215e1fc1cb1eb8782b83321aae4
workflow-type: tm+mt
source-wordcount: '1252'
ht-degree: 4%

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
> JWT (JSON Web Tokens) håller på att tas ur bruk och ersätts med OAuth. Övergången genomförs stegvis i de kommande versionerna av Campaign och dokumentationen kommer att uppdateras för att återspegla dessa uppdateringar.

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

1. Åtkomst [Adobe Developer Console](https://developer.adobe.com/console/home) och logga in med utvecklaråtkomst i din organisation. Se till att du är inloggad på rätt organisationsportal.
   **Varning**: Om du har fler än en organisation måste du välja rätt organisation. Läs mer om organisationer [på den här sidan](https://experienceleague.adobe.com/docs/control-panel/using/faq.html#ims-org-id){_blank}.
1. Välj **[!UICONTROL Create new project]**.
   ![](assets/New-Project.png)

   >[!CAUTION]
   >
   >Om du redan använder Adobe IO JWT-autentiseringsfunktioner för en annan integrering, till exempel Analytics Connector eller Adobe Triggers, måste du uppdatera projektet genom att lägga till **Kampanj-API** till det projektet.

1. Välj **[!UICONTROL Add API]**.
   ![](assets/Add-API.png)
1. I **[!UICONTROL Add an API]** fönster, markera **[!UICONTROL Adobe Campaign]**.
   ![](assets/AC-API.png)
1. Om ditt klient-ID var tomt väljer du **[!UICONTROL Generate a key pair]** för att skapa ett nyckelpar för offentlig och privat nyckel.
   ![](assets/Generate-a-key-pair.png)

   Nycklarna laddas sedan ned automatiskt med ett standardutgångsdatum på 365 dagar. När det har gått ut måste du skapa ett nytt nyckelpar och uppdatera integreringen i konfigurationsfilen. Med alternativ 2 kan du välja att manuellt skapa och överföra **[!UICONTROL Public key]** med ett längre utgångsdatum.
   ![](assets/New-key-pair.png)

   >[!CAUTION]
   >
   >Du bör spara `config.zip` när nedladdningsprompten visas eftersom du inte kan ladda ned den igen.

1. Klicka på **[!UICONTROL Next]**.
1. Välj en befintlig **[!UICONTROL Product profile]** eller skapa en ny vid behov. Ingen behörighet krävs för detta **[!UICONTROL Product profile]**. Mer information om **[!UICONTROL Product Profiles]**, se [den här sidan](https://helpx.adobe.com/enterprise/using/manage-developers.html){_blank}.
   ![](assets/Product-Profile-API.png)

   Klicka sedan på **[!UICONTROL Save configured API]**.

1. Välj **[!UICONTROL Adobe Campaign]** och kopiera följande information under **[!UICONTROL Service Account (JWT)]**

   ![](assets/Config-API.png)

   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

>[!CAUTION]
>
>Adobe Developer-certifikatet upphör att gälla efter 12 månader. Du måste generera ett nytt nyckelpar varje år.

### Steg 2: Lägg till projektautentiseringsuppgifterna i Adobe Campaign {#add-credentials-campaign}

Den privata nyckeln ska kodas i base64 UTF-8-format.

För att göra detta:

1. Använd den privata nyckel som genereras i stegen ovan.
1. Koda den privata nyckeln med följande kommando: `base64 ./private.key > private.key.base64`. Detta sparar base64-innehållet i en ny fil `private.key.base64`.

   >[!NOTE]
   >
   >Extra rader kan ibland läggas till automatiskt när du kopierar/klistrar in den privata nyckeln. Kom ihåg att ta bort den innan du kodar din privata nyckel.

1. Kopiera innehållet från filen `private.key.base64`.
1. Logga in via SSH i varje behållare där Adobe Campaign-instansen är installerad och lägg till projektinloggningsuppgifterna i Adobe Campaign genom att köra följande kommando som `neolane` användare. Det här infogar **[!UICONTROL Technical Account]** autentiseringsuppgifter i instanskonfigurationsfilen.

   ```sql
   nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID/<Client_Secret>/<Base64_encoded_Private_Key>
   ```

1. Du måste stoppa och sedan starta om servern för att ändringen ska kunna beaktas. Du kan också köra en `config -reload` -kommando.

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
