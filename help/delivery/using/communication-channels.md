---
title: Kommunikationskanaler
seo-title: Kommunikationskanaler
description: Skapa leveranser för att skicka personaliserade meddelanden i olika kanaler.
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
source-git-commit: eccf0e9899426c2517748c7a72611ff098291cd2
workflow-type: tm+mt
source-wordcount: '1183'
ht-degree: 11%

---


# Kommunikationskanaler{#communication-channels}

Med Adobe Campaign kan ni skicka flerkanalskampanjer, inklusive e-post, SMS, LINE-meddelanden, push-meddelanden och direktreklam, och mäta hur effektiva de är med hjälp av olika dedikerade [rapporter](../../reporting/using/delivery-reports.md). Dessa meddelanden är utformade och skickas genom leveranser och kan anpassas för varje mottagare.

De viktigaste funktionerna är målinriktning, definition och personalisering av meddelanden, genomförande av kommunikation och tillhörande verksamhetsrapporter. Den huvudsakliga funktionella åtkomstpunkten är leveransguiden. Den här åtkomstpunkten leder till flera funktioner som täcks av Adobe Campaign.

>[!NOTE]
>
>Adobe Campaign har en uppsättning verktyg för att övervaka leveransen och optimera e-postutskick. Mer information finns i Komma igång med [slutprodukten](../../delivery/using/deliverability-key-points.md) och i Hantering [av](../../delivery/using/about-deliverability.md)slutprodukter.

Leveransprocessen kan automatiseras genom att man förbereder en leverans och/eller skickar den i ett arbetsflöde. Mer information om aktiviteter av leveranstyp i arbetsflöden finns i [det här avsnittet](../../workflow/using/about-action-activities.md).

Adobe Campaign erbjuder följande leveranskanaler:

