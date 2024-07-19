---
product: campaign
title: Klientkonsolens tillgänglighet i Windows
description: Klientkonsolens tillgänglighet i Windows
feature: Installation, Upgrade
badge-v7-prem: label="Endast lokal/hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 57845eae-1f1a-42f4-b2ba-46d454677ae0
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 4%

---

# Klientkonsolens tillgänglighet i Windows{#client-console-availability-for-windows}



För att Adobe Campaign-användare ska kunna logga in på den instans som du har skapat och konfigurerat måste de använda klientkonsolen.

## Gör klientkonsolen tillgänglig

När datorn som används för att starta en Adobe Campaign-programserver (**nlserver web**) tar emot användaranslutningar från klientkonsolen kan du konfigurera den så att installationsprogrammet för Adobe Campaign-klienten blir tillgängligt via ett HTML-gränssnitt. När det finns en ny version av klientkonsolen får användarna en inbjudan om att ladda ned den när de startar klientkonsolen.

För att göra detta måste du:

1. Välj det paket som innehåller installationsprogrammet för konsolen.

   Den här filen kallas `setup-client-7.X.XXXX.exe`, där `X` är underversionen av Adobe Campaign och `XXXX` är versionsnumret.

1. Kopiera och klistra in det här paketet i installationsmappen för Adobe Campaign (på marknadsföringsservern för hybridinstallationer), under **/data it/nl/eng/jsp**.
1. Starta Adobe Campaign-servern.

Kampanjanvändare kan sedan hämta konsolinstallationsprogrammet via en webbläsare tack vare följande URL:

```
https://<your Adobe Campaign server>:>port number>/nl/jsp/logon.jsp
```

Den här sidan kräver inloggning och lösenord som definierats i programmet.

Lär dig hur du installerar konsolen [ i det här avsnittet](../../installation/using/installing-the-client-console.md).

## Föreslå att slutanvändare uppgraderar sin klientkonsol

När konsolen är tillgänglig i Campaign-servermappen bjuds användarna in att hämta den senaste klientkonsolversionen i ett dedikerat fönster. Adobe rekommenderar att du låter alternativet **[!UICONTROL No longer ask this question]** vara avmarkerat för att se till att alla användare får ett meddelande när en ny version av konsolen är tillgänglig.

Om du väljer det här alternativet och väljer att inte hämta den senaste versionen informeras ingen annan användare om nya tillgängliga versioner.

Om alternativet har valts kan du återställa den här uppmaningen. Det är bara systemadministratörer som kan redigera Windows-registret som kan göra följande ändringar:

1. Öppna Registereditorn med kommandot **regedit** på menyn **[!UICONTROL Start > Run]**.
1. Sök efter noden och expandera den.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. Ta bort posten **confAdvisedUpgrade** och stäng Registereditorn.
