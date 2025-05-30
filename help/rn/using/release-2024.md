---
product: campaign
title: Campaign Classic 2024-versioner
description: Läs mer om Campaign Classic 2024-versioner
feature: Release Notes
role: User
level: Beginner
exl-id: 8e20391d-3628-4d0c-b413-c34e046ae810
source-git-commit: bf45c8bcdd41e614f9be09bc0fd6385707159841
workflow-type: ht
source-wordcount: '387'
ht-degree: 100%

---

# 2024-versioner{#release-2024}

## Version 7.4.1 – build 9383 {#release-7-4-1}

[!BADGE Allmän tillgänglighet]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=sv#rn-statuses" tooltip="Allmän tillgänglighet"}

_18 juni 2024_

### Ändringar och förbättringar {#release-7-4-1-changes}

* Eftersom JWT-autentiseringsuppgifterna (Service Account) har tagits bort av Adobe är utgående Campaign-integreringar med Adobe-lösningar och appar nu beroende av autentiseringsuppgifter för OAuth Server-till-Server. Om du har implementerat utgående integreringar, som integrering med Campaign-Analytics eller med Experience Cloud Triggers måste du uppgradera din Campaign-miljö till v7.4.1 och migrera ditt tekniska konto till oAuth innan den 27 januari 2025. [Läs mer](../../integrations/using/oauth-technical-account.md)

* När du har [migrerat dina tekniska operatörer för Campaign till Developer Console](../../technotes/using/ims-migration.md) och [har övergått till IMS för autentisering av slutanvändare](../../technotes/using/migrate-users-to-ims.md) kan du nu aktivera användargränssnittet och API-begränsningarna för att ta bort alternativ och funktioner som är specifika för inbyggd autentisering. [Läs mer](../../technotes/using/impact-ims-migration.md)


### Kompatibilitetsuppdateringar {#release-7-4-1-compat}

[Kompatibilitetsmatris för Adobe Campaign](compatibility-matrix.md) har uppdaterats med ändringarna i den nya versionen och anges nedan.

* Adobe Campaign är nu kompatibelt med **Microsoft Server 2022** som operativsystem.
* Adobe Campaign är nu kompatibelt med **RHEL 9** som operativsystem.

  >[!CAUTION]
  >
  >Om du är en lokal kund som använder RHEL 9 och vill använda DKIM-autentisering (Domain Keys Identified Mail) måste du uppdatera systeminställningarna enligt informationen i [det här avsnittet](../../installation/using/installing-packages-with-linux.md#rhel-9-update).


* Adobe Campaign är nu kompatibelt med **Microsoft SQL Server 2022** och **Oracle 23c** som hanteringssystem för relationsdatabaser och i federal dataåtkomst (FDA).

* Adobe Campaign kräver nu minst Java Development Kit (JDK) 11. I Windows måste JRE vara tillgängligt enligt beskrivningen i [det här avsnittet](../../installation/using/application-server.md#jdk).

* SDK:et för mobilprogram i Campaign (Neolane) är nu föråldrat. Nu måste du gå över till Adobe Experience Platform SDK. [Läs mer](deprecated-features.md).

  Under tiden innehåller Campaign v7.4 följande för att säkerställa kontinuitet:

   * ett nytt Campaign-SDK 1.0.27 för iOS som är kompatibelt med iOS 16 och 17 samt de senaste [kraven för sekretessbegäran i Apple iOS](https://developer.apple.com/news/?id=r1henawx){target="_blank"}.
   * ett nytt Campaign-SDK för Android 14.

### Andra ändringar {#release-7-4-1-other}

Från och med v7.4.1 ingår inte längre XML-bibliotek för RPM Linux-paket i Campaign. Administratören måste installera dessa bibliotek som en lokal eller hybridkund. [Läs mer](../../installation/using/installing-packages-with-linux.md)

### Korrigeringar {#release-7-4-1-patches}

Den här versionen innehåller följande korrigeringar:

NEO-74754, NEO-73174, NEO-72504, NEO-71534, NEO-71473, NEO-70195, NEO-69663, NEO-69651, NEO-67620, NEO-67235, NEO-66797, NEO-64680, NEO-63706, NEO-63657, NEO-62964, NEO-62575, NEO-58734, NEO-40531, NEO-36189, NEO-29592


