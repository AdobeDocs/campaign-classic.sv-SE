---
title: Installera klientkonsolen
description: Lär dig hur du installerar klientkonsolen
page-status-flag: never-activated
uuid: 1279c0d8-bf27-4a58-ae94-796d6147231a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
discoiquuid: d1069b23-e08d-43c5-bbfb-3158ac40dc7e
translation-type: tm+mt
source-git-commit: 48176ebb19689855f3ee5e61fa6492be5a682291
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 5%

---


# Installerar klientkonsolen för Campaign{#installing-the-client-console}

Campaign Client-konsolen är en avancerad klient som gör att du kan ansluta till dina Campaign-programservrar.

Innan du startar måste du kontrollera [kompatibilitetsmatrisen](https://helpx.adobe.com/se/campaign/kb/compatibility-matrix.html)för Campaign, hämta URL:en för Campaign-servern och inloggningsuppgifterna.

>[!CAUTION]
>
>Kampanjklientkonsolen och Campaign-programservern måste köras på samma produktversion. Adobe rekommenderar också att du använder samma produktbygge.

## Ladda ned konsolen{#download-the-client-console}

Följ stegen nedan för att hämta och installera Adobe Campaign klientkonsol:

1. Öppna en webbläsare och hämta konsolen från följande adress:

   [`https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`](https://machine/nl/jsp/logon.jsp).

1. I identifieringsfönstret anger du din inloggning och ditt lösenord.

   ![](assets/s_ncs_install_setup_download01.png)

   Om det behövs använder du autentiseringsuppgifterna för det interna konto som definierats när instansen skapades.

1. Klicka på **[!UICONTROL Download]** länken på installationssidan.
1. Hämta och spara klientinstallationsfilen.
1. Kör den hämtade filen på en dator i Windows: Installationen startar. Standardinstallationssökvägen för klientkonsolen är **$PROGRAMFILES$/Adobe/Adobe Campaign Classic vX Client**, där X är 6 eller 7 enligt din Adobe Campaign-version.

>[!NOTE]
>
>I Windows kan du starta filen **nlclient.exe** direkt från `[INSTALL]/bin` katalogen på en Windows-server, där `[INSTALL]` sökvägen till Adobe Campaign-installationsmappen finns.

## Skapa anslutningen{#create-the-connection}

När klientkonsolen har installerats följer du stegen nedan för att skapa anslutningen till programservern:

1. Starta konsolen från Windows- **[!UICONTROL Start]** menyn i **Adobe Campaign** -programgruppen.

1. Klicka på länken i det övre högra hörnet av inloggningsfälten för att komma åt fönstret för anslutningskonfiguration.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Klicka **[!UICONTROL Add > Connection]** och ange etiketten och URL-adressen för Adobe Campaign-programservern.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Ange en anslutning till Adobe Campaign-programservern via en URL. Använd antingen en DNS eller ett alias för datorn eller din IP-adress.

   Du kan till exempel använda [`https://<machine>.<domain>.com`](https://machine) typen URL.

1. Om Adobe IMS är konfigurerat för din organisation markerar du alternativet **[!UICONTROL Connect with an Adobe ID]**

1. Click **[!UICONTROL Ok]** to save your settings.

Du kan lägga till så många anslutningar som behövs för att ansluta till test-, scen- och produktionsmiljöer, till exempel.

>[!NOTE]
>
>Med knappen **[!UICONTROL Add]** kan du skapa **[!UICONTROL folders]** för att ordna alla dina anslutningar. Bara dra och släpp varje anslutning till en mapp.

## Logga in på Adobe Campaign

Så här loggar du in på en befintlig instans:

1. Starta konsolen från Windows- **[!UICONTROL Start]** menyn i **Adobe Campaign** -programgruppen.

1. Klicka på länken i det övre högra hörnet av inloggningsfälten för att komma åt fönstret för anslutningskonfiguration.

1. Välj den Campaign-instans som du måste logga in på.

1. Klicka på **[!UICONTROL Ok]**

1. Ange dina inloggningsuppgifter och klicka på **[!UICONTROL Log in]**

**Relaterade ämnen**

* [Skapa en instans och logga in](../../installation/using/creating-an-instance-and-logging-on.md).
* [Kompatibilitetsmatris](https://helpx.adobe.com/se/campaign/kb/compatibility-matrix.html)
* [Installera och konfigurera Adobe Campaign Client](https://docs.adobe.com/content/help/en/campaign-classic-learn/tutorials/getting-started/install-and-setup-the-adobe-campaign-client.html) (video)
