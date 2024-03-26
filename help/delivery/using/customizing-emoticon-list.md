---
product: campaign
title: Anpassa listan över uttryckssymboler
description: Lär dig hur du anpassar uttryckslistan när du använder Adobe Campaign
badge-v7: label="v7" type="Informative" tooltip="Gäller Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Email, Push
role: User, Data Engineer
exl-id: b8642df3-1960-4f2c-8273-c3988a3e85f0
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 4%

---

# Anpassa listan över uttryckssymboler {#customize-emoticons}

Uttryckslistan som visas i popup-fönstret styrs av en uppräkning som gör att du kan visa värden i en lista för att begränsa vilka val användaren har för ett visst fält.
Ordningen på uttryckslistan kan anpassas. Du kan också lägga till andra uttryckssymboler i listan.
Det finns uttryckssymboler tillgängliga för e-post och du behöver mer information om detta [page](defining-the-email-content.md#inserting-emoticons).

## Lägga till en ny uttryckssymbol {#add-new-emoticon}

>[!CAUTION]
>
>Uttryckssymbollistan får inte innehålla fler än 81 poster.

1. Välj den nya uttryckssymbolen som du vill lägga till här [page](https://unicode.org/emoji/charts/full-emoji-list.html). Observera att det måste vara kompatibelt med olika plattformar som webbläsare och operativsystem.

1. Från **[!UICONTROL Explorer]**, markera **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Enumerations]** och klicka på **[!UICONTROL Emoticon list]** färdig uppräkning.

   >[!NOTE]
   >
   >Enkla uppräkningar kan bara hanteras av en administratör för din Adobe Campaign Classic-konsol.

   ![](assets/emoticon_1.png)

1. Klicka på **[!UICONTROL Add]**.

1. Fyll i fälten:

   * **[!UICONTROL U+]**: Kod för din nya uttryckssymbol. Här finns en lista med uttryckssymbolkoder [page](https://unicode.org/emoji/charts/full-emoji-list.html).
För att undvika kompatibilitetsproblem rekommenderar vi att du väljer uttryckssymboler som stöds i webbläsare och i alla operativsystem.

   * **[!UICONTROL Label]**: Etikett på din nya uttryckssymbol.

   ![](assets/emoticon_5.png)

1. Klicka **[!UICONTROL Ok]** sedan **[!UICONTROL Save]** när konfigurationen är klar.
Din nya uttryckssymbol placeras automatiskt i butiken.

1. Så här visar du den i **[!UICONTROL Insert emoticon]** fönstret med dina leveranser väljer du din nya uttryckssymbol genom att dubbelklicka på den.

1. Välj i dialogrutan **[!UICONTROL Display order]** i vilken ordning din nya uttryckssymbol ska visas. Observera att om du väljer en redan tilldelad visningsordning flyttas den befintliga uttryckssymbolen automatiskt till butiken.

   <br>I det här exemplet har vi valt visningsordernummer 61, vilket innebär att om en post redan har den här beställningen flyttas den automatiskt till butiken och den nya posten får plats i uppräkningslistan.

   ![](assets/emoticon_2.png)

1. Din nya uttryckssymbol har nu lagts till i **[!UICONTROL Insert emoticon list]** färdig uppräkning. Du kan ändra dess **[!UICONTROL Display order]** när som helst eller flytta den till butiken om du inte behöver den längre.

1. Ta hänsyn till dina ändringar genom att koppla från och sedan ansluta igen från Adobe Campaign Classic. Om din nya uttryckssymbol fortfarande inte visas i **[!UICONTROL Insert emoticon]** kan du behöva rensa cachen i popup-fönstret. Mer information om detta hittar du i det här [avsnittet](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear).

1. Din nya uttryckssymbol finns nu i dina leveranser i **[!UICONTROL Insert emoticon]** popup-fönstret i den 61:a positionen som konfigurerats i föregående steg. Mer information om hur du använder uttryckssymboler i leveranser finns i [page](defining-the-email-content.md#inserting-emoticons).

   ![](assets/emoticon_4.png)

1. Om följande uttryckssymboler visas i **[!UICONTROL Insert emoticon]** popup-fönstret innebär att de inte var korrekt konfigurerade. Kontrollera om din **[!UICONTROL U+]** kod eller **[!UICONTROL Display order]** är korrekt i **[!UICONTROL Emoticon list]**.

   ![](assets/emoticon_6.png)
