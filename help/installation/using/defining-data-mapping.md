---
product: campaign
title: Definiera extern datamappning
description: Lär dig mappa data i en extern databas
exl-id: a7253ca7-47e5-4def-849d-3ce1c9b948fb
source-git-commit: 3af4f259b80b3e03c81ee278b470ef6ffe3fe4d0
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 3%

---

# Definiera extern datamappning {#defining-data-mapping}

![](../../assets/v7-only.svg)

Med Adobe Campaign kan du definiera mappning av data i en extern tabell.

För att göra detta måste du skapa en ny leveransmappning för att kunna använda data i den här tabellen som leveransmål när schemat för den externa tabellen har skapats.

Gör så här:

1. Skapa en ny leveranskarta och välj målinriktningsdimensionen, det schema du just skapade, till exempel.

   ![](assets/wf_new_mapping_create_fda.png)

1. Ange fälten där leveransinformationen lagras (efternamn, förnamn, e-postadress, adress osv.).

   ![](assets/wf_new_mapping_define_join.png)

1. Ange parametrarna för informationslagring, inklusive suffixet för tilläggsscheman för att de ska vara enkla att identifiera.

   ![](assets/wf_new_mapping_define_names.png)

   Du kan välja om du vill lagra undantag (**excludelog**), med meddelanden (**broadlog**) eller i en separat tabell.

   Du kan också välja om du vill hantera spårning för den här leveransmappningen (**trackinglog**).

1. Välj sedan de tillägg som ska beaktas. Tilläggstypen beror på plattformens parametrar och alternativ (se licensavtalet).

   ![](assets/wf_new_mapping_define_extensions.png)

   Klicka på **[!UICONTROL Save]** knapp för att starta framtagning av leveransmappning: alla länkade tabeller skapas automatiskt baserat på de valda parametrarna.
