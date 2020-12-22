---
solution: Campaign Classic
product: campaign
title: Om mobilappskanal i Adobe Campaign Classic
description: I det här avsnittet finns allmän information om mobilappskanalen i Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
translation-type: tm+mt
source-git-commit: a9d58e25ab17baaabf4ff8c109b53e83c7d93218
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 5%

---


# Om mobilappskanalen{#about-mobile-app-channel}

>[!CAUTION]
>
>I det här dokumentet beskrivs hur du integrerar mobilapplikationer med Adobe Campaign. Det innehåller ingen information om hur du skapar mobilprogrammet eller hur du konfigurerar det för att hantera meddelanden. Om du vill ha mer information om detta läser du den officiella Apple [dokumentationen](https://developer.apple.com/) och Android [dokumentationen](https://developer.android.com/index.html).

Avsnitten nedan innehåller information som är specifik för mobilappskanalen.

Global information om hur du skapar en leverans finns i [det här avsnittet](../../delivery/using/steps-about-delivery-creation-steps.md).

Med **Mobile App Channel** kan du använda Adobe Campaign-plattformen för att skicka personaliserade meddelanden till iOS- och Android-terminaler via appar. Det finns två leveranskanaler:

* En iOS-kanal som gör att du kan skicka meddelanden till Apple-mobilenheter.

   ![](assets/nmac_intro_2.png)

* En Android-kanal som gör att du kan skicka datameddelanden till mobila Android-enheter.

   ![](assets/nmac_intro_1.png)

Motsvarar dessa två kanaler finns det två leveransaktiviteter i kampanjarbetsflödena:

![](assets/nmac_intro_3.png)

>[!NOTE]
>
>Det finns även två mallar för transaktionsmeddelanden.

Du kan definiera programbeteendet för när användaren aktiverar meddelandet för att visa skärmen som matchar programsammanhanget. Exempel:

* Ett meddelande skickas till kunden för att meddela att deras paket har avslutats. När du aktiverar meddelandet öppnas en sida med leveransrelaterad information.
* Användaren har lagt till artiklar i kundvagnen, men lämnat programmet utan att slutföra köpet. Ett meddelande om att kundvagnen har övergetts skickas. När de aktiverar meddelandet visas objektet på skärmen.

>[!CAUTION]
>
>* Du måste kontrollera att de meddelanden som skickas till ett mobilprogram är kompatibla med de krav och villkor som anges av Apple (Apple Push Notification Service) och Google (Firebase Cloud Messaging).
>* Varning: I vissa länder kräver lagen att du informerar användarna om dina insamlade datatyper för mobilprogram och syftet med deras behandling. Ni måste kontrollera lagstiftningen.


Arbetsflödet för **[!UICONTROL NMAC opt-out management]** (mobileAppOptOutMgt) uppdaterar meddelanden om att prenumerationen har avbrutits på mobila enheter. Mer information om det här arbetsflödet finns i [listan över tekniska arbetsflöden](../../workflow/using/about-technical-workflows.md).

Adobe Campaign är kompatibelt med både binära och HTTP/2 APN:er. Mer information om konfigurationsstegen finns i avsnittet [Konfigurera ett mobilprogram i Adobe Campaign](../../delivery/using/configuring-the-mobile-application.md).

## Datasökväg {#data-path}

I följande scheman beskrivs de steg som gör att mobilprogram kan utbyta data med Adobe Campaign. Denna process inbegriper tre enheter:

* mobilapplikationen
* meddelandetjänsten: APN:er (Apple Push Notification Service) för Apple och FCM (Firebase Cloud Messaging) för Android
* Adobe Campaign

De tre huvudstegen i anmälningsprocessen är: registrering av programmet i Adobe Campaign (prenumerationssamling), leveranser och spårning.

### Steg 1: Prenumerationssamling {#step-1--subscription-collection}

Mobilprogrammet hämtas av användaren från App Store eller Google Play. Det här programmet innehåller anslutningsinställningarna (iOS-certifikat och projektnyckel för Android) och integrationsnyckeln. Första gången programmet öppnas (beroende på konfiguration) kan användaren uppmanas att ange registreringsinformation (@userKey: e-post eller kontonummer (till exempel). Samtidigt skickar programmet frågor till meddelandetjänsten för att samla in ett meddelande-ID (push-ID). All den här informationen (anslutningsinställningar, integrationsnyckel, meddelandeidentifierare, userKey) skickas till Adobe Campaign.

![](assets/nmac_register_view.png)

### Steg 2: Leverans {#step-2--delivery}

Marknadsförarna riktar sig till programprenumeranter. Leveransprocessen skickar anslutningsinställningarna till meddelandetjänsten (iOS-certifikat och projektnyckel för Android), meddelande-ID:t (push-ID) och meddelandets innehåll. Meddelandetjänsten skickar meddelanden till målterminalerna.

Följande information finns i Adobe Campaign:

* Endast Android: antal enheter som har visat meddelandet (avtryck)
* Android och iOS: antal klick i meddelandet

![](assets/nmac_delivery_view.png)

Adobe Campaign-servern måste kunna kontakta APN-servern på följande portar:

* 2195 (sändning) och 2186 (feedbacktjänst) för binär iOS-anslutning
* 443 för iOS HTTP/2-anslutning

   >[!NOTE]
   >
   > Från och med Campaign version 20.3 är den gamla binära kopplingen för iOS inaktuell. Om du använder den här kopplingen måste du anpassa implementeringen i enlighet med detta. [Läs mer](https://helpx.adobe.com/se/campaign/kb/migrate-to-apns-http2.html)

Använd följande kommandon för att kontrollera att den fungerar som den ska:

* För provningar:

   ```
   telnet gateway.sandbox.push.apple.com
   ```

* I produktion:

   ```
   telnet gateway.push.apple.com
   ```

Om en binär iOS-anslutning används måste MTA- och webbservern kunna kontakta APN:er på port 2195 (skicka), arbetsflödesservern måste kunna kontakta APN:er på port 2196 (feedbacktjänst).

Om en iOS HTTP/2-anslutning används måste MTA-, webbservern och arbetsflödesservern kunna kontakta APN:erna på port 443.

