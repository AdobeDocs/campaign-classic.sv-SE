---
title: Vanliga kommandon
seo-title: Vanliga kommandon
description: Vanliga kommandon
seo-description: null
page-status-flag: never-activated
uuid: f06df8c0-d4ec-4d6b-84d5-f46d852388a3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: 90718075-87a7-4e9a-935b-571010908e79
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5f3ceab5ee82587d9f1829792bdabf2209f793cd

---


# Vanliga kommandon{#usual-commands}

I det här avsnittet visas de vanliga kommandona i Adobe Campaign.

Kommandot **nlserver** är indatakommandot för hela Adobe Campaign-programmet.

Det här kommandot har följande syntax: **nlserver **`<command>`****`<arguments>`****

Parametern **`<command>`** motsvarar modulen.

>[!NOTE]
>
>* I vilket fall som helst kan du lägga till argumentet **-noconsole** för att ta bort kommentarer som visas när modulerna har startats.
>* Omvänt kan du lägga till argumentet **-verbose** för att visa mer information.
>



## Övervakningskommandon {#monitoring-commands-}

>[!NOTE]
>
>Om du vill visa alla moduler måste du använda kommandot **nlserver pdump** .

Du kan lägga till parametern **-vem** för att lista pågående anslutningar (databas och program).

```
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

Ett annat användbart kommando är **lserver monitor**. Den listar XML-filen för övervakning (hämtas i Adobe Campaign-klienten eller via webbsidan **monitor.jsp** ).

Du kan lägga till den parameter som **saknas** för att visa de saknade modulerna (fel i moduler, moduler som stängs av osv.)

```
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
inMail@test
mta@test
wfserver@test
```

Detta motsvarar modulerna med automatisk start men som inte har startats.

## Kommandon för att starta modulen {#module-launch-commands}

Syntaxen för att starta moduler har fortfarande följande format:

```
nlserver start <module>@<INSTANCE>
```

```
nlserver stop <module>@<INSTANCE>
```

>[!NOTE]
>
>**`<instance>`** motsvarar namnet på instansen så som det anges i konfigurationsfilerna, eller **standardvärdet** för moduler med en instans.

## Stäng av tjänster {#shut-down-services}

Om du vill stoppa Adobe Campaign-tjänster använder du något av följande kommandon:

* Om du har rot- eller administratörsåtkomst:

   * I Linux:

      ```
      /etc/init.d/nlserver6 stop
      ```

   * I Windows:

      ```
      net stop nlserver6
      ```

* Om inte, så i Adobe Campaign-kontot:

   ```
   nlserver shutdown 
   ```

## Starta om tjänster {#restart-services}

På samma sätt kan du använda något av följande kommandon för att starta om Adobe Campaign:

* Om du har rot- eller administratörsåtkomst:

   * I Linux:/etc/init.d/nlserver6 - start
   * I Windows:net start nlserver6

* I annat fall, på Adobe Campaign-kontot: **nlserver watchdog -svc -noconsole**

## Kommandot config {#the-config-command}

Med **kommandot config** kan du hantera serverkonfigurationen, inklusive omkonfigurationen av databasanslutningen.

Använd kommandot **config** för den körbara **nlserver** -filen med parametern **-setdblogin** .

```
nlserver config -setdblogin:<[dbms:]account[:database][/password]@server>
```

```
nlserver config -setdblogin:PostgreSQL:<accountName>:test6@dbserver
```

Ange lösenordet.

Så här ändrar du det **interna** lösenordet: **nlserver config -internalPassword**

>[!CAUTION]
>
>Om du vill logga in med den **interna** identifieraren måste du ha definierat ett lösenord i förväg. Mer information finns i [det här avsnittet](../../installation/using/campaign-server-configuration.md#internal-identifier).

>[!NOTE]
>
>* I allmänhet kan du använda kommandot **config** i stället för att ändra konfigurationsfilerna manuellt
>* Använd **-? om du vill visa parameterlistan.** parameter: **nlserver config -?**
>* Om det är en Oracle-databas får du inte ange kontot. Syntaxen är följande:
>
>  
nlserver config -setdblogin:Oracle:test6@dbserver


