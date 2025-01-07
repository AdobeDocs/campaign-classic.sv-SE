---
product: campaign
title: Kom igång med mobilappskanalen
description: Kom igång med mobilappskanalen i Adobe Campaign
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Push
role: User
exl-id: c3b0406f-f652-42f4-ad0d-23fb719cd1b6
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 9%

---

# Kom igång med mobilappskanalen{#about-mobile-app-channel}

Med **mobilappskanalen** kan du använda Adobe Campaign-plattformen för att skicka personaliserade push-meddelanden till iOS- och Android-terminaler via appar.

Det finns två leveranskanaler:

* En iOS-kanal som gör att du kan skicka meddelanden till Apple mobila enheter.

  ![](assets/nmac_intro_2.png)

* En Android-kanal som gör att du kan skicka datameddelanden till Android mobila enheter.

  ![](assets/nmac_intro_1.png)

  >[!IMPORTANT]
  >
  >Vissa viktiga ändringar av tjänsten Android Firebase Cloud Messaging (FCM) kommer att släppas 2024 och kan komma att påverka din Adobe Campaign-implementering. Konfigurationen för prenumerationstjänster för push-meddelanden för Android kan behöva uppdateras för att den här ändringen ska fungera. Du kan redan kontrollera och vidta åtgärder. Läs mer i den här [Adobe Campaign v8-tekniken](https://experienceleague.adobe.com/docs/campaign/technotes-ac/tn-new/push-technote.html?lang=sv){target="_blank"}.

Motsvarar dessa två kanaler finns det två leveransaktiviteter i kampanjarbetsflödena. Det finns även två mallar för transaktionsmeddelanden.

![](assets/nmac_intro_3.png)


Du kan definiera programbeteendet för när användaren aktiverar meddelandet för att visa skärmen som matchar programsammanhanget. Exempel:

* Ett meddelande skickas till kunden för att meddela att deras paket har avslutats. När du aktiverar meddelandet öppnas en sida med leveransrelaterad information.
* Användaren har lagt till artiklar i kundvagnen, men lämnat programmet utan att slutföra köpet. Ett meddelande om att kundvagnen har övergetts skickas. När de aktiverar meddelandet visas objektet på skärmen.

>[!CAUTION]
>
>* Du måste kontrollera att de meddelanden som skickas till ett mobilprogram är kompatibla med de krav och villkor som anges av Apple (Apple Push Notification Service) och Google (Firebase Cloud Messaging).
>* Varning! I vissa länder kräver lagen att du informerar användarna om dina insamlade datatyper för mobilprogram och syftet med deras behandling. Ni måste kontrollera lagstiftningen.

Arbetsflödet **[!UICONTROL NMAC opt-out management]** (mobileAppOptOutMgt) uppdaterar meddelanden om att prenumerationen har avbrutits på mobila enheter. Mer information om det här arbetsflödet finns i [listan över tekniska arbetsflöden](../../workflow/using/about-technical-workflows.md).

Adobe Campaign är kompatibelt med HTTP/2 APN:er. Mer information om konfigurationsstegen finns i avsnittet [this](configuring-the-mobile-application.md).

Global information om hur du skapar en leverans finns i [det här avsnittet](steps-about-delivery-creation-steps.md).


## Konfigurera kanal för push-meddelanden {#push-notification-configuration}

Om du vill skicka push-meddelanden med Adobe Campaign måste du först konfigurera miljön och appen. Innan du börjar skicka push-meddelanden med Adobe Campaign måste du se till att det finns konfigurationer och integreringar på mobilappen och för taggar i Adobe Experience Platform. Adobe Experience Platform Mobile SDK erbjuder API:er för integrering på klientsidan för mobiler via Android och iOS-kompatibla SDK:er. Konfigurationen av SDK:er hanteras via användargränssnittet för datainsamling för flexibel konfiguration och utbyggbara, regelbaserade integreringar. Läs mer i [Adobe Campaign v8-dokumentationen](https://experienceleague.adobe.com/sv/docs/campaign/campaign-v8/send/push/push-settings).


## Datasökväg {#data-path}

I följande scheman beskrivs de steg som gör att mobilprogram kan utbyta data med Adobe Campaign. Den här processen omfattar tre enheter:

* mobilapplikationen
* meddelandetjänsten: APN (Apple Push Notification Service) för Apple och FCM (Firebase Cloud Messaging) för Android
* Adobe Campaign

De tre huvudstegen i meddelandeprocessen är: registrering av programmet i Adobe Campaign (prenumerationssamling), leveranser och spårning.

### Steg 1: Prenumerationssamling {#step-1--subscription-collection}

Mobilprogrammet hämtas av användaren från App Store eller Google Play. Det här programmet innehåller anslutningsinställningarna (iOS-certifikat och projektnyckel för Android) och integrationsnyckeln. Första gången programmet öppnas (beroende på konfiguration) kan användaren uppmanas att ange registreringsinformation (@userKey: exempel på e-post eller kontonummer). Samtidigt skickar programmet frågor till meddelandetjänsten för att samla in ett meddelande-ID (push-ID). All den här informationen (anslutningsinställningar, integrationsnyckel, meddelandeidentifierare, userKey) skickas till Adobe Campaign.

![](assets/nmac_register_view.png)

### Steg 2: Leverans {#step-2--delivery}

Marknadsförarna riktar sig till programprenumeranter. Leveransprocessen skickar anslutningsinställningarna till meddelandetjänsten (iOS-certifikat och projektnyckel för Android), meddelande-ID:t (push-ID) och meddelandets innehåll. Meddelandetjänsten skickar meddelanden till målterminalerna.

Följande information finns i Adobe Campaign:

* Endast Android: antal enheter som har visat meddelandet (visningar)
* Android och iOS: antal klick i meddelandet

![](assets/nmac_delivery_view.png)

Adobe Campaign-servern måste kunna kontakta APN-servern på 443-porten för iOS HTTP/2-anslutningen.

Använd följande kommandon för att kontrollera att den fungerar som den ska:

* För provningar:

  ```
  api.development.push.apple.com:443
  ```

* I produktion:

  ```
  api.push.apple.com:443
  ```

Med iOS HTTP/2-kontakten måste MTA och webbservern kunna kontakta APN på port 443.

Om du behöver använda iOS HTTP/2-anslutningen via en proxy, se [sidan](../../installation/using/file-res-management.md#proxy-connection-configuration).
