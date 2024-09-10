---
product: campaign
title: Kommunikationskanaler
description: Skapa leveranser för att skicka personanpassade meddelanden i olika kanaler
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Cross Channel Orchestration, Email, SMS, In App, Direct Mail, Push
role: User
exl-id: 92b5e013-b619-4f0b-b0b1-1fc2e653ceac
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '1214'
ht-degree: 10%

---

# Kommunikationskanaler{#communication-channels}

Med Adobe Campaign kan du skicka flerkanalskampanjer, inklusive e-post, SMS, LINE-meddelanden, push-meddelanden och direktreklam, och mäta hur effektiva de är med hjälp av olika dedikerade [rapporter](../../reporting/using/delivery-reports.md). Dessa meddelanden är utformade och skickas genom leveranser och kan anpassas för varje mottagare.

De viktigaste funktionerna är målinriktning, definition och personalisering av meddelanden, genomförande av kommunikation och tillhörande verksamhetsrapporter. Den huvudsakliga funktionella åtkomstpunkten är leveransassistenten. Den här åtkomstpunkten leder till flera funktioner som täcks av Adobe Campaign.

>[!NOTE]
>
>Adobe Campaign har en uppsättning verktyg för att övervaka leveransen och optimera e-postutskick. Läs mer i [det här avsnittet](about-deliverability.md).

Leveransprocessen kan automatiseras genom att man förbereder en leverans och/eller skickar den i ett arbetsflöde. Mer information om aktiviteter av leveranstyp i arbetsflöden finns i [det här avsnittet](../../workflow/using/about-action-activities.md).

Adobe Campaign erbjuder följande leveranskanaler:

