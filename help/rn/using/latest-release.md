---
product: campaign
title: Senaste versionen
description: Senaste versionsinformation för Campaign Classic v7
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: cdbcfc5aa0614e41ce76cb777fec58fbd01797d2
workflow-type: ht
source-wordcount: '903'
ht-degree: 100%

---

# Senaste versionen {#latest-release}

Den här sidan listar nya funktioner, förbättringar och korrigeringar som kommer med den **senaste versionen av Campaign Classic v7**. Varje ny version kommer med en status som visas med en färg. Läs mer om versionsstatusen för Campaign Classic v7 på [den här sidan](rn-overview.md).

## Version 7.4.2  {#release-7-4-2}

### Bygge 9391 {#build-9391}

[!BADGE Begränsad tillgänglighet]{type=Informative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=sv#rn-statuses" tooltip="Begränsad tillgänglighet"}

_12 maj 2025_

Bygget innehåller följande korrigeringar:

* Korrigerade ett efteruppgraderingsfel som påträffades i icke-Oracle-inställningar. (NEO-87012)
* Korrigerade ett TLS/HTTPS-serverdelsproblem som påverkade både klientkonsolen och servern. (NEO-87432)

### Bygge 9390 {#build-9390}

[!BADGE Allmän tillgänglighet]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=sv#rn-statuses" tooltip="Allmän tillgänglighet"}

_2 april 2025_

<!--
### Compatibility updates {#comp-7-4-2}

This release comes with the following compatibility updates:

* JQuery library update: fixes multiple UI issues (reports, web apps)
* PostgreSQL 15 and 16

-->

**Säkerhetsförbättringar**

Den här versionen innehåller flera säkerhetskorrigeringar.

Anslutningen till lösningar och appar från Adobe via det externa **[!UICONTROL Adobe Experience Cloud]**-kontot har uppdaterats för att stärka säkerheten.

**Stora korrigeringar**

Den här versionen kommer med följande huvudkorrigeringar:

* TLS-/SMPP-anslutning – korrigerade SMPP-stabilitetsproblem

* Google BigQuery-korrigeringar:

   * Korrigerade regressioner för BOOLEAN-datatyper
   * Korrigerade problem med proxyinställningar
   * Korrigerade regressioner för DATETIME-datatyper
   * Korrigerade bulklaststabilitet
   * Förbättrade interna tester av ODBC-versioner
   * Korrigerade ett problem med specialtecken i anslutningssträngen
   * Standardtimeout (5 min) för Google BigQuery-frågor har tagits bort

* MTA (Mail Transfer Agent) – korrigerade ett överblivet MTA-underordnat element som ska ha statusen **[!UICONTROL Start pending]**.


**Andra korrigeringar**

Följande problem har också korrigerats i den här versionen:

* Ett problem har korrigerats där aktiviteten **Datainläsning (fil)** inte kunde överföra filer till servern<!--after an upgrade to version 8.3.8-->. Användarna kan nu överföra filer utan att stöta på förlopp som fastnar eller konsolfel. (NEO-47269)

* Löste segmenteringsfel i Apache <!--following an upgrade to Adobe Campaign Classic 7.2.2 build 9349-->. Den här korrigeringen förhindrar att kärnfiler genereras och säkerställer en stabil serverdrift. (NEO-59059)

* Ett anslutningsproblem med Google BigQuery-databasen <!--after upgrading to version 7.3.3 build 9359--> har åtgärdats. Användarna kan nu testa anslutningarna med hjälp av det externa GCP-kontot. (NEO-62455)

* Förbättrad kompatibilitet för kolumnerna Boolean och Datetime i Google BigQuery-tabeller med federerad dataåtkomst (Federated Data Access, FDA). Med den här korrigeringen kan du hantera datatyper korrekt under infognings-/uppdateringsåtgärder. (NEO-65774)

* Korrigerade en sårbarhet vid resursinjektion som gjorde att angripare kunde injicera HTML-element i e-postslutpunkter. Den här säkerhetsförbättringen förhindrar obehörig åtkomst och försök till nätfiske. (NEO-66462)

* Löste intermittenta fel vid infogande av data i Google BigQuery-tabeller till följd av problem med HTTP-innehåll eller överföringskodning. Den här korrigeringen säkerställer stabila arbetsflöden för datainläsning. (NEO-66989)

* Åtgärdade en sårbarhet inom sökvägsförflyttning i metoden `File.list()` i arbetsflöden. Den här säkerhetsförbättringen förhindrar obehörig åtkomst till katalogen och skyddar känsliga filer. (NEO-77898)

* Ett problem har korrigerats där sms-leveransloggar inte uppdaterades korrekt till statusen ”togs emot på mobilen”. Den här förbättringen säkerställer korrekt leveransrapportering. (NEO-78843)

* Åtgärdade inloggningsfel i Adobe Campaign Classic vid användning av Azure Federated Data Access (FDA). Användarna kan nu logga in via klientkonsolen. (NEO-79373)

* Korrigerade en krasch i arbetsflöden som orsakades av metoden `CCurlAzureBlobStorage::UploadStream()`. Den här förbättringen säkerställer stabil arbetsflödeskörning. (NEO-79598)

* Två kritiska kompileringsflaggor (`ControlFlowGuard` och `StackProtection`) har aktiverats i Windows för att förbättra produktsäkerheten och minska risken för exploatering. (NEO-80145)

* Korrigerade ett problem där händelsestatusar skickades felaktigt medan broadloggen var i ett feltillstånd. Den här förbättringen säkerställer korrekt händelserapportering. (NEO-80245)

* POP3 OAuth-uppdatering och åtkomsttoken har nu sparats i databasen och felet `Authentication failure: unknown user name or bad password` visas inte längre efter att uppdateringstoken har upphört att gälla. (NEO-80683)

* Ett alternativ `XApiKey` används nu som värde för klient-ID för att ansluta till Adobe Analytics istället för att använda klient-ID för det externa Marketing Cloud-kontot (MAC). (NEO-80434)

* Ett problem där InMail-användare fick ett autentiseringsfel på grund förfallen token har åtgärdats. Användarna kan nu testa anslutningen och starta om servern för att lösa liknande problem. (NEO-80683)

* Förbättrade API-funktioner för analys genom att säkerställa att alla analysanrop använder en konsekvent API-nyckel (Campaign1) för autentisering, även när de byter till ett slumpmässigt klient-ID. Detta säkerställer en smidig analysspårning. (NEO-80434)

* Förbättrade BigQuery FDA-kopplingen (federerad dataåtkomst) genom att låta användare justera tidsgränsen för frågor. Den här förbättringen förhindrar tidsgränsfel för frågor som körs under lång tid. (NEO-81222)

* Uppdaterade uppgraderingsprocessen för Campaign <!--7.4.1-->-versionen för att inkludera nödvändiga beroenden. Den här förbättringen förenklar uppgraderingsprocessen för användare. (NEO-81433)

* Korrigerade ett problem med konsolkrasch när ett delarbetsflöde användes i kombination med ett `enum`-fält. Den här förbättringen säkerställer stabil arbetsflödeskörning. (NEO-81864)

* Löste ett problem där underordnade MTA-processer fastnade, vilket blockerade leveranstider. Den här korrigeringen säkerställer smidig leverans för Push- och WhatsApp-kommunikation. (NEO-82351)

* Korrigerade ett problem där leveranser fastnade i väntan på personalisering när leveransaktiviteter pausades. Den här förbättringen säkerställer att leveranser genomförs. (NEO-82781)

* Förbättrade IMS-inloggningsfunktioner genom att använda CampaignIO-slutpunkten för autentisering. Den här förbättringen effektiviserar inloggningsprocessen. (NEO-82838)

* Åtgärdade tidsgränsfel i Google BigQuery Federated Data Access (FDA) för att säkerställa stabil frågekörning efter distributionen av korrigeringen. (NEO-82923)

* Ett utrymmesproblem har åtgärdats vid inläsning av stora datavolymer i Teradata-tabeller. Den här förbättringen säkerställer stabil datainläsning. (NEO-83252)

* Korrigerade ett problem där GCP-frågor misslyckades på grund av felaktig matchning av jämförelser mellan datum och tidsstämpel <!--after upgrading to version 9383-->. Den här förbättringen säkerställer kompatibilitet för frågor. (NEO-83826)

* Åtgärdade leveransfel som orsakades av återupptagning av pausade leveransaktiviteter. Den här korrigeringen säkerställer att leveranser genomförs. (NEO-83809)

* Korrigerade autentiseringsfel med Snowflake Federated Data Access-kopplingen (FDA) när autentisering med privat nyckel användes. Den här förbättringen säkerställer att databasanslutningar kan genomföras. (NEO-84024)

* Implementerade övervakningsändringar för att åtgärda blockering av underordnade MTA-fack som orsakas av processer som har fastnat. Den här förbättringen säkerställer smidiga leveranser. (NEO-84553)

* Förenklade Javascript-väntekontroller för att åtgärda blockering av underordnade MTA-fack som orsakades av processer som befann sig i ett arbetstillstånd. Den här korrigeringen säkerställer stabila leveranser. (NEO-85150)

