---
title: Anpassa uttryckslistan
description: Lär dig hur du anpassar uttryckslistan när du använder Adobe Campaign Classic.
page-status-flag: never-activated
uuid: ddcc2e3b-e251-4a7a-a22a-28701522839f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-emails
discoiquuid: 2ea2747f-957f-41a9-a03f-20c03fa99116
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 3beb62d0264cfcb03486c291ce79cc7ff582e9c7
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---


# Anpassa uttryckslistan {#customize-emoticons}

Uttryckslistan som visas i popup-fönstret styrs av en uppräkning som gör att du kan visa värden i en lista för att begränsa vilka val användaren har för ett visst fält.
Ordningen på uttryckslistan kan anpassas. Du kan också lägga till andra uttryckssymboler i listan.
Det finns uttryckssymboler som du kan skicka via e-post och som du kan trycka på om du vill ha mer information om den här [sidan](../../delivery/using/defining-the-email-content.md#inserting-emoticons).

## Lägga till en ny uttryckssymbol {#add-new-emoticon}

>[!CAUTION]
>
>Uttryckssymbollistan får inte innehålla fler än 81 poster.

1. Välj den nya uttryckssymbol du vill lägga till på den här [sidan](https://unicode.org/emoji/charts/full-emoji-list.html). Observera att det måste vara kompatibelt med olika plattformar som webbläsare och operativsystem.

1. I **[!UICONTROL Explorer]** väljer du **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Enumerations]** och klickar på uppräkningen **[!UICONTROL Emoticon list]** som är klar.

   >[!NOTE]
   >
   >Enkla uppräkningar kan bara hanteras av en administratör för Adobe Campaign Classic-konsolen.

   ![](assets/emoticon_1.png)

1. Klicka på **[!UICONTROL Add]**.

1. Fyll i fälten:

   * **[!UICONTROL U+]**: Kod för din nya uttryckssymbol. Du hittar listan med uttryckssymbolkoder på den här [sidan](https://unicode.org/emoji/charts/full-emoji-list.html).
För att undvika kompatibilitetsproblem rekommenderar vi att du väljer uttryckssymboler som stöds i webbläsare och i alla operativsystem.

   * **[!UICONTROL Label]**: Etikett på din nya uttryckssymbol.
   ![](assets/emoticon_5.png)

1. Klicka **[!UICONTROL Ok]** sedan **[!UICONTROL Save]** när konfigurationen är klar.
Din nya uttryckssymbol placeras automatiskt i butiken.

1. Om du vill visa den i leveransfönstret väljer du den nya uttryckssymbolen genom att dubbelklicka på den. **[!UICONTROL Insert emoticon]**

1. Välj i **[!UICONTROL Display order]** listrutan i vilken ordning din nya uttryckssymbol ska visas. Observera att om du väljer en redan tilldelad visningsordning flyttas den befintliga uttryckssymbolen automatiskt till butiken.

   <br>I det här exemplet har vi valt visningsordernummer 61, vilket innebär att om en post redan har den här beställningen flyttas den automatiskt till butiken och den nya posten får plats i uppräkningslistan.

   ![](assets/emoticon_2.png)

1. Din nya uttryckssymbol har nu lagts till i uppräkningen som är **[!UICONTROL Insert emoticon list]** färdig. Du kan när som **[!UICONTROL Display order]** helst ändra den eller flytta den till butiken om du inte behöver den längre.

1. Om du vill ta hänsyn till dina ändringar måste du koppla från och sedan koppla från Adobe Campaign Classic igen. Om din nya uttryckssymbol fortfarande inte visas i **[!UICONTROL Insert emoticon]** popup-fönstret kanske du måste rensa cachen. For more on this, refer to this [section](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear).

1. Din nya uttryckssymbol finns nu i dina leveranser i **[!UICONTROL Insert emoticon]** popup-fönstret i den 61:a positionen som konfigurerats i föregående steg. Mer information om hur du använder uttryckssymboler i leveranser finns på den här [sidan](../../delivery/using/defining-the-email-content.md#inserting-emoticons).

   ![](assets/emoticon_4.png)

1. Om följande uttryckssymboler visas i **[!UICONTROL Insert emoticon]** popup-fönstret betyder det att de inte har konfigurerats korrekt. Kontrollera om din **[!UICONTROL U+]** eller **[!UICONTROL Display order]** rätt kod finns i **[!UICONTROL Emoticon list]**.

   ![](assets/emoticon_6.png)
