---
product: campaign
title: Senaste versionen
description: Senaste versionsinformation för Campaign Classic v7
feature: Release Notes
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: abaeef25b03a9699a4851786380d467bfa299c9f
workflow-type: tm+mt
source-wordcount: '1873'
ht-degree: 98%

---

# Senaste versionen{#latest-release}

Den här sidan listar nya funktioner, förbättringar och korrigeringar som kommer med den **senaste versionen av Campaign Classic v7**. Varje ny version kommer med en status som visas med en färg. Läs mer om versionsstatusen för Campaign Classic v7 på [den här sidan](rn-overview.md).

## Version 7.3.4 – build 9364 {#release-7-3-4}

[!BADGE Allmän tillgänglighet]{type=Informative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=sv#rn-statuses" tooltip="Allmän tillgänglighet"}

>[!CAUTION]
>
>Uppgradering av klientkonsolen är obligatorisk. Lär dig hur du uppgraderar din klientkonsol på den här [sidan](../../installation/using/installing-the-client-console.md).
>
> Om du använder [Campaign – Microsoft Dynamics CRM Connector](../../platform/using/crm-connectors.md)måste du uppgradera både din marknadsföring och dina mid-sourcingsservrar med den här nya builden.

_7 september 2023_

**Säkerhetsförbättring**

* Säkerheten har förbättrats i API:erna för IMS. Klientkänslig information (t.ex. åtkomsttoken) har tagits bort från URL-parametrar. Dessa referenser skickas nu i postdata- eller auktoriseringshuvudet, vilket säkerställer en säkrare kommunikationsprocess. (NEO-63045)
* Säkerheten har förbättrats i webbprogram för att förhindra DDOS-attacker. (NEO-50757)
* Säkerheten har förbättrats för att förhindra att PII-data visas i webbloggfelen. (NEO-46827)
* Säkerheten har optimerats för att förhindra att säkerhetstoken inkluderas i URL:en för Campaign-hemsidan. (NEO-38519)

**Kompatibilitetsuppdateringar**

* Tomcat har uppdaterats till version 8.5.91
* Libexpat-biblioteket har uppdaterats till 2.5.0 för att förbättra säkerheten. (NEO-51023)

**Förbättringar**

* Parametern MaxWorkingSetMb i serverkonfigurationsfilen (serverConf.xml) har ändrats för att optimera minnesallokeringen för leveranser. (NEO-49204)
* Det externa BigQuery-kontot har förbättrats med nya alternativ som används för att konfigurera GCloud SDK. (NEO-63879) [Läs mer](../../installation/using/configure-fda-google-big-query.md#google-external)
* En ny `cusHeader` har lagts till i serverkonfigurationsfilen (serverConf.xml). Den låter dig lägga till anpassade rubriker när du laddar upp en fil från en extern server. (NEO-58339) [Läs mer](../../installation/using/the-server-configuration-file.md#cusheaders).
* Hanteringen av spårningsloggen har förbättrats för att undvika negativa ID:n för lastMsgId. Den har ändrats från int32 till int64. (NEO-52290)
* Mid-sourcingsarbetsflödet (leveransstatistik) har lagts till direkt. Det nya arbetsflödet synkroniserar leveransstatistik (nms:deliveryStat) från mitten till marknadsinstansen. (NEO-36802)

**Korrigeringar**

* Korrigerade ett problem som kunde inträffa när en tjänstbegäran gjordes före IMS-inloggning, om autentiseringen av anropet till tjänsten använde en tjänsttoken. (NEO-64903)
* Korrigerade ett regressionsproblem som kan leda till skrollningsproblem när du använder Redigeraren för digitalt innehåll. (NEO-64671, NEO-59256)
* Korrigerade ett regressionsproblem när innehåll klistrades in från Excel till Redigeraren för digitalt innehåll. (NEO-63287)
* Korrigerade ett problem som kunde förhindra att webbprogram visas korrekt i v5-kompatibilitetsläge. (NEO-63174)
* Korrigerade ett problem som förhindrade icke-adminoperatörer från att skicka webAnalytics-leveranser. (NEO-62750)
* Korrigerade ett problem som förhindrar att webbläsare lägger till extra mellanslag när villkorsstyrt innehåll används i en leverans. (NEO-62132)
* Korrigerade ett regressionsproblem som förhindrade att den aktiva kontaktberäkningen fungerade korrekt i faktureringsarbetsflödet när målscheman som är associerade med flera loggscheman användes. (NEO-61468)
* Korrigerade ett problem som kan leda till ett fel och förhindra att du skrollar när du redigerar innehållet i en leverans. (NEO-61364)
* Korrigerade ett problem som gjorde att ett popup-fönster öppnades när du klickade på en bild i e-postredigeraren. (NEO-60752)
* Korrigerade ett problem som kunde leda till att specialtecken i HTML-innehållet i en leverans kodades felaktigt i flera webbläsare. (NEO-60081)
* Korrigerade ett synkroniseringsfel som kan uppstå när arbetsflödesaktiviteten i InSMS används. (NEO-59544)
* Korrigerade ett problem när Big Query-anslutningen användes med fält för tidsstämpel eller datum/tid. (NEO-59502, NEO-49768)
* Korrigerade ett problem som gjorde att du inte kunde använda kumulativa leveransrapporter. (NEO-59211)
* Korrigerade ett problem som kunde leda till fel när målgrupper delades med People Core Service. (NEO-58637)
* Korrigerade ett problem när spegelsidan för en leverans visades. (NEO-58325)
* Korrigerade ett problem som gjorde att xtk-uttrycket XtkLibrary.Right() inte fungerade. (NEO-57870)
* Korrigerade ett problem som ledde till att formategenskapen för brödtexttaggen ändrades när en bild laddades upp i Redigeraren för digitalt innehåll. (NEO-57697)
* Korrigerade ett problem med specialtecken vid utförandet av massexport med CRM-anslutningsaktiviteten. (NEO-54300)
* Korrigerade ett problem som förhindrade massinläsning från att arbeta med datatyperna ”sträng” när en datainläsningsaktivitet och Big Query-anslutningen användes. (NEO-53748)
* Korrigerade ett cachenyckelproblem som kunde leda till problem med återgivningen. (NEO-51516, NEO-49995)
* Korrigerade ett problem som kan leda till ett valideringsfel när en leverans med direktmeddelanden skickas med targetMapping med godkännanden. (NEO-50758)
* Korrigerade ett frågehanteringsproblem som kunde påverka leveransresultatet. (NEO-49991)
* Korrigerade ett problem när externa konton används i aktiviteter för Campaign-arbetsflöde, vilket kan leda till problem med konfigurationen av externa konton. (NEO-49959)
* Korrigerade ett prestandaproblem när push-meddelanden skickades. (NEO-49953) 
Korrigerade ett fel som kunde medföra att japanska tecken inte visades korrekt vid export av rapporter (NEO-49308).
* Korrigerade ett fel som gjorde att Tomcat-felrapporten visade för mycket felinformation. (NEO-49029)
* Korrigerade ett problem som kunde leda till ett leveransfel vid användning av ett stort antal erbjudanden. (NEO-48807)
* Korrigerade ett problem som kunde förhindra att arbetsflödesaktiviteten **Uppdatera data** fungerade korrekt. (NEO-48140)
* Korrigerade ett problem som kunde förhindra att klickspårningsdata synkroniseras för leveranser med ett annat externt konto än e-post.(NEO-47277)
* Korrigerade ett problem som kunde förhindra att loggar för realtidsspårning synkroniseras på Message Center-marknadsinstansen. (NEO-42540)
* Korrigerade ett problem som gjorde att arbetsyteprefixet inte kunde visas i identifieringsfönstret för ett schema för databastabeller i Snowflake. (NEO-40297)
* Korrigerade ett fel som förhindrade `<img-amp>`-taggar från att arbeta med e-postinnehåll. (NEO-38685)
* Korrigerade ett problem som kunde få arkiveringsarbetsflödet i Message Center att misslyckas när ett HTTP-relä användes. (NEO-33783)
* Korrigerade ett problem som kunde orsaka fel i teckensnittsnamn och storlek i e-postinnehållets redigerare. (NEO-61342)

## Version 7.3.3 – build 9359 {#release-7-3-3}

[!BADGE Begränsad tillgänglighet]{type=Neutral url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=sv#rn-statuses" tooltip="Begränsad tillgänglighet"}

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

* Social marknadsföring med Facebook är nu inaktuell. Du kan använda X-integrering (tidigare Twitter) för att publicera på sociala medier, eller arbeta med Adobe för att skapa en anpassad kanal.
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
