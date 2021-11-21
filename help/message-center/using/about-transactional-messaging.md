---
product: campaign
title: Kom igång med transaktionsmeddelanden
description: 'Läs mer om Adobe Campaign Classic transaktionsregler och viktiga steg. '
audience: message-center
content-type: reference
topic-tags: introduction
exl-id: dc52e789-d0bf-4e8f-b448-9d69a2762cc1
source-git-commit: f007dcbf63d7a69a6d532d0be99b0fa90f4f6d7a
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 6%

---


# Kom igång med transaktionsmeddelanden {#about-transactional-messaging}

![](../../assets/v7-only.svg)

## Översikt {#overview}

**Transaktionsmeddelanden** (Message Center) är en Campaign-modul som är utformad för att hantera anpassade utlösarmeddelanden som genereras från händelser som skickas av ett externt informationssystem.

Ett transaktionsmeddelande är en individ och en unik kommunikation som skickas i realtid av en leverantör, till exempel en webbplats. Det är särskilt väntat eftersom det innehåller viktig information som mottagaren vill kontrollera eller bekräfta.

Funktioner för transaktionsmeddelanden är utformade för att stödja skalbarhet och tillhandahålla en dygnet runt-tjänst.

* **När ska det vara klart?** Eftersom det här meddelandet innehåller viktig information förväntar sig användaren att det skickas i realtid. Följaktligen måste fördröjningen mellan den händelse som utlöses och det meddelande som anländer vara mycket kort.

* **Varför är det viktigt?** Vanligtvis har ett transaktionsmeddelande höga öppningsfrekvenser. Den bör därför utformas noggrant, eftersom den kan ha stor inverkan på kundernas beteende när den definierar kundrelationen.

* **Exempel?** Det kan vara ett välkomstmeddelande när du har skapat ett konto, en bekräftelse på att en beställning har skickats, en faktura, ett meddelande som bekräftar en lösenordsändring, ett meddelande efter att en kund har bläddrat på din webbplats, ett meddelande om att produkten inte är tillgänglig, ett kontoutdrag osv.

>[!IMPORTANT]
>
>Transactional messaging kräver en specifik licens. Kontrollera licensavtalet.

<!--Before starting with transactional messaging, make sure you read the corresponding [best practices and limitations]().-->

## Driftspolicy för transaktionsmeddelanden {#transactional-messaging-operating-principle}

Adobe Campaign Transactional Messaging-modulen integreras i ett informationssystem som returnerar händelser som ska ändras till personaliserade transaktionsmeddelanden. Dessa meddelanden kan skickas individuellt eller gruppvis via e-post, SMS eller push-meddelanden.

Den här funktionen är beroende av en viss arkitektur, där **körningsinstans** separeras från **kontrollinstans**. Distributionen ger högre tillgänglighet och bättre lasthantering. Mer information finns i [Arkitektur för transaktionsmeddelanden](../../message-center/using/transactional-messaging-architecture.md).

>[!NOTE]
>
>Om du vill skapa nya användare för Message Center-körningsinstanser på Adobe Cloud måste du kontakta [Adobe kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). Message Center-användare är specifika operatorer som kräver dedikerad behörighet för åtkomst **[!UICONTROL Real time events (nmsRtEvent)]** mappar.

Den övergripande processen för transaktionsmeddelanden beskrivs på följande sätt:

![](assets/transactional-msg-overview.png)

Tänk dig att du är ett företag med en webbplats där kunderna kan köpa produkter.

Med Adobe Campaign kan du skicka ett e-postmeddelande till kunder som har lagt till produkter i kundvagnen. När någon av dem lämnar er webbplats utan att gå igenom sina inköp (en extern händelse som utlöser en Campaign-händelse) skickas ett e-postmeddelande om att kunden har lämnat en kundvagn (leverans av transaktionsmeddelande).

De viktigaste stegen för att implementera detta beskrivs nedan i [det här avsnittet](#key-steps).

>[!NOTE]
>
>Adobe Campaign prioriterar bearbetning av transaktionsmeddelanden framför annan leverans.

## Viktiga steg {#key-steps}

De viktigaste stegen när du skapar och hanterar personaliserade transaktionsmeddelanden i Adobe Campaign sammanfattas nedan.

### Steg som ska utföras på kontrollinstansen

På **kontrollinstans** måste du utföra följande åtgärder:

1. [Skapa en händelsetyp](../../message-center/using/creating-event-types.md).
1. [Skapa och utforma meddelandemallen](../../message-center/using/creating-the-message-template.md). Du måste länka en händelse till ditt meddelande under det här steget.
1. [Testa meddelandet](../../message-center/using/testing-message-templates.md).
1. [Publicera meddelandemallen](../../message-center/using/publishing-message-templates.md).

>[!NOTE]
>
>Alla steg ovan utförs på **kontrollinstans**. När du publicerar mallen på kontrollinstansen publiceras den också på alla **körningsinstanser**. Mer information om transaktionsmeddelandeinstanser finns i [Arkitektur för transaktionsmeddelanden](../../message-center/using/transactional-messaging-architecture.md).

### Händelsebearbetning på körningsinstansen

När du har utformat och publicerat transaktionsmeddelandemallen utförs huvudstegen nedan på **körningsinstans**:

1. När händelsen genereras av det externa informationssystemet skickas relevanta data till Campaign via **PushEvent** och **PushEvents** metoder. Se [Händelsesamling](../../message-center/using/about-event-processing.md#event-collection).
1. Händelsen är länkad till rätt meddelandemall. Se [Cirkulera mot en mall](../../message-center/using/about-event-processing.md#routing-towards-a-template).
1. När anrikningsfasen är klar skickas leveransen. Se [Leveranskörning](../../message-center/using/delivery-execution.md). Varje mottagare får ett personligt meddelande.

## Relaterade ämnen {#related-topics}

* [Kom igång med kommunikationskanaler](../../delivery/using/communication-channels.md)
* [Nyckelsteg för att skapa leverans](../../delivery/using/steps-about-delivery-creation-steps.md)
* [Transaktionsmeddelandens arkitektur](../../message-center/using/transactional-messaging-architecture.md)
* [Rapporter om transaktionsmeddelanden](../../message-center/using/about-transactional-messaging-reports.md)
