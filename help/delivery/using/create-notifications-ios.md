---
product: campaign
title: Skapa ett push-meddelande för iOS-enheter
description: Lär dig hur du skapar push-meddelanden för iOS
feature: Push
exl-id: 4520504a-0d9f-4ea7-a5a8-0c07948af4f0
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 3%

---

# Skapa meddelanden för iOS{#create-notifications-ios}

![](../../assets/common.svg)

I det här avsnittet beskrivs de element som är specifika för leveransen av iOS-meddelanden. Globala koncept för leveransskapande presenteras i [det här avsnittet](steps-about-delivery-creation-steps.md).

Börja med att skapa en ny leverans.

![](assets/nmac_delivery_1.png)

Följ stegen nedan för att skapa ett push-meddelande för iOS-enheter:

1. Välj **[!UICONTROL Deliver on iOS]** leveransmall.

   ![](assets/nmac_delivery_ios_1.png)

1. Om du vill definiera målet för meddelandet klickar du på knappen **[!UICONTROL To]** klicka på **[!UICONTROL Add]**.

   ![](assets/nmac_delivery_ios_2.png)

   >[!NOTE]
   >
   >Den detaljerade processen när målpopulationen för en leverans väljs presenteras i [det här avsnittet](steps-defining-the-target-population.md).
   >
   >Mer information om användning av anpassningsfält finns i [det här avsnittet](about-personalization.md).
   >
   >Mer information om hur du tar med en lista med startvärden finns i [Om dirigeringsadresser](about-seed-addresses.md).

1. Välj **[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]** väljer du den tjänst som är relevant för ditt mobilprogram (i det här fallet Neotrips) och väljer sedan iOS-versionen av programmet.

   ![](assets/nmac_delivery_ios_3.png)

1. Välj meddelandetyp: **[!UICONTROL Alert]**, **[!UICONTROL Badge]**, eller **[!UICONTROL Alert and badge]** eller **[!UICONTROL Silent Push]**.

   ![](assets/nmac_delivery_ios_4.png)

   >[!NOTE]
   >
   >The **Tyst push** I läget kan ett tyst meddelande skickas till ett mobilprogram. Användaren har inte informerats om meddelandets ankomst. Den överförs direkt till programmet.

1. I **[!UICONTROL Title]** anger du etiketten för den titel som du vill ska visas i meddelandet. Den visas bara i listan över meddelanden som är tillgängliga från meddelandecentret. I det här fältet kan du definiera värdet för **title** -parametern för iOS-meddelandenyttolasten.

1. Om du använder HTTP/2-kopplingen kan du lägga till en underrubrik (värdet för **underrubrik** -parameter för iOS-meddelandenyttolast). Se [det här avsnittet](configuring-the-mobile-application.md).

1. Ange sedan **[!UICONTROL Message]** och **[!UICONTROL Value of the badge]** baserat på den valda meddelandetypen.

   ![](assets/nmac_delivery_ios_5.png)

   >[!NOTE]
   >
   >**[!UICONTROL Badge]** och **[!UICONTROL Alert and badge]** typmeddelanden gör att du kan ändra värdet på märket (numret ovanför mobilprogrammets logotyp). Om du vill uppdatera märket behöver du bara ange 0 som värde. Om fältet är tomt ändras inte badge-värdet.

1. Klicka på **[!UICONTROL Insert emoticon]** om du vill infoga uttryckssymboler i ditt push-meddelande. Information om hur du anpassar uttryckslistan finns i [det här avsnittet](customizing-emoticon-list.md)

