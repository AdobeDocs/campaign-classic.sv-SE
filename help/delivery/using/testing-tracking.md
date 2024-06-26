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
1. När du har omdirigerats till spegelsidan kan du gå till **Administration > Tekniska arbetsflöden** och öppna **Spårning** arbetsflöde.
1. Starta arbetsflödet, högerklicka på **Schemaläggare** aktivitet och välj **Kör väntande uppgift nu**.
1. Vänta i cirka 30 sekunder och välj sedan **Granskning** -fliken. Se till att minst en loggpost för spårning hittas.

   Klicka **Uppdatera** om inga nya loggar visas.

1. Gå till profilsidan för mottagaren som du använde för testet och välj **Spårning** -fliken. Vissa poster ska visas med **Spegelsida** värdet i **Typ** kolumn.

   >[!NOTE]
   >
   >Mottagarens profilsida finns i **Profiler och mål > Mottagare** som standard.

   Kontrollera loggspårningen genom att leta efter värdena **Öppna** och **[!UICONTROL Email click]** i **Typ** kolumn.

   Om de öppna loggarna inte visas går du till leveransen och öppnar den **Egenskaper** för att säkerställa att båda **Aktivera spårning** och **[!UICONTROL Opens tracking]** alternativen är markerade.
