---
product: campaign
title: Skapa push-meddelanden
description: Lär dig hur du skapar push-meddelanden
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
exl-id: 13ccc5d6-4355-42ba-80dc-30a45d3b69a4
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '835'
ht-degree: 4%

---

# Skapa meddelanden{#creating-notifications}

I det här avsnittet beskrivs de element som är specifika för leveransen av iOS- och Android-meddelanden. Globala koncept för leveransskapande beskrivs i [det här avsnittet](../../delivery/using/steps-about-delivery-creation-steps.md).

Börja med att skapa en ny leverans.

![](assets/nmac_delivery_1.png)

## Skicka meddelanden på iOS {#sending-notifications-on-ios}

1. Välj leveransmallen **[!UICONTROL Deliver on iOS]**.

   ![](assets/nmac_delivery_ios_1.png)

1. Om du vill definiera målet för meddelandet klickar du på länken **[!UICONTROL To]** och sedan på **[!UICONTROL Add]**.

   ![](assets/nmac_delivery_ios_2.png)

   >[!NOTE]
   >
   >Den detaljerade processen när målpopulationen för en leverans väljs visas i [det här avsnittet](../../delivery/using/steps-defining-the-target-population.md).
   >
   >Mer information om användning av anpassningsfält finns i [Om personalisering](../../delivery/using/about-personalization.md).
   >
   >Mer information om att ta med en startvärdeslista finns i [Om startadresser](../../delivery/using/about-seed-addresses.md).

1. Välj **[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]**, välj den tjänst som är relevant för ditt mobilprogram (Neotrips, i det här fallet) och välj sedan iOS-versionen av programmet.

   ![](assets/nmac_delivery_ios_3.png)

1. Välj meddelandetyp: **[!UICONTROL Alert]**, **[!UICONTROL Badge]**, eller **[!UICONTROL Alert and badge]** eller **[!UICONTROL Silent Push]**.

   ![](assets/nmac_delivery_ios_4.png)

   >[!NOTE]
   >
   >Läget **Tyst push** är tillgängligt från iOS 7. Detta gör att ett tyst meddelande kan skickas till ett mobilprogram. Användaren har inte informerats om meddelandets ankomst. Den överförs direkt till programmet.

1. I fältet **[!UICONTROL Title]** anger du etiketten för titeln som du vill ska visas i meddelandet. Den visas bara i listan över meddelanden som är tillgängliga från meddelandecentret. I det här fältet kan du definiera värdet för parametern **title** för iOS-meddelandenyttolasten.

1. Om du använder HTTP/2-kopplingen kan du lägga till en underrubrik (värdet för parametern **subtitle** för iOS-meddelandenyttolasten). Se avsnittet [Konfigurera mobilprogrammet i Adobe Campaign](../../delivery/using/configuring-the-mobile-application.md).

1. Ange sedan **[!UICONTROL Message]** och **[!UICONTROL Value of the badge]** baserat på den valda meddelandetypen.

   ![](assets/nmac_delivery_ios_5.png)

   >[!NOTE]
   >
   >**[!UICONTROL Badge]** och  **[!UICONTROL Alert and badge]** typmeddelanden gör att du kan ändra värdet på märket (numret ovanför mobilprogrammets logotyp). Om du vill uppdatera märket behöver du bara ange 0 som värde. Om fältet är tomt ändras inte badge-värdet.

1. Klicka på ikonen **[!UICONTROL Insert emoticon]** för att infoga uttryckssymboler i push-meddelandet. Mer information om hur du anpassar uttryckslistan finns i [anpassa uttryckslistan](../../delivery/using/customizing-emoticon-list.md)

