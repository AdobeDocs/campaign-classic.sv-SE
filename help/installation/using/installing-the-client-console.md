---
product: campaign
title: Installera klientkonsolen
description: Lär dig installera klientkonsolen
feature: Installation, Upgrade
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 7cc78214-92b8-4b1f-a307-96ec6af818d1
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '1124'
ht-degree: 0%

---

# Installera och uppdatera Campaign-klientkonsolen{#installing-the-client-console}

Campaign Client Console är en avancerad klient som gör att du kan ansluta till dina Campaign-programservrar.

Innan du börjar installera klientkonsolen måste du:

* Kontrollera system- och verktygskompatibiliteten med Adobe Campaign i [kompatibilitetsmatrisen](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)
* Hämta webbadressen till Campaign-servern
* Hämta inloggningsuppgifter
* Ha Microsoft Edge Webview2 installerat på datorn (från version 7.3 av Campaign Classic). [Läs mer](#webview)

Processen att installera eller uppdatera klientkonsolen skiljer sig åt beroende på hur du implementerar Adobe Campaign Classic.
Läs informationen nedan för att ta reda på vad som krävs för implementeringen.

![](assets/do-not-localize/how-to-video.png) Upptäck hur du installerar och konfigurerar Adobe Campaign Client i [video](#video)

>[!CAUTION]
>
>* Kampanjklientkonsolen och Campaign-programservern måste köra **på samma produktversion**. Adobe rekommenderar också att du använder **samma produktbygge**. Lär dig hur du kontrollerar dina Campaign Client- och Server-versioner i [det här avsnittet](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).
>
>* Åtkomsten till installationsmappen där konsolen är installerad bör begränsas till endast den avsedda användaren, vilket säkerställer att skrivbehörigheterna begränsas i enlighet med detta.



## Installation av Microsoft Edge Webview2 {#webview}

Från och med version 7.3 av Campaign Classic krävs installation av Microsoft Edge Webview 2 för alla konsolinstallationer.

Webbvyn installeras som standard som en del av Windows 11. Om det inte redan finns på datorn uppmanas du att hämta det från [Microsoft Developer-webbplatsen](https://www.adobe.com/go/acc-ms-webview2-runtime-download). Observera att nedladdningslänken inte fungerar i webbläsaren Internet Explorer 11 eftersom Microsoft inte längre stöder det. Kontrollera att du använder en annan webbläsare för att komma åt länken.

## Implementeringar via Adobe Hosted {#hosted-customers}

Som värdkund har du två alternativ för att installera eller uppdatera klientkonsolerna:

1. Adobe kan driftsätta direkt. När konsolen har uppdaterats uppmanas användarna att hämta den senaste klientkonsolversionen i ett popup-fönster.

1. Du kan hämta till klientkonsolen/klientkonsolerna från [Programvarudistribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)

   **Användare behöver administratörsåtkomst för att kunna slutföra uppdateringen. Om användarna inte har administratörsbehörighet måste en systemadministratör distribuera till alla klientkonsoler**

## Hybrid- och lokala implementeringar {#hybrid-onprem-customers}

För att Adobe Campaign-användare ska kunna logga in på den instans som du har skapat och konfigurerat måste de använda klientkonsolen.

### Göra konsolen tillgänglig för användare {#make-console-available}

När datorn som används för att starta en Adobe Campaign-programserver (nlserver web) tar emot användaranslutningar från klientkonsolen kan du konfigurera den så att installationsprogrammet för Adobe Campaign RIA-klienten blir tillgängligt via ett HTML-gränssnitt. När det finns en ny version av klientkonsolen får användarna en inbjudan om att ladda ned den när de startar klientkonsolen.

För att göra detta måste du:

1. Välj det paket som innehåller installationsprogrammet för konsolen.

   Den här filen kallas setup-client-7.X.XXXX.exe, där X är underversionen av Adobe Campaign och XXXX är build-numret.

1. Kopiera och klistra in det här paketet i Adobe Campaign installationsmapp (på marknadsföringsservern för hybridinstallationer), under /datakit/nl/eng/jsp.

1. Starta Adobe Campaign-servern.


### Fråga inte längre det här frågealternativet

Adobe rekommenderar att du låter alternativet **[!UICONTROL No longer ask this question]** vara avmarkerat för att se till att alla användare får ett meddelande när en ny version av konsolen är tillgänglig.  Om det här alternativet väljs informeras användaren inte om nya tillgängliga versioner.

Om **[!UICONTROL No longer ask this question]** har valts kan du återställa den här uppmaningen. Det är bara systemadministratörer som kan redigera Windows-registret som kan göra följande ändringar:

1. Öppna Registereditorn med kommandot **regedit** på menyn **[!UICONTROL Start > Run]**.

1. Sök efter noden och expandera den.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. Ta bort posten **confAdvisedUpgrade** och stäng Registereditorn.

>[!NOTE]
>
>Om du använder en uppdaterad konsol för en befintlig implementering får användarna automatiskt en uppmaning om att uppdatera sin klientkonsol. Om ni implementerar Campaign för första gången måste användarna hämta konsolen. Nedan finns mer information om båda alternativen

### Uppdatera konsolen för befintlig implementering{#update-the-client-console}

När konsolen är tillgänglig i Campaign-servermappen uppmanas användarna att hämta den senaste klientkonsolversionen i ett popup-fönster.

**Användarna måste ha administratörsåtkomst för att kunna slutföra uppdateringen. Om användarna inte har administratörsbehörighet måste en systemadministratör distribuera till alla klientkonsoler**


### Hämta konsolen för ny implementering{#download-the-client-console}

Användare bör nu hämta och installera konsolen genom att följa stegen nedan:

1. Öppna en webbläsare och hämta konsolen från följande adress:

   `https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`.

1. I identifieringsfönstret anger du din inloggning och ditt lösenord.

   ![](assets/s_ncs_install_setup_download01.png)

   Om det behövs använder du autentiseringsuppgifterna för det interna konto som definierats när instansen skapades.

1. Klicka på länken **[!UICONTROL Download]** på installationssidan.
1. Hämta och spara klientinstallationsfilen.
1. Kör den hämtade filen på en dator i Windows: Installationen startar. Standardinstallationssökvägen för klientkonsolen är **$PROGRAMFILES$/Adobe/Adobe Campaign Classic vX Client**, där X är 6 eller 7 enligt din Adobe Campaign-version.

### Skapa anslutningen - endast för första gången{#create-the-connection}

När klientkonsolen har installerats följer du stegen nedan för att skapa anslutningen till programservern:

1. Starta konsolen från Windows **[!UICONTROL Start]**-menyn i programgruppen **Adobe Campaign**.

1. Klicka på länken i det övre högra hörnet av inloggningsfälten för att komma åt fönstret för anslutningskonfiguration.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Klicka på **[!UICONTROL Add > Connection]** och ange etiketten och URL:en för Adobe Campaign-programservern.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Ange en anslutning till Adobe Campaign-programservern via en URL. Använd antingen en DNS eller ett alias för datorn eller din IP-adress.

   Du kan till exempel använda URL-typen `https://<machine>.<domain>.com`.

1. Om Adobe IMS har konfigurerats för din organisation kontrollerar du alternativet **[!UICONTROL Connect with an Adobe ID]**

1. Klicka på **[!UICONTROL Ok]** om du vill spara inställningarna.

Du kan lägga till så många anslutningar som behövs för att ansluta till test-, scen- och produktionsmiljöer, till exempel.

>[!NOTE]
>
>Med knappen **[!UICONTROL Add]** kan du skapa **[!UICONTROL folders]** för att ordna alla dina anslutningar. Bara dra och släpp varje anslutning till en mapp.

### Logga in på Adobe Campaign

Så här loggar du in på en befintlig instans:

1. Starta konsolen från Windows **[!UICONTROL Start]**-menyn i programgruppen **Adobe Campaign**.

1. Klicka på länken i det övre högra hörnet av inloggningsfälten för att komma åt fönstret för anslutningskonfiguration.

1. Välj den Campaign-instans som du måste logga in på.

1. Klicka på **[!UICONTROL Ok]**

1. Ange dina inloggningsuppgifter och klicka på **[!UICONTROL Log in]**

>[!NOTE]
>
>För kampanjversioner med klassisk version 7.3 kan Adobe Campaign-klientkonsolen begära proxyautentiseringsuppgifter två gånger under proxyautentiseringen. Detta beror på att Microsoft Edge Webview2 inte sparar proxyautentiseringsuppgifter i cache-/lösenordsarkivet, till skillnad från Internet Explorer.

**Relaterade ämnen**

* [Skapar en instans och loggar in](../../installation/using/creating-an-instance-and-logging-on.md).
* [Kompatibilitetsmatris](https://helpx.adobe.com/se/campaign/kb/compatibility-matrix.html)

## Självstudievideo

I den här videon visas hur du installerar och konfigurerar Adobe Campaign Client.

>[!VIDEO](https://video.tv.adobe.com/v/35124?quality=12)

Ytterligare Campaign Classic om instruktionsvideor finns [här](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=sv).
