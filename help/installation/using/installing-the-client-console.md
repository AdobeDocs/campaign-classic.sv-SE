---
solution: Campaign Classic
product: campaign
title: Installera klientkonsolen
description: Lär dig hur du installerar klientkonsolen
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
translation-type: tm+mt
source-git-commit: 1b02c3870ddc01705f01ea992e734cf0810e003a
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 6%

---


# Installerar klientkonsolen för Campaign{#installing-the-client-console}

Campaign Client-konsolen är en avancerad klient som gör att du kan ansluta till dina Campaign-programservrar.

Innan du startar måste du kontrollera Campaign [kompatibilitetsmatrisen](https://helpx.adobe.com/se/campaign/kb/compatibility-matrix.html), hämta URL:en för Campaign-servern och inloggningsuppgifterna.

>[!CAUTION]
>
>Kampanjklientkonsolen och Campaign-programservern måste köras på samma produktversion. Adobe rekommenderar också att du använder samma produktbygge.

![](assets/do-not-localize/how-to-video.png) Lär dig installera och konfigurera Adobe Campaign Client i  [video](#video)

## Hämta konsolen{#download-the-client-console}

Följ stegen nedan för att hämta och installera Adobe Campaign klientkonsol:

1. Öppna en webbläsare och hämta konsolen från följande adress:

   [`https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`](https://myserver.adobe.com/nl/jsp/logon.jsp).

1. I identifieringsfönstret anger du din inloggning och ditt lösenord.

   ![](assets/s_ncs_install_setup_download01.png)

   Om det behövs använder du autentiseringsuppgifterna för det interna konto som definierats när instansen skapades.

1. Klicka på länken **[!UICONTROL Download]** på installationssidan.
1. Hämta och spara klientinstallationsfilen.
1. Kör den hämtade filen på en dator i Windows: Installationen startar. Standardinstallationssökvägen för klientkonsolen är **$PROGRAMFILES$/Adobe/Adobe Campaign Classic vX Client**, där X är 6 eller 7 enligt din Adobe Campaign-version.

>[!NOTE]
>
>Du kan föreslå att alla användare av Campaign-klientkonsolen uppdaterar den senaste versionen genom att kopiera den körbara konsolfilen till en specifik mapp på Campaign Marketing-servern. [Läs mer](../../installation/using/client-console-availability-for-windows.md).


## Skapa anslutningen{#create-the-connection}

När klientkonsolen har installerats följer du stegen nedan för att skapa anslutningen till programservern:

1. Starta konsolen från Windows **[!UICONTROL Start]**-menyn i **Adobe Campaign**-programgruppen.

1. Klicka på länken i det övre högra hörnet av inloggningsfälten för att komma åt fönstret för anslutningskonfiguration.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Klicka på **[!UICONTROL Add > Connection]** och ange etiketten och URL:en för Adobe Campaign-programservern.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Ange en anslutning till Adobe Campaign-programservern via en URL. Använd antingen en DNS eller ett alias för datorn eller din IP-adress.

   Du kan till exempel använda URL-adressen [`https://<machine>.<domain>.com`](https://myserver.adobe.com).

1. Om Adobe IMS är konfigurerat för din organisation kontrollerar du alternativet **[!UICONTROL Connect with an Adobe ID]**

1. Klicka på **[!UICONTROL Ok]** för att spara inställningarna.

Du kan lägga till så många anslutningar som behövs för att ansluta till test-, scen- och produktionsmiljöer, till exempel.

>[!NOTE]
>
>Med knappen **[!UICONTROL Add]** kan du skapa **[!UICONTROL folders]** för att ordna alla dina anslutningar. Bara dra och släpp varje anslutning till en mapp.

## Logga in på Adobe Campaign

Så här loggar du in på en befintlig instans:

1. Starta konsolen från Windows **[!UICONTROL Start]**-menyn i **Adobe Campaign**-programgruppen.

1. Klicka på länken i det övre högra hörnet av inloggningsfälten för att komma åt fönstret för anslutningskonfiguration.

1. Välj den Campaign-instans som du måste logga in på.

1. Klicka på **[!UICONTROL Ok]**

1. Ange dina inloggningsuppgifter och klicka på **[!UICONTROL Log in]**

**Relaterade ämnen**

* [Skapa en instans och logga in](../../installation/using/creating-an-instance-and-logging-on.md).
* [Kompatibilitetsmatris](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

## Videokurs

I den här videon visas hur du installerar och konfigurerar Adobe Campaign Client.

>[!VIDEO](https://video.tv.adobe.com/v/35124?quality=12)

Ytterligare Campaign Classic-instruktionsvideor finns [här](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=sv).
