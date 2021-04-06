---
solution: Campaign Classic
product: campaign
title: Senaste versionen
description: Senaste versionsinformationen om Campaign Classic
feature: Översikt
role: Yrkesverksam
level: Nybörjare
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
translation-type: tm+mt
source-git-commit: 3db426580ba72668cd9fa274b57f925600eda27b
workflow-type: tm+mt
source-wordcount: '905'
ht-degree: 96%

---

# Senaste versionen{#latest-release}

Den här sidan listar nya funktioner, förbättringar och korrigeringar som ingår i den **senaste versionen av Campaign Classic Release Candidate**.

>[!NOTE]
>
>Kampanjbyggen **General Availability (GA)** är: [[!DNL Gold Standard] 11 release](../../rn/using/gold-standard.md#gs-11) och [Campaign 20.2.5 release](../../rn/using/release--20-2.md).


## ![](assets/do-not-localize/blue_2.png) Version 21.1.1 – build 9277 {#release-21-1-1-build-9277}

_22 februari 2021_

**Säkerhetsförbättringar**

* Konsolens autentiseringsmekanism har förbättrats för att optimera säkerheten. (NEO-26944)
* Korrigerade ett säkerhetsproblem för att förstärka skyddet mot problem med SSRF (Server Side Request Forgery). (NEO-28532)

**Kompatibilitetsuppdateringar**

Campaign har nu stöd för följande system:

* API för Salesforce version 49 stöds nu när det externa Salesforce CRM-kontot används.

**Inaktuella funktioner**

Rapporten **Teknisk leveransövervakning** är nu inaktuell.

Läs mer på sidan [Funktioner som är inaktuella eller har tagits bort](../../rn/using/deprecated-features.md).

**Förbättringar**

**Tjänsten Email Feedback Service (EFS)** är en skalbar tjänst som hämtar in feedback direkt från det förbättrade MTA-programmet och därmed ökar rapporteringens noggrannhet. Denna funktion lanseras som en privat betaversion och kommer successivt att finnas tillgänglig för alla kunder i framtida versioner.

* Alla kategorier av feedback hämtas nu in för en fullständig och exakt rapportering.
* Beräkningen av indikatorn Levererad baseras nu på feedback i realtid från det förbättrade MTA-programmet för ökad precision och reaktivitet.
* EFS löser problemet med förseningar genom synkroniserad rapportering av mjuka studsar.

Mer information finns i den [detaljerade dokumentationen](../../delivery/using/sending-with-enhanced-mta.md#efs).
Om du är intresserad av att delta i den här privata betaversionen ska du fylla i det här [formuläret](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4Rol2vQGupxItW9_BerXV6VUQTJPN1Q5WUI4OFNTWkYzQjg3WllUSDAxWi4u). Vi kontaktar dig sedan.

**Andra ändringar**

* Överföringshastigheten har förbättrats för stora spårningsloggar genom komprimering.
* Arbetsflödets värmekarta har förbättrats för att undvika timeout när arbetsflöden med flera aktiviteter körs. (NEO-27423).
* Korrigerade ett problem som gjorde att ett erbjudande kunde presenteras även om slutdatumet hade passerats. Campaign Classic tar nu hänsyn till slutdatumets hela tidsstämpel, i stället för enbart datumet. (NEO-27590)
* Länken Google+ har tagits bort från personaliseringsblocket **Dela på sociala nätverk**.
* Korrigerade ett problem efter implementeringen av en felkorrigering i den senaste versionen. En kontroll lades till i värdnamnet vid anslutning med SSL/TLS,vilket ledde till att SMS-leveranser misslyckades. Verifiering av värdnamn har inaktiverats för de flesta protokoll såsom POP3, SMS och HTTP med proxy och certifikatkontrollen för det externa SMS-kontot har förbättrats med tre värden (NEO-29581). [Läs mer](../../delivery/using/sms-protocol.md#skip-tls)

**Felkorrigeringar**

* Korrigerade ett problem som gjorde att kortkommandona för Tabb, Retur och Esc inte kunde användas på den nya inloggningsskärmen.
* Korrigerade ett problem där ett uppdateringsfel gjorde att namnet på ett nyligen skapat arbetsflöde ersattes med standardvärdet efter att det hade sparats (NEO-26106).
* Korrigerade ett problem som uppstod när arbetsflöden kördes där ett nytt fält lades till som en del av en **berikande**-aktivitet före en **leverans**-aktivitet med en målkartläggning av en **extern fil**: oönskade fält lades till i målkartläggningen av den **externa filen**. (NEO-27687)
* Korrigerade ett problem som gjorde att vissa tecken i källkoden ändrades när ett webbprogram, som hade skapats och sparats tidigare, öppnades igen. (NEO-27597)
* Korrigerade ett problem som kunde inträffa vid uppgradering till en ny version som innehöll den nya signaturfunktionen för spårning av länkar (från version 19.1.4 och Campaign 20.2): när flera mallar var kopplade till en händelse kunde en uppgradering göra att fel mall valdes när transaktionsmeddelandet skickades. (NEO-28326)
* Korrigerade ett problem som gjorde att MTA inte svarade och inte kunde bearbeta leveranser om den inte startades om. (NEO-27455)
* Korrigerade ett problem med MSSQL-databasen relaterat till tidsstämpelhantering under massinläsningsåtgärder för en kolumn av typ datum/tid.
* Korrigerade ett problem med arbetsflödesfrågor när xkt-funktioner i Redshift användes. SubDays, SubSeconds, SubMinutes och SubHours accepterar nu båda typerna av tidstämplar i Redshift (NEO-24962).
* Korrigerade ett problem som visade ett skriptfelmeddelande när en rapport med anonym åtkomst skulle förhandsgranskas. (NEO-27081)
* Korrigerade ett problem som kunde minska minnesanvändningen på servern vid leveransanalys.
* Korrigerade ett problem som kunde förhindra instansen från att fungera när vissa komplexa frågor skulle köras.
* Korrigerade ett problem som kunde förhindra att det tekniska arbetsflödet för **synkronisering av Twitter-sidor** kördes. (NEO-28634)
* Korrigerade ett problem som kunde visa ett felmeddelande relaterat till funktionen decryptPassword när man försökte publicera på Twitter med hjälp av leveransmallen **Tweet (twitter)**. (NEO-28216)
* Korrigerade ett fel som uppstod när en **Javascript**-aktivitet användes för att göra en HTTP-begäran i ett arbetsflöde. När portnumret hade definierats i värdnamnet misslyckades anropet med följande fel (NEO-29146):

```
IOB-090020 Error in SSL library: 'IOB-090013 error:14090086:SSL routines:ssl3_get_server_certificate:certificate verify failed (code 336134278)'
```

* Korrigerade ett fel som förhindrade att nya leveranser med måldataanpassning skickades (NEO-30323).
* Korrigerade ett problem där flera krascher inträffade i marknadsföringsinstansen som orsakade en minnesdump.
* Korrigerade ett problem som medförde att arbetsflödet **Spårning** misslyckades med följande fel (NEO-25206):

```
There is no index on the sourceId field of the 'NmsTrackingLogRcp' table required for the current Web tracking mode. Please add this index.
```

* Korrigerade ett problem som uppstod när en leverans skapades och sparades på fliken **Målinrikta och arbetsflöde** i en kampanj: förhandsgranskningen misslyckas med följande fel (NEO-29440):

```
XTK-170024 The temporary 'temp:deliveryEmail-all' schema is not defined in the current context
```

* Korrigerade ett fel som uppstod när ett externt konto skulle skapas mellan en marknadsföringsinstans och en Adobe Campaign Standard-instans eller mid-sourcing-instans i Campaign Classic samt med alternativet ”DisableFOH2=1”. När alternativet ”DisableFOH2=1” används i det externa kontot stängdes inte anslutningarna korrekt och detta resulterar i följande fel (NEO-26258):

```
The maximum number of connections has been reached (50) by connections pool 'nms:extAccount:acsDefaultRelayAccount XXX'. The server is overloaded. Please try again later.
```

* Korrigerade ett fel med SMS när anslutningsproblem uppstod mellan servern och leverantören. Anslutningen inaktiverades sedan automatiskt av det underordnade MTA-objektet. Adobe Campaign Classic försökte inte ansluta till den felaktiga anslutningen så länge som ett nytt underordnat objekt inte hade startats.