1. **E-postkanal**: Med e-postleveranser kan du skicka personaliserade e-postmeddelanden till målpopulationen. Mer information finns i [Om e-postkanal](../../delivery/using/about-email-channel.md).
1. **Direktpostkanal**: Med direktutskick kan du generera en extraheringsfil som innehåller data om målpopulationen. Mer information finns i [Om direktmeddelandekanal](../../delivery/using/about-direct-mail-channel.md).
1. **Mobilkanal**: leveranser i mobilkanaler gör att du kan skicka personaliserade SMS- eller LINE-meddelanden till målpopulationen. Se [SMS-kanal](../../delivery/using/sms-channel.md).
1. **Mobil programkanal**: mobilappsleveranser gör att du kan skicka meddelanden till iOS- och Android-system. Se kapitlet om [mobilappskanalen](../../delivery/using/about-mobile-app-channel.md) .

   Andra kanaler beskrivs på [den här sidan](../../delivery/using/steps-about-delivery-creation-steps.md#other-channels).

   >[!NOTE]
   >
   >Användningen av flera kanaler beror på ditt paket. Kontrollera licensavtalet.

Leveranser kan göras **online** (via e-post, en av mobilkanalerna och push-meddelanden) och **offline** (direktreklamkanal).

Beroende på kanalen kan leveranslägena vara:

* Direktleverans via Adobe Campaign (standardläge för e-postkanal).
* Extern leverans via en specialoperator som får den utdatafil som genereras av leveransguiden (standardläge för direktpostkanal).

Externa konton konfigureras via **[!UICONTROL Administration > Platform > External accounts]** noden. Den här konfigurationen bör endast utföras av expertanvändare.

## E-postleveranser {#email-deliveries}

E- [postkanalen](../../delivery/using/about-email-channel.md) är en av huvudkanalerna i Adobe Campaign, vilket gör att du kan schemalägga och skicka personaliserade e-postmeddelanden till specifika mål.

Du kan skicka olika typer av e-postmeddelanden:

* E-post för enstaka sändning: e-postmeddelanden som du kan skicka en gång till ett definierat mål. De används vanligtvis för att marknadsföra ett visst innehåll som bara ska förberedas och skickas en gång (nyhetsbrev, e-postreklam osv.).
* Återkommande e-postmeddelanden: i en kampanj skicka samma e-postmeddelande regelbundet och sammanställa varje sändning och dess rapporter regelbundet. Samma e-post skickas, men vanligtvis till ett annat mål, baserat på det giltiga målet för den dag då meddelandet skickas. Ett vanligt exempel är ett födelsedagsmeddelande. For more on this, refer to [Recurring deliveries](../../workflow/using/recurring-delivery.md).
* Transactional emails: enhetliga e-postmeddelanden som triggas utifrån kundernas beteende. Se [Transactional Messaging](../../message-center/using/about-transactional-messaging.md).

Mer information om leveransanvändning och rekommendationer finns i Bästa praxis för Campaign [Delivery](../../delivery/using/delivery-best-practices.md).

Mer information om olika typer av leveranser finns i [det här avsnittet](#types-of-deliveries).

## Mobila leveranser {#mobile-deliveries}

Med Adobe Campaign kan ni leverera [SMS](../../delivery/using/sms-channel.md) - och [LINE](../../delivery/using/line-channel.md) -meddelanden till mobiler.

För SMS-meddelanden kan du skapa, ändra och anpassa meddelanden endast i textformat. Du kan även förhandsgranska dina SMS-meddelanden innan de skickas.

För LINE-meddelanden kan du skicka text, bilder och länkar.

För att kunna leverera SMS- eller LINE-meddelanden till en mobiltelefon behöver du:

* Ett externt konto har konfigurerats på **[!UICONTROL Mobile (SMS)]** kanalen eller i **[!UICONTROL LINE]** kanalen.
* En SMS- eller LINE-leveransmall som är korrekt länkad till det här externa kontot.

## Push-meddelanden {#push-notifications}

Adobe Campaign allows you to send personalized and segmented [push notifications](../../delivery/using/about-mobile-app-channel.md) on iOS and Android mobile devices, through dedicated apps. När konfigurations- och integrationsstegen är klara kan iOS- och Android-leveranser skapas och skickas. Du kan också utforma avancerade meddelanden med bilder eller videoklipp.

## Direktmeddelande {#direct-mail}

[Direktmeddelanden är en offlinekanal som gör att du kan anpassa och generera den fil som leverantören av direktmeddelanden behöver.  ](../../delivery/using/about-direct-mail-channel.md) Det ger dig möjligheten att blanda online- och offline-kanaler i kundresorna.

Med onlinekanaler kan du skapa meddelanden (e-post, SMS, leveransmeddelanden för mobilappar etc.)  och skicka dem till din målgrupp direkt från Adobe Campaign.  Med offlinekanaler fungerar det annorlunda.  När du förbereder ett direktutskick genererar Adobe Campaign en fil som innehåller samtliga målprofiler och den valda kontaktinformationen (exempelvis postadress).  Du kan sedan skicka den här filen till din leverantör för direktmeddelanden som i sin tur tar hand om själva utskicket.

## Andra kanaler {#other-channels}

Adobe Campaign erbjuder mallar för extern leverans. Om du använder dessa kanaler måste du konfigurera dedikerade metoder för att bearbeta utdatafiler. Konfigurationsstegen är desamma som för [Direct-postkanalen](../../delivery/using/about-direct-mail-channel.md).

För leveranser av typen Annan används dessutom en specifik teknisk mall som inte utför någon process: på så sätt kan de hantera marknadsföringsåtgärder som utförs utanför Adobe Campaign.

Den här kanalen har ingen specifik mekanism. Det är en allmän kanal som har ett eget alternativ för extern kontodirigering, leveransmalltyp och kampanjarbetsflödesaktivitet, precis som alla andra kommunikationskanaler som finns i Adobe Campaign.

Den här kanalen är avsedd endast för beskrivande syften, till exempel för att definiera leveranser för vilka du vill hålla reda på målet för en kampanj som har utförts i ett annat verktyg än Adobe Campaign.

## Typer av leveranser{#types-of-deliveries}

Det finns tre typer av leveransobjekt i Campaign:

### Enskild leverans {#single-delivery}

En **leverans** är ett fristående leveransobjekt som körs en gång. Den kan dupliceras, förberedas på nytt, men så länge den är i det slutliga tillståndet (avbryts, stoppas, slutförd) kan den inte återanvändas.

Leveranser kan skapas antingen i listan över leveranser eller i ett arbetsflöde via en [leveransaktivitet](../../workflow/using/delivery.md) .

Arbetsflödena innehåller också specifika leveransaktiviteter beroende på vilken typ av kanal du vill använda. For more on these activities, refer to [this section](../../workflow/using/cross-channel-deliveries.md).

### Återkommande leverans {#recurring-delivery}

Med en **återkommande leverans** kan du skapa en ny leverans varje gång aktiviteten körs. På så sätt slipper du skapa en ny leverans för återkommande uppgifter.

Om du till exempel kör den här typen av aktivitet en gång i månaden får du 12 leveranser efter ett år.

Återkommande leveranser skapas i arbetsflöden via aktiviteten [Återkommande leverans](../../workflow/using/recurring-delivery.md). Ett exempel på den här aktiviteten visas i det här avsnittet: [Skapa en återkommande leverans i ett målarbetsflöde](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow).

### Kontinuerlig leverans {#continuous-delivery}

Med en **kontinuerlig leverans** kan du lägga till nya mottagare till en befintlig leverans, vilket innebär att du slipper skapa en ny leverans varje gång den körs.

Om en information i leveransen ändras (innehåll, namn osv.) skapas ett nytt leveransobjekt vid leveranskörningen. Om ingen information ändrades återanvänds samma leveransobjekt och leverans- och spårningsloggarna läggs till i samma objekt.

Om du till exempel kör den här typen av aktivitet en gång i månaden får du en leverans efter ett år (förutsatt att du inte har ändrat leveransen).

Kontinuerliga leveranser skapas i arbetsflöden via aktiviteten [](../../workflow/using/continuous-delivery.md)Kontinuerlig leverans.
