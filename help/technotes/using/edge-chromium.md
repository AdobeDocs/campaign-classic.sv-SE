---
product: campaign
title: Technote - Aktivera Microsoft Edge Chromium i din Campaign-miljö
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

Efter att Microsoft Internet Explorer 11 har upphört att gälla används Edge Chromium i renderingsmotorn HTML för kontrollpaneler i klientkonsolen, med början från Campaign Classic v7.3.

Förutom installationen av Microsoft Edge Webview 2 runtime, som nu är [obligatoriskt för alla klientkonsolinstallationer](../../installation/using/installing-the-client-console.md#webview), måste Microsoft Edge Chromium vara aktiverat på dina instanser.

>[!NOTE]
>
>När du har aktiverat Microsoft Edge Chromium kommer genvägen `Ctrl+F` (Windows) eller `Command+F` (Mac) för att öppna webbläsarens sökdialogruta inte längre att fungera.

## Påverkas du?

Om din miljö har uppgraderats till Campaign Classic v7.3 (eller senare) påverkas du.

## Hur uppdaterar jag?

* Som **värd**-kund har Adobe redan aktiverat Microsoft Edge Chromium på din(a) instans(er). Ingen ytterligare åtgärd krävs.

* Som **lokal/hybridkund** måste du aktivera Microsoft Edge Chromium för dina instanser.

  När du uppgraderar till Campaign Classic v7.3 (och senare) finns ett nytt `webView2Mode`-attribut i konfigurationsfilen för Campaign-servern `serverConf.xml`. Det här attributet måste aktiveras.

  Om du vill göra det utför du följande steg i alla miljöer (MKT, MID, RT):

   1. Redigera konfigurationsfilen för Campaign-servern (`serverConf.xml`)
   1. Ange `webView2Mode = "1"` i modulen `<web>`
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
