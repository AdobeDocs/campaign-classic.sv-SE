---
product: campaign
title: Senaste versionen
description: Versionsinformation om senaste Campaign Classic v7
feature: Overview
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: e4dfdd32c07753ee9e202ab4e4bf815485e47d8b
workflow-type: tm+mt
source-wordcount: '1032'
ht-degree: 3%

---

# Senaste versionen{#latest-release}

![](../../assets/v7-only.svg)

På den här sidan visas nya funktioner, förbättringar och korrigeringar som ingår i **senaste Campaign Classic v7-utgåvan**. Varje ny version har en status som materialiseras av en färg. Läs mer om byggstatus för Campaign Classic v7 i [den här sidan](rn-overview.md).

## ![](assets/do-not-localize/green_2.png) Version 7.2.1 – build 9346 {#release-7-2-1}

_10 januari 2022_

**Säkerhetsförbättring**

Flera säkerhetsförbättringar har gjorts i FDA-konton:

* ODBC-drivrutiner installeras nu direkt med Adobe Campaign Third Party. Manuella steg krävs inte längre för att installera dessa drivrutiner.
* När du konfigurerar ditt externa FDA-konto kan du nu logga in på ditt Snowflake-konto med nyckelpars autentisering för förbättrad autentiseringssäkerhet. [Läs mer](../../installation/using/configure-fda-snowflake.md)
* När du konfigurerar ett externt FDA-konto kan du nu logga in på ditt Azure synapse Analytics-konto med hjälp av den systemtilldelade hanterade identiteten. [Läs mer](../../installation/using/configure-fda-synapse.md#azure-external)


**Förbättringar**

* Microsoft Dynamics CRM 365 Connector

   Kritiska korrigeringar har tillämpats för webb-API:t för Microsoft Dynamics Connector:

   * Korrigerade ett problem, under en import som utlöstes av ett arbetsflöde, som gjorde att null-värden för strängtypsfält sparades som null i stället för som tomma värden.
   * Ett problem som orsakade följande fel vid import eller export av data med webb-API-anrop har korrigerats: &quot;Ogiltig URI: URI-schemat är för långt.&quot;
   * Olika problem med import av data som innehåller sökfält från Microsoft Dynamics 365 har korrigerats.

* Google BigQuery FDA Connector

   * Google BigQuery FDA Connector är nu tillgänglig för värdbaserade distributioner. [Läs mer](../../installation/using/configure-fda-google-big-query.md)
   * Stöd har lagts till för att aktivera anslutningar till en proxyserver för Google BigQuery FDA-anslutning. Du kan ange nödvändiga proxyalternativ i fältet Alternativ i konfigurationen för det externa kontot. [Läs mer](../../installation/using/configure-fda-google-big-query.md#google-external)

**Andra ändringar**

* Efter borttagningen har åtgärderna Microsoft CRM, Salesforce och Oracle CRM On Demand tagits bort från gränssnittet. Om du vill konfigurera datasynkroniseringen mellan Adobe Campaign och ett CRM-system kan du använda CRM-anslutningsaktiviteten. [Läs mer](../../workflow/using/crm-connector.md)
* The **[!UICONTROL Encrypted identifier]** fältet har lagts till i besökarschemat (nms:visitor). Det här fältet beräknas och ska användas för webbprogram. Detta gäller när Line-kanalen är konfigurerad på mellankällarinstansen.
* CRM-datakällor kan nu användas med **Ändra datakälla** aktivitet.
* Ett nytt alternativ har lagts till i **Felhantering** egenskaper för arbetsflödesaktiviteter: The **Avbryt vid fel** kommer att stoppa arbetsflödet automatiskt. Du kommer inte att kunna starta om den efteråt (NEO-29661). [Läs mer](../../workflow/using/advanced-parameters.md#in-case-of-errors)
* En dedikerad sekvens används nu för att generera primärnycklar för tabellen nmsGroup, som används för att skapa statistiska grupper av mottagare. Tidigare användes xtknownId-sekvensen. (NEO-30832)
* Stöd för batchuppdateringsåtgärder har lagts till med CRM-anslutningsaktiviteten.

**Felkorrigeringar**

* Ett problem som orsakade ett fel i **Bilder** -fliken i **Spårning och bilder** -fönstret. Detta inträffade när en automatisk proxykonfiguration användes. (NEO-33260)
* Korrigerade ett problem som kunde förhindra dig från att överföra en fil till en Debian 10-server (HTTPS) i synkront läge.
* Ett problem som kunde förhindra poster i tabellen för leveransstatistik har korrigerats (`nmsDeliveryLogStats`) rensas från mellankällarinstansen under databasrensning efter att relaterade leveranser har tagits bort. (NEO-31034)
* Ett problem som gjorde att du inte kunde skicka mobilappsmeddelanden på iOS när du använde tokenbaserad autentisering (NEO-38640) har åtgärdats.
* Korrigerade ett problem som kunde visa skriptfelmeddelanden när rapporter skulle skapas och konfigureras (NEO-38393).
* Korrigerade ett problem som kunde göra att arbetsflödet för spårning misslyckades på Oraclet på grund av att stora volymer leveransindikatorer uppdateras samtidigt (NEO-39653).
* Korrigerade ett problem som kunde förhindra att en leverans skickades på grund av ett fel som uppstod när en kontrolltypologi kördes (NEO-39833).
* Korrigerade ett fel på landningssidor som kunde förhindra att specialtecken visas korrekt på HTML-sidorna i onlinesvarningar (NEO-39438).
* Ett problem som kunde förhindra Campaign Classic-konsolen från att fungera när du högerklickade på någon av mapparna på Utforskarfliken (NEO-38884) har korrigerats.
* Ett fel har korrigerats när en leveransmall som är länkad till ett Web Analytics-konto används i en ny leverans där Web Analytics-konfigurationen saknas. (NEO-28666)
* Ett problem som kunde förhindra dig från att förhandsgranska mobila leveranser som var kopplade till ett arbetsflöde har åtgärdats.
* Korrigerade ett fel som förhindrade att personaliserade spårnings-URL:er omdirigeras när URL-signaturmekanismen för spårning av länkar aktiverades.
* Korrigerade ett problem som kunde orsaka fel efter uppgraderingen på grund av ett problem med indexhantering.
* Ett fel som uppstod när datatyperna för sökfält användes med Microsoft Dynamics CRM i **Importera** eller **Exportera** arbetsflödesaktiviteter.
* Korrigerade ett problem som kunde förhindra dig från att logga in på konsolen på grund av ett proxykonfigurationsproblem. (NEO-38388)
* Ett regressionsproblem som förhindrade **Rensa mapp** funktionen inte fungerar som den ska. (NEO-37459)
* Korrigerade ett problem som ledde till ett felaktigt begärandefel när xml-datafält användes med Microsoft Dynamics CRM-kontot om den refererade xml-filen innehöll dubbla citattecken.
* Korrigerade ett problem som orsakade att problem med nätverkstimeout inte loggades korrekt som problem med skriptavbrott i stället för nätverksfel. Detta problem uppstod vid HTTP-begäranden som inkluderades i JavaScript-aktiviteter. (NEO-38079)
* Korrigerade ett problem som returnerade felaktiga resultat när funktionerna Amazon Redshift HoursDiff och MinutesDiff kördes när tidskomponenten skulle extraheras.(NEO-31673)
* Ett problem som förhindrade **Hot Clicks** rapportera från inläsning för leveranser sedan version 9182. (NEO-28900)
* Ett fel som ersatte &amp;-symbolen i en URL med teckenentitetsreferensen (`&amp;`) som förhindrar användare att få åtkomst till den URL som är länkad till en QR-kod. (NEO-28621)
* Korrigerade ett problem som skapade ett nytt externt konto varje gång en användare skapade ett nytt kampanjarbetsflöde och en leveransaktivitet länkad till ett Web Analytics-konto. Detta orsakades av ett saknat ID i leveransobjektet webAnalyticsAccount. (NEO-39691)
* Ett problem som kunde förhindra **Läslista** arbetsflödesaktivitet från att fungera när listan identifierades i databasen med ett negativt ID. (NEO-39607)
* Ett problem som kunde leda till **Mid-sourcing (leveransloggar)** arbetsflödet misslyckas. (NEO-39662)
* Ett problem som kunde förhindra dig från att förhandsgranska e-postleveranser som var kopplade till ett arbetsflöde har åtgärdats. (NEO-37840)
* Korrigerade ett problem som kunde medföra att giltiga tabeller som innehöll listvärden togs bort av arbetsflödet för databasrensning. (NEO-34911)
* Korrigerade ett problem som kunde få faktureringsarbetsflödet att krascha på marknadsinstanser.
