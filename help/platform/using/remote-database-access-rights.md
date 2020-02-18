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


# Åtkomsträttigheter till fjärrdatabas {#remote-database-access-rights}

För det första, för att användaren ska kunna utföra åtgärder på en extern databas via FDA, måste den senare ha en specifik namngiven behörighet i Adobe Campaign.

1. Markera **[!UICONTROL Administration > Access Management > Named Rights]** noden i Adobe Campaign Explorer.
1. Skapa en ny rättighet genom att ange den valda etiketten.
1. Fältet måste **[!UICONTROL Name]** ha följande format: **användare: base@server**, där:

   * **-användaren** motsvarar namnet på användaren i den externa databasen.
   * **base** motsvarar namnet på den externa databasen.
   * **servern** motsvarar namnet på den externa databasservern.

      >[!NOTE]
      >
      >Delen **:base** är valfri i Oracle.

1. Spara den namngivna rättigheten och länka den till den valda användaren från noden **[!UICONTROL Administration > Access Management > Operators]** i Adobe Campaign Explorer.

För att bearbeta data i en extern databas måste Adobe Campaign-användaren ha minst skrivbehörighet för databasen för att kunna skapa arbetstabeller. Dessa tas bort automatiskt av Adobe Campaign.

I allmänhet är följande rättigheter nödvändiga:

* **ANSLUT**: anslutning till fjärrdatabasen,
* **LÄS data**: skrivskyddad åtkomst till tabeller som innehåller kunddata,
* **LÄS &#39;MetaData&#39;**: åtkomst till serverns datakataloger för att få fram tabellstrukturen,
* **LADDA**: massinläsning i arbetstabeller (krävs vid arbete med samlingar och kopplingar),
* **CREATE/DROP** for **TABLE/INDEX/PROCEDURE/FUNCTION**,
* **FÖRKLARA** (rekommenderas): för övervakning av prestanda vid problem,
* **SKRIV data** (beroende på integrationsscenariot).

>[!NOTE]
>
>Databasadministratören måste se till att dessa rättigheter matchar de rättigheter som är specifika för varje databasmotor. Mer information finns i [RDBMS-specifika rättigheter](https://docs.campaign.adobe.com/doc/AC6.1/en/technicalResources/technicalResources.html).