---
solution: Campaign Classic
product: campaign
title: Senaste versionen
description: Senaste versionsinformationen om Campaign Classic
audience: rns
content-type: reference
topic-tags: latest-release-notes
translation-type: tm+mt
source-git-commit: 14513d5ecbfdd5637b764c8f19bc01358e63c130
workflow-type: tm+mt
source-wordcount: '903'
ht-degree: 18%

---


# Senaste versionen{#latest-release}

Den här sidan listar nya funktioner, förbättringar och korrigeringar som ingår i den **senaste versionen av Campaign Classic Release Candidate**.

Se [den här sidan](../../rn/using/gold-standard.md) för versionen Campaign Classic Gold Standard (senaste GA-builden).

## ![](assets/do-not-localize/blue_2.png) Version 21.1.1 – build 9277 {#release-21-1-1-build-9277}

_22 februari 2021_

**Säkerhetsförbättringar**

* Konsolautentiseringsmekanismen har förbättrats för att optimera säkerheten. (NEO-26944)
* Korrigerade ett säkerhetsproblem för att förstärka skyddet mot problem med SSRF (Server Side Request Forgery). (NEO-28532)

**Kompatibilitetsuppdateringar**

Campaign har nu stöd för följande system:

* Salesforce API version 49 stöds nu när det externa Salesforce CRM-kontot används.

**Inaktuella funktioner**

Rapporten **Technical Deliverability Monitoring** är nu föråldrad.

Läs mer på sidan [Funktioner som är inaktuella eller har tagits bort](../../rn/using/deprecated-features.md).

**Förbättringar**

**Tjänsten Email Feedback Service (EFS)** är en skalbar tjänst som direkt hämtar in feedback från det förbättrade MTA-systemet och därmed förbättrar rapporteringsnoggrannheten. Denna funktion lanseras som en privat betaversion och kommer successivt att finnas tillgänglig för alla kunder i framtida versioner.

* Alla kategorier av feedback hämtas nu in för en fullständig och exakt rapportering.
* Beräkningen av indikatorn Levererad baseras nu på feedback i realtid från det förbättrade MTA-programmet för ökad precision och reaktivitet.
* EFS löser problemet med förseningar genom synkroniserad rapportering av mjuka studsar.