1. The **[!UICONTROL Action button]** gör att du kan definiera en etikett för åtgärdsknappen som visas i varningsmeddelanden (**action_loc_key** nyttolastens fält). Om ditt iOS-program hanterar lokaliserbara strängar (**Localizable.strings**) anger du motsvarande nyckel i det här fältet. Om programmet inte hanterar lokaliserbar text anger du den etikett som du vill se på åtgärdsknappen. Mer information om översättningsbara strängar finns i [Apple-dokumentation](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/CreatingtheNotificationPayload.html#//apple_ref/doc/uid/TP40008194-CH10-SW1) .
1. I **[!UICONTROL Play a sound]** markerar du det ljud som ska spelas upp av mobilterminalen när meddelandet tas emot.

   >[!NOTE]
   >
   >Ljud måste inkluderas i programmet och definieras när tjänsten skapas. Se [det här avsnittet](configuring-the-mobile-application.md#configuring-external-account-ios).

1. I **[!UICONTROL Application variables]** anger du värdet för varje variabel. Med programvariabler kan du definiera meddelandebeteende: Du kan till exempel konfigurera en specifik programskärm som ska visas när användaren aktiverar meddelandet.

   >[!NOTE]
   >
   >Programvariabler måste definieras i koden för mobilprogrammet och anges när tjänster skapas. Mer information om detta finns i [det här avsnittet](configuring-the-mobile-application.md).

1. När meddelandet har konfigurerats klickar du på **[!UICONTROL Preview]** för att förhandsgranska meddelandet.

   ![](assets/nmac_intro_2.png)

   >[!NOTE]
   >
   >Meddelandeformatet (banner eller alert) har inte definierats i Adobe Campaign. Det beror på vilken konfiguration användaren har valt i sina iOS-inställningar. I Adobe Campaign kan du dock förhandsgranska varje typ av meddelandeformat. Klicka på pilen längst ned till höger för att växla från ett format till ett annat.
   >
   >Förhandsgranskningen använder iOS 10-utseendet.

Använd samma process som för e-postleveranser om du vill skicka ett korrektur och den slutliga leveransen.

När du har skickat meddelanden kan du övervaka och spåra dina leveranser. Mer information om detta hittar du i dessa avsnitt.

* [Kantlinjer för push-meddelanden](understanding-quarantine-management.md#push-notification-quarantines)
* [Övervaka en leverans](about-delivery-monitoring.md)
* [Förstå leveransfel](understanding-delivery-failures.md)


## Skapa ett iOS-meddelande {#creating-ios-delivery}

Med iOS 10 eller senare är det möjligt att generera omfattande meddelanden. Adobe Campaign kan skicka meddelanden med variabler som gör att enheten kan visa ett omfattande meddelande.

Nu måste du skapa en ny leverans och länka den till mobilappen som du har skapat.

1. Gå till **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. Klicka på **[!UICONTROL New]**.

   ![](assets/nmac_android_3.png)

1. Välj **[!UICONTROL Deliver on iOS (ios)]** i **[!UICONTROL Delivery template]** nedrullningsbar meny. Lägg till en **[!UICONTROL Label]** till leveransen.

1. Klicka **[!UICONTROL To]** för att definiera målpopulationen. Som standard är **[!UICONTROL Subscriber application]** målmappning används. Klicka **[!UICONTROL Add]** om du vill välja en tjänst som vi skapat tidigare.

   ![](assets/nmac_ios_9.png)

1. I **[!UICONTROL Target type]** fönster, markera **[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]** och klicka **[!UICONTROL Next]**.

1. I **[!UICONTROL Service]** väljer du en tjänst som du har skapat tidigare, det program du vill ha som mål och klickar på **[!UICONTROL Finish]**.
The **[!UICONTROL Application variables]** läggs till automatiskt beroende på vad som lades till under konfigurationsstegen.

   ![](assets/nmac_ios_6.png)

1. Redigera dina meddelanden.

   ![](assets/nmac_ios_7.png)

1. Kontrollera **[!UICONTROL Mutable content]** i fönstret för redigeringsmeddelanden så att mobilprogrammet kan hämta medieinnehåll.

1. Klicka **[!UICONTROL Save]** och skicka leveransen.

Bilden och webbsidan ska visas i push-meddelandet när de tas emot på prenumerantens mobila iOS-enheter.

![](assets/nmac_ios_8.png)
