---
product: campaign
title: E-postparametrar
description: Läs mer om alternativ och inställningar som är specifika för e-postleverans
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Email
role: User, Developer, Data Engineer
exl-id: 1bb36e71-9f1a-4553-b266-eca3f48688e2
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '912'
ht-degree: 7%

---

# E-postparametrar {#email-parameters}

I det här avsnittet visas alternativ och parametrar som är specifika för e-postleverans.

## BCC för e-post {#email-bcc}

Med Adobe Campaign kan du lagra e-postmeddelanden på ett externt system via BCC genom att helt enkelt lägga till en e-postadress för hemlig kopia till meddelandemålet.

När alternativet är aktiverat sparas en exakt kopia av alla skickade meddelanden för den här leveransen.

Mer information om konfiguration av BCC för e-post och metodtips finns i [det här avsnittet](../../installation/using/email-archiving.md).

>[!NOTE]
>
>Hemlig kopia via e-post är en valfri funktion. Kontrollera licensavtalet och kontakta eran kontoansvarige om du vill aktivera det.

När du skapar en ny leverans- eller leveransmall är e-postkopia inte aktiverat som standard. Du måste aktivera det manuellt på e-postleveransnivå eller leveransmallnivå.

>[!NOTE]
>
>Om du använder e-postkopia med förbättrad MTA aktiveras det här alternativet automatiskt för alla leveranser.

Följ stegen nedan för att aktivera e-postkopia för en e-postleveransmall:

1. Gå till **[!UICONTROL Campaign Management]** > **[!UICONTROL Deliveries]** eller **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Delivery templates]**.
1. Välj leveransalternativ eller duplicera den färdiga mallen **E-postleverans** och välj sedan den duplicerade mallen.
1. Klicka på knappen **Egenskaper** .
1. Klicka på fliken **[!UICONTROL Delivery]**.  
1. Markera alternativet **BCC för e-post**. En kopia av alla skickade meddelanden för varje leverans som baseras på den här mallen skickas till den konfigurerade e-post-BCC-adressen.

   ![](assets/s_ncs_user_wizard_archiving.png)

>[!NOTE]
>
>Om e-postmeddelanden som skickas till BCC-adressen öppnas och klickas igenom, kommer detta att beaktas i **[!UICONTROL Total opens]** och **[!UICONTROL Clicks]** från sändningsanalysen, vilket kan orsaka några felberäkningar.

## Välja meddelandeformat {#selecting-message-formats}

Du kan ändra formatet för skickade e-postmeddelanden. Om du vill göra det redigerar du leveransegenskaperna och klickar på fliken **[!UICONTROL Delivery]**.

![](assets/s_ncs_user_wizard_email_param.png)

Välj formatet för e-postmeddelandet i fönstrets nedre del:

* **[!UICONTROL Use recipient preferences]** (standardläge)

  Meddelandeformatet definieras enligt data som lagras i mottagarprofilen och lagras som standard i fältet **[!UICONTROL email format]** (@emailFormat). Om en mottagare vill ta emot meddelanden i ett visst format är detta det format som skickas. Om fältet inte är ifyllt skickas ett multipart-alternativt meddelande (se nedan).

* **[!UICONTROL Let recipient mail client choose the most appropriate format]**

  Meddelandet innehåller båda formaten: text och HTML. Formatet som visas vid mottagning beror på konfigurationen av mottagarens e-postprogramvara (multipart-option).

  >[!IMPORTANT]
  >
  >Det här alternativet inkluderar båda versionerna av dokumentet. Det påverkar därför leveransgraden eftersom meddelandestorleken är större.

* **[!UICONTROL Send all messages in text format]**

  Meddelandet skickas i textformat. Formatet HTML skickas inte, utan används endast för spegelsidan när mottagaren klickar på meddelandet.

>[!NOTE]
>
>Mer information om hur du definierar e-postinnehållet finns i [det här avsnittet](defining-the-email-content.md).

## Generera spegelsidan {#generating-mirror-page}

Spegelsidan är en HTML-sida som är tillgänglig online via en webbläsare. Innehållet är identiskt med e-postmeddelandet.

