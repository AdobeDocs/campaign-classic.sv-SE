---
product: campaign
title: Anpassa listan med uttryckssymboler
description: Lär dig hur du anpassar uttryckslistan när du använder Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: sending-emails
exl-id: b8642df3-1960-4f2c-8273-c3988a3e85f0
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 3%

---

# Anpassa listan med uttryckssymboler {#customize-emoticons}

Uttryckslistan som visas i popup-fönstret styrs av en uppräkning som gör att du kan visa värden i en lista för att begränsa vilka val användaren har för ett visst fält.
Ordningen på uttryckslistan kan anpassas. Du kan också lägga till andra uttryckssymboler i listan.
Det finns uttryckssymboler tillgängliga för e-post och för mer information om detta finns på [sidan](defining-the-email-content.md#inserting-emoticons).

## Lägga till en ny uttryckssymbol {#add-new-emoticon}

>[!CAUTION]
>
>Uttryckssymbollistan får inte innehålla fler än 81 poster.

1. Välj den nya uttryckssymbol du vill lägga till på den här [sidan](https://unicode.org/emoji/charts/full-emoji-list.html). Observera att det måste vara kompatibelt med olika plattformar som webbläsare och operativsystem.

1. I **[!UICONTROL Explorer]** väljer du **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Enumerations]** och klickar på den körklara uppräkningen **[!UICONTROL Emoticon list]**.

   >[!NOTE]
   >
   >Enkla uppräkningar kan bara hanteras av en administratör för din Adobe Campaign Classic-konsol.

   ![](assets/emoticon_1.png)

1. Klicka på **[!UICONTROL Add]**.

1. Fyll i fälten:

   * **[!UICONTROL U+]**: Kod för din nya uttryckssymbol. Du hittar listan med uttryckssymboler på den här [sidan](https://unicode.org/emoji/charts/full-emoji-list.html).
För att undvika kompatibilitetsproblem rekommenderar vi att du väljer uttryckssymboler som stöds i webbläsare och i alla operativsystem.

   * **[!UICONTROL Label]**: Etikett på din nya uttryckssymbol.

   ![](assets/emoticon_5.png)

1. Klicka på **[!UICONTROL Ok]** och sedan på **[!UICONTROL Save]** när konfigurationen är klar.
Din nya uttryckssymbol placeras automatiskt i butiken.

1. Om du vill visa den i fönstret **[!UICONTROL Insert emoticon]** för dina leveranser väljer du den nya uttryckssymbolen genom att dubbelklicka på den.

1. Välj i listrutan **[!UICONTROL Display order]** i vilken ordning din nya uttryckssymbol ska visas. Observera att om du väljer en redan tilldelad visningsordning flyttas den befintliga uttryckssymbolen automatiskt till butiken.

   <br>I det här exemplet har vi valt visningsordernummer 61, vilket innebär att om en post redan har den här beställningen flyttas den automatiskt till butiken och den nya posten får plats i uppräkningslistan.

   ![](assets/emoticon_2.png)

1. Din nya uttryckssymbol har nu lagts till i uppräkningen **[!UICONTROL Insert emoticon list]** som är klar att användas. Du kan när som helst ändra dess **[!UICONTROL Display order]** eller flytta den till butiken om du inte behöver den längre.

1. Ta hänsyn till dina ändringar genom att koppla från och sedan ansluta igen från Adobe Campaign Classic. Om din nya uttryckssymbol fortfarande inte visas i popup-fönstret **[!UICONTROL Insert emoticon]** kanske du måste rensa cacheminnet. Mer information om detta hittar du i det här [avsnittet](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear).

1. Din nya uttryckssymbol finns nu i leveranserna i popup-fönstret **[!UICONTROL Insert emoticon]** i den 61:a positionen som konfigurerats i föregående steg. Mer information om hur du använder uttryckssymboler i leveranser finns på den här [sidan](defining-the-email-content.md#inserting-emoticons).

   ![](assets/emoticon_4.png)

1. Om följande uttryckssymboler visas i popup-fönstret **[!UICONTROL Insert emoticon]** betyder det att de inte har konfigurerats korrekt. Kontrollera om din **[!UICONTROL U+]**-kod eller **[!UICONTROL Display order]** är korrekt i **[!UICONTROL Emoticon list]**.

   ![](assets/emoticon_6.png)
