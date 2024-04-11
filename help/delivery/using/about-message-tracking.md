---
product: campaign
title: Kom igång med spårning
description: Läs mer om de allmänna riktlinjerna för spårning i Adobe Campaign
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Monitoring, Email
role: User
exl-id: 43779505-9917-4e99-af25-b00a9d29a645
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '692'
ht-degree: 9%

---

# Kom igång med meddelandespårning {#get-started-tracking}



Tack vare spårningsfunktionerna i Adobe Campaign kan du spåra skickade meddelanden och kontrollera mottagarnas beteende: öppna, klicka på länkar, ta bort prenumeration osv.

Den här informationen hämtas i **[!UICONTROL Tracking]** -fliken för profilen för varje mottagare av leveransen. På den här fliken visas alla URL-länkar som spårats och klickats av mottagaren som valts i listan. Detta är en ackumulering av alla URL:er som spåras i leveranser som fortfarande finns på leveransskärmen. Listan kan konfigureras och innehåller vanligtvis: den URL-adress som klickades på, datum och tid för klickningen samt det dokument där URL-adressen hittades. Mer information om detta finns i [det här avsnittet](../../platform/using/editing-a-profile.md#tracking-tab).

The **kontrollpanel för leverans** är också avgörande för att övervaka leveranser och eventuella problem som uppstår när meddelanden skickas. Mer information om detta finns i [det här avsnittet](delivery-dashboard.md).

I följande diagram visas de olika stegen i dialogen mellan användaren och de olika servrarna.

![](assets/tracking-diagram.png)

## Konfigurera spårning {#configure-tracking}

<img src="assets/do-not-localize/icon-configure.svg" width="60px">

**Verksamhetsprincip**

Innan du använder spårning måste du först konfigurera den för din instans. [Läs mer](../../installation/using/deploying-an-instance.md#operating-principle)

**Spårningsserver**

Om du vill konfigurera spårning måste instansen deklareras och registreras hos spårningsservern(arna). [Läs mer](../../installation/using/deploying-an-instance.md#tracking-server)

**Spårning sparas**

När spårning har konfigurerats och URL:erna har fyllts i måste spårningsservern registreras. [Läs mer](../../installation/using/deploying-an-instance.md#saving-tracking)

## Meddelandespårning {#message-tracking}

<img src="assets/do-not-localize/icon-message-tracking.svg" width="60px">

**Spårade länkar**

Du kan spåra mottagning av meddelanden och aktivering av länkar som infogats i meddelandeinnehållet för att bättre förstå mottagarnas beteende. [Läs mer](how-to-configure-tracked-links.md)

**URL-uppföljning**

Spårningsalternativen kan konfigureras genom att aktivera eller inaktivera spårade URL:er. [Läs mer](personalizing-url-tracking.md)

**Spårad länkpersonalisering**

Med spårningsfunktionerna kan du lägga till länkar i e-postmeddelanden som kan personaliseras och som stöder spårning. [Läs mer](tracking-personalized-links.md)

**Spårningsloggar**

Det tekniska arbetsflödet för spårning hämtar spårningsdata när leveransen har skickats och spårningen har aktiverats. Dessa data finns på fliken Spårning för leveransen. [Läs mer](accessing-the-tracking-logs.md)

**Testa spårning**

Innan du skickar meddelanden med din spårning kan du testa spårningen på din spegelsida, e-postloggar och länkar. [Läs mer](testing-tracking.md)

## Spårning av webbprogram {#web-application-tracking}

<img src="assets/do-not-localize/icon-web-app.svg" width="60px">

**Spåra en webbapplikation**

Du kan också spåra och mäta besök på webbprogramsidor med hjälp av spårningstaggar. Den här funktionaliteten kan användas för alla webbapplikationstyper som formulär och landningssidor. [Läs mer](../../web/using/tracking-a-web-application.md)

**Välj att inte delta i spårning av webbapplikation**

Med avanmälan om spårning av webbprogram kan du sluta spåra webbbeteenden för slutanvändare som avanmäler sig från beteendespårning. Du kan inkludera möjligheten att visa en banderoll i webbprogram eller landningssidor så att användarna kan välja bort den. [Läs mer](../../web/using/web-application-tracking-opt-out.md)

## Spåra rapporter {#tracking-reports}

<img src="assets/do-not-localize/icon_monitor.svg" width="60px">

**Spårningsstatistik**

Den här rapporten innehåller statistik om öppningar, klick och transaktioner och gör att du kan spåra marknadsföringseffekten av leveransen. [Läs mer](../../reporting/using/delivery-reports.md#tracking-statistics)

**URL:er och klickbara strömmar**

Den här rapporten innehåller en lista över besökta sidor efter en leverans. [Läs mer](../../reporting/using/delivery-reports.md#urls-and-click-streams)

**Person/personer och mottagare**

I det här exemplet är det lättare att förstå skillnaden mellan en person/en person och en mottagare i Adobe Campaign. [Läs mer](../../reporting/using/person-people-recipients.md)

**Spårningsindikatorer**

I den här rapporten kombineras nyckelindikatorer för att spåra mottagarnas beteende när de får leveransen, till exempel öppnings- och klickfrekvens och klickströmmar. [Läs mer](../../reporting/using/delivery-reports.md#tracking-indicators)

**Indikatorberäkning**

De olika tabellerna ger dig en lista över indikatorer som används i de olika rapporterna och deras beräkningsformel beroende på leveranstyp. [Läs mer](../../reporting/using/indicator-calculation.md)

## Felsökning av spårning {#tracking-troubleshooting}

<img src="assets/do-not-localize/icon-troubleshooting.svg" width="60px">

Följande felsökningstips hjälper dig att lösa de vanligaste problemen som inträffar när du använder spårning i Adobe Campaign Classic. Om du vill ha en mer avancerad felsökning går du till [det här avsnittet](tracking-troubleshooting.md).

* Kontrollera att spårningsloggsprocessen körs

  Den här processen läser från det delade minnet för IIS/webbservern och skriver omdirigeringsloggarna.

  Du kommer åt den från hemsidan genom att välja fliken Övervakning i din instans. Du kan också köra följande kommando på instansen: `<user>@<instance>:~$ nlserver pdump`

  Om spårningsloggsprocessen inte visas i listan startar du den med följande kommando på instansen: `<user>@<instance>:~$ nlserver start trackinglogd`

* Kontrollera att det tekniska arbetsflödet för spårning har körts nyligen.

  Du hittar det tekniska arbetsflödet för spårning i mapparna Administration > Produktion > Tekniska arbetsflöden.
