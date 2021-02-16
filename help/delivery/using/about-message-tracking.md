---
solution: Campaign Classic
product: campaign
title: Kom igång med spårning
description: Läs mer om de allmänna riktlinjerna för spårning i Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 55cc09c0446e389029890e45b790bb5ec6ffdc27
workflow-type: tm+mt
source-wordcount: '690'
ht-degree: 8%

---


# Kom igång med meddelandespårning {#get-started-tracking}

Tack vare spårningsfunktionerna i Adobe Campaign kan du spåra skickade meddelanden och kontrollera mottagarnas beteende: öppna, klicka på länkar, ta bort prenumeration osv.

Den här informationen hämtas på fliken **[!UICONTROL Tracking]** i profilen för varje mottagare av leveransen. På den här fliken visas alla URL-länkar som spårats och klickats av mottagaren som valts i listan. Detta är en ackumulering av alla URL:er som spåras i leveranser som fortfarande finns på leveransskärmen. Listan kan konfigureras och innehåller vanligtvis: den URL som klickades på, datum och tid för klickningen samt det dokument där URL:en hittades. Mer information om detta finns i [det här avsnittet](../../platform/using/editing-a-profile.md#tracking-tab).

Kontrollpanelen **för leverans** är också viktig för att övervaka dina leveranser och eventuella problem som uppstår när meddelanden skickas. Mer information finns i [det här avsnittet](../../delivery/using/delivery-dashboard.md).

I följande diagram visas de olika stegen i dialogen mellan användaren och de olika servrarna.

![](assets/tracking-diagram.png)

## Konfigurera spårning {#configure-tracking}

<img src="assets/do-not-localize/icon-configure.svg" width="60px">

**Verksamhetsprincip**

Innan du använder spårning måste du först konfigurera den för din instans. [Läs mer](../../installation/using/deploying-an-instance.md#operating-principle)

**Spårningsserver**

Om du vill konfigurera spårning måste instansen deklareras och registreras hos spårningsservern(arna). [Läs mer](../../installation/using/deploying-an-instance.md#tracking-server)

**Spårning sparas**

När spårning har konfigurerats och URL:erna har fyllts i måste spårningsservern registreras. [Läs mer](../../installation/using/deploying-an-instance.md#tracking-configuration#saving-tracking)

## Meddelandespårning {#message-tracking}

<img src="assets/do-not-localize/icon-message-tracking.svg" width="60px">

**Spårade länkar**

Du kan spåra mottagning av meddelanden och aktivering av länkar som infogats i meddelandeinnehållet för att bättre förstå mottagarnas beteende. [Läs mer](../../delivery/using/how-to-configure-tracked-links.md)

**URL-spårning**

Spårningsalternativen kan konfigureras genom att aktivera eller inaktivera spårade URL:er. [Läs mer](../../delivery/using/personalizing-url-tracking.md)

**Spårad länkpersonalisering**

Med spårningsfunktionerna i Campaign Classic kan du lägga till länkar i e-postmeddelanden som kan personaliseras och som stöder spårning. [Läs mer](https://helpx.adobe.com/campaign/kb/tracking-personnalized-links.html)

**Spårningsloggar**

Det tekniska arbetsflödet för spårning hämtar spårningsdata när leveransen har skickats och spårningen har aktiverats. Dessa data finns på fliken Spårning för leveransen. [Läs mer](../../delivery/using/accessing-the-tracking-logs.md)

**Testa spårning**

Innan du skickar meddelanden med din spårning kan du testa spårningen på din spegelsida, e-postloggar och länkar. [Läs mer](../../delivery/using/testing-tracking.md)

## Webbprogramspårning {#web-application-tracking}

<img src="assets/do-not-localize/icon-web-app.svg" width="60px">

**Spåra en webbapplikation**

Du kan också spåra och mäta besök på webbprogramsidor med hjälp av spårningstaggar. Den här funktionen kan användas för alla typer av webbprogram, t.ex. formulär och onlineundersökningar. [Läs mer](../../web/using/tracking-a-web-application.md)

**Välja att inte delta i spårning av webbapplikation**

Med avanmälan om spårning av webbprogram kan du sluta spåra webbbeteenden för slutanvändare som avanmäler sig från beteendespårning. Du kan inkludera möjligheten att visa en banderoll i webbprogram eller landningssidor så att användarna kan välja bort den. [Läs mer](../../web/using/web-application-tracking-opt-out.md)

## Spåra rapporter {#tracking-reports}

<img src="assets/do-not-localize/icon_monitor.svg" width="60px">

**Spårningsstatistik**

Den här rapporten innehåller statistik om öppningar, klick och transaktioner och gör att du kan spåra marknadsföringseffekten av leveransen. [Läs mer](../../reporting/using/delivery-reports.md#tracking-statistics)

**URL:er och klickbara strömmar**

Den här rapporten innehåller en lista över besökta sidor efter en leverans. [Läs mer](../../reporting/using/delivery-reports.md#urls-and-click-streams)

**Person/personer och mottagare**

I det här exemplet är det lättare att förstå skillnaden mellan en person/person och en mottagare i Adobe Campaign. [Läs mer](../../reporting/using/person-people-recipients.md)

**Spårningsindikatorer**

I den här rapporten kombineras nyckelindikatorer för att spåra mottagarnas beteende när de får leveransen, till exempel öppnings- och klickfrekvens och klickströmmar. [Läs mer](../../reporting/using/delivery-reports.md#tracking-indicators)

**Indikatorberäkning**

De olika tabellerna ger dig en lista över indikatorer som används i de olika rapporterna och deras beräkningsformel beroende på leveranstyp. [Läs mer](../../reporting/using/indicator-calculation.md)

## Felsökning av spårning {#tracking-troubleshooting}

<img src="assets/do-not-localize/icon-troubleshooting.svg" width="60px">

Följande felsökningstips hjälper dig att lösa de vanligaste problemen som inträffar när du använder spårning i Adobe Campaign Classic. Mer avancerad felsökning finns i [det här avsnittet](../../delivery/using/tracking-troubleshooting.md).

* Kontrollera att spårningsloggsprocessen körs

   Den här processen läser från det delade minnet för IIS/webbservern och skriver omdirigeringsloggarna.

   Du kommer åt den från hemsidan genom att välja fliken Övervakning i din instans. Du kan också köra följande kommando på instansen: `<user>@<instance>:~$ nlserver pdump`

   Om spårningsprocessen inte visas i listan startar du den med följande kommando på instansen: `<user>@<instance>:~$ nlserver start trackinglogd`

* Kontrollera att det tekniska arbetsflödet för spårning har körts nyligen.

   Du hittar det tekniska arbetsflödet för spårning i mapparna Administration > Produktion > Tekniska arbetsflöden.
