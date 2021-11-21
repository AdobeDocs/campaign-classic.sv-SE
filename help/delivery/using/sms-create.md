---
product: campaign
title: Skapa SMS med Campaign
description: Lär dig hur du skapar SMS med Campaign
audience: delivery
content-type: reference
topic-tags: sending-messages-on-mobiles
exl-id: 94aa4628-d973-433d-b963-b078e2d6672b
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 3%

---

# Skapa en SMS-leverans {#creating-a-sms-delivery}

![](../../assets/common.svg)

## Välj leveranskanal {#selecting-the-delivery-channel}

Följ stegen nedan för att skapa en ny SMS-leverans:

>[!NOTE]
>
>Globala koncept för leveransskapande presenteras i [det här avsnittet](steps-about-delivery-creation-steps.md).

1. Skapa en ny leverans, till exempel från kontrollpanelen Leverans.
1. Välj leveransmall **Skickat till mobiler (SMPP)** som du skapade tidigare. Mer information finns i [Ändra leveransmallen](sms-set-up.md#changing-the-delivery-template) -avsnitt.

   ![](assets/s_user_mobile_wizard.png)

1. Identifiera leveransen med en etikett, kod och beskrivning. Mer information om detta finns i [det här avsnittet](steps-create-and-identify-the-delivery.md#identifying-the-delivery).
1. Klicka **[!UICONTROL Continue]** för att bekräfta den här informationen och visa meddelandekonfigurationsfönstret.

## Definiera SMS-innehållet {#defining-the-sms-content}

Följ stegen nedan för att skapa innehållet i SMS:et:

1. Ange innehållet i meddelandet i **[!UICONTROL Text content]** i guiden. Med verktygsfältsknapparna kan du importera, spara och söka i innehåll. Den sista knappen används för att infoga anpassningsfält.

   ![](assets/s_ncs_user_wizard_sms01_138.png)

   Användningen av personaliseringsfält beskrivs i [Om personalisering](about-personalization.md) -avsnitt.

1. Klicka **[!UICONTROL Preview]** längst ned på sidan för att visa återgivningen av meddelandet med dess personalisering. Om du vill starta förhandsgranskningen väljer du en mottagare med **[!UICONTROL Test personalization]** i verktygsfältet. Du kan välja en mottagare bland de definierade målen eller en annan mottagare.

   ![](assets/s_ncs_user_wizard_sms01_139.png)

   Du kan godkänna SMS-meddelandet. Du kan även visa innehållet i SMS-meddelandet på mobiltelefonskärmen till höger om innehållsredigeraren. Klicka på skärmen och använd musen för att bläddra igenom innehållet.

   ![](assets/s_ncs_user_wizard_sms01_140.png)

1. Klicka på **[!UICONTROL Data loaded]** om du vill visa information om mottagaren.

   ![](assets/s_user_mobile_wizard_sms_02.png)

   >[!NOTE]
   >
   >SMS-meddelanden är begränsade till en längd på 160 tecken om den latinska 1-teckentabellen (ISO-8859-1) används. Om meddelandet skrivs i Unicode får det inte innehålla fler än 70 tecken. Vissa specialtecken kan påverka meddelandets längd. Mer information om meddelandets längd finns i [SMS-teckentranskribering](#about-character-transliteration) -avsnitt.
   >
   >När det finns anpassningsfält eller fält för villkorligt innehåll varierar meddelandets storlek från en mottagare till en annan. Meddelandets längd måste utvärderas när personalisering har utförts.
   >
   >När du startar analysen kontrolleras meddelandets längd och en varning visas om det skulle uppstå ett spill.

1. Om du använder NetSize-anslutningen eller en SMPP-anslutning kan du anpassa namnet på leveransavsändaren. Mer information finns i [Avancerade parametrar](#advanced-parameters) -avsnitt.

## Välj målpopulation {#selecting-the-target-population}

Den detaljerade processen när målpopulationen för en leverans väljs presenteras i [det här avsnittet](steps-defining-the-target-population.md).

Mer information om användning av anpassningsfält finns i [det här avsnittet](about-personalization.md).

Mer information om hur du tar med en lista med startvärden finns i [den här sidan](about-seed-addresses.md).
