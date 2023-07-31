---
product: campaign
title: Skapa och konfigurera databasen
description: Skapa och konfigurera databasen
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
badge-v7-prem: label="lokal och hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: f40bab8c-5064-40d9-beed-101a9f22c094
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '1321'
ht-degree: 3%

---

# Skapa och konfigurera databasen{#creating-and-configuring-the-database}

När du skapar en databas finns det två olika alternativ i Adobe Campaign:

1. Skapa eller återanvända en databas: välj det här alternativet om du vill skapa en ny databas eller återanvända en befintlig databas. Se [Fall 1: Skapa/återvinna en databas](#case-1--creating-recycling-a-database).
1. Använda en befintlig databas: välj det här alternativet om en tom databas redan har skapats av administratören och du vill använda den, eller om du vill utöka strukturen för en befintlig databas. Se [Fall 2: Använda en befintlig databas](#case-2--using-an-existing-database).

Konfigurationsstegen beskrivs nedan.

>[!CAUTION]
>
>Namn på databaser, användare och scheman får inte börja med en siffra eller innehålla specialtecken.
>
>Endast **internal** identifieraren kan utföra dessa åtgärder. Mer information om detta finns i [det här avsnittet](../../installation/using/configuring-campaign-server.md#internal-identifier).

## Fall 1: Skapa/återvinna en databas {#case-1--creating-recycling-a-database}

Stegen för att skapa en databas eller återvinna en befintlig bas beskrivs nedan. Vissa konfigurationer beror på vilken databasmotor som används:

Följande steg ingår:

* [Steg 1 - Välja databasmotor](#step-1---selecting-the-database-engine),
* [Steg 2 - Ansluta till servern](#step-2---connecting-to-the-server),
* [Steg 3 - Databasens anslutning och egenskaper](#step-3---connection-and-characteristics-of-the-database),
* [Steg 4 - Paket som ska installeras](#step-4---packages-to-install),
* [Steg 5 - Skapa steg](#step-5---creation-steps),
* [Steg 6 - Skapa databasen](#step-6---creating-the-database).

### Steg 1 - Välja databasmotor {#step-1---selecting-the-database-engine}

Välj databasmotorn bland dem i listrutan.

![](assets/s_ncs_install_db_select_engine.png)

Databaser som stöds listas i Campaign [Kompatibilitetsmatris](../../rn/using/compatibility-matrix.md).

Identifiera servern och välj vilken typ av åtgärd som ska utföras. I detta fall **[!UICONTROL Create or recycle a database]**.

![](assets/s_ncs_install_db_oracle_creation01.png)

Beroende på vilken databasmotor som valts kan serveridentifieringsinformationen variera.

* För **Oracle** motor, fylla i **TNS-namn** definierad för programservern.
* För **PostgreSQL** eller **DB2** måste du ange det DNS-namn (eller IP-adress) som definierats på programservern för att få åtkomst till databasservern.
* För **Microsoft SQL Server** engine, you must define: the DNS name (or IP address) defined on the application server to access the database server: **DNS** eller **DNS`\<instance>`** (instansläge),

  >[!CAUTION]
  >
  > Från och med 20.3 har Windows NT-autentisering avaktiverats. **[!UICONTROL SQL Server authentication]** är nu det enda autentiseringsläget som är tillgängligt för Microsoft SQL Server. [Läs mer](../../rn/using/deprecated-features.md)

  ![](assets/s_ncs_install_db_mssql_creation01.png)

### Steg 2 - Ansluta till servern {#step-2---connecting-to-the-server}

I **[!UICONTROL Server access]** anger du databasserveråtkomsten.

![](assets/s_ncs_install_db_oracle_creation02.png)

Om du vill göra det anger du namnet och lösenordet för **Administrationssystemkonto** som har behörighet att komma åt databaserna, dvs.

* **system** för en Oraclena databas,
* **sa** för en Microsoft SQL Server-databas,
* **affischer** för en PostgreSQL-databas,
* **db2inst1** för en databas2.

### Steg 3 - Databasens anslutning och egenskaper {#step-3---connection-and-characteristics-of-the-database}

I följande steg kan du konfigurera inställningarna för inloggning i databasen.

![](assets/s_ncs_install_db_oracle_creation03.png)

Du måste definiera följande inställningar:

* Ange namnet på den databas som ska skapas.

  >[!NOTE]
  >
  >För en DB2-databas får databasens namn inte överstiga 8 tecken.

* Ange lösenordet för kontot som är länkat till den här databasen.
* Ange om databasen måste vara i Unicode eller inte.

  The **[!UICONTROL Unicode database]** Med kan du lagra alla teckentyper i Unicode oavsett språk.

  >[!NOTE]
  >
  >Med en Oraclena databas **[!UICONTROL Unicode storage]** kan du använda **NCLOB** och **NVARCHAR** textfält.
  > 
  >Om du inte markerar det här alternativet måste teckenuppsättningen (teckenuppsättningen) i Oraclets databas aktivera datalagring på alla språk (AL32UTF8 rekommenderas).

* Välj en tidszon för databasen och ange om den ska vara i UTC (om tillgängligt).

  Mer information finns i [Tidszonshantering](../../installation/using/time-zone-management.md).

### Steg 4 - Paket som ska installeras {#step-4---packages-to-install}

Markera de paket som du vill installera.

Se licensavtalet för att se vilka lösningar och alternativ du har rätt att installera, till exempel&quot;Interaktion&quot; eller&quot;Social marknadsföring&quot;.

![](assets/s_ncs_install_modules.png)

### Steg 5 - Skapa steg {#step-5---creation-steps}

The **[!UICONTROL Creation steps]** I kan du visa och redigera SQL-skriptet som används för att skapa tabellerna.

![](assets/s_ncs_install_db_oracle_creation04.png)

* För ett Oracle, Microsoft SQL Server eller PostgreSQL-databas kan administratören också definiera **lagringsparametrar** som ska användas när databasobjekt skapas.

  De här parametrarna tar emot de exakta tabellutrymmesnamnen (varning: skiftlägeskänsligt). De lagras i **[!UICONTROL Administration > Platform > Options]** i följande alternativ (se [det här avsnittet](../../installation/using/configuring-campaign-options.md#database)):

   * **WdbcOptions_TableSpaceUser**: användartabeller baserade på ett schema
   * **WdbcOptions_TableSpaceIndex**: index för användartabeller baserat på ett schema
   * **WdbcOptions_TableSpaceWork**: arbetstabeller utan schema
   * **WdbcOptions_TableSpaceWorkIndex**: index för arbetstabeller utan schema

* För en Oraclena databas måste Adobe Campaign-användaren ha tillgång till Oraclena, vanligtvis som medlem i **oinstall** grupp.
* The **[!UICONTROL Set or change the administrator password]** gör att du kan ange det lösenord som är länkat till Adobe Campaign-operatorn med administratörsbehörighet.

  Vi rekommenderar att du definierar ett Adobe Campaign-administratörslösenord av säkerhetsskäl.

### Steg 6 - Skapa databasen {#step-6---creating-the-database}

I det sista steget i guiden kan du skapa databasen. Klicka på **[!UICONTROL Start]** för att bekräfta.

![](assets/s_ncs_install_db_oracle_creation06.png)

När databasen har skapats kan du ansluta igen för att slutföra instanskonfigurationen.

Du måste nu starta distributionsguiden för att slutföra konfigurationen av instansen. Se [Distributionsguide](../../installation/using/deploying-an-instance.md#deployment-wizard).

Anslutningsinställningarna för databasen som är länkad till instansen lagras i filen **`/conf/config-<instance>.xml`** finns i Adobe Campaign installationskatalog.

Exempel på en Microsoft SQL Server-konfiguration på base61-databasen som är länkad till kampanjkontot med dess krypterade lösenord:

```
<dbcnx encrypted="1" login="campaign:myBase" password="myPassword" provider="DB" server="dbServer"/>
```

## Fall 2: Använda en befintlig databas {#case-2--using-an-existing-database}

Databasen, liksom användaren, måste ha skapats av databasadministratören och behörigheterna måste vara korrekt konfigurerade.

För en Oracle-databas är minimibehörigheten: GRANT CONNECT, RESOURCE och UNLIMITED TABLESPACE.

Så här använder du en befintlig databas:

* [Steg 1 - Välja databasmotor](#step-1---choosing-the-database-engine),
* [Steg 2 - Inställningar för databasanslutning](#step-2---database-connection-settings),
* [Steg 3 - Paket som ska installeras](#step-3---packages-to-install),
* [Steg 4 - Skapa steg](#step-4---creation-steps),
* [Steg 5 - Skapa databasen](#step-5---creating-the-database).

### Steg 1 - Välja databasmotor {#step-1---choosing-the-database-engine}

Välj databasmotorn i listrutan.

![](assets/s_ncs_install_db_select_engine.png)

Identifiera servern och välj vilken typ av åtgärd du vill utföra. I detta fall **[!UICONTROL Use an existing database]**.

![](assets/s_ncs_install_db_oracle_exists_01.png)

Beroende på vilken databasmotor som valts kan serveridentifieringsinformationen variera.

* För **Oracle** motor, fylla i **TNS-namn** definierad för programservern.
* För **PostgreSQL** eller **DB2** måste du ange det DNS-namn (eller IP-adress) som definierats på programservern för att få åtkomst till databasservern.
* För **Microsoft SQL Server** måste du definiera:

   1. det DNS-namn (eller den IP-adress) som definierats på programservern för åtkomst till databasservern,
   1. den säkerhetsmetod som används för att få åtkomst till Microsoft SQL Server: **[!UICONTROL SQL Server authentication]** eller **[!UICONTROL Windows NT authentication]**.

      ![](assets/s_ncs_install_db_mssql_exists_01.png)

### Steg 2 - Inställningar för databasanslutning {#step-2---database-connection-settings}

I **[!UICONTROL Database]** anger du anslutningsinställningarna för databasen.

![](assets/s_ncs_install_db_oracle_exists_02.png)

Du måste definiera följande inställningar:

* Ange namnet på den databas som ska användas,
* Ange namn och lösenord för kontot som är kopplat till den här databasen,

  >[!NOTE]
  >
  >Kontrollera att både schemanamnet och användarnamnet matchar. Rekommenderat sätt att skapa databaser är via kampanjkonsolklienten.
  >För en Oraclena databas behöver du inte ange kontonamnet.

* Ange om databasen ska vara Unicode eller inte.

### Steg 3 - Paket som ska installeras {#step-3---packages-to-install}

Markera de paket som du vill installera.

Se licensavtalet för att se vilka lösningar och alternativ du har rätt att installera, till exempel&quot;Interaktion&quot; eller&quot;Leads&quot;.

![](assets/s_ncs_install_modules.png)

### Steg 4 - Skapa steg {#step-4---creation-steps}

The **[!UICONTROL Creation steps]** I kan du visa och redigera SQL-skriptet som används för att skapa tabellerna.

![](assets/s_ncs_install_db_oracle_creation04.png)

* För Oracle-, Microsoft SQL Server- eller PostgreSQL-databaser kan administratören definiera **lagringsparametrar** som ska användas när databasobjekt skapas.
* För en Oraclena databas måste Adobe Campaign-användaren ha tillgång till Oraclena, vanligtvis som medlem i **oinstall** grupp.
* The **[!UICONTROL Set or change the administrator password]** gör att du kan ange det lösenord som är länkat till Adobe Campaign-operatorn med administratörsbehörighet.

  Vi rekommenderar att du definierar ett Adobe Campaign-administratörslösenord av säkerhetsskäl.

### Steg 5 - Skapa databasen {#step-5---creating-the-database}

I det sista steget i guiden kan du skapa databasen. Klicka på **[!UICONTROL Start]** för att bekräfta.

![](assets/s_ncs_install_db_oracle_creation06.png)

När databasen har skapats kan du ansluta igen för att slutföra instanskonfigurationen.

Du måste nu starta distributionsguiden för att slutföra konfigurationen av instansen. Se [Distributionsguide](../../installation/using/deploying-an-instance.md#deployment-wizard).

Anslutningsinställningarna för databasen som är länkad till instansen lagras i filen **`/conf/config-<instance>.xml`** finns i Adobe Campaign installationskatalog.

Exempel på en Microsoft SQL Server-konfiguration på base61-databasen som är länkad till kampanjkontot med dess krypterade lösenord:

```
<dbcnx encrypted="1" login="campaign:myBase" password="myPassword" provider="DB" server="dbServer"/>
```
