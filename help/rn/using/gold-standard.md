---
title: Gold Standard
seo-title: Gold Standard
description: Gold Standard
seo-description: null
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: ac2d993f525eb918ad5e15104eb3ede9eeadfb43
workflow-type: tm+mt
source-wordcount: '815'
ht-degree: 14%

---


# Gold Standard{#gold-standard}

Som Gold Standard-användare har du automatiskt tillgång till uppgraderingen av Gold Standard med den senaste stabila versionen utan någon åtgärd.

Anskaffade kunder på plats och Hybrid kan också dra nytta av Gold Standard-releaser.

Det här är vår långsiktiga supportrelease. Om du migrerar från en gammal version rekommenderar vi att du först uppgraderar till den här versionen.

På den här sidan visas Gold Standard-utgåvor.

Mer information om uppgradering av Gold Standard finns i den här [artikeln](https://helpx.adobe.com/se/campaign/kb/gold-standard.html).

## ![](assets/do-not-localize/limited_2.png) Gold Standard 10{#gs-10}

_7 juli 2020_

Version 9032@efd8a94 innehåller följande korrigering:

Korrigerade ett problem som hindrade spårning från att fungera när signaturfunktionen inaktiverades. (NEO-26411)

>[!CAUTION]
>
>Vi rekommenderar att du uppgraderar klientkonsolen med den som finns i den här versionen. Refer to this [page](../../installation/using/installing-the-client-console.md)

## ![](assets/do-not-localize/red_2.png) Gold Standard 9 release{#gs-9}

_22 juni 2020_

Version 9032@800be2e innehåller följande korrigeringar:

* iOS HTTP2-anslutningen har förbättrats (tredjepartsuppdateringar och felhantering). (NEO-25904, NEO-25903 och NEO-25799)

Följande korrigeringar är relaterade till säkerhetsmekanismen för spårningslänkar (se checklistan för [säkerhet och sekretess](https://helpx.adobe.com/campaign/kb/acc-security.html#signature-mechanism)):

* Korrigerade ett problem som hindrade spårningen av&quot;meddelandeklickningar&quot; från att fungera (iOS- och Android-push-meddelanden). (NEO-25965)
* Korrigerade ett problem som kunde hindra dig från att öppna/klicka på spårnings-URL:er när du använde vissa äldre versioner av Outlook.  (NEO-25688)
* Korrigerade ett problem som förhindrade spårning av URL-adresser som använder fragment i personaliseringsparametrar (ankartaggar med nummertecken) från att fungera. (NEO-25774)
* Ett problem med tjänsten mot nätfiske har korrigerats. (NEO-25283)
* Ett spårningsproblem har korrigerats när särskilda anpassade spårningsformler användes. (NEO-25277)

## ![](assets/do-not-localize/red_2.png) Gold Standard 8{#gs-8}

_29 april 2020_

Version 9032@3a9dc9c innehåller följande korrigeringar:

* Förbättrad säkerhet vid spårning av länkar i e-post. Detta är aktiverat som standard för alla kunder. Det finns ytterligare en förbättrad säkerhetsfunktion som kan aktiveras genom att kontakta kundtjänst. Mer information om funktionen och stegen för icke-värdbaserade kunder som vill aktivera den finns i [checklistan över säkerhet och sekretess](https://helpx.adobe.com/campaign/kb/acc-security.html#signature-mechanism).

>[!CAUTION]
>
>Om du får problem med push-meddelanden med hjälp av spårningslänkar, eller leveranser med ankartaggar, rekommenderar vi att du inaktiverar den nya signaturfunktionen för spårning av länkar. Proceduren beskrivs på den här [sidan](https://helpx.adobe.com/campaign/kb/acc-security.html#signature-mechanism)

* Korrigerade ett problem som kunde förhindra att bilder visas på radleveranser. (NEO-23207)
* Ett problem med **filöverföringar** som hindrade SFTP-nyckelbaserad autentisering från att fungera i Debian 9 har korrigerats. (NEO-23183)
* Korrigerade ett problem som kunde påverka push-meddelanden när de skickades med hög frekvens. (NEO-20516)
* Ett problem i hanteringen av erbjudanden som kan leda till att webbservern kraschar har åtgärdats. (NEO-19482)
* Korrigerade ett fel i LibraryOffice-hanteringen som hindrade dig från att exportera rapporter. (NEO-20982)
* Korrigerade ett problem som orsakade ett fel när flera arbetsflöden uppgraderades med en undersökningsaktivitet.
* Förbättrad LiveOffice-hantering för att undvika fel vid e-postförhandsgranskning med .odt-filer.
* Förbättrad hantering av Apache-anslutning för att undvika latens i webbtjänsten.
* Förbättrad visning av versionstagg (7 siffror) på menyn **Om** .
* Korrigerade en regression i listhantering som förhindrade att erbjudanden publicerades.
* Korrigerade en regression som fick arbetsflödet för rensning att krascha.
* Korrigerade en mindre regression i loggfilerna för arbetsflödet för rensning.

## ![](assets/do-not-localize/green_2.png) Gold Standard 6 release{#gs-6}

_9 mars 2020_

Version 9032@19f73c5 innehåller följande korrigering:

* Korrigerade ett problem med externa konton som använder FTP över SSL. (NEO-20498)

## ![](assets/do-not-localize/orange_2.png) Gold Standard 5-utgåva{#gs-5}

_17 december 2019_

Version 9032@d6b8062 innehåller följande korrigering:

* Korrigerade ett spårningsproblem i följande kommunikationskanaler: mobil (SMS, MMS), push (iOS, Android) och sociala nätverk (Facebook, Twitter). (NEO-19595)

## ![](assets/do-not-localize/orange_2.png) Gold Standard 4{#gs-4}

_11 december 2019_

Version 9032@bc4a935 innehåller följande korrigering:

* Ett prestandaproblem har korrigerats när meddelanden skickades med en MSSQL-databas. (NEO-17558)

## ![](assets/do-not-localize/orange_2.png) Gold Standard 3 release{#gs-3}

_20 november 2019_

Version 9032@3468c7b innehåller följande korrigeringar:

* Ett inloggningsproblem via IMS-autentisering har korrigerats. (NEO-17312)
* Korrigerade ett problem när kumulativa rapporter för flera leveranser visades. (NEO-18165)
* Korrigerade ett problem som kunde blockera eller få webbservern att krascha.

## ![](assets/do-not-localize/red_2.png) Gold Standard 2{#gs-2}

_19 september 2019_

Version 9032@cee805c innehåller följande korrigeringar:

* Ett problem har korrigerats när CRM Connector för Salesforce användes. (NEO-17712)
* Korrigerade ett indexproblem som kunde orsaka prestandaproblem när transaktionsmeddelanden skickades.

## ![](assets/do-not-localize/red_2.png) Version 19.1.4 - build 9032{#release-19-1-4-build-9032}

_13 augusti 2019_

Den första versionen av 19.1.4 innehåller följande korrigeringar:

* Korrigerade ett problem med schemaläggaraktiviteten som genererade oönskade felmeddelanden under guidekonfigurationen. Återställer uppdatering från NEO-11662. (NEO-17097)
* Korrigerade en regression orsakad av NEO-12727 som kunde leda till att arbetsflöden stoppades när en testaktivitet kördes två gånger. (NEO-16835)
* Korrigerade ett problem som ledde till att en felaktig HTTP-kod returnerades (HTTP 200 OK i stället för HTTP 403 Forbidden) när en ogiltig eller utgången sessionstoken användes i API-anrop. (NEO-16826)
* Korrigerade ett problem med DKIM-nyckeln som inte längre var inbäddad i e-postmeddelanden, vilket orsakade leveransproblem. (NEO-16804)
* Åtgärdade olika problem med arbetsflödesplanering. Arbetsflödena har schemalagts att köras en gång om dagen utan att schemaläggarens konfiguration har beaktats. (NEO-16619 och NEO-16426)
