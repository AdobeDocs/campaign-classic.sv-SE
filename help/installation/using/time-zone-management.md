---
product: campaign
title: Hantering av tidszoner
description: Hantering av tidszoner
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: e5ed96cc-3fc7-4af4-a29e-5a4c81f4fe39
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '886'
ht-degree: 1%

---

# Hantering av tidszoner{#time-zone-management}



## Verksamhetsprincip {#operating-principle}

Med Adobe Campaign kan du uttrycka datum som en funktion av deras tidszon: på så sätt kan internationella användare arbeta över hela världen i olika tidszoner. Varje land som använder samma instans kan hantera kampanjer, spårning, arkivering osv. beroende på lokal tid.

För att Adobe Campaign-plattformen ska kunna användas internationellt måste alla datum som används av systemen kunna länkas till en tidszon. Ett datum vars tidszon är känd kan alltså importeras till vilken annan tidszon som helst, eller oavsett tidszon.

I Adobe Campaign kan du lagra datum/tid i UTC-format (Coordinated Universal Time). När data exponeras konverteras de till operatorns lokala datum/tid. Konverteringen utförs automatiskt när databasen är konfigurerad i UTC (se [Konfiguration](#configuration)). Om databasen inte är konfigurerad i UTC lagras information om tidszonen för datum på plattformen i ett alternativ.

De viktigaste plattformsfunktionerna för hantering av tidszoner är: importera/exportera data, operatorer och arbetsflödeshantering. The **arvskoncept** är tillgängligt för import/export eller arbetsflöden. Som standard är de konfigurerade för databasserverns tidszon, men du kan definiera om nya tidszoner för ett arbetsflöde och till och med för en enda aktivitet.

**Operatorer** kan ändra tidszoner under **leveranskonfiguration** och kan ange i vilken tidszon leveransen ska utföras.

>[!IMPORTANT]
>
>Om databasen inte hanterar flera tidszoner måste SQL-frågor köras i databasserverns tidszon för alla datafiltreringsändringar.

Varje Adobe Campaign-operator är länkad till en tidszon: den här informationen är konfigurerad i deras profil. Mer information finns i [det här dokumentet](../../platform/using/access-management.md).

Om Adobe Campaign-plattformen inte kräver tidszonshantering kan du behålla ett lagringsläge i lokalt format med en viss länkad tidszon.

## Rekommendationer {#recommendations}

Tidszoner kombinerar flera realiteter: uttrycket kan beskriva en konstant tidsfördröjning med UTC-datumet, eller tidpunkterna i ett område som kan ändras två gånger per år (sommartid).

I postgreSQL är **ANGE TIDSZON &quot;Europa/Paris&quot;;** Kommandot tar hänsyn till sommar- och vintertid: Datumet kommer att anges i UTC+1 eller UTC+2 beroende på tidpunkten på året.

Om du använder **ANGE TIDSZON 0200;** kommer tidsfördröjningen alltid att vara UTC+2.

## Konfiguration {#configuration}

Lagringsläget för datum och tidpunkter väljs när databasen skapas (se [Skapa en ny instans](#creating-a-new-instance)). Vid migrering konverteras de timmar som är länkade till datum till lokala datum och timmar (se [Migrering](#migration)).

Ur teknisk synvinkel finns det två sätt att lagra **Datum+tid** typinformation i databasen:

1. TIDSSTÄMPEL MED TIMEZONE-format: databasmotorn lagrar datum i UTC. Varje session som öppnas har en tidszon och datumen konverteras enligt den.
1. Lokalt format + lokal tidszon: alla datum lagras i det lokala formatet (ingen hantering av tidsfördröjning) och en enda tidszon tilldelas dem. Tidszonen lagras i **WdbcTimeZone** Adobe Campaign-instansen och kan ändras via **[!UICONTROL Administration > Platform > Options]** Trädets meny.

>[!IMPORTANT]
>
>Observera att den här ändringen kan leda till problem med datakonsekvens och synkronisering.

### Skapa en ny instans {#creating-a-new-instance}

För att flera internationella användare ska kunna arbeta med samma instans måste du konfigurera tidszoner när du skapar instansen för att hantera tidsförskjutningar mellan länder. När du skapar en instans väljer du datum- och tidshanteringsläget i **[!UICONTROL Time zone]** -avsnittet på databaskonfigurationsscenen.

Kontrollera **[!UICONTROL UTC database (date fields with time zone)]** för att lagra alla data med datum och tidpunkter i UTC-format (SQL-fält och XML-fält).

![](assets/install_wz_select_utc_option.png)

>[!IMPORTANT]
>
>Om du använder **Oracle** måste tidszonsfilerna (.dat) för Oraclets klientlager vara kompatibla med de tidszonsfiler som är installerade på servern.

Om databasen inte är UTC kan du välja en av de tidszoner som finns i listrutan. Du kan också använda serverns tidszon eller välja alternativet UTC (Coordinated Universal Time).

![](assets/install_wz_unselect_utc_option.png)

När **[!UICONTROL UTC Database (date fields with time zone)]** Om du väljer det här alternativet sparas SQL-fälten i TIMESTAMP WITH TIMEZONE-format.

Annars lagras de i det lokala formatet och du måste välja vilken tidszon som ska användas för databasen.

### Migrering {#migration}

När du migrerar till en tidigare version (utan tidszonshantering) måste du definiera lagringsläget för datum i databasen.

För att garantera kompatibilitet med externa verktyg som har åtkomst till Adobe Campaign-databasen har **Datum+tid** SQL-fält av typen sparas som standard i lokalt format.

XML-fält som innehåller datum lagras nu i UTC. Vid inläsning konverteras fält som inte är i UTC-format automatiskt med serverns tidszon. Det innebär att alla XML-fält konverteras stegvis till UTC-format.

Om du vill använda en befintlig instans lägger du till **WdbcTimeZone** och ange instansens tidszon.

>[!IMPORTANT]
>
>Kontrollera att rätt värde har konfigurerats för alternativet WdbcTimeZone: senare ändringar kan leda till inkonsekvenser.

Exempel på möjliga värden:

* Europa/Paris,
* Europa/London,
* America/New_York, osv.

   Dessa värden hämtas från tz-databasen (Olson). Mer information finns i [https://en.wikipedia.org/wiki/List_of_tz_database_time_zones](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones).
