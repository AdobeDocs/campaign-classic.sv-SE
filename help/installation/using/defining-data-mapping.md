---
product: campaign
title: Åtkomst till en extern databas
description: Åtkomst till en extern databas
audience: platform
content-type: reference
topic-tags: connectors
exl-id: a7253ca7-47e5-4def-849d-3ce1c9b948fb
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 5%

---

# Definiera datakartläggning {#defining-data-mapping}

Med Adobe Campaign kan du definiera mappning av data i en extern tabell.

För att göra detta måste du skapa en ny leveransmappning för att kunna använda data i den här tabellen som leveransmål när schemat för den externa tabellen har skapats.

Gör så här:

1. Skapa en ny leveranskarta och välj målinriktningsdimensionen, det schema du just skapade, till exempel.

   ![](assets/wf_new_mapping_create_fda.png)

1. Ange fälten där leveransinformationen lagras (efternamn, förnamn, e-postadress, adress osv.).

   ![](assets/wf_new_mapping_define_join.png)

1. Ange parametrarna för informationslagring, inklusive suffixet för tilläggsscheman för att de ska vara enkla att identifiera.

   ![](assets/wf_new_mapping_define_names.png)

   Du kan välja om undantag ska lagras (**excludelog**), med meddelanden (**broadlog**) eller i en separat tabell.

   Du kan också välja om spårning ska hanteras för den här leveransmappningen (**spårningslogg**).

1. Välj sedan de tillägg som ska beaktas. Tilläggstypen beror på plattformens parametrar och alternativ (se licensavtalet).

   ![](assets/wf_new_mapping_define_extensions.png)

   Klicka på knappen **[!UICONTROL Save]** för att starta skapandet av leveransmappningen: alla länkade tabeller skapas automatiskt baserat på de valda parametrarna.
