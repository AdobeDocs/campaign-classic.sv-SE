---
title: Skicka ett e-postmeddelande med Adobe Campaign Classic
description: Läs mer om de parametrar som är specifika för att leverera e-postmeddelanden i Adobe Campaign Classic.
page-status-flag: never-activated
uuid: 791f7a54-3225-46ca-ad6f-6c32e9c62d75
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-emails
discoiquuid: e2dd8161-fe38-48bf-a288-8ec328b2660e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7c800c20fff89b97f6fa38b3c659ca765765e157

---


# Skicka ett e-postmeddelande{#sending-an-email}

Om du vill godkänna e-postmeddelandet och skicka det till mottagarna av leveransen som skapas klickar du på **[!UICONTROL Send]**.

Den detaljerade processen för att validera och skicka en leverans presenteras i avsnitten nedan:

* [Verifierar leveransen](../../delivery/using/steps-validating-the-delivery.md)
* [Skicka leveransen](../../delivery/using/steps-sending-the-delivery.md)

Avsnitten nedan beskriver de parametrar som är specifika för att leverera e-postmeddelanden.

## Arkivera e-post {#archiving-emails}

Med Adobe Campaign kan ni lagra e-post på ett externt system via BCC genom att bara lägga till en e-postadress för hemlig kopia till ert meddelandemål. När alternativet är aktiverat sparas en exakt kopia av alla skickade meddelanden för den här leveransen.

Mer information om hur du konfigurerar e-postkopia finns i [det här avsnittet](../../installation/using/email-archiving.md).

>[!NOTE]
>
>Den här funktionen är valfri. Kontrollera licensavtalet och kontakta er kontoansvarige för att aktivera det.

När du skapar en ny leverans- eller leveransmall är e-postkopia inte aktiverat som standard, även om alternativet har köpts. Du måste aktivera den manuellt i varje leverans eller mall där du vill använda den.

Gör så här:

1. Gå till **[!UICONTROL Campaign Management]** > **[!UICONTROL Deliveries]** eller **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Delivery templates]**.
1. Välj leveransen eller duplicera den färdiga mallen för **e-postleverans** och välj sedan den duplicerade mallen.
1. Klicka på knappen **Egenskaper** .
1. Klicka på **[!UICONTROL Delivery]** fliken.
1. Markera rutan **Arkivera e-post** om du vill behålla en kopia av alla skickade meddelanden för den här leveransen eller för varje leverans baserat på den här mallen.

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

Skriptet som anges i det här fönstret måste referera till en rubrik per rad i följande formulär: **name:value**.

Värden kodas automatiskt om det behövs.

>[!CAUTION]
>
>Att lägga till ett skript för att infoga ytterligare SMTP-rubriker är reserverat för avancerade användare.
>
>Syntaxen för det här skriptet måste uppfylla kraven för den här innehållstypen: inget oanvänt utrymme, ingen tom rad o.s.v.
