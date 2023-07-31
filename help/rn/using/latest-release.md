---
product: campaign
title: Senaste versionen
description: Senaste versionsinformation för Campaign Classic v7
feature: Release Notes
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '993'
ht-degree: 100%

---

# Senaste versionen{#latest-release}

Den här sidan listar nya funktioner, förbättringar och korrigeringar som kommer med den **senaste versionen av Campaign Classic v7**. Varje ny version kommer med en status som visas med en färg. Läs mer om versionsstatusen för Campaign Classic v7 på [den här sidan](rn-overview.md).

## Version 7.3.3 – build 9359 {#release-7-3-3}

[!BADGE Allmän tillgänglighet]{type=Informative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=sv#rn-statuses" tooltip="Allmän tillgänglighet"}

>[!CAUTION]
>
>Uppgradering av klientkonsolen är obligatorisk. Lär dig hur du uppgraderar din klientkonsol på den här [sidan](../../installation/using/installing-the-client-console.md).

_20 mars 2023_

**Säkerhetsförbättring**

* För att optimera säkerheten har Tomcat uppdaterats från version 8.5.81 till 8.5.85. (NEO-56936)

**Förbättringar**

* Arbetsflödet för fakturering har förbättrats för att optimera prestanda. (NEO-47658)
* Arbetsflödet för spårning har förbättrats för att optimera prestanda om leveransstorleken är hög. (NEO-45064)
* Spårningshanteraren har förbättrats för att åtgärda eventuella problem med dynamiska parametrar i URL:er. Spårningshanteraren v3 hanterar nu URL:er av typen ajax (med parametrar efter ”#”) och förhindrar att verktyg från tredje part ändrar spårnings-URL:er. Om du vill tillämpa den här ändringen måste du kontakta Adobe. (NEO-46535)

<!--To apply this change, the marketing, tracking and mid servers need to be updated to 7.3.3. To enable the new tracking management mode, set the `emailLinksVersion` parameter to '3' in the configuration file of the marketing server. (NEO-46535)-->

**Korrigeringar**

* Korrigerade ett problem som kunde förhindra att push-meddelanden för korrektur i iOS skickades från kontrollinstansen (kontext för transaktionsmeddelanden). (NEO-54713)
* Korrigerade ett problem som kunde förhindra dig från att skrolla i fliken **Redigera** i Redigeraren för digitalt innehåll (DCE). (NEO-54474)
* Korrigerade ett problem där två berikningsaktiviteter använde samma namnidentifierare i sin länkning, vilket ledde till att den andra berikningsaktiviteten använde länkarna till den första. (NEO-48851)

## Version 7.3.2 – build 9356 {#release-7-3-2}

[!BADGE Begränsad tillgänglighet]{type=Neutral url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=sv#rn-statuses" tooltip="Begränsad tillgänglighet"}

_21 november 2022_

>[!CAUTION]
>
>Uppgradering av klientkonsolen är obligatorisk. Lär dig hur du uppgraderar din klientkonsol på den här [sidan](../../installation/using/installing-the-client-console.md).

**Kompatibilitetsuppdateringar**

* Adobe Campaign är nu kompatibelt med PostgreSQL 14. Mer information hittar du i detta [tekniska dokument](../../technotes/using/tech-stack-upgrade.md).

* Efter att Microsoft Internet Explorer 11 har nått slutet av sin livscykel använder nu HTML-återgivningsmotorn för kontrollpaneler i klientkonsolen Edge Chromium. (NEO-20741)

Läs mer i [kompatibilitetsmatrisen för Campaign](../../rn/using/compatibility-matrix.md#RDBMSservers).

**Förbättringar**

* Google BigQuery-anslutningen har nu fullständigt stöd för booleska fält. (NEO-49181)
* Nu kan du konfigurera giltighetsperioden för IMS-cookies i avsnittet `Configuration for the redirection service` i filen serverConf.xml. Detta gäller följande cookies: `uuid230`, `nllastdelid` och `AMCV_` (NEO-42541)
* IP-adressen kan nu döljas i begäran /r/test genom att ange `showSourceIP` som felaktig i omdirigeringsnoden för filen serverConf.xml. [Läs mer](../../installation/using/the-server-configuration-file.md#redirection-redirection)(NEO-46656)

**Inaktuella funktioner**

* Social marknadsföring med Facebook är nu inaktuell. Du kan använda Twitter-integrering för att publicera på sociala medier, eller arbeta med Adobe för att skapa en anpassad kanal.
* ACS-anslutning (Prime-erbjudande) är nu inaktuell. Du kan använda funktionerna export/import för Campaign för att extrahera och mata in data i båda produkterna.

Läs mer på sidan [Funktioner som är inaktuella eller har tagits bort](deprecated-features.md).

**Andra ändringar**

* Webbloggarna har förbättrats: `logonEscalation` varningar visas nu endast för användare med administratörsbehörighet. (NEO-47167)
* För att undvika fel stoppas nu arbetsflödet **Samla in data för tjänsten Heatmap** (collectDataHeatMapService) som standard. (NEO-33959)
* Flera förbättringar har implementerats för att optimera processoranvändningen för kontrollpanelen för kampanjer. (NEO-46417)
* För att förhindra krascher har JS-metoden loadLibraryDebug tagits bort. (NEO-46968)
* Återstående referenser till log4j-biblioteket har tagits bort från Campaign-installationen i Windows. (NEO-44851)

**Korrigeringar**

* Korrigerade ett problem som hindrade dig från att använda arbetsflödesalternativet **Sammanfoga markerade rader**. (NEO-48488)
* Korrigerade ett problem som förhindrade leveransindikatorn **Lyckades** från att uppdateras korrekt när du använder Adobe Campaign Enhanced MTA. (NEO-50462)
* Korrigerade ett problem som orsakade att du inte kunde godkänna innehållet i ett e-postmeddelande på nytt. (NEO-44259)
* Korrigerade ett problem som kunde förhindra knappen **Leveransgodkännande** från att visas. (NEO-47547)
* Korrigerade ett prestandaproblem på fliken HTML för en leverans som kan uppstå för stor HTML-kod. (NEO-47440)
* Korrigerade ett problem som påverkade statusuppdateringarna för leveransloggen på MID-instansen när alternativet `FeatureFlag_GZIP_Compression` aktiverades. (NEO-49183)
* Korrigerade ett problem som förhindrade dig från att skicka aviseringar från iOS-mobilappar från en körningsinstans när du använde tokenbaserad autentisering. (NEO-45961)
* Korrigerade ett problem med arbetsflödet **Uppdatera för leverans** (deliverabilityUpdate) som fastnade när det fanns för många utsändningsloggar att synkronisera. (NEO-48287)
* Korrigerade ett problem med händelsetypen som blockerade arbetsflödet **Synkronisering av meddelandecenter** (mcSynch).
* Korrigerade ett problem som kan leda till ett fel när indikatorn **Mottagare som har öppnat** (estimatedRecipientOpen) lades till i ytterligare data för arbetsflödesaktiviteten **Fråga**. (NEO-46665)
* Korrigerade ett problem med arbetsflödet **Fakturering** som misslyckades när paket för Message Center Control och körning installerades på samma instans. (NEO-47674)
* Korrigerade ett problem med arbetsflödet **Fakturering** som misslyckades när tabeller med primärnyckeln definierad som en sträng i stället för ett heltal ingår. (NEO-46254)
* Korrigerade ett problem med heatmap-filter när arbetsflödets namn var för långt. (NEO-46301)
* Korrigerade ett fel som introducerades i 7.3.1 på Snowflake FDA-anslutning som ledde till att poster utelämnades när ”0 eller 1 enkel kardinalitetsanslutning” användes under berikningen. (NEO-48737)
* Korrigerade ett problem med Snowflake FFDA när sorteringsparametern används i arbetsflödesaktiviteten **Dela**. (NEO-45899)
* Korrigerade ett problem som kunde förhindra dig från att spara konfiguration för externt konto. Det externa kontot sparas nu automatiskt efter anslutningstestet för anslutningar med tolkningsfunktioner (Snowflake och Google BigQuery). (NEO-47636)
* Korrigerade ett problem som gjorde att du inte kunde infoga en tidsdatatyp i arbetsflödesaktiviteten **Datauppdatering** på MSSQL. (NEO-47763)
* Korrigerade ett problem som ledde till att MTA-processen kraschade när motorns tidszon inte hade angetts (gäller för MSSQL). (NEO-46619)
* Korrigerade ett problem med import av HTML-fil när bildnoder (img) innehöll URL:er med personaliseringsfält. (NEO-48396)
* Korrigerade ett HTTP 500-fel vid försök att ansluta till en instans där `limit`-noden har inte konfigurerats i filen serverConf.xml.
* Korrigerade ett problem som kan leda till felet Felmatchad teckenuppsättning vid användning av vissa funktioner som `to_nclob` med en Oracle Unicode-databas där NChar inte aktiverats. (NEO-49361)
* Korrigerade ett problem som orsakade ett fel när en användare med läsbehörighet i mappen nmsDeliveryMapping försökte köra en kampanj eller ett arbetsflöde. (NEO-48230)
* Korrigerade ett problem som förhindrade funktionen `JSPContext.sqlExecWithOneParam` från att arbeta. (NEO-50066)
* Korrigerade olika omdirigeringsfel. (NEO-50030)
