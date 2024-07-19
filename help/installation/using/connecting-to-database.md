---
product: campaign
title: Ansluta till en extern databas
description: Lär dig ansluta till en extern databas
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 240d7e11-da3a-4d64-8986-1f1c8ebcea3c
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '645'
ht-degree: 0%

---

# Ansluta till databasen {#connecting-to-the-database}



Om du vill aktivera en anslutning till den externa databasen måste du ange anslutningsparametrarna, dvs. måldatakällan och namnet på tabellen med data som behöver läsas in.

>[!CAUTION]
>
>Adobe Campaign-användaren behöver specifika rättigheter för den externa databasen och Adobe Campaign-programservern för att kunna bearbeta data från en extern databas. Mer information finns i avsnittet [Åtkomstbehörighet för fjärrdatabas](../../installation/using/remote-database-access-rights.md).
>
>För att undvika felfunktioner måste operatorer som har åtkomst till delade fjärrdata arbeta från separata blanksteg.

## Skapa en delad anslutning {#creating-a-shared-connection}

Om du vill aktivera en anslutning till en delad extern databas kan du komma åt databasen via Adobe Campaign så länge den här anslutningen är aktiv.

1. Konfigurationen måste definieras i förväg via noden **[!UICONTROL Administration > Platform > External accounts]**.
1. Klicka på knappen **[!UICONTROL New]** och välj typ **[!UICONTROL External database]**.
1. Definiera **[!UICONTROL Connection]**-parametrarna för den externa databasen.

   För anslutningar till en **ODBC**-typdatabas måste fältet **[!UICONTROL Server]** innehålla namnet på ODBC-datakällan och inte servernamnet. Dessutom kan vissa ytterligare konfigurationer vara nödvändiga beroende på vilka databaser som används. Se avsnittet [Specifika konfigurationer per databastyp](../../installation/using/configure-fda.md).

1. När parametrarna har angetts klickar du på knappen **[!UICONTROL Test the connection]** för att godkänna dem.

   ![](assets/wf-external-account-create.png)

1. Om det behövs avmarkerar du alternativet **[!UICONTROL Enabled]** för att inaktivera åtkomst till den här databasen utan att ta bort konfigurationen.
1. Om du vill att Adobe Campaign ska kunna komma åt den här databasen måste du distribuera SQL-funktionerna. Klicka på fliken **[!UICONTROL Parameters]** och sedan på knappen **[!UICONTROL Deploy functions]**.

   ![](assets/wf-external-account-functions.png)

Du kan definiera särskilda arbetskatalogutrymmen för tabellerna och för indexet på fliken **[!UICONTROL Parameters]**.

## Skapa en tillfällig anslutning {#creating-a-temporary-connection}

Du kan definiera en anslutning till en extern databas direkt från arbetsflödesaktiviteter. I det här fallet kommer den att finnas i en lokal extern databas, reserverad för att användas i ett aktuellt arbetsflöde: den kommer inte att sparas på de externa kontona. Den här typen av punktanslutning kan skapas för olika aktiviteter i arbetsflödet, särskilt **[!UICONTROL Query]**, **[!UICONTROL Data loading (RDBMS)]**, **[!UICONTROL Enrichment]** eller **[!UICONTROL Split]**-aktiviteten.

>[!CAUTION]
>
>Den här typen av konfiguration rekommenderas inte, men kan användas regelbundet för att samla in data. Du bör ändå skapa ett externt konto enligt beskrivningen i avsnittet [Skapa en delad anslutning](#creating-a-shared-connection).

I frågeaktiviteten är stegen för att skapa en periodisk anslutning till en extern databas följande:

1. Klicka på **[!UICONTROL Add data...]** och välj **[!UICONTROL External data]**-alternativen.
1. Välj alternativet **[!UICONTROL Locally defining the data source]**.

   ![](assets/wf_add_data_local_external_data.png)

1. Välj måldatabasmotorn i listrutan. Ange namnet på servern och ange autentiseringsparametrarna.

   Ange också namnet på den externa databasen.

   ![](assets/wf_add_data_local_external_data_param.png)

   Klicka på knappen **[!UICONTROL Next]**.

1. Markera tabellen där data lagras.

   Du kan ange namnet på tabellen direkt i motsvarande fält eller klicka på redigeringsikonen för att öppna listan med databastabeller.

   ![](assets/wf_add_data_local_external_data_select_table.png)

1. Klicka på knappen **[!UICONTROL Add]** för att definiera ett eller flera avstämningsfält mellan den externa databasinformationen och data i Adobe Campaign-databasen. Ikonerna **[!UICONTROL Edit expression]** för **[!UICONTROL Remote field]** och **[!UICONTROL Local field]** ger dig åtkomst till listan med fält i varje tabell.

   ![](assets/wf_add_data_local_external_data_join.png)

1. Om det behövs anger du ett filtreringsvillkor och datasorteringsläget.
1. Välj de ytterligare data som ska samlas in i den externa databasen. Om du vill göra det dubbelklickar du på de fält som du vill lägga till för att visa dem i **[!UICONTROL Output columns]**.

   ![](assets/wf_add_data_local_external_data_select.png)

   Bekräfta konfigurationen genom att klicka på **[!UICONTROL Finish]**.

## Säker anslutning {#secure-connection}

>[!NOTE]
>
>Säker anslutning är bara tillgänglig för PostgreSQL.

Du kan skydda åtkomsten till en extern databas när du konfigurerar ett externt FDA-konto.

Det gör du genom att lägga till **:ssl** efter serveradressen och adressen för porten som används. Exempel: **192.168.0.52:4501:ssl**.

Data skickas sedan via det säkra SSL-protokollet.

## Ytterligare konfigurationer {#additional-configurations}

Om det behövs kan du skapa schemat för databearbetning i en extern databas. På samma sätt kan du i Adobe Campaign definiera mappning av data i en extern tabell. Dessa konfigurationer är allmänna och gäller inte enbart arbetsflöden.

>[!NOTE]
>
>Mer information om hur du skapar scheman i Adobe Campaign och definierar en ny datamappning finns på [den här sidan](../../configuration/using/about-schema-edition.md).
