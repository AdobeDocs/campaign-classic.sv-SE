---
product: campaign
title: Definiera extern datamappning
description: Lär dig mappa data i en extern databas
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
exl-id: a7253ca7-47e5-4def-849d-3ce1c9b948fb
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 6%

---

# Definiera extern datamappning {#defining-data-mapping}



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

   Klicka på **[!UICONTROL Save]** för att starta framtagning av leveransmappning: alla länkade tabeller skapas automatiskt baserat på de valda parametrarna.
