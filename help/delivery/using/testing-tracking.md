---
title: Testspårning
seo-title: Testspårning
description: Testspårning
seo-description: null
page-status-flag: never-activated
uuid: 76d84ab4-b632-4498-96a1-ce9c773ec125
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: tracking-messages
discoiquuid: 4ed23249-4ecf-4e57-91b3-6fae1387bd6a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Testspårning{#testing-tracking}

Du kan testa spårning på spegelsidor, e-postloggar och länkar. Så här gör du:

1. Skapa en ny e-postleverans som ska användas för testning.
1. Ange den användare som ska ta emot e-postmeddelandet. Eftersom den här användaren måste öppna e-postmeddelandet och klicka på de länkar det innehåller måste du markera en testmottagaradress som du kontrollerar.
1. Lägg till ett anpassningsblock för spegelsida (MirrorPage) i e-postinnehållet.
1. Skicka leveransen som innehåller en länk till spegelsidan.
1. När du har fått e-postmeddelandet öppnar du det och klickar på länken för spegelsidan.
1. När du har omdirigerats korrekt till spegelsidan öppnar du mappen **Administration > Tekniska arbetsflöden** och öppnar arbetsflödet för **spårning** .
1. Starta arbetsflödet, högerklicka på aktiviteten **Schemaläggaren** och välj **Kör väntande aktivitet nu**.
1. Vänta i cirka 30 sekunder och välj sedan fliken **Granskning** . Se till att minst en loggpost för spårning hittas.

   Klicka på **Uppdatera** om du inte ser några nya loggar.

1. Gå till profilsidan för mottagaren som du använde för testet och välj fliken **Spärra/knip** . Vissa poster ska visas med värdet för **Spegelsida** i kolumnen **Typ** .

   >[!NOTE]
   >
   >Mottagarens profilsida finns som standard i mappen **Profiler och mål > Mottagare** .

   Om du vill kontrollera spårningen av e-postloggen söker du efter värdena **Öppna** och **[!UICONTROL Email click]** i kolumnen **Typ** .

   Om de öppna loggarna inte visas går du till leveransen och öppnar **Egenskaper** för att kontrollera att både **Aktivera spårning** och **[!UICONTROL Opens tracking]** alternativ är markerade.

