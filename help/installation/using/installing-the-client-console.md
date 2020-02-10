---
title: Installera klientkonsolen
seo-title: Installera klientkonsolen
description: Installera klientkonsolen
seo-description: null
page-status-flag: never-activated
uuid: 1279c0d8-bf27-4a58-ae94-796d6147231a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
discoiquuid: d1069b23-e08d-43c5-bbfb-3158ac40dc7e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: be590c6d993eecacf51736e3c3e415addae5c6bd

---


# Installera klientkonsolen{#installing-the-client-console}

Installationsproceduren för Adobe Campaign-konsolen beskrivs nedan.

Innan du installerar Adobe Campaign-konsolen kontrollerar du de krav som anges i [kompatibilitetsmatrisen](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html).

Så här installerar du Adobe Campaign-konsolen:

1. Öppna en webbläsare och ladda ned konsolen från följande adress:

   [`https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`](https://machine/nl/jsp/logon.jsp).

1. I identifieringsfönstret anger du din inloggning och ditt lösenord.

   ![](assets/s_ncs_install_setup_download01.png)

   Om det behövs använder du autentiseringsuppgifterna för det interna konto som definierats när instansen skapades.

1. Klicka på **[!UICONTROL Download]** länken på installationssidan.
1. Hämta och spara klientinstallationsfilen.
1. Kör den hämtade filen på en dator i Windows: Installationen startar. Standardinstallationssökvägen för klientkonsolen är **$PROGRAMFILES$/Adobe/Adobe Campaign Classic vX Client**, där X är 6 eller 7, enligt din Adobe Campaign-version.
1. När installationsprogrammet är klart startar du konsolen från Windows- **[!UICONTROL Start]** menyn (i **Adobe Campaign** -programgruppen).

>[!NOTE]
>
>I Windows kan du starta filen **nlclient.exe** direkt från `[INSTALL]/bin` katalogen på en Windows-server, där `[INSTALL]` sökvägen till installationsmappen för Adobe Campaign finns.\
>Mer information om hur du skapar en ny anslutning finns i [Skapa en instans och logga in](../../installation/using/creating-an-instance-and-logging-on.md).

