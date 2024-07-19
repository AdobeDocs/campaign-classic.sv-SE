---
product: campaign
title: Testa meddelandespårning
description: Lär dig hur du testar meddelandespårning
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Monitoring
role: User
exl-id: 16ad36b7-c13e-4b77-86ca-41c9ef174172
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 1%

---

# Testa meddelandespårning{#testing-tracking}

Du kan testa spårning på spegelsidor, e-postloggar och länkar. Så här gör du:

1. Skapa en ny e-postleverans som ska användas för testning.
1. Ange den användare som ska ta emot e-postmeddelandet. Eftersom den här användaren måste öppna e-postmeddelandet och klicka på de länkar det innehåller måste du markera en testmottagaradress som du kontrollerar.
1. Lägg till ett anpassningsblock för spegelsida (MirrorPage) i e-postinnehållet.
1. Skicka leveransen som innehåller en länk till spegelsidan.
1. När du har fått e-postmeddelandet öppnar du det och klickar på länken för spegelsidan.
1. När du har omdirigerats korrekt till spegelsidan öppnar du mappen **Administration > Tekniska arbetsflöden** och öppnar arbetsflödet **Spårning**.
1. Starta arbetsflödet, högerklicka på aktiviteten **Schemaläggaren** och välj **Kör väntande aktivitet nu**.
1. Vänta i cirka 30 sekunder och välj sedan fliken **Granskning**. Se till att minst en loggpost för spårning hittas.

   Klicka på **Uppdatera** om du inte ser några nya loggar.

1. Gå till profilsidan för mottagaren som du använde för testet och välj fliken **Spärra/knip**. Vissa poster ska visas med värdet **Spegelsida** i kolumnen **Typ**.

   >[!NOTE]
   >
   >Mottagarens profilsida finns som standard i mappen **Profiler och mål > Mottagare** .

   Om du vill kontrollera spårningen av e-postloggen söker du efter värdena **Öppna** och **[!UICONTROL Email click]** i kolumnen **Typ**.

   Om de öppna loggarna inte visas går du till leveransen och öppnar **Egenskaper** för att kontrollera att både alternativet **Aktivera spårning** och alternativet **[!UICONTROL Opens tracking]** är markerade.
