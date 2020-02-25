---
title: Kommunikationskanaler
seo-title: Kommunikationskanaler
description: Kommunikationskanaler
seo-description: null
page-status-flag: never-activated
uuid: 42975431-64c9-4ecb-98ed-b1f9b13c157e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
discoiquuid: 2e2d1134-9b83-4ada-b74f-c3842a0cf044
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 3641e438784d40aa097f8c89ca19bdbb52f4bc7d

---


# Kommunikationskanaler{#communication-channels}

Med Adobe Campaign kan ni skicka kampanjer i flera kanaler, inklusive e-post, SMS, LINE-meddelanden, push-meddelanden och direktreklam, och mäta hur effektiva de är med hjälp av olika dedikerade [rapporter](../../reporting/using/delivery-reports.md). Dessa meddelanden är utformade och skickas genom leveranser och kan anpassas för varje mottagare.

De viktigaste funktionerna är målinriktning, definition och personalisering av meddelanden, genomförande av kommunikation och tillhörande verksamhetsrapporter. Den huvudsakliga funktionella åtkomstpunkten är leveransguiden. Den här åtkomstpunkten leder till flera funktioner som täcks av Adobe Campaign.

>[!NOTE]
>
>Adobe Campaign har en uppsättning verktyg för att övervaka er leveransförmåga och optimera e-postutskick. Mer information finns i Komma igång med [slutprodukten](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) och i Hantering [av](../../delivery/using/about-deliverability.md)slutprodukter.

Leveransprocessen kan automatiseras genom att man förbereder en leverans och/eller skickar den i ett arbetsflöde. Mer information om aktiviteter av leveranstyp i arbetsflöden finns i [det här avsnittet](../../workflow/using/about-action-activities.md).

Adobe Campaign erbjuder följande leveranskanaler:

1. **E-postkanal**: Med e-postleveranser kan du skicka personaliserade e-postmeddelanden till målpopulationen. Mer information finns i [Om e-postkanal](../../delivery/using/about-email-channel.md).
1. **Direktpostkanal**: Med direktutskick kan du generera en extraheringsfil som innehåller data om målpopulationen. Mer information finns i [Om direktmeddelandekanal](../../delivery/using/about-direct-mail-channel.md).
1. **Mobilkanal**: leveranser i mobilkanaler gör att du kan skicka personaliserade SMS- eller LINE-meddelanden till målpopulationen. Se [SMS-kanal](../../delivery/using/sms-channel.md).
1. **Mobil programkanal**: mobilappsleveranser gör att du kan skicka meddelanden till iOS- och Android-system. Se kapitlet om [mobilappskanalen](../../delivery/using/about-mobile-app-channel.md) .

   Andra kanaler beskrivs på [den här sidan](../../delivery/using/other-channels.md).

   >[!NOTE]
   >
   >Användningen av flera kanaler beror på ditt paket. Kontrollera licensavtalet.

Leveranser kan göras **online** (via e-post, en av mobilkanalerna och push-meddelanden) och **offline** (direktreklamkanal).

Beroende på kanalen kan leveranslägena vara:

* Direktleverans via Adobe Campaign (standardläge för e-postkanal).
* Extern leverans via en specialoperator som får den utdatafil som genereras av leveransguiden (standardläge för direktpostkanal).

Externa konton konfigureras via **[!UICONTROL Administration > Platform > External accounts]** noden. Den här konfigurationen bör endast utföras av expertanvändare.

## E-postleveranser {#email-deliveries}

E- [postkanalen](../../delivery/using/about-email-channel.md) är en av huvudkanalerna i Adobe Campaign, och du kan schemalägga och skicka personaliserade e-postmeddelanden till specifika mål.

Du kan skicka olika typer av e-postmeddelanden:

* E-post för enstaka sändning: e-postmeddelanden som du kan skicka en gång till ett definierat mål. De används vanligtvis för att marknadsföra ett visst innehåll som bara ska förberedas och skickas en gång (nyhetsbrev, e-postreklam osv.).
* Återkommande e-postmeddelanden: i en kampanj skicka samma e-postmeddelande regelbundet och sammanställa varje sändning och dess rapporter regelbundet. Samma e-post skickas, men vanligtvis till ett annat mål, baserat på det giltiga målet för den dag då meddelandet skickas. Ett vanligt exempel är ett födelsedagsmeddelande. Mer information finns i [Återkommande leveranser](../../workflow/using/recurring-delivery.md).
* Transactional emails: enhetliga e-postmeddelanden som triggas utifrån kundernas beteende. Se [Transactional Messaging](../../message-center/using/about-transactional-messaging.md).

Mer information om leveransanvändning och rekommendationer finns i Bästa praxis för Campaign [Delivery](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html).

Mer information om olika typer av leveranser finns i [det här avsnittet](../../delivery/using/types-of-deliveries.md).

## Mobila leveranser {#mobile-deliveries}

Med Adobe Campaign kan ni leverera [SMS](../../delivery/using/sms-channel.md) - och [LINE](../../delivery/using/line-channel.md) -meddelanden till mobiler.

För SMS-meddelanden kan du skapa, ändra och anpassa meddelanden endast i textformat. Du kan även förhandsgranska dina SMS-meddelanden innan de skickas.

För LINE-meddelanden kan du skicka text, bilder och länkar.

För att kunna leverera SMS- eller LINE-meddelanden till en mobiltelefon behöver du:

* Ett externt konto har konfigurerats på **[!UICONTROL Mobile (SMS)]** kanalen eller i **[!UICONTROL LINE]** kanalen.
* En SMS- eller LINE-leveransmall som är korrekt länkad till det här externa kontot.

## Push-meddelanden {#push-notifications}

Med Adobe Campaign kan ni skicka personaliserade och segmenterade [push-meddelanden](../../delivery/using/about-mobile-app-channel.md) på iOS- och Android-mobilenheter via dedikerade appar. När konfigurations- och integrationsstegen är klara kan iOS- och Android-leveranser skapas och skickas. Du kan också utforma avancerade meddelanden med bilder eller videoklipp.

## Direktreklam {#direct-mail}

[Direktreklam](../../delivery/using/about-direct-mail-channel.md) är en offlinekanal som gör att du kan anpassa och generera den fil som direktreklamleverantörer behöver. Det ger er möjlighet att blanda online- och offlinekanaler i era kundresor.

Med onlinekanaler kan du skapa meddelanden (e-post, SMS, mobilappsleverans osv.) och skicka dem till er målgrupp direkt från Adobe Campaign. Med offlinekanaler är det annorlunda. När du förbereder en direktutskick genererar Adobe Campaign en fil som innehåller alla målprofiler och den valda kontaktinformationen (till exempel postadress). Du kan sedan skicka den här filen till din direktreklamleverantör som tar hand om själva sändningen.