Mer information finns i den [detaljerade dokumentationen](../../delivery/using/sending-with-enhanced-mta.md#efs).
Om du är intresserad av att delta i den här privata betaversionen fyller du i det här [formuläret](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4Rol2vQGupxItW9_BerXV6VUQTJPN1Q5WUI4OFNTWkYzQjg3WllUSDAxWi4u) så kommer vi tillbaka till dig.

**Andra ändringar**

* Överföringshastigheten har förbättrats för stora spårningsloggar genom komprimering.
* Arbetsflödets heatmap har förbättrats för att undvika timeout när arbetsflöden med flera aktiviteter körs. (NEO-27423).
* Ett problem som gjorde att ett erbjudande kunde presenteras även om slutdatumet passerades har åtgärdats. Campaign Classic tar nu hänsyn till slutdatumets hela tidsstämpel, i stället för enbart datumet. (NEO-27590)
* Google+-länken har tagits bort från **personaliseringsblocket** Dela sociala nätverk.
* Ett problem har korrigerats efter implementeringen av en felkorrigering i den senaste versionen. En kontroll lades till i värdnamnet vid anslutning med SSL/TLS, vilket ledde till att SMS-leveranser misslyckades. Verifiering av värdnamn har inaktiverats för de flesta protokoll som POP3, SMS och HTTP med proxy och certifikatkontrollen för det externa SMS-kontot har förbättrats med tre värden (NEO-29581). [Läs mer](../../delivery/using/sms-protocol.md#skip-tls)

**Felkorrigeringar**

* Ett problem som gjorde att kortkommandona för Tabb, Enter och Esc inte kunde användas på den nya inloggningsskärmen har åtgärdats.
* Korrigerade ett uppdateringsfel som gjorde att namnet på ett nyligen skapat arbetsflöde ersattes med standardvärdet efter att det sparats (NEO-26106).
* Ett problem som uppstod när arbetsflöden kördes där ett nytt fält lades till som en del av en **Enrichment**-aktivitet före en **Delivery**-aktivitet med en **extern fil**-målmappning korrigerades: oönskade fält lades till i målmappningen för **den externa filen**. (NEO-27687)
* Korrigerade ett problem som gjorde att vissa tecken i källkoden ändrades när ett webbprogram som skapats och sparats tidigare öppnades igen. (NEO-27597)
* Korrigerade ett problem som kunde inträffa vid uppgradering till en version, inklusive den nya signaturfunktionen för spårning av länkar (från version 19.1.4 och Campaign 20.2): när flera mallar var kopplade till en händelse kan en uppgradering göra att fel mall väljs när transaktionsmeddelandet skickas. (NEO-28326)
* Korrigerade ett problem som gjorde att MTA inte svarade och inte kunde bearbeta leveranser om inte starten om. (NEO-27455)
* Korrigerade ett problem med MSSQL-databasen relaterat till tidsstämpelhantering under massinläsningsåtgärder för en datetime-typkolumn.
* Korrigerade ett problem med arbetsflödesfrågan när XTK-funktioner för Redshift användes. UnderDays, SubSeconds, SubMinutes och SubHours accepteras nu båda tidstämpeltyperna för Redshift (NEO-24962).
* Korrigerade ett problem som visade ett skriptfelmeddelande när en rapport med anonym åtkomst skulle förhandsgranskas. (NEO-27081)
* Ett problem som kunde minska minnesanvändningen på servern vid leveransanalys har åtgärdats.
* Korrigerade ett problem som kunde förhindra instansen från att fungera när vissa komplexa frågor skulle köras.
* Ett problem som kunde förhindra att det tekniska arbetsflödet **för synkronisering av Twitter-sidor** kördes har åtgärdats. (NEO-28634)
* Korrigerade ett problem som kunde visa ett felmeddelande relaterat till funktionen dekrypptPassword när du försökte publicera på Twitter med hjälp av leveransmallen **Tweet (twitter)**. (NEO-28216)
* Korrigerade ett fel som uppstod när en **Javascript**-aktivitet användes för att göra en HTTP-begäran i ett arbetsflöde. När portnumret har definierats i värdnamnet misslyckas anropet med följande fel (NEO-29146):

```
IOB-090020 Error in SSL library: 'IOB-090013 error:14090086:SSL routines:ssl3_get_server_certificate:certificate verify failed (code 336134278)'
```

* Korrigerade ett problem som förhindrade att nya leveranser med måldataanpassning skickades.
* Korrigerade ett problem där flera krascher inträffade i marknadsföringsinstansen som orsakade kärnfiler.
* Korrigerade ett problem som medförde att arbetsflödet **Spårning** misslyckades med följande fel (NEO-25206):

```
There is no index on the sourceId field of the 'NmsTrackingLogRcp' table required for the current Web tracking mode. Please add this index.
```

* Ett problem som uppstod när en leverans skapades och sparades på fliken **Mål och arbetsflöde** i en kampanj har korrigerats: Förhandsgranskningen misslyckas med följande fel (NEO-29440):

```
XTK-170024 The temporary 'temp:deliveryEmail-all' schema is not defined in the current context
```

* Korrigerade ett fel som uppstod när ett externt konto skulle skapas mellan en marknadsföringsinstans och en Adobe Campaign Standard-instans eller en Campaign Classic-instans och med alternativet DisableFOH2=1. När alternativet DisableFOH2=1 används i det externa kontot stängdes inte anslutningarna korrekt och detta resulterar i följande fel (NEO-26258):

```
The maximum number of connections has been reached (50) by connections pool 'nms:extAccount:acsDefaultRelayAccount XXX'. The server is overloaded. Please try again later.
```

* Korrigerade ett fel med SMS när anslutningsproblem uppstod mellan servern och providern. Anslutningen inaktiveras sedan automatiskt av det underordnade MTA-objektet. Adobe Campaign Classic försöker inte ansluta till den felaktiga anslutningen så länge som ett nytt barn inte har startats.
