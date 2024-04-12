---
product: campaign
title: Verksamhetsprincip
description: Verksamhetsprincip
feature: Monitoring
badge-v7-prem: label="Endast lokal/hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 1c032ef9-af11-4947-90c6-76cb9434ae85
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 1%

---

# Verksamhetsprincip{#operating-principle}



Tekniskt sett bygger Adobe Campaign-plattformen på flera moduler.

Det finns många Adobe Campaign-moduler. Vissa arbetar kontinuerligt medan andra startas ibland för att utföra administrativa uppgifter (t.ex. konfigurera databasanslutningen) eller för att köra en återkommande uppgift (t.ex. konsolidera spårningsinformation).

Det finns tre typer av Adobe Campaign-moduler:

* Moduler med flera instanser: en enda process körs för alla instanser. Detta gäller följande moduler: **webb**, **syslogd**, **trackinglogd** och **övervakningsenhet** (aktiviteter från **config-default.xml** fil).
* Eninstansmoduler: en process körs per instans. Detta gäller följande moduler: **mta**, **wfserver**, **inMail**, **sms** och **stat** (aktiviteter från **config-`<instance>`XML** fil).
* Verktygsmoduler: det här är moduler som körs ibland för att utföra tillfälliga eller återkommande åtgärder (**rensa**, **config**, hämtar spårningsloggar osv.).

Moduladministration utförs med kommandoradsverktyget **nlserver** som finns i **bin** installationsmappen.

Den allmänna syntaxen för **nlserver** är följande:

**nlserver `<command>``<command arguments>`**

I listan över tillgängliga moduler använder du **nlserver** -kommando.

De tillgängliga modulerna beskrivs i följande tabell:

| Kommando | Beskrivning |
|---|---|
| aliasCleansing | Standardisera uppräkningsvärden |
| fakturering | Skicka systemaktivitetsrapporten till billing@neolane.net |
| rensa | Rensar databasen: tar bort föråldrade data från databasen och kör en uppdatering av statistiken som används av databasmotoroptimeraren. |
| config | Ändrar serverkonfiguration |
| export | Exportera till kommandorad: gör att du kan skicka en exportmodell som skapats i Adobe Campaign klientkonsol till kommandoraden |
| filconvert | Konvertera en fil med fast storlek |
| import | Importera till kommandoraden: gör att du kan skicka en importmodell som skapats i Adobe Campaign klientkonsol till kommandoraden. |
| inMail | Analysera inkommande e-post |
| installsetup | Tillgång till kundinstallationsfilen |
| javascript | Köra JavaScript-skript med tillgång till SOAP API:er. |
| jobb | Kommandoradsbearbetning |
| sammanfoga | Koppla formulär |
| midSource | Återvinning av leveransinformation i läget mitt i källkoden |
| monitor | XML Visa status för serverprocesser och schemalagda aktiviteter, som exempel. |
| mta | Överföringsmeddelande för huvudagent |
| package | Importera eller exportera enhetspaketfiler |
| pdump | Visa status för serverprocess |
| förberedda | Förbereda en leveransåtgärd |
| starta | Omstart av partiell server |
| runwf | Körning av en arbetsflödesinstans |
| avstängning | Fullständig systemavstängning |
| sms | SMS-meddelandebearbetning |
| sql | SQL-skriptkörning |
| start | Ytterligare starter |
| stat | Underhåller statistik för MTA-anslutning |
| stop | Delvis avstängning av systemet |
| inskickad | Skicka en leveransåtgärd |
| syslogd | Logga och spåra skrivserver |
| spårning | Konsolidera och hämta spårningsloggar |
| trackinglogd | Spåra loggskrivnings- och tömningsserver |
| övervakningsenhet | Instans för start och övervakning |
| webb | Programserver (HTTP och SOAP) |
| wfserver | Arbetsflödesserver |

>[!IMPORTANT]
>
>Det finns en sista modul: Modulen för spårning och vidarebefordran som är länkad till programservern, som för prestandans skull är integrerad via inbyggda mekanismer i en Apache- eller IIS-webbserver via ett dynamiskt bibliotek. Det finns inget Adobe Campaign-kommando som du kan använda för att starta eller administrera den här modulen. Du måste därför använda kommandona från själva webbservern.

Modulanvändning och syntaxen för dess parametrar visas med följande kommando: **nlserver `[module]` -?**

Exempel:

**nlserver config -?**

```
Usage: nlserver [-verbose:<verbose mode>] [-?|h|H] [-version] [-noconsole]
 [-tracefile:<file>] [-tracefilter:<[type|!type],...>]
 [-instance:<instance>] [-low] [-high] [-queryplans] [-detach]
 [-internalpassword:<[password/newpassword]>] [-postupgrade]
 [-nogenschema] [-force] [-allinstances]
 [-addinstance:<instance/DNS masks[/language]>]
 [-setdblogin:<[dbms:]account[:database][/password]@server>]
 [-monoinstance]
 [-addtrackinginstance:<instance/masks DNS[/databaseId/[/language[/password]]]>]
 [-trackingpassword:<[password][/newpassword]>]
 [-setproxy:<protocol/server:port[/login]>] [-reload]
 [-applyxsl:<schema/file.xsl>] [-filter:<file>]
 [-setactivationkey:<activation key>]
 [-getactivationkey:<client identifier>]
-verbose : verbose mode
-? : display this help message
-version : display version number
-noconsole : no longer display logs and traces on the console
-tracefile : name of trace file to be generated (without extension)
-tracefilter : filter for the traces to be generated e.g.: wdbc,soap,!xtkquery.
-instance : instance to be used (default instance if this option is not present).
-low : start up with low priority
-high : start up with high priority (not recommended)
-queryplans : generate traces with the execution plans of SQL queries.
-detach : detaches the process from its parent (internal option)
-internalpassword : changes the password of the server internal account.
-postupgrade : updates the database following upgrade to a higher version. 
-nogenschema : does not recompute the schemas during database update
-force : updates the database even if this has already been done with the current build 
-allinstances : updates the database over all configured instances
-addinstance : adds a new instance.
-setdblogin : sets the parameters for connection to the database of an instance. The DBMS can be 'oracle', 'postgresql', 'mssql' or 'odbc' (default=postgresql)
-monoinstance : initializes for a single instance ().
-addtrackinginstance : adds a new tracking instance.
-trackingpassword : changes the tracking password of an instance
-setproxy : sets the parameters for connection to a proxy server. The protocol can be 'http', 'https' or 'all'.
-reload : asks the server to reload the configuration of the instances. 
-applyxsl : applies an XSL stylesheet to all entities of a schema. 
-filter : applies the XTK filter contained in the file during loading of the schema entities.
-setactivationkey : sets the activation key
```
