---
solution: Campaign Classic
product: campaign
title: 'Gold Standard-version '
description: Versionsinformation om Campaign Classic Gold Standard
audience: rns
content-type: reference
topic-tags: latest-release-notes
translation-type: tm+mt
source-git-commit: 0abdbbc33350cf6ec85488483dadb177e685818b
workflow-type: tm+mt
source-wordcount: '820'
ht-degree: 100%

---


# Gold Standard-version{#gold-standard}

Gold Standard är versionen av Campaign Classic med långsiktig support. Som Gold Standard-användare har du automatiskt tillgång till uppgraderingen av Gold Standard med den senaste stabila versionen utan någon åtgärd. Kunder med lokala installationer eller hybridlösningar kan också dra nytta av Gold Standard-versioner.

Om du migrerar från en gammal version rekommenderar vi att du först uppgraderar till den här versionen.

Den här sidan listar Gold Standard-versioner.

Se [den här artikeln](https://helpx.adobe.com/se/campaign/kb/gold-standard.html) för mer information om Campaign Gold Standard.

## ![](assets/do-not-localize/green_2.png) Gold Standard version 10{#gs-10}

_7 juli 2020_

Build 9032@efd8a94 har följande korrigering:

Korrigerade ett problem som hindrade spårning från att fungera när signaturfunktionen var inaktiverad. (NEO-26411)

>[!CAUTION]
>
>Vi rekommenderar att du uppgraderar klientkonsolen till den som finns i den här versionen. Se [den här sidan](../../installation/using/installing-the-client-console.md)

## ![](assets/do-not-localize/red_2.png) Gold Standard version 9{#gs-9}

_22 juni 2020_

Build 9032@800be2e har följande korrigeringar:

* iOS HTTP2-kopplingen har förbättrats (tredjepartsuppdateringar och felhantering). (NEO-25904, NEO-25903 och NEO-25799)

Följande korrigeringar är relaterade till spårningslänkens säkerhetsmekanism (läs mer i [checklistan försäkerhet och sekretess](https://helpx.adobe.com/se/campaign/kb/acc-security.html#signature-mechanism)):

* Korrigerade ett problem som hindrade spårningen av ”meddelandeklickningar” från att fungera (iOS- och Android-push-meddelanden). (NEO-25965)
* Korrigerade ett problem som kunde hindra dig från att öppna/klicka på spårnings-URL:er när du använde vissa äldre versioner av Outlook.  (NEO-25688)
* Korrigerade ett problem som förhindrade spårning av URL:er, som använder fragment i personaliseringsparametrar (ankartaggar med pundtecken), från att fungera. (NEO-25774)
* Korrigerade ett problem med tjänsten mot nätfiske. (NEO-25283)
* Korrigerade ett problem med spårning när särskilda anpassade spårningsformler användes. (NEO-25277)

## ![](assets/do-not-localize/red_2.png) Gold Standard version 8{#gs-8}

_29 april 2020_

Build 9032@3a9dc9c har följande korrigeringar:

* Förbättrad säkerhet vid spårning av länkar i e-postmeddelanden. Detta är aktiverat som standard för alla kunder. Det finns ytterligare en förbättrad säkerhetsfunktion som kan aktiveras genom att kontakta kundtjänst. Mer information om funktionen och stegen för icke-värdbaserade kunder som vill aktivera den finns i [checklistan över säkerhet och sekretess](https://helpx.adobe.com/campaign/kb/acc-security.html#signature-mechanism).

>[!CAUTION]
>
>Om du upplever problem med push-meddelanden när du använder spårningslänkar eller leveranser med ankartaggar rekommenderar vi att du inaktiverar den nya signaturfunktionen för spårningslänkar. Förfarandet beskrivs [på den här sidan](https://helpx.adobe.com/campaign/kb/acc-security.html#signature-mechanism)

* Korrigerade ett problem som kunde förhindra att bilder visades i Line-leveranser. (NEO-23207)
* Ett problem med **filöverföringar** som hindrade SFTP-nyckelbaserad autentisering från att fungera i Debian 9 har korrigerats. (NEO-23183)
* Korrigerade ett problem som kunde påverka push-meddelanden när de skickades med hög frekvens. (NEO-20516)
* Korrigerade ett problem vid hantering av svar på erbjudanden som kunde leda till att webbservern kraschar. (NEO-19482)
* Korrigerade ett problem i LibreOffice-hanteringen som hindrade dig från att exportera rapporter. (NEO-20982)
* Korrigerade ett problem som orsakade ett fel när flera arbetsflöden uppgraderades med en undersökningsaktivitet.
* Förbättrad LibreOffice-hantering för att undvika fel vid förhandsgranskning av e-postmeddelanden med .odt-filer.
* Förbättrad hantering av Apache-kopplingar för att undvika latens i webbtjänsten.
* Förbättrad visning av versionstaggar (7 siffror) på menyn **Om**.
* Korrigerade en regression i listhanteringen som förhindrade att erbjudanden publicerades.
* Korrigerade en regression som fick arbetsflödet för rensning att krascha.
* Korrigerade en mindre regression i loggfilerna för arbetsflödet för rensning.

## ![](assets/do-not-localize/orange_2.png) Gold Standard version 6{#gs-6}

_9 mars 2020_

Build 9032@19f73c5 har följande korrigering:

* Korrigerade ett problem med externa konton som använder FTP över SSL. (NEO-20498)

## ![](assets/do-not-localize/orange_2.png) Gold Standard version 5{#gs-5}

_17 december 2019_

Build 9032@d6b8062 har följande korrigering:

* Korrigerade ett problem med spårning i följande kommunikationskanaler: mobil (SMS, MMS), push (iOS, Android) och sociala nätverk (Facebook, Twitter). (NEO-19595)

## ![](assets/do-not-localize/orange_2.png) Gold Standard version 4{#gs-4}

_11 december 2019_

Build 9032@bc4a935 har följande korrigering:

* Korrigerade ett problem med prestandan när meddelanden skickades med en MSSQL-databas. (NEO-17558)

## ![](assets/do-not-localize/orange_2.png) Gold Standard version 3{#gs-3}

_20 november 2019_

Build 9032@3468c7b har följande korrigeringar:

* Korrigerade ett problem med inloggningen via IMS-autentisering. (NEO-17312)
* Korrigerade ett problem när kumulativa rapporter för flera leveranser visades. (NEO-18165)
* Korrigerade ett problem som kunde blockera eller få webbservern att krascha.

## ![](assets/do-not-localize/red_2.png) Gold Standard version 2{#gs-2}

_19 september 2019_

Build 9032@cee805c har följande korrigeringar:

* Korrigerade ett problem när CRM-kopplingen för Salesforce användes. (NEO-17712)
* Korrigerade ett problem med index som kunde orsaka prestandaproblem när transaktionsmeddelanden skickades.

## ![](assets/do-not-localize/red_2.png) Version 19.1.4 – build 9032{#release-19-1-4-build-9032}

_13 augusti 2019_

Den första versionen 19.1.4 innehåller följande korrigeringar:

* Korrigerade ett problem med schemaläggaraktiviteten som genererade oönskade felmeddelanden under guidekonfigurationen. Återställer uppdatering från NEO-11662. (NEO-17097)
* Korrigerade en regression som orsakades av NEO-12727 och som kunde leda till att arbetsflöden stoppades när en testaktivitet kördes två gånger. (NEO-16835)
* Korrigerade ett problem som ledde till att en felaktig HTTP-kod returnerades (HTTP 200 OK i stället för HTTP 403 Forbidden) när en ogiltig eller utgången sessionstoken användes i API-anrop. (NEO-16826)
* Korrigerade ett problem med DKIM-nyckeln som inte längre var inbäddad i e-postmeddelanden vilket orsakade leveransproblem. (NEO-16804)
* Korrigerade flera problem med arbetsflödesplanering. Arbetsflödena schemalades att köras en gång om dagen utan att konfigurationen av Scheduler hade beaktats. (NEO-16619 och NEO-16426)
