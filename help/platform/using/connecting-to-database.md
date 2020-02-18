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
source-git-commit: 4969c5e56f1911b3abfd770ca4f8f5ed25784a52

---


# Ansluta till databasen {#connecting-to-the-database}

Om du vill aktivera en anslutning till den externa databasen måste du ange anslutningsparametrarna, dvs. måldatakällan och namnet på tabellen med data som behöver läsas in.

>[!CAUTION]
>
>Adobe Campaign-användaren behöver specifika rättigheter för den externa databasen och Adobe Campaign-programservern för att bearbeta data från en extern databas. Mer information finns i avsnittet [Åtkomstbehörighet](#remote-database-access-rights) för fjärrdatabas.
>
>För att undvika felfunktioner måste operatorer som har åtkomst till delade fjärrdata arbeta från separata blanksteg.

## Skapa en delad anslutning {#creating-a-shared-connection}

Om du vill aktivera en anslutning till en delad extern databas kan du komma åt databasen via Adobe Campaign, så länge den här anslutningen är aktiv.

1. Konfigurationen måste definieras i förväg via **[!UICONTROL Administration > Platform > External accounts]** noden.
1. Klicka på **[!UICONTROL New]** knappen och välj **[!UICONTROL External database]** typ.
1. Definiera den externa databasens **[!UICONTROL Connection]** parametrar.

   För anslutningar till en **ODBC** -typdatabas måste **[!UICONTROL Server]** fältet innehålla namnet på ODBC-datakällan och inte servernamnet. Dessutom kan vissa ytterligare konfigurationer vara nödvändiga beroende på vilka databaser som används. Se avsnittet [Specifika konfigurationer per databastyp](#specific-configurations-by-database-type) .

1. När parametrarna har angetts klickar du på **[!UICONTROL Test the connection]** knappen för att godkänna dem.

   ![](assets/wf-external-account-create.png)

1. Om det behövs avmarkerar du alternativet för att inaktivera åtkomsten till den här databasen utan att ta bort dess konfiguration. **[!UICONTROL Enabled]**
1. Om du vill att Adobe Campaign ska få åtkomst till den här databasen måste du distribuera SQL-funktionerna. Klicka på **[!UICONTROL Parameters]** fliken och sedan på **[!UICONTROL Deploy functions]** knappen.

   ![](assets/wf-external-account-functions.png)

Du kan definiera särskilda arbetstabellutrymmen för tabellerna och för indexet på **[!UICONTROL Parameters]** fliken.

## Skapa en tillfällig anslutning {#creating-a-temporary-connection}

Du kan definiera en anslutning till en extern databas direkt från arbetsflödesaktiviteter. I det här fallet kommer den att finnas i en lokal extern databas som är reserverad för att användas i ett aktuellt arbetsflöde: den sparas inte på externa konton. Den här typen av punktlig anslutning kan skapas för olika aktiviteter i arbetsflödet, särskilt **[!UICONTROL Query]**, **[!UICONTROL Data loading (RDBMS)]**, **[!UICONTROL Enrichment]** aktiviteten eller **[!UICONTROL Split]** aktiviteten.

>[!CAUTION]
>
>Den här typen av konfiguration rekommenderas inte, men kan användas regelbundet för att samla in data. Du bör ändå skapa ett externt konto, vilket beskrivs i avsnittet [Skapa en delad anslutning](#creating-a-shared-connection) .

I frågeaktiviteten är till exempel stegen för att skapa en periodisk anslutning till en extern databas följande:

1. Klicka på **[!UICONTROL Add data...]** och välj **[!UICONTROL External data]** alternativ.
1. Välj **[!UICONTROL Locally defining the data source]** alternativet.

   ![](assets/wf_add_data_local_external_data.png)

1. Välj måldatabasmotorn i listrutan. Ange namnet på servern och ange autentiseringsparametrarna.

   Ange också namnet på den externa databasen.

   ![](assets/wf_add_data_local_external_data_param.png)

   Klicka på **[!UICONTROL Next]** knappen.

1. Markera tabellen där data lagras.

   Du kan ange namnet på tabellen direkt i motsvarande fält eller klicka på redigeringsikonen för att öppna listan med databastabeller.

   ![](assets/wf_add_data_local_external_data_select_table.png)

1. Klicka på **[!UICONTROL Add]** knappen för att definiera ett eller flera avstämningsfält mellan externa databasdata och data i Adobe Campaign-databasen. Ikonerna **[!UICONTROL Edit expression]** i **[!UICONTROL Remote field]** och **[!UICONTROL Local field]** ger dig tillgång till listan med fält i varje tabell.

   ![](assets/wf_add_data_local_external_data_join.png)

1. Om det behövs anger du ett filtreringsvillkor och datasorteringsläget.
1. Välj de ytterligare data som ska samlas in i den externa databasen. Det gör du genom att dubbelklicka på de fält som du vill lägga till för att visa dem i **[!UICONTROL Output columns]**.

   ![](assets/wf_add_data_local_external_data_select.png)

   Klicka **[!UICONTROL Finish]** för att bekräfta konfigurationen.

## Säker anslutning {#secure-connection}

>[!NOTE]
>
>Säker anslutning är bara tillgänglig för PostgreSQL.

Du kan skydda åtkomsten till en extern databas när du konfigurerar ett externt FDA-konto.

Det gör du genom att lägga till &quot;**:ssl**&quot; efter serveradressen och adressen för den port som används. Till exempel: **192.168.0.52:4501:ssl**.

Data skickas sedan via det säkra SSL-protokollet.

## Ytterligare konfigurationer {#additional-configurations}

Om det behövs kan du skapa schemat för databearbetning i en extern databas. På samma sätt kan du med Adobe Campaign definiera mappning för data i en extern tabell. Dessa konfigurationer är allmänna och gäller inte enbart arbetsflöden.

>[!NOTE]
>
>Mer information om hur du skapar scheman i Adobe Campaign och definierar en ny datamappning finns på [den här sidan](../../configuration/using/about-schema-edition.md).