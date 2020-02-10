---
title: Skapa och konfigurera databasen
seo-title: Skapa och konfigurera databasen
description: Skapa och konfigurera databasen
seo-description: null
page-status-flag: never-activated
uuid: e5143d55-61fa-416a-80db-c29a0caf9a3e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: initial-configuration
discoiquuid: 7dd8a6a5-7cca-4e92-8226-1b9e450dfaf9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4869eb41f942a89c48bc213913c44b70ae777bfc

---


# Skapa och konfigurera databasen{#creating-and-configuring-the-database}

När du skapar en databas finns det två olika alternativ i Adobe Campaign:

1. Skapa eller återvinna en databas: Välj det här alternativet om du vill skapa en ny databas eller återanvända en befintlig databas. Se [ärende 1: Skapa/återvinna en databas](#case-1--creating-recycling-a-database).
1. Använda en befintlig databas: Välj det här alternativet om en tom databas redan har skapats av administratören och du vill använda den; eller för att utöka strukturen i en befintlig databas. Se [ärende 2: Använda en befintlig databas](#case-2--using-an-existing-database).

Konfigurationsstegen beskrivs nedan.

>[!CAUTION]
>
>Namn på databaser, användare och scheman får inte börja med en siffra eller innehålla specialtecken.
>
>Det är bara den **interna** identifieraren som kan utföra dessa åtgärder. Mer information finns i [Intern identifierare](../../installation/using/campaign-server-configuration.md#internal-identifier).

## Fall 1: Skapa/återvinna en databas {#case-1--creating-recycling-a-database}

Stegen för att skapa en databas eller återvinna en befintlig bas beskrivs nedan. Vissa konfigurationer beror på vilken databasmotor som används:

Följande steg ingår:

* [Steg 1 - Välj databasmotor](#step-1---selecting-the-database-engine),
* [Steg 2 - Ansluta till servern](#step-2---connecting-to-the-server),
* [Steg 3 - Databasens](#step-3---connection-and-characteristics-of-the-database)anslutning och egenskaper.
* [Steg 4 - Paket som ska installeras](#step-4---packages-to-install),
* [Steg 5 - Skapa steg](#step-5---creation-steps),
* [Steg 6 - Skapa databasen](#step-6---creating-the-database).

### Steg 1 - Välja databasmotor {#step-1---selecting-the-database-engine}

Välj databasmotorn bland dem i listrutan.

![](assets/s_ncs_install_db_select_engine.png)

Databaser som stöds visas i [avsnittets kompatibilitetsmatris](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html).

Identifiera servern och välj vilken typ av åtgärd som ska utföras. I det här fallet, **[!UICONTROL Create or recycle a database]**..

![](assets/s_ncs_install_db_oracle_creation01.png)

Beroende på vilken databasmotor som valts kan serveridentifieringsinformationen variera.

* För en **Oracle** -motor fyller du i det **TNS-namn** som definierats för programservern.
* För en **PostgreSQL** - eller **DB2** -motor måste du ange det DNS-namn (eller IP-adress) som definierats på programservern för att få åtkomst till databasservern.
* För en **Microsoft SQL Server** -motor måste du definiera:

   1. DNS-namnet (eller IP-adressen) som definierats på programservern för åtkomst till databasservern: **DNS** eller **DNS\`<instance>`**(instansläge),
   1. den autentiseringsmetod som används för att komma åt Microsoft SQL Server: **[!UICONTROL SQL Server authentication]** eller **[!UICONTROL Windows NT authentication]**.

      ![](assets/s_ncs_install_db_mssql_creation01.png)

### Steg 2 - Ansluta till servern {#step-2---connecting-to-the-server}

I **[!UICONTROL Server access]** fönstret definierar du databasserveråtkomsten.

![](assets/s_ncs_install_db_oracle_creation02.png)

Om du vill göra det anger du namn och lösenord för ett **administratörssystemkonto** som har behörighet att komma åt databaserna, dvs:

* **system** för en Oracle-databas,
* **som** för en Microsoft SQL Server-databas,
* **postgres** för en PostgreSQL-databas,
* **db2inst1** för en DB2-databas.

### Steg 3 - Databasens anslutning och egenskaper {#step-3---connection-and-characteristics-of-the-database}

I följande steg kan du konfigurera inställningarna för inloggning i databasen.

![](assets/s_ncs_install_db_oracle_creation03.png)

Du måste definiera följande inställningar:

* Ange namnet på den databas som ska skapas.

   >[!NOTE]
   >
   >För en DB2-databas får databasens namn inte vara längre än 8 tecken.

* Ange lösenordet för kontot som är länkat till den här databasen.
* Ange om databasen måste vara i Unicode eller inte.

   Med det här **[!UICONTROL Unicode database]** alternativet kan du lagra alla teckentyper i Unicode oavsett språk.

   >[!NOTE]
   >
   >Med en Oracle-databas kan du med det här **[!UICONTROL Unicode storage]** alternativet använda **typfälten NCLOB** och **NVARCHAR** .
   > 
   >Om du inte markerar det här alternativet måste teckenuppsättningen (teckenuppsättningen) för Oracle-databasen aktivera datalagring på alla språk (AL32UTF8 rekommenderas).

* Välj en tidszon för databasen och ange om den ska vara i UTC (om tillgängligt).

   Mer information finns i [Tidszonshantering](../../installation/using/time-zone-management.md).

### Steg 4 - Paket som ska installeras {#step-4---packages-to-install}

Markera de paket som du vill installera.

Se licensavtalet för att se vilka lösningar och alternativ du har rätt att installera, till exempel&quot;Interaktion&quot; eller&quot;Social marknadsföring&quot;.

![](assets/s_ncs_install_modules.png)

### Steg 5 - Skapa steg {#step-5---creation-steps}

I **[!UICONTROL Creation steps]** fönstret kan du visa och redigera det SQL-skript som användes för att skapa tabellerna.

![](assets/s_ncs_install_db_oracle_creation04.png)

* För en Oracle-, Microsoft SQL Server- eller PostgreSQL-databas kan administratören också definiera de **lagringsparametrar** som ska användas när databasobjekt skapas.

   De här parametrarna tar emot de exakta tabellutrymmesnamnen (varning: skiftlägeskänsligt). De lagras i noden **[!UICONTROL Administration > Platform > Options]** i följande alternativ:

   * **WdbcOptions_TableSpaceUser**: användartabeller baserade på ett schema
   * **WdbcOptions_TableSpaceIndex**: index för användartabeller baserat på ett schema
   * **WdbcOptions_TableSpaceWork**: arbetstabeller utan schema
   * **WdbcOptions_TableSpaceWorkIndex**: index för arbetstabeller utan schema

* För en Oracle-databas måste Adobe Campaign-användaren ha tillgång till Oracle-biblioteken, vanligtvis som medlem i **avinstallationsgruppen** .
* Med **[!UICONTROL Set or change the administrator password]** alternativet kan du ange lösenordet som är länkat till Adobe Campaign-operatorn med administratörsbehörighet.

   Vi rekommenderar att du definierar ett Adobe Campaign-kontoadministratörslösenord av säkerhetsskäl.

### Steg 6 - Skapa databasen {#step-6---creating-the-database}

I det sista steget i guiden kan du skapa databasen. Bekräfta genom **[!UICONTROL Start]** att klicka.

![](assets/s_ncs_install_db_oracle_creation06.png)

När databasen har skapats kan du ansluta igen för att slutföra instanskonfigurationen.

Du måste nu starta distributionsguiden för att slutföra konfigurationen av instansen. Se [Distributionsguiden](../../installation/using/deploying-an-instance.md#deployment-wizard).

Anslutningsinställningarna för databasen som är länkad till instansen lagras i filen som **`/conf/config-<instance>.xml`** finns i installationskatalogen för Adobe Campaign.

Exempel på en Microsoft SQL Server-konfiguration på base61-databasen som är länkad till kampanjkontot med dess krypterade lösenord:

```
<dbcnx encrypted="1" login="campaign:myBase" password="myPassword" provider="DB" server="dbServer"/>
```

## Fall 2: Använda en befintlig databas {#case-2--using-an-existing-database}

Databasen, liksom användaren, måste ha skapats av databasadministratören och behörigheterna måste vara korrekt konfigurerade.

För en Oracle-databas är till exempel lägsta nödvändiga behörighet: BEVILJA CONNECT, RESOURCE och UNLIMITED TABLESPACE.

Så här använder du en befintlig databas:

* [Steg 1 - Välj databasmotor](#step-1---choosing-the-database-engine),
* [Steg 2 - Databasanslutningsinställningar](#step-2---database-connection-settings),
* [Steg 3 - Paket som ska installeras](#step-3---packages-to-install),
* [Steg 4 - Skapa steg](#step-4---creation-steps),
* [Steg 5 - Skapa databasen](#step-5---creating-the-database).

### Steg 1 - Välja databasmotor {#step-1---choosing-the-database-engine}

Välj databasmotorn i listrutan.

![](assets/s_ncs_install_db_select_engine.png)

Identifiera servern och välj vilken typ av åtgärd du vill utföra. I det här fallet, **[!UICONTROL Use an existing database]**..

![](assets/s_ncs_install_db_oracle_exists_01.png)

Beroende på vilken databasmotor som valts kan serveridentifieringsinformationen variera.

* För en **Oracle** -motor fyller du i det **TNS-namn** som definierats för programservern.
* För en **PostgreSQL** - eller **DB2** -motor måste du ange det DNS-namn (eller IP-adress) som definierats på programservern för att få åtkomst till databasservern.
* För en **Microsoft SQL Server** -motor måste du definiera:

   1. det DNS-namn (eller den IP-adress) som definierats på programservern för åtkomst till databasservern,
   1. den säkerhetsmetod som används för att komma åt Microsoft SQL Server: **[!UICONTROL SQL Server authentication]** eller **[!UICONTROL Windows NT authentication]**.

      ![](assets/s_ncs_install_db_mssql_exists_01.png)

### Steg 2 - Inställningar för databasanslutning {#step-2---database-connection-settings}

I **[!UICONTROL Database]** fönstret definierar du inställningarna för databasanslutningen.

![](assets/s_ncs_install_db_oracle_exists_02.png)

Du måste definiera följande inställningar:

* Ange namnet på den databas som ska användas,
* Ange namn och lösenord för kontot som är kopplat till den här databasen,

   >[!NOTE]
   >
   >För en Oracle-databas behöver du inte ange kontonamnet.

* Ange om databasen ska vara Unicode eller inte.

### Steg 3 - Paket som ska installeras {#step-3---packages-to-install}

Markera de paket som du vill installera.

Se licensavtalet för att se vilka lösningar och alternativ du har rätt att installera, till exempel&quot;Interaktion&quot; eller&quot;Leads&quot;.

![](assets/s_ncs_install_modules.png)

### Steg 4 - Skapa steg {#step-4---creation-steps}

I **[!UICONTROL Creation steps]** fönstret kan du visa och redigera det SQL-skript som användes för att skapa tabellerna.

![](assets/s_ncs_install_db_oracle_creation04.png)

* För Oracle-, Microsoft SQL Server- eller PostgreSQL-databaser kan administratören definiera de **lagringsparametrar** som ska användas när databasobjekt skapas.
* För en Oracle-databas måste Adobe Campaign-användaren ha tillgång till Oracle-biblioteken, vanligtvis som medlem i **avinstallationsgruppen** .
* Med **[!UICONTROL Set or change the administrator password]** alternativet kan du ange lösenordet som är länkat till Adobe Campaign-operatorn med administratörsbehörighet.

   Vi rekommenderar att du definierar ett Adobe Campaign-kontoadministratörslösenord av säkerhetsskäl.

### Steg 5 - Skapa databasen {#step-5---creating-the-database}

I det sista steget i guiden kan du skapa databasen. Bekräfta genom **[!UICONTROL Start]** att klicka.

![](assets/s_ncs_install_db_oracle_creation06.png)

När databasen har skapats kan du ansluta igen för att slutföra instanskonfigurationen.

Du måste nu starta distributionsguiden för att slutföra konfigurationen av instansen. Se [Distributionsguiden](../../installation/using/deploying-an-instance.md#deployment-wizard).

Anslutningsinställningarna för databasen som är länkad till instansen lagras i filen som **`/conf/config-<instance>.xml`** finns i installationskatalogen för Adobe Campaign.

Exempel på en Microsoft SQL Server-konfiguration på base61-databasen som är länkad till kampanjkontot med dess krypterade lösenord:

```
<dbcnx encrypted="1" login="campaign:myBase" password="myPassword" provider="DB" server="dbServer"/>
```