1. **E-postkanal**: Med e-postleveranser kan du skicka personaliserade e-postmeddelanden till målpopulationen. Mer information finns i [Om e-postkanal](about-email-channel.md).
1. **Direktutskick**: Med direktutskick kan du generera en extraheringsfil som innehåller data om målpopulationen. Mer information finns i [Om direktmeddelandekanal](about-direct-mail-channel.md).
1. **Mobilkanal**: Med leveranser i mobilkanaler kan du skicka personaliserade SMS- eller LINE-meddelanden till målpopulationen. Se [SMS-kanal](sms-channel.md).
1. **Mobilappskanal**: Med mobilappsleveranser kan du skicka meddelanden till iOS- och Android-system. Se kapitlet [Mobilappskanalen](about-mobile-app-channel.md).

   Andra kanaler beskrivs i [det här avsnittet](#other-channels).

   >[!NOTE]
   >
   >Antalet tillgängliga kanaler beror på ditt kontrakt. Kontrollera licensavtalet.

Leveranser kan utföras **online** (via e-post, en av mobilkanalerna och push-meddelanden) och **offline** (direktreklamkanal).

Beroende på kanalen kan leveranslägena vara:

* Direktleverans via Adobe Campaign (standardläge för e-postkanal).
* Extern leverans via en specialoperator som får den utdatafil som skapas av leveransassistenten (standardläge för direktreklamkanal).

Externa konton konfigureras via noden **[!UICONTROL Administration > Platform > External accounts]**. Den här konfigurationen bör endast utföras av expertanvändare.

## E-postleveranser {#email-deliveries}

[E-postkanalen](about-email-channel.md) är en av huvudkanalerna i Adobe Campaign, vilket gör att du kan schemalägga och skicka personaliserade e-postmeddelanden till specifika mål.

Du kan skicka olika typer av e-postmeddelanden:

* Skicka e-post en gång: e-postmeddelanden som du kan skicka en gång till ett definierat mål. De används vanligtvis för att marknadsföra ett visst innehåll som bara ska förberedas och skickas en gång (nyhetsbrev, e-postreklam osv.).
* Återkommande e-postmeddelanden: skicka samma e-postmeddelande regelbundet i en kampanj och samla varje sändning och dess rapporter regelbundet. Samma e-post skickas, men vanligtvis till ett annat mål, baserat på det giltiga målet för den dag då meddelandet skickas. Ett vanligt exempel är ett födelsedagsmeddelande. Mer information finns i [Återkommande leveranser](../../workflow/using/recurring-delivery.md).
* Transaktionsbaserade e-postmeddelanden: enhetliga e-postmeddelanden som utlöses utifrån kundernas beteende. Se [Transactional messaging](../../message-center/using/about-transactional-messaging.md).

Mer information om leveransanvändning och rekommendationer finns i [Bästa praxis för leverans](delivery-best-practices.md).

Mer information om olika typer av leveranser finns i [det här avsnittet](#types-of-deliveries).

## Mobila leveranser {#mobile-deliveries}

Med Adobe Campaign kan du leverera [SMS](sms-channel.md)- och [LINE](line-channel.md)-meddelanden på mobiler.

För SMS-meddelanden kan du skapa, ändra och anpassa meddelanden endast i textformat. Du kan även förhandsgranska dina SMS-meddelanden innan de skickas.

För LINE-meddelanden kan du skicka text, bilder och länkar.

För att kunna leverera SMS- eller LINE-meddelanden till en mobiltelefon behöver du:

* Ett externt konto har konfigurerats på **[!UICONTROL Mobile (SMS)]**-kanalen eller på **[!UICONTROL LINE]**-kanalen.
* En SMS- eller LINE-leveransmall som är korrekt länkad till det här externa kontot.

## Push-meddelanden {#push-notifications}

Med Adobe Campaign kan du skicka personliga och segmenterade [push-meddelanden](about-mobile-app-channel.md) på iOS- och Android-mobilenheter via dedikerade appar. När konfigurations- och integrationsstegen är klara kan iOS och Android levereras. Du kan också utforma avancerade meddelanden med bilder eller videoklipp.

## Direktmeddelande {#direct-mail}

[Direktutskick](about-direct-mail-channel.md) är en offlinekanal som gör att du kan anpassa och generera den fil som direktutskick kräver. Det ger dig möjligheten att blanda online- och offline-kanaler i kundresorna.

Med onlinekanaler kan du skapa meddelanden (e-post, SMS, leveransmeddelanden för mobilappar etc.)  och skicka dem till din målgrupp direkt från Adobe Campaign.  Med offlinekanaler fungerar det annorlunda.  När du förbereder ett direktutskick genererar Adobe Campaign en fil som innehåller samtliga målprofiler och den valda kontaktinformationen (exempelvis postadress).  Du kan sedan skicka den här filen till din leverantör för direktmeddelanden som i sin tur tar hand om själva utskicket.

## Andra kanaler {#other-channels}

Adobe Campaign erbjuder en mall för telefonleverans som används för att skapa externa leveranser. Om du använder den här kanalen måste du konfigurera dedikerade metoder för att bearbeta utdatafiler. Konfigurationsstegen är desamma som för [Direct-postkanalen](about-direct-mail-channel.md).

>[!NOTE]
>
>Telefonkanalen är inte tillgänglig direkt. För att implementeringen ska fungera måste Adobe Consulting eller en Adobe-partner vara engagerade. Kontakta din Adobe-representant om du vill ha mer information.

För leveranser av typen Annan används dessutom en specifik teknisk mall som inte utför någon process: på så sätt kan de hantera marknadsföringsåtgärder som utförs utanför Adobe Campaign-plattformen.

Den här kanalen har ingen specifik mekanism. Det är en allmän kanal som har ett eget alternativ för extern kontodirigering, leveransmalltyp och kampanjarbetsflödesaktivitet, precis som alla andra kommunikationskanaler som finns i Adobe Campaign.

Den här kanalen är avsedd endast för beskrivande syften, till exempel för att definiera leveranser för vilka du vill hålla reda på målet för en kampanj som har utförts i ett annat verktyg än Adobe Campaign.

## Typer av leveranser{#types-of-deliveries}

Det finns tre typer av leveransobjekt i Campaign:

### Enskild leverans {#single-delivery}

En **leverans** är ett fristående leveransobjekt som körs en gång. Den kan dupliceras, förberedas på nytt, men så länge den är i det slutliga tillståndet (avbryts, stoppas, slutförd) kan den inte återanvändas.

Leveranser kan skapas antingen från listan över leveranser eller i ett arbetsflöde via en [Leverans](../../workflow/using/delivery.md) -aktivitet.

Arbetsflödena innehåller också specifika leveransaktiviteter beroende på vilken typ av kanal du vill använda. Mer information om de här aktiviteterna finns i [det här avsnittet](../../workflow/using/cross-channel-deliveries.md).

### Återkommande leverans {#recurring-delivery}

Med en **återkommande leverans** kan du skapa en ny leverans varje gång aktiviteten körs. På så sätt slipper du skapa en ny leverans för återkommande uppgifter.

Om du till exempel kör den här typen av aktivitet en gång i månaden får du 12 leveranser efter ett år.

Återkommande leveranser skapas i arbetsflöden via aktiviteten [Återkommande leverans](../../workflow/using/recurring-delivery.md). Ett exempel på den här aktiviteten visas i det här avsnittet: [Skapa en återkommande leverans i ett målarbetsflöde](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow).

### Kontinuerlig leverans {#continuous-delivery}

Med en **kontinuerlig leverans** kan du lägga till nya mottagare i en befintlig leverans, vilket innebär att du slipper skapa en ny leverans varje gång den körs.

Om en information i leveransen ändras (innehåll, namn osv.) skapas ett nytt leveransobjekt vid leveranskörningen. Om ingen information har ändrats återanvänds samma leveransobjekt och leverans- och spårningsloggarna läggs till i samma objekt.

Om du till exempel kör den här typen av aktivitet en gång i månaden får du en leverans efter ett år (förutsatt att du inte har ändrat leveransen).

Kontinuerliga leveranser skapas i arbetsflöden via [Kontinuerlig leveransaktivitet](../../workflow/using/continuous-delivery.md).
