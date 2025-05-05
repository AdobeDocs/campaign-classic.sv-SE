---
product: campaign
title: Vanliga kommandon
description: Vanliga kommandon
feature: Monitoring
badge-v7-prem: label="Endast lokal/hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 472ccc04-e68e-4ccb-90e9-7d626a4e794f
source-git-commit: b8a6a0db27826309456c285c08d4f1d85de70283
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 3%

---

# Vanliga kommandon{#usual-commands}



I det här avsnittet visas vanliga kommandon i Adobe Campaign.

Kommandot **nlserver** är indatakommandot för hela Adobe Campaign-programmet.

Det här kommandot har följande syntax: **nlserver &#x200B;**`<command>`**&#x200B;**`<arguments>`**&#x200B;**

Parametern **`<command>`** motsvarar modulen.

>[!NOTE]
>
>* I vilket fall som helst kan du lägga till argumentet **-noconsole** för att ta bort kommentarer som visas när modulerna har startats.
>* Omvänt kan du lägga till argumentet **-verbose** om du vill visa mer information.
>

## Övervakningskommandon {#monitoring-commands-}

>[!NOTE]
>
>Om du vill visa alla moduler måste du använda kommandot **nlserver pdump** .

Du kan lägga till parametern **-who** för att lista pågående anslutningar (databas och program).

```sql
nlserver pdump -who
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
web@default (9984) - 50.1 Mo
watchdog (2273) - 6.6 Mo
syslogd@default (9931) - 7.0 Mo
trackinglogd@default (9985) - 45.6 Mo
mta@test (9986) - 9.6 Mo
wfserver@test (9987) - 8.8 Mo

Connections ------------------------------------------------------
Last Access IP Instance Login 
DD/MM/YYYY HH:MM:SS 127.0.0.1 default formation_fr|tracking
DD/MM/YYYY HH:MM:SS 127.0.0.1 default internal|monitoring

Connection pool --------------------------------------------------
Datasource Server Provider Login 
default xxxxx myserver myprovider test400
```

Ett annat användbart kommando är **nlserver monitor**. Den listar XML-filen för övervakning (hämtas från Adobe Campaign-klienten eller via webbsidan **monitor.jsp**).

Du kan lägga till parametern **-missing** om du vill visa de saknade modulerna (fel i moduler, stängda moduler osv.)

```sql
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
inMail@test
mta@test
wfserver@test
```

Detta motsvarar modulerna med automatisk start men som inte har startats.

## Kommandon för att starta modulen {#module-launch-commands}

Syntaxen för att starta moduler har fortfarande följande format:

```sql
nlserver start <module>@<INSTANCE>
```

```sql
nlserver stop <module>@<INSTANCE>
```

>[!NOTE]
>
>**`<instance>`** motsvarar namnet på instansen enligt inställningarna i konfigurationsfilerna, eller **standard** för enkelinstansmoduler.

## Stäng av tjänster {#shut-down-services}

Om du vill stoppa Adobe Campaign-tjänster använder du något av följande kommandon:

* Om du har rot- eller administratörsåtkomst:

   * I Linux:

     ```sql
     /etc/init.d/nlserver6 stop
     ```

     >[!NOTE]
     >
     >Från 20.1 rekommenderar vi att du använder följande kommando i stället (för Linux): **systemctl stop nlserver**

   * I Windows:

     ```sql
     net stop nlserver6
     ```

* Om inte, så i Adobe Campaign-kontot:

  ```sql
  nlserver shutdown 
  ```

## Starta om tjänster {#restart-services}

På samma sätt kan du använda något av följande kommandon för att starta om Adobe Campaign:

* Om du har rot- eller administratörsåtkomst:

   * I Linux: `/etc/init.d/nlserver6 start`

     >[!NOTE]
     >
     >Från 20.1 rekommenderar vi att du använder följande kommando i stället (för Linux): **systemctl start nlserver**

   * I Windows: `net start nlserver6`

* I annat fall, i Adobe Campaign-kontot: **nlserver watchdog -svc -noconsole**

## Kommandot config {#the-config-command}

Med kommandot **config** kan du hantera serverkonfigurationen, inklusive omkonfigurationen av databasanslutningen.

Använd kommandot **config** i den körbara filen **nlserver** med parametern **-setdblogin** .

```sql
nlserver config -setdblogin:<[dbms:]account[:database][/password]@server>
```

```sql
nlserver config -setdblogin:PostgreSQL:<accountName>:test6@dbserver
```

Ange lösenordet.

Så här ändrar du det **interna** lösenordet: **nlserver config -internalPassword**

>[!IMPORTANT]
>
>Om du vill logga in med identifieraren **Internal** måste du ha definierat ett lösenord i förväg. Mer information om detta finns i [det här avsnittet](../../installation/using/configuring-campaign-server.md#internal-identifier).

>[!NOTE]
>
>* I allmänhet kan du använda kommandot **config** i stället för att ändra konfigurationsfilerna manuellt
>* Använd **-? om du vill hämta parameterlistan.**-parameter: **nlserver config -?**
>* Om det är en Oracle-databas får du inte ange kontot. Syntaxen är följande:
>
>  `nlserver config -setdblogin:Oracle:test6@dbserver`
>

Här är ett exempel för MSSQL:

```sql
nlserver config -setdblogin:mssql:<login>/"<password>"@<server> -instance:<instance_name> 
```

* inloggning (t.ex. account:user) och servern finns i noden dataSource i filen config-&lt;instance_name>.xml.
* Lösenordet måste omslutas med citattecken &quot;&quot;.

