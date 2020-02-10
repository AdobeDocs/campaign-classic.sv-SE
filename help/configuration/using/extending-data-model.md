---
title: Använda tabellen Adobe Campaign Classic-mottagare
description: Lär dig hur du använder den färdiga mottagartabellen i Adobe Campaign Classic när du utformar din datamodell.
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 65affa58a66090c3bffc837fdbd85aa46338bd3e

---


# Utöka datamodellen{#extending-data-model}

När ni börjar med Adobe Campaign måste ni utvärdera standarddatamodellen för att kontrollera vilken tabell som är bäst lämpad för att lagra era marknadsföringsdata.

Om det är relevant kan du använda den förvalda mottagartabellen med de färdiga fälten, som beskrivs i det här [avsnittet](../../configuration/using/default-recipient-table.md).

Om det behövs kan du utöka den med två mekanismer:

* Utöka en befintlig tabell med nya fält. Du kan till exempel lägga till ett nytt&quot;Lojalitet&quot;-fält i mottagartabellen.
* Skapa en ny tabell, t.ex. en&quot;Inköpstabell&quot; med alla inköp som gjorts av varje profil i databasen, och länka den till mottagartabellen.

Mer information om hur du konfigurerar tilläggsscheman för att utöka den konceptuella datamodellen finns i [Om schemautgåva](../../configuration/using/about-schema-edition.md).

>[!IMPORTANT]
>
>Att utöka datamodellen är reserverat för avancerade användare.
