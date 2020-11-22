---
solution: Campaign Classic
product: campaign
title: Skicka ett e-postmeddelande med Adobe Campaign Classic
description: Läs mer om parametrar för e-postleverans
audience: delivery
content-type: reference
topic-tags: sending-emails
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 8%

---


# Skicka ett e-postmeddelande{#sending-an-email}

Om du vill godkänna e-postmeddelandet och skicka det till mottagarna av leveransen som skapas klickar du på **[!UICONTROL Send]**.

Den detaljerade processen för att validera och skicka en leverans presenteras i avsnitten nedan:

* [Verifierar leveransen](../../delivery/using/steps-validating-the-delivery.md)
* [Skicka leveransen](../../delivery/using/steps-sending-the-delivery.md)

Avsnitten nedan beskriver de parametrar som är specifika för att leverera e-postmeddelanden.

## BCC för e-post {#archiving-emails}

Med Adobe Campaign kan du lagra e-postmeddelanden på ett externt system via BCC genom att helt enkelt lägga till en e-postadress för hemlig kopia till meddelandemålet. När alternativet är aktiverat sparas en exakt kopia av alla skickade meddelanden för den här leveransen.

Mer information om konfiguration av BCC för e-post och metodtips finns i [det här avsnittet](../../installation/using/email-archiving.md).

>[!NOTE]
>
>Hemlig kopia via e-post är en valfri funktion. Kontrollera licensavtalet och kontakta eran kontoansvarige om du vill aktivera det.

När du skapar en ny leverans- eller leveransmall är e-postkopia inte aktiverat som standard. Du måste aktivera det manuellt på e-postleveransnivå eller leveransmallnivå.

Följ stegen nedan för att aktivera e-postkopia för en e-postleveransmall:

1. Gå till **[!UICONTROL Campaign Management]** > **[!UICONTROL Deliveries]** eller **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Delivery templates]**.
1. Välj leveransen eller duplicera den färdiga mallen för **e-postleverans** och välj sedan den duplicerade mallen.
1. Click the **Properties** button.
1. Klicka på fliken **[!UICONTROL Delivery]**.  
1. Markera alternativet **E-postkopia** . En kopia av alla skickade meddelanden för varje leverans som baseras på den här mallen skickas till den konfigurerade e-post-BCC-adressen.

   ![](assets/s_ncs_user_wizard_archiving.png)

   >[!NOTE]
   >
   >Om e-postmeddelanden som skickas till BCC-adressen öppnas och klickas igenom, kommer detta att beaktas i **[!UICONTROL Total opens]** och **[!UICONTROL Clicks]** från sändningsanalysen, vilket kan orsaka vissa felberäkningar.

## Generera spegelsidan {#generating-the-mirror-page}

Spegelsidan är en HTML-sida som är tillgänglig online via en webbläsare. Innehållet är identiskt med e-postmeddelandet.

Spegelsidan genereras som standard om länken infogas i postens innehåll. Mer information om infogning av personaliseringsblock finns i [personaliseringsblock](../../delivery/using/personalization-blocks.md).

I leveransegenskaperna kan du ändra genereringsläget för den här sidan med hjälp **[!UICONTROL Mode]** av fältet på **[!UICONTROL Validity]** fliken.

![](assets/s_ncs_user_wizard_miror_page_mode.png)

>[!CAUTION]
>
>Ett HTML-innehåll måste ha definierats för leveransen för den spegelsida som ska skapas.

Förutom standardläget är följande alternativ också tillgängliga:

* **[!UICONTROL Force the generation of the mirror page]** : även om ingen länk till spegelsidan infogas i leveransen, skapas spegelsidan.
* **[!UICONTROL Do not generate the mirror page]** : ingen spegelsida genereras, även om länken finns i leveransen.
* **[!UICONTROL Generates a mirror page accessible using only the message identifier]** : Med det här alternativet kan du komma åt spegelsidans innehåll, med anpassningsinformation, i leveransloggfönstret. Det gör du genom att klicka på **[!UICONTROL Delivery]** fliken efter leveransens slut och markera raden för mottagaren vars spegelsida du vill visa. Klicka på **[!UICONTROL Display the mirror page for this message...]** länken.

   ![](assets/s_ncs_user_wizard_miror_page_link.png)

## Hantera studsmeddelanden {#managing-bounce-emails}

På fliken **[!UICONTROL SMTP]** för leveransparametrarna kan du konfigurera hanteringen av studsmeddelanden.

![](assets/s_ncs_user_email_del_properties_smtp_tab.png)

Som standard tas studsade e-postmeddelanden emot i standardfelrutan för plattformen, men du kan definiera en specifik feladress för en leverans.

Du kan också definiera en specifik adress från den här skärmen för att undersöka orsaken till avhoppsmeddelanden när dessa inte automatiskt kunde kvalificeras av programmet. För vart och ett av dessa fält kan du lägga till personaliseringsparametrar med ikonen Lägg till anpassade fält.

## Teckenkodning {#character-encoding}

På fliken **[!UICONTROL SMTP]** i leveransparametrarna kan du ange en viss kodning i **[!UICONTROL Character encoding]** avsnittet.

Standardkodningen är UTF-8. Om vissa av mottagarnas e-postleverantörer inte har stöd för UTF-8-standardkodning kanske du vill ställa in en specifik kodning så att specialtecknen visas korrekt för mottagarna av e-postmeddelanden.

Du vill till exempel skicka ett e-postmeddelande som innehåller japanska tecken. Om du vill vara säker på att alla tecken visas korrekt för mottagarna i Japan kan du använda en kodning som stöder de japanska tecknen i stället för standard UTF-8.

Det gör du genom att markera **[!UICONTROL Force the encoding used for messages]** alternativet i **[!UICONTROL Character encoding]** avsnittet och välja en kodning i listrutan som visas.

![](assets/s_ncs_user_email_del_properties_smtp_tab_encoding.png)

## Lägga till SMTP-rubriker {#adding-smtp-headers}

Det går att lägga till SMTP-huvuden i leveranserna. Det gör du genom att använda relevanta avsnitt på fliken **[!UICONTROL SMTP]** i leveransen.

The script entered in this window must reference one header per line in the following form: **name:value**.

Värden kodas automatiskt om det behövs.

>[!CAUTION]
>
>Tillägg av ett skript för att infoga ytterligare SMTP-rubriker är reserverat för avancerade användare.
>
>Syntaxen för det här skriptet måste uppfylla kraven för den här innehållstypen: Inget oanvänt utrymme, ingen tom rad, o.s.v.
