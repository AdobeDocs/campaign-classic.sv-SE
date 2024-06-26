---
product: campaign
title: TechNote - Aktivera Microsoft Edge Chromium i kampanjmiljön
description: Campaign - Edge Chromium
feature: Technote, Upgrade
exl-id: 22f4cbaf-ca37-47b9-b7dd-1ee73d5b348d
source-git-commit: 8734e6ef26a7342042a5242d54854b7d3a5e6244
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 5%

---

# Så här aktiverar du Microsoft Edge Chromium i din miljö {#edge-conf}

## Vad har ändrats?

Efter att Microsoft Internet Explorer 11 har upphört att gälla använder återgivningsmotorn HTML för kontrollpaneler i klientkonsolen Edge Chromium, med början från Campaign Classic v7.3.

Förutom installationen av Microsoft Edge Webview 2 runtime, som nu [krävs för installation av klientkonsolen](../../installation/using/installing-the-client-console.md#webview)måste Microsoft Edge Chromium vara aktiverat på dina instanser.

>[!NOTE]
>
>När du har aktiverat Microsoft Edge Chromium `Ctrl+F` (Windows) eller `Command+F` (Mac) genvägen för att öppna webbläsarens sökdialogruta fungerar inte längre.

## Påverkas du?

Om din miljö har uppgraderats till Campaign Classic v7.3 (eller senare) påverkas du.

## Hur uppdaterar jag?

* Som en **värdbaserad** Adobe har redan aktiverat Microsoft Edge Chromium på dina instanser. Ingen ytterligare åtgärd krävs.

* Som en **lokal/hybrid** -kund måste du aktivera Microsoft Edge Chromium för dina instanser.

  Vid uppgradering till Campaign Classic v7.3 (och senare) finns en ny `webView2Mode` attributet är tillgängligt i konfigurationsfilen för Campaign-servern `serverConf.xml`. Det här attributet måste aktiveras.

  Om du vill göra det utför du följande steg i alla miljöer (MKT, MID, RT):

   1. Redigera konfigurationsfilen för Campaign-servern (`serverConf.xml`)
   1. I `<web>` modul, ange `webView2Mode = "1"`
   1. Kör följande kommando för att läsa in serverkonfigurationen igen:

      ```
      nlserver config -reload
      ```

   1. Kör följande kommando för att starta om webbservern:

      ```
      nlserver restart web
      ```

   1. Om din miljö använder Apache som webbserver kör du följande kommando för att starta om Apache:

      ```
      /etc/init.d/apache2 restart
      ```


>[!NOTE]
>
>Om du har frågor om de här ändringarna kan du kontakta [Adobes kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).
>

## Relaterade ämnen

* [Uppgradera din miljö](../../production/using/build-upgrade.md)
* [Vanliga frågor och svar om builduppgradering](../../platform/using/faq-build-upgrade.md)
* [Installera Campaign Client Console](../../installation/using/installing-the-client-console.md)
