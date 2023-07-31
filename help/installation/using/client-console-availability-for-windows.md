---
product: campaign
title: Klientkonsolens tillgänglighet i Windows
description: Klientkonsolens tillgänglighet i Windows
feature: Installation, Upgrade
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
badge-v7-prem: label="lokal och hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 57845eae-1f1a-42f4-b2ba-46d454677ae0
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 7%

---

# Klientkonsolens tillgänglighet i Windows{#client-console-availability-for-windows}



För att Adobe Campaign-användare ska kunna logga in på den instans som du har skapat och konfigurerat måste de använda klientkonsolen.

## Gör klientkonsolen tillgänglig

När datorn använde för att starta en Adobe Campaign-programserver (**nlserver web**) tar emot användaranslutningar från klientkonsolen och konfigurerar den så att installationsprogrammet för Adobe Campaign-klienten blir tillgängligt via ett HTML-gränssnitt. När det finns en ny version av klientkonsolen får användarna en inbjudan om att ladda ned den när de startar klientkonsolen.

För att göra detta måste du:

1. Välj det paket som innehåller installationsprogrammet för konsolen.

   Filen anropas `setup-client-7.X.XXXX.exe`, där `X` är en underversion av Adobe Campaign och `XXXX` är build-numret.

1. Kopiera och klistra in det här paketet i Adobe Campaign installationsmapp (på marknadsföringsservern för hybridinstallationer), under **/datakit/nl/eng/jsp**.
1. Starta Adobe Campaign-servern.

Kampanjanvändare kan sedan hämta konsolinstallationsprogrammet via en webbläsare tack vare följande URL:

```
https://<your Adobe Campaign server>:>port number>/nl/jsp/logon.jsp
```

Den här sidan kräver inloggning och lösenord som definierats i programmet.

Lär dig installera konsolen [i det här avsnittet](../../installation/using/installing-the-client-console.md).

## Föreslå att slutanvändare uppgraderar sin klientkonsol

När konsolen är tillgänglig i Campaign-servermappen bjuds användarna in att hämta den senaste klientkonsolversionen i ett dedikerat fönster. Adobe rekommenderar att du låter alternativet vara kvar **[!UICONTROL No longer ask this question]** avmarkerat för att se till att alla användare får en varning när en ny version av konsolen är tillgänglig.

Om du väljer det här alternativet och väljer att inte hämta den senaste versionen informeras ingen annan användare om nya tillgängliga versioner.

Om alternativet har valts kan du återställa den här uppmaningen. Det är bara systemadministratörer som kan redigera Windows-registret som kan göra följande ändringar:

1. Öppna Registereditorn med **regedit** från **[!UICONTROL Start > Run]** -menyn.
1. Sök efter noden och expandera den.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. Ta bort **confAdvisedUpgrade** och stäng Registereditorn.
