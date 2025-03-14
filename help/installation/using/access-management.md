---
product: campaign
title: Åtkomsthantering
description: Läs mer om de effektivaste strategierna för åtkomsthantering
feature: Installation, Access Management, Permissions
exl-id: af88e4e7-0ee3-48b4-9db4-7dd390d9d46a
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 8%

---

# Åtkomsthantering {#access-management}



## Webbprogramsoperatör

WebApp-operatorn är administratör. Följ dessa riktlinjer för att förbättra säkerheten:

* Ersätt administratören med namnet right från den här operatorn med en ny (kan heta &#39;webapp&#39;). För mer information om detta hittar du i [det här avsnittet](../../platform/using/access-management.md).

* Lägg till operatorn webApp i mappar (främst mottagarmappar) för att ge mottagare läs- och skrivåtkomst. Mer information finns på [den här sidan](../../platform/using/access-management.md).

* Om du använder en instans med flera varumärken (eller flera geo) kanske du vill dela upp webbprogramåtkomsten till olika mottagarmappar. För att göra detta:

   1. Duplicera operatorn webApp

   1. Ange ett namn för varje dubblett. Exempel: webapp_brand, webapp_brand2, osv.

   1. Duplicera en webbprogrammall så att den har en mall per varumärke och redigera egenskaperna för att ändra operator genom att välja Använd ett specifikt konto.  Läs mer på [den här sidan](../../web/using/defining-web-forms-properties.md).

## Säkerhetsgrupper och administratörsoperatörer

Skapa tillräckligt många säkerhetsgrupper för att ge precis den behörighet som krävs till era operatorer så att de kan göra det de behöver, och inte mer.

Använd inte operatorn admin (eller dela den inte). Skapa en operator per fysisk användare (för korrekt granskning/loggning). Lägg till dina nynamngivna administratörer i administratörsgruppen. Om du inte använder admin-operatorn ska du inte ta bort den, och inte inaktivera den: den här operatorn används internt för att köra bearbetningen. Men du kan förbjuda åtkomst till [klientkonsolen](../../platform/using/access-management.md) och begränsa dess säkerhetszon (till localhost).

Undvik att lägga till för många operatorer i administratörsgruppen (eller med administratörsnamnrättigheter). De är mycket kraftfulla operatorer (de kan utföra alla SQL-satser, köra kommandon på servern osv.).

Adobe Campaign ger tre högnivåbehörigheter via [namngivna rättigheter](../../platform/using/access-management.md#named-rights):

* **ADMINISTRATION** (admin): ger åtkomst till allt och tillåter att göra allt, och ignorerar alla namngivna högerkontroller, så det inkluderar namngivna rättigheter för PROGRAM EXECUTION (createProcess) och SQL

* **PROGRAM-KÖRNING** (createProcess): tillåter körning av externa program (på servern)

* **SQL**: tillåter att SQL-skript körs i databasen (så att säkerhetsmodellen kan kringgås). Obs! Om du behöver utföra komplexa beräkningar (till exempel filtrering) kan du be databasadministratören att skapa en SQL-funktion och lägga till dem i tillåtelselista. Läs mer på [den här sidan](../../installation/using/scripting-coding-guidelines.md).

* **Bevilja dem till mycket få (och betrodda) operatorer**
