---
product: campaign
title: Skapa ett push-meddelande för iOS-enheter
description: Lär dig hur du skapar push-meddelanden för iOS
feature: Push
exl-id: 4520504a-0d9f-4ea7-a5a8-0c07948af4f0
source-git-commit: 8d635722b8961b3edac9cc98f00f17b86f4ee523
workflow-type: tm+mt
source-wordcount: '965'
ht-degree: 6%

---

# Skapa meddelanden för iOS{#create-notifications-ios}

![](../../assets/v7-only.svg)

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

1. Välj **[!UICONTROL Notification type]** mellan **[!UICONTROL General notification (Alert, Sound, Badge)]** eller **[!UICONTROL Silent notification]**.

   ![](assets/nmac_delivery_ios_4.png)

   >[!NOTE]
   >
   >The **Tyst push** I läget kan ett tyst meddelande skickas till ett mobilprogram. Användaren har inte informerats om meddelandets ankomst. Den överförs direkt till programmet.

1. I **[!UICONTROL Title]** anger du etiketten för den titel som du vill ska visas i listan med meddelanden som är tillgängliga från meddelandecentret.

   I det här fältet kan du definiera värdet för **title** -parametern för iOS-meddelandenyttolasten.

1. Du kan lägga till en **[!UICONTROL Subtitle]**, värdet för undertitelparametern för iOS-meddelandenyttolasten. Se [det här avsnittet](configuring-the-mobile-application.md).

1. Ange innehållet i meddelandet i **[!UICONTROL Message content]** i guiden. Användningen av personaliseringsfält beskrivs i [Om personalisering](about-personalization.md) -avsnitt.

   ![](assets/nmac_delivery_ios_5.png)

1. Klicka på **[!UICONTROL Insert emoticon]** om du vill infoga uttryckssymboler i ditt push-meddelande. Information om hur du anpassar uttryckslistan finns i [det här avsnittet](customizing-emoticon-list.md)

1. Från **[!UICONTROL Sound and Badge]** kan du redigera följande alternativ:

   * **[!UICONTROL Clean Badge]**: aktivera det här alternativet för att uppdatera badge-värdet.

   * **[!UICONTROL Value]**: Ange ett tal som ska användas för att visa antalet nya olästa uppgifter direkt på programikonen.

   * **[!UICONTROL Critical alert mode]**: aktivera det här alternativet för att lägga till ljud i meddelandet även om användarens telefon är inställd på fokusläge eller om iPhone är avstängt.

   * **[!UICONTROL Name]**: Välj det ljud som ska spelas upp av mobilterminalen när meddelandet tas emot.

   * **[!UICONTROL Volume]**: ljudvolymen från 0 till 100.
   >[!NOTE]
   >
   >Ljud måste inkluderas i programmet och definieras när tjänsten skapas. Se [det här avsnittet](configuring-the-mobile-application.md#configuring-external-account-ios).

   ![](assets/nmac_delivery_ios_6.png)

1. Från **[!UICONTROL Application variables]** -fliken, **[!UICONTROL Application variables]** läggs till automatiskt. De gör att du kan definiera meddelandebeteende, till exempel kan du konfigurera en specifik programskärm som ska visas när användaren aktiverar meddelandet.

   Mer information om detta finns i [det här avsnittet](configuring-the-mobile-application.md).

1. Från **[!UICONTROL Advanced]** kan du redigera följande allmänna alternativ:

   * **[!UICONTROL Mutable content]**: aktivera det här alternativet om du vill tillåta att mobilprogrammet hämtar medieinnehåll.

   * **[!UICONTROL Thread-id]**: identifierare som används för att gruppera relaterade meddelanden tillsammans.

   * **[!UICONTROL Category]**: namnet på ditt kategori-ID som kommer att visa åtgärdsknappar. Dessa meddelanden ger användaren ett snabbare sätt att utföra olika åtgärder som svar på ett meddelande utan att öppna eller navigera i programmet.

   ![](assets/nmac_delivery_ios_7.png)

1. För tidskänsliga meddelanden kan du ange följande alternativ:

   * **[!UICONTROL Target content ID]**: Identifierare som används för att ange vilket programfönster som ska flyttas fram när meddelandet öppnas.

   * **[!UICONTROL Launch image]**: namnet på startbildfilen som ska visas. Om användaren väljer att starta programmet visas den valda bilden i stället för programmets startskärm.

   * **[!UICONTROL Interruption level]**:

      * **[!UICONTROL Active]**: Som standard visas meddelandet omedelbart, skärmen visas och ett ljud kan spelas upp. Meddelanden går inte igenom fokusläget.

      * **[!UICONTROL Passive]**: Systemet lägger till meddelandet i meddelandelistan utan att skärmen eller ljudet ljussätts upp. Meddelanden går inte igenom fokusläget.

      * **[!UICONTROL Time sensitive]**: Systemet visar meddelandet omedelbart, lyser upp skärmen, kan spela upp ett ljud och gå igenom fokus-lägen. Den här nivån kräver inget särskilt tillstånd från Apple.

      * **[!UICONTROL Critical]**: Systemet visar meddelandet omedelbart, lyser upp skärmen och kringgår avstängningsväxeln eller fokusläget. Observera att den här nivån kräver ett särskilt tillstånd från Apple.
   * **[!UICONTROL Relevance score]**: Ange ett relevansvärde mellan 0 och 100. Systemet använder detta för att sortera meddelandena i meddelandesammanfattningen.

   ![](assets/nmac_delivery_ios_8.png)

1. När meddelandet har konfigurerats klickar du på **[!UICONTROL Preview]** för att förhandsgranska meddelandet.

   ![](assets/nmac_intro_2.png)

   >[!NOTE]
   >
   >Meddelandeformatet (banner eller alert) har inte definierats i Adobe Campaign. Det beror på vilken konfiguration användaren har valt i sina iOS-inställningar. I Adobe Campaign kan du dock förhandsgranska varje typ av meddelandeformat. Klicka på pilen längst ned till höger för att växla från ett format till ett annat.
   >
   >Förhandsgranskningen använder iOS 10-utseendet.

Använd samma process som för e-postleveranser om du vill skicka ett korrektur och den slutliga leveransen. [Läs mer](steps-validating-the-delivery.md)

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

   ![](assets/nmac_ios_6.png)

1. Redigera dina meddelanden.

   ![](assets/nmac_ios_7.png)

1. Från **[!UICONTROL Application variables]** -fliken, **[!UICONTROL Application variables]** läggs till automatiskt beroende på vad som lades till under konfigurationsstegen.

   >[!NOTE]
   >
   >Programvariabler måste definieras i koden för mobilprogrammet och anges när tjänster skapas. Mer information om detta finns i [det här avsnittet](configuring-the-mobile-application.md).

   ![](assets/nmac_ios_10.png)

1. Från **[!UICONTROL Advanced]** -fliken, kontrollera **[!UICONTROL Mutable content]** så att mobilprogrammet kan hämta medieinnehåll.

1. Klicka **[!UICONTROL Save]** och skicka leveransen.

Bilden och webbsidan ska visas i push-meddelandet när de tas emot på prenumerantens mobila iOS-enheter.

![](assets/nmac_ios_8.png)