Spegelsidan genereras som standard om länken infogas i postens innehåll. Mer information om infogning av anpassningsblock finns i [Personaliseringsblock](personalization-blocks.md).

I leveransegenskaperna kan du ändra genereringsläget för den här sidan med fältet **[!UICONTROL Mode]** på fliken **[!UICONTROL Validity]**.

![](assets/s_ncs_user_wizard_miror_page_mode.png)

>[!IMPORTANT]
>
>Ett HTML-innehåll måste ha definierats för leveransen för den spegelsida som ska skapas.

Förutom standardläget är följande alternativ också tillgängliga:

* **[!UICONTROL Force the generation of the mirror page]**: även om ingen länk till spegelsidan har infogats i leveransen skapas spegelsidan.
* **[!UICONTROL Do not generate the mirror page]**: ingen spegelsida genereras, även om länken finns i leveransen.
* **[!UICONTROL Generates a mirror page accessible using only the message identifier]**: Med det här alternativet kan du komma åt spegelsidans innehåll, med anpassningsinformation, i leveransloggfönstret. Det gör du genom att klicka på fliken **[!UICONTROL Delivery]** efter leveransens slut och markera raden för mottagaren vars spegelsida du vill visa. Klicka på länken **[!UICONTROL Display the mirror page for this message...]**.

  ![](assets/s_ncs_user_wizard_miror_page_link.png)

## Teckenkodning {#character-encoding}

På fliken **[!UICONTROL SMTP]** i leveransparametrarna kan du ange en specifik kodning i avsnittet **[!UICONTROL Character encoding]**.

Standardkodningen är UTF-8. Om vissa av mottagarnas e-postleverantörer inte har stöd för UTF-8-standardkodning kanske du vill ställa in en specifik kodning så att specialtecknen visas korrekt för mottagarna av e-postmeddelanden.

Du vill till exempel skicka ett e-postmeddelande som innehåller japanska tecken. Om du vill vara säker på att alla tecken visas korrekt för mottagarna i Japan kan du använda en kodning som stöder de japanska tecknen i stället för standard UTF-8.

Det gör du genom att välja alternativet **[!UICONTROL Force the encoding used for messages]** i avsnittet **[!UICONTROL Character encoding]** och välja en kodning i listrutan som visas.

![](assets/s_ncs_user_email_del_properties_smtp_tab_encoding.png)

## Hantera studsmeddelanden {#managing-bounce-emails}

På fliken **[!UICONTROL SMTP]** i leveransparametrarna kan du konfigurera hanteringen av studsmeddelanden.

Som standard tas studsade e-postmeddelanden emot i standardfelrutan [för plattformen](../../installation/using/deploying-an-instance.md#parameters-for-delivered-emails-parameters-for-delivered-emails), men du kan definiera en specifik feladress för en leverans.

Du kan också definiera en specifik adress från den här skärmen för att undersöka orsaken till avhoppsmeddelanden när dessa inte automatiskt kunde kvalificeras av programmet. För vart och ett av dessa fält kan du lägga till personaliseringsparametrar med ikonen **Lägg till anpassade fält** .

![](assets/s_ncs_user_email_del_properties_smtp_tab.png)

Mer information om hantering av studsade e-postmeddelanden finns i [det här avsnittet](understanding-delivery-failures.md#bounce-mail-management).

## Lägga till SMTP-rubriker {#adding-smtp-headers}

Det går att lägga till SMTP-huvuden i leveranserna. Det gör du genom att använda relevant avsnitt på fliken **[!UICONTROL SMTP]** i leveransen.

Skriptet som anges i det här fönstret måste referera till en rubrik per rad i följande format: **name:value**.

Värden kodas automatiskt om det behövs.

>[!IMPORTANT]
>
>Att lägga till ett skript för att infoga ytterligare SMTP-rubriker är reserverat för avancerade användare.
>
>Syntaxen för det här skriptet måste uppfylla kraven för den här innehållstypen: Inget oanvänt utrymme, ingen tom rad, o.s.v.
