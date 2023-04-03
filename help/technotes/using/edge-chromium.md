---
product: campaign
title: TechNote - Aktivera Microsoft Edge Chromium i kampanjmiljön
description: Campaign - Edge Chromium
hide: true
hidefromtoc: true
source-git-commit: d883db444ef7cc243241833b86e8b946454e5d2a
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 12%

---


# Så här aktiverar du Microsoft Edge Chromium i din miljö {#edge-conf}

![](../../assets/v7-only.svg)


## Vad har ändrats?

Efter att Microsoft Internet Explorer 11 har upphört att gälla använder återgivningsmotorn HTML för kontrollpaneler i klientkonsolen Edge Chromium från och med Campaign Classic v7.3.

Förutom installationen av Microsoft Edge Webview 2, som nu [krävs för installation av klientkonsolen](../../installation/using/installing-the-client-console.md#webview)måste Microsoft Edge Chromium vara aktiverat på dina instanser.

## Påverkas du?

Om din miljö har uppgraderats till Campaign Classic v7.3 (eller senare) påverkas du.

## Hur uppdaterar jag?

* Som **värdbaserad** Adobe har redan aktiverat Microsoft Edge Chromium på dina instanser. Ingen ytterligare åtgärd krävs.

* Som en **lokal/hybrid** -kund måste du aktivera Microsoft Edge Chromium på dina instanser.

   Vid uppgradering till Campaign Classic v7.3 (och senare) finns en ny `webView2Mode` attributet är tillgängligt i konfigurationsfilen för Campaign-servern `serverConf.xml`. Det här attributet måste aktiveras.

   Om du vill göra det utför du följande steg i alla miljöer (MKT, MID, RT):

   1. Redigera konfigurationsfilen för Campaign-servern (`serverConf.xml`)
   1. I `<web>` modul, ange `webView2Mode = "1"`
   1. Läs in serverkonfigurationen igen

      ```
      nlserver config -reload
      ```

   1. Starta om webbservern

      ```
      nlserver restart web
      ```

   1. Om miljön körs på Apache startar du om Apache

      ```
      /etc/init.d/apache2 restart
      ```


>[!NOTE]
>
>Om du har frågor om de här ändringarna kan du kontakta [Adobes kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Relaterade ämnen

* [Uppgradera din miljö](../../production/using/build-upgrade.md)
* [Vanliga frågor och svar om builduppgradering](../../platform/using/faq-build-upgrade.md)
* [Installera Campaign Client Console](../../installation/using/installing-the-client-console.md)

