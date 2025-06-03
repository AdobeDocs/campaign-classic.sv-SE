---
product: campaign
title: Skapa och identifiera leveransen
description: Skapa och identifiera leveransen
feature: Channel Configuration
role: User
hide: true
hidefromtoc: true
exl-id: 6e37bc14-b1a9-42af-8c28-ae4b5bcaa055
source-git-commit: 42cec0e9bede94a2995a5ad442822512bda14f2b
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 5%

---

# Skapa och identifiera leveransen {#create-and-identify-the-delivery}

## Skapa leveransen {#creating-the-delivery}

Du kan skapa en leverans via översikten eller via menyn **[!UICONTROL Create > Delivery]**.


Om du vill skapa en leverans klickar du på **[!UICONTROL Create]** ovanför listan över leveranser. När du skapar en ny leverans måste du ange vilken leveranskanal som används. Det gör du genom att välja lämplig leveransmall i listrutan i fältet **[!UICONTROL Delivery template]**.

![](assets/s_ncs_user_wizard_email01_1.png)

En standardmall tillhandahålls för varje kanal som du har installerat: direktreklam, e-post, fax, telefon, mobilkanal (SMS), Facebook, X (tidigare Twitter) osv.

>[!NOTE]
>
>Vilka kanaler som erbjuds i listan beror på ditt licensavtal.

Du kan skapa nya leveransmallar för att förkonfigurera specifika parametrar så att de passar dina behov. Mer information om mallar finns i [det här avsnittet](about-templates.md).

## Identifiera leveransen {#identifying-the-delivery}

Du måste ange parametrar för att kunna identifiera leveransen. Så här gör du:

1. Ange ett namn för leveransen i fältet **[!UICONTROL Label]**.

   Leveransen kan även tilldelas en leveranskod. Namnet på leveransen och dess kod visas i listan över leveranser, men kan inte ses av mottagarna.

1. Lägg till en beskrivning i fältet **[!UICONTROL Description]**.
1. Välj leveranstyp i det relevanta fältet. Den här informationen är användbar för leveransspårning: du kan filtrera baserat på det här villkoret i leveranslistan eller skapa frågor med det här urvalskriteriet.

   ![](assets/s_ncs_user_email_del_nature.png)

1. Klicka på **[!UICONTROL Continue]** för att bekräfta den här informationen och visa meddelandekonfigurationsfönstret.

Leveransinnehållet kan konfigureras. Definitionen av leveransinnehåll är specifik för varje kanal. Mer information finns i det dedikerade avsnittet:

* [Definiera e-postinnehållet](defining-the-email-content.md)
* [Definiera SMS-innehållet](sms-create.md#defining-the-sms-content)
* [Definiera innehållet i direktmeddelanden](defining-the-direct-mail-content.md)
* [Push-meddelanden](about-mobile-app-channel.md)
