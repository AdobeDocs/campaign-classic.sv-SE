---
title: Åtkomst till en extern databas
seo-title: Åtkomst till en extern databas
description: Åtkomst till en extern databas
seo-description: null
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d2758b5e81d1720a4f01a610e51c4a33995d88d1

---


# Definiera datamappning {#defining-data-mapping}

Med Adobe Campaign kan ni definiera mappning av data i en extern tabell.

För att göra detta måste du skapa en ny leveransmappning för att kunna använda data i den här tabellen som leveransmål när schemat för den externa tabellen har skapats.

Gör så här:

1. Skapa en ny leveranskarta och välj målinriktningsdimensionen, det schema du just skapade, till exempel.

   ![](assets/wf_new_mapping_create_fda.png)

1. Ange fälten där leveransinformationen lagras (efternamn, förnamn, e-postadress, adress osv.).

   ![](assets/wf_new_mapping_define_join.png)

1. Ange parametrarna för informationslagring, inklusive suffixet för tilläggsscheman för att de ska vara enkla att identifiera.

   ![](assets/wf_new_mapping_define_names.png)

   Du kan välja att lagra undantag (**exkluderande**), med meddelanden (**utsändning**) eller i en separat tabell.

   Du kan också välja om du vill hantera spårning för den här leveranskartan (**spårningslogg**).

1. Välj sedan de tillägg som ska beaktas. Tilläggstypen beror på plattformens parametrar och alternativ (se licensavtalet).

   ![](assets/wf_new_mapping_define_extensions.png)

   Klicka på **[!UICONTROL Save]** knappen för att starta framtagningen av leveransmappningen: alla länkade tabeller skapas automatiskt baserat på de valda parametrarna.
