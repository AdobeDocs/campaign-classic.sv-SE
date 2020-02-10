---
title: Klientkonsolens tillgänglighet för Windows
seo-title: Klientkonsolens tillgänglighet för Windows
description: Klientkonsolens tillgänglighet för Windows
seo-description: null
page-status-flag: never-activated
uuid: d1cbb34e-87e0-481b-a78b-3616047eb5cb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
discoiquuid: 4fa2e8c1-33d1-4d14-941b-ca528b8ceabb
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 46f5bfb41bfe9c938ac0ffa767ead3e47a32047d

---


# Klientkonsolens tillgänglighet för Windows{#client-console-availability-for-windows}

För att Adobe Campaign-användare ska kunna logga in på den instans som du har skapat och konfigurerat måste de använda klientkonsolen.

När datorn som används för att starta en Adobe Campaign-programserver (**webbservern** på lserver) tar emot användaranslutningar från klientkonsolen kan du konfigurera den så att installationsprogrammet för Adobe Campaign-klienten blir tillgängligt via ett HTML-gränssnitt.

För att göra detta måste du:

1. Återställ paketet som innehåller konsolens installationsprogram.

   Den här filen anropas `setup-client-7.X.XXXX.exe` för v7 eller `setup-client-6.X.XXXX.exe` för v6.1, där `X` är underversionen av Adobe Campaign och `XXXX` är versionsnumret.

1. Kopiera och klistra in det här paketet i installationsmappen för Adobe Campaign, under **/data/nl/eng/jsp**.
1. Starta Adobe Campaign-servern.

Slutanvändarna kan sedan ladda ned installationsprogrammet för konsolen via en webbläsare tack vare följande URL:

```
https://<your Adobe Campaign server>:>port number>/nl/jsp/logon.jsp
```

Den här sidan kräver inloggning och lösenord som definierats i programmet.

Information om hur du hämtar och installerar konsolen finns i [Installera klientkonsolen](../../installation/using/installing-the-client-console.md).

När det finns en ny version av klientkonsolen får du en inbjudan om att ladda ned den.

>[!NOTE]
>
>I den fråga som visas rekommenderar Adobe att du låter alternativet vara **[!UICONTROL No longer ask this question]** omarkerat för att se till att alla användare får en varning när en ny version av konsolen är tillgänglig.\
>Om du väljer det här alternativet och väljer att inte hämta den senaste versionen informeras ingen annan användare om nya tillgängliga versioner.

Om du vill återställa den här uppmaningen följer du stegen nedan (endast systemadministratörer som är bekväma med att redigera registret bör göra dessa ändringar):

1. Öppna Registereditorn med **kommandot regedit** på **[!UICONTROL Start > Run]** menyn.
1. Sök efter noden och expandera den.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. Ta bort **confAdvisedUpgrade** -posten och stäng Registereditorn.