1. Med **[!UICONTROL Action button]** kan du definiera en etikett för åtgärdsknappen som visas i varningsmeddelanden (**action_loc_key** fält för nyttolasten). Om ditt iOS-program hanterar lokaliserbara strängar (**Localizable.strings**) anger du motsvarande nyckel i det här fältet. Om programmet inte hanterar lokaliserbar text anger du den etikett som du vill se på åtgärdsknappen. Mer information om översättningsbara strängar finns i [Apple-dokumentationen](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/CreatingtheNotificationPayload.html#//apple_ref/doc/uid/TP40008194-CH10-SW1).
1. I fältet **[!UICONTROL Play a sound]** väljer du det ljud som ska spelas upp av mobilterminalen när meddelandet tas emot.

   >[!NOTE]
   >
   >Ljud måste inkluderas i programmet och definieras när tjänsten skapas. Se [Konfigurera iOS-externt konto](../../delivery/using/configuring-the-mobile-application.md#configuring-external-account-ios).

1. I fältet **[!UICONTROL Application variables]** anger du värdet för varje variabel. Med programvariabler kan du definiera meddelandebeteende: Du kan till exempel konfigurera en specifik programskärm som ska visas när användaren aktiverar meddelandet.

   >[!NOTE]
   >
   >Programvariabler måste definieras i koden för mobilprogrammet och anges när tjänster skapas. Mer information finns i: [Konfigurera ett mobilprogram i Adobe Campaign](../../delivery/using/configuring-the-mobile-application.md).

1. När meddelandet har konfigurerats klickar du på fliken **[!UICONTROL Preview]** för att förhandsgranska meddelandet.

   ![](assets/nmac_intro_2.png)

   >[!NOTE]
   >
   >Meddelandeformatet (banner eller alert) har inte definierats i Adobe Campaign. Det beror på vilken konfiguration användaren har valt i sina iOS-inställningar. I Adobe Campaign kan du dock förhandsgranska varje typ av meddelandeformat. Klicka på pilen längst ned till höger för att växla från ett format till ett annat.
   >
   >Förhandsgranskningen använder iOS 10-utseendet.

Använd samma process som för e-postleveranser om du vill skicka ett korrektur och den slutliga leveransen.

När du har skickat meddelanden kan du övervaka och spåra dina leveranser. Mer information om detta hittar du i dessa avsnitt.

* [Kantlinjer för push-meddelanden](../../delivery/using/understanding-quarantine-management.md#push-notification-quarantines)
* [Övervaka en leverans](../../delivery/using/about-delivery-monitoring.md)
* [Om leveransfel](../../delivery/using/understanding-delivery-failures.md)

## Skicka meddelanden på Android {#sending-notifications-on-android}

1. Börja med att välja leveransmallen **[!UICONTROL Deliver on Android (android)]**.

   ![](assets/nmac_delivery_android_1.png)

1. Om du vill definiera målet för meddelandet klickar du på länken **[!UICONTROL To]** och sedan på **[!UICONTROL Add]**.

   ![](assets/nmac_delivery_android_2.png)

1. Välj **[!UICONTROL Subscribers of an Android mobile application]**, välj den tjänst som är relevant för ditt mobilprogram (Neotrips, i det här fallet) och välj sedan Android-versionen av programmet.

   ![](assets/nmac_delivery_android_3.png)

1. Ange sedan innehållet för meddelandet.

   ![](assets/nmac_delivery_android_4.png)

1. Klicka på ikonen **[!UICONTROL Insert emoticon]** för att infoga uttryckssymboler i push-meddelandet. Mer information om hur du anpassar uttryckslistan finns i [anpassa uttryckslistan](../../delivery/using/defining-interactive-content.md)

1. I fältet **[!UICONTROL Application variables]** anger du värdet för varje variabel. Med programvariabler kan du definiera meddelandebeteende: Du kan till exempel konfigurera en specifik programskärm som ska visas när användaren aktiverar meddelandet.

   >[!NOTE]
   >
   >Programvariabler måste definieras i koden för mobilprogrammet och anges när tjänster skapas. Mer information finns i: [Konfigurera ett mobilprogram i Adobe Campaign](../../delivery/using/configuring-the-mobile-application.md).

1. När meddelandet har konfigurerats klickar du på fliken **[!UICONTROL Preview]** för att förhandsgranska meddelandet.

   ![](assets/nmac_intro_1.png)

Använd samma process som för e-postleveranser om du vill skicka ett korrektur och den slutliga leveransen.

Den detaljerade processen för att validera och skicka en leverans presenteras i avsnitten nedan:

* [Verifierar leveransen](../../delivery/using/steps-validating-the-delivery.md)
* [Skicka leveransen](../../delivery/using/steps-sending-the-delivery.md)

När du har skickat meddelanden kan du övervaka och spåra dina leveranser. Mer information om detta hittar du i dessa avsnitt.

* [Kantlinjer för push-meddelanden](../../delivery/using/understanding-quarantine-management.md#push-notification-quarantines)
* [Övervaka en leverans](../../delivery/using/about-delivery-monitoring.md)
* [Om leveransfel](../../delivery/using/understanding-delivery-failures.md)
