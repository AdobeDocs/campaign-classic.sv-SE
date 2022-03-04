---
product: campaign
title: Skapa och identifiera leveransen
description: Skapa och identifiera leveransen
feature: Channel Configuration
exl-id: 6e37bc14-b1a9-42af-8c28-ae4b5bcaa055
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 6%

---

# Skapa och identifiera leveransen {#create-and-identify-the-delivery}

![](../../assets/common.svg)

## Skapa leveransen {#creating-the-delivery}

Du kan skapa en leverans via översikten eller via **[!UICONTROL Create > Delivery]** -menyn.


Om du vill skapa en leverans klickar du på **[!UICONTROL Create]** ovanför listan över leveranser. När du skapar en ny leverans måste du ange vilken leveranskanal som används. Det gör du genom att välja lämplig leveransmall i listrutan i dialogrutan **[!UICONTROL Delivery template]** fält.

![](assets/s_ncs_user_wizard_email01_1.png)

En standardmall finns för varje kanal som du har installerat: direktreklam, e-post, fax, telefon, mobilkanal (SMS), Facebook, Twitter osv.

>[!NOTE]
>
>Vilka kanaler som erbjuds i listan beror på ditt licensavtal.

Du kan skapa nya leveransmallar för att förkonfigurera specifika parametrar så att de passar dina behov. Mer information om mallar finns i [det här avsnittet](about-templates.md).

## Identifiera leveransen {#identifying-the-delivery}

Du måste ange parametrar för att kunna identifiera leveransen. Så här gör du:

1. Ange ett namn för leveransen i dialogrutan **[!UICONTROL Label]** fält.

   Leveransen kan även tilldelas en leveranskod. Namnet på leveransen och dess kod visas i listan över leveranser, men kan inte ses av mottagarna.

1. Lägg till en beskrivning i **[!UICONTROL Description]** fält.
1. Välj leveranstyp i det relevanta fältet. Den här informationen är användbar för leveransspårning: Du kan filtrera baserat på det här kriteriet i leveranslistan eller skapa frågor med det här urvalskriteriet.

   ![](assets/s_ncs_user_email_del_nature.png)

1. Klicka **[!UICONTROL Continue]** för att bekräfta den här informationen och visa meddelandekonfigurationsfönstret.

Leveransinnehållet är klart att konfigureras. Definitionen av leveransinnehåll är specifik för varje kanal. Mer information finns i det dedikerade avsnittet:

* [Definiera e-postinnehållet](defining-the-email-content.md)
* [Definiera SMS-innehållet](sms-create.md#defining-the-sms-content)
* [Definiera innehållet i direktmeddelanden](defining-the-direct-mail-content.md)
* [Push-meddelanden](about-mobile-app-channel.md)
