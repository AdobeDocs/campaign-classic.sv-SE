---
product: campaign
title: Infoga en streckkod i ett e-postmeddelande
description: Infoga en streckkod i ett e-postmeddelande
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Email Design
role: User
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 0%

---

# Infoga en streckkod i ett e-postmeddelande{#insert-a-barcode-in-an-email}

Med modulen för streckkodsgenerering kan du skapa flera typer av streckkoder som följer många vanliga standarder, inklusive 2D-streckkoder.

Det går att dynamiskt generera en streckkod som en bitmapp med ett värde som definierats enligt kundkriterierna. Personaliserade streckkoder kan inkluderas i e-postkampanjer. Mottagaren kan skriva ut meddelandet och visa det för det utgivande företaget för skanning (t.ex. vid utcheckning).

Om du vill infoga en streckkod i ett e-postmeddelande placerar du markören i innehållet där du vill visa den och klickar sedan på knappen för anpassning. Välj **[!UICONTROL Include > Barcode...]**.

![](assets/barcode_insert_14.png)

Konfigurera sedan följande element efter dina behov:

1. Välj typ av streckkod.

   * För 1D-format finns följande typer i Adobe Campaign: Codabar, Code 128, GS1-128 (tidigare EAN-128), UPC-A, UPC-E, ISBN, EAN-8, Code39, Interleaved 2 of 5, POSTNET och Royal Mail (RM4SCC).

     Exempel på en 1D-streckkod:

     ![](assets/barcode_insert_08.png)

   * Typerna DataMatrix och PDF417 gäller 2D-formatet.

     Exempel på en 2D-streckkod:

     ![](assets/barcode_insert_09.png)

   * Om du vill infoga en QR-kod väljer du den här typen och anger den felkorrigeringsgrad som ska användas. Denna frekvens definierar mängden information som upprepas och toleransen för försämring.

     ![](assets/barcode_insert_06.png)

     Exempel på en QR-kod:

     ![](assets/barcode_insert_12.png)

1. Ange storleken på streckkoden som du vill infoga i e-postmeddelandet: om du konfigurerar skalan kan du öka eller minska storleken på streckkoden, från x1 till x10.
1. I fältet **[!UICONTROL Value]** kan du definiera värdet för streckkoden. Ett värde kan matcha ett specialerbjudande och kan vara funktionen för ett villkor, det kan vara värdet för ett databasfält som är länkat till kunderna.

   I det här exemplet visas en EAN-8-typstreckkod, till vilken en mottagares kontonummer har lagts till. Om du vill lägga till det här kontonumret klickar du på personaliseringsknappen till höger om fältet **[!UICONTROL Value]** och väljer **[!UICONTROL Recipient > Account number]**.

   ![](assets/barcode_insert_15.png)

1. I fältet **[!UICONTROL Height]** kan du konfigurera höjden på streckkoden utan att ändra bredden, genom att ändra avståndet mellan varje fält.

   Det finns ingen begränsande inmatningskontroll beroende på streckkodstypen. Om ett streckkodsvärde är felaktigt visas det bara i läget **Förhandsgranska** där streckkoden stryks över med rött.

   >[!NOTE]
   >
   >Vilket värde som tilldelas en streckkod beror på dess typ. En EAN-8-typ ska till exempel ha exakt 8 siffror.
   >
   >Med personaliseringsknappen till höger om fältet **[!UICONTROL Value]** kan du lägga till data utöver själva värdet. Detta förbättrar streckkoden, förutsatt att den accepteras av streckkodsstandarden.
   >
   >Om du till exempel använder en GS1-128-typstreckkod och vill ange kontonumret för en mottagare utöver värdet, klickar du på personaliseringsknappen och väljer **[!UICONTROL Recipient > Account number]**. Om kontonumret för den valda mottagaren anges korrekt kommer streckkoden att ta hänsyn till det.

När dessa element har konfigurerats kan du slutföra e-postmeddelandet och skicka det. För att undvika fel ska du alltid se till att ditt innehåll visas korrekt innan du utför en leverans genom att klicka på fliken **[!UICONTROL Preview]**.

![](assets/barcode_insert_10.png)

>[!NOTE]
>
>Om värdet för en streckkod är felaktigt visas dess bitmapp överstruket i rött.

![](assets/barcode_insert_11.png)
