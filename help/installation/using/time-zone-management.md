---
solution: Campaign Classic
product: campaign
title: Hantera tidszoner
description: Hantera tidszoner
audience: installation
content-type: reference
topic-tags: additional-configurations
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '886'
ht-degree: 1%

---


# Hantera tidszoner{#time-zone-management}

## Verksamhetsprincip {#operating-principle}

Med Adobe Campaign kan du uttrycka datum som en funktion av deras tidszon: på så sätt kan internationella användare arbeta över hela världen i olika tidszoner. Varje land som använder samma instans kan hantera kampanjer, spårning, arkivering osv. beroende på lokal tid.

För att Adobe Campaign-plattformen ska kunna användas internationellt måste alla datum som används av systemen kunna länkas till en tidszon. Ett datum vars tidszon är känd kan alltså importeras till vilken annan tidszon som helst, eller oavsett tidszon.

I Adobe Campaign kan du lagra datum/tid i UTC-format (Coordinated Universal Time). När data exponeras konverteras de till operatorns lokala datum/tid. Konverteringen utförs automatiskt när databasen har konfigurerats i UTC (se [Konfiguration](#configuration)). Om databasen inte är konfigurerad i UTC lagras information om tidszonen för datum på plattformen i ett alternativ.

De viktigaste plattformsfunktionerna för hantering av tidszoner är: importera/exportera data, operatorer och arbetsflödeshantering. Arvskonceptet **är** tillgängligt för import/export eller arbetsflöden. Som standard är de konfigurerade för databasserverns tidszon, men du kan definiera om nya tidszoner för ett arbetsflöde och till och med för en enda aktivitet.

**Operatörer** kan ändra tidszoner under **leveranskonfigurationen** och kan ange i vilken tidszon leveransen ska köras.

>[!IMPORTANT]
>
>Om databasen inte hanterar flera tidszoner måste SQL-frågor köras i databasserverns tidszon för alla datafiltreringsändringar.

Varje Adobe Campaign-operator är länkad till en tidszon: den här informationen är konfigurerad i deras profil. For more on this, refer to [this document](../../platform/using/access-management.md).

Om Adobe Campaign-plattformen inte kräver tidszonshantering kan du behålla ett lagringsläge i lokalt format med en viss länkad tidszon.

## Rekommendationer {#recommendations}

Tidszoner kombinerar flera realiteter: uttrycket kan beskriva en konstant tidsfördröjning med UTC-datumet, eller tidpunkterna i ett område som kan ändras två gånger per år (sommartid).

I postgreSQL, till exempel, **SET TIME ZONE &#39;Europe/Paris&#39;,** Kommandot tar hänsyn till sommar- och vintertid: Datumet kommer att anges i UTC+1 eller UTC+2 beroende på tidpunkten på året.

Om du däremot använder **SET TIME ZONE 0200,** kommer tidsfördröjningen alltid att vara UTC+2.

## Konfiguration {#configuration}

Lagringsläget för datum och tidpunkter väljs när databasen skapas (se [Skapa en ny instans](#creating-a-new-instance)). Vid migrering konverteras de timmar som är länkade till datum till lokala datum och timmar (se [Migrering](#migration)).

Ur teknisk synvinkel finns det två sätt att lagra **information av typen Datum+tid** i databasen:

1. TIDSSTÄMPEL MED TIMEZONE-format: databasmotorn lagrar datum i UTC. Varje session som öppnas har en tidszon och datumen konverteras enligt den.
1. Lokalt format + lokal tidszon: alla datum lagras i det lokala formatet (ingen hantering av tidsfördröjning) och en enda tidszon tilldelas dem. Tidszonen lagras i alternativet **WdbcTimeZone** i Adobe Campaign-instansen och kan ändras via trädens **[!UICONTROL Administration > Platform > Options]** meny.

>[!IMPORTANT]
>
>Observera att den här ändringen kan leda till problem med datakonsekvens och synkronisering.

### Creating a new instance {#creating-a-new-instance}

För att flera internationella användare ska kunna arbeta med samma instans måste du konfigurera tidszoner när du skapar instansen för att hantera tidsförskjutningar mellan länder. När du skapar en instans ska du välja datum- och tidshanteringsläge i avsnittet **[!UICONTROL Time zone]** på databaskonfigurationsscenen.

Markera alternativet för att lagra alla data med datum och tidpunkter i UTC-format (SQL-fält och XML-fält). **[!UICONTROL UTC database (date fields with time zone)]**

![](assets/install_wz_select_utc_option.png)

>[!IMPORTANT]
>
>Om du använder **Oracle** måste tidszonsfilerna (.dat) för Oracle-klientlager vara kompatibla med de tidszonsfiler som är installerade på servern.

Om databasen inte är UTC kan du välja en av de tidszoner som finns i listrutan. Du kan också använda serverns tidszon eller välja alternativet UTC (Coordinated Universal Time).

![](assets/install_wz_unselect_utc_option.png)

När alternativet är markerat sparas SQL-fälten i TIMESTAMP WITH TIMEZONE-format. **[!UICONTROL UTC Database (date fields with time zone)]**

Annars lagras de i det lokala formatet och du måste välja vilken tidszon som ska användas för databasen.

### Migrering {#migration}

När du migrerar till en tidigare version (utan tidszonshantering) måste du definiera lagringsläget för datum i databasen.

För att garantera kompatibilitet med externa verktyg som har åtkomst till Adobe Campaign-databasen förblir SQL-fälten av typen **Datum+tid** lagrade som standard i lokalt format.

XML-fält som innehåller datum lagras nu i UTC. Vid inläsning konverteras fält som inte är i UTC-format automatiskt med serverns tidszon. Det innebär att alla XML-fält konverteras stegvis till UTC-format.

Om du vill använda en befintlig instans lägger du till alternativet **WdbcTimeZone** och anger instansens tidszon.

>[!IMPORTANT]
>
>Kontrollera att rätt värde har konfigurerats för alternativet WdbcTimeZone: senare ändringar kan leda till inkonsekvenser.

Exempel på möjliga värden:

* Europa/Paris,
* Europa/London,
* America/New_York, osv.

   Dessa värden hämtas från tz-databasen (Olson). Mer information finns på [https://en.wikipedia.org/wiki/List_of_tz_database_time_zones](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones).

