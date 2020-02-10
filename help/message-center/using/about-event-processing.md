---
title: Om händelsebearbetning
seo-title: Om händelsebearbetning
description: Om händelsebearbetning
seo-description: null
page-status-flag: never-activated
uuid: 6c3e02b3-0d4d-4661-952a-e4915ca9ef92
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: a78c9986-7c49-47db-99a0-9f0949c4dee7
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c2c53041d8a19a491b8ec4da12a8a0ced25cf9a

---


# Om händelsebearbetning{#about-event-processing}

När det gäller transaktionsmeddelanden genereras en händelse av ett externt informationssystem och skickas till Adobe Campaign via metoderna **[!UICONTROL PushEvent]** och **[!UICONTROL PushEvents]** (se [händelsebeskrivningen](../../message-center/using/event-description.md)). Den innehåller data som är länkade till händelsen, till exempel dess typ (orderbekräftelse eller kontoskapande på en webbplats till exempel), e-postadress eller mobilnummer, samt annan information som gör att du kan förbättra och anpassa transaktionsmeddelandet före leverans. Det kan vara kundens kontaktinformation, meddelandespråket eller e-postformatet.

Exempel på händelsedata:

![](assets/messagecenter_events_request_001.png)

Om du vill bearbeta transaktionsmeddelandehändelser måste följande steg utföras:

1. Händelsesamling,
1. Händelseberikning innan de överförs till en meddelandemall (om du har förvärvat anrikningsalternativet som är tillgängligt för transaktionsmeddelandemodulen i Campaign),
1. Händelseöverföring till en meddelandemall,
1. händelseberikning med personaliseringsdata,
1. Leveranssätt,
1. Återvinning av händelser vars länkade leverans misslyckades (det här steget kan utföras via ett Adobe Campaign-arbetsflöde).

## Händelsestatus {#event-statuses}

I **Händelsehistoriken**, under **[!UICONTROL Message Center]** > **[!UICONTROL Event history]** , grupperas alla bearbetade händelser i en enda vy. De kan kategoriseras efter händelsetyp eller **status**. Dessa statusvärden är:

* **Väntande**: vilket innebär att händelsen kan vara

   * en händelse som precis har samlats in och som ännu inte har bearbetats. I **[!UICONTROL Number of errors]** kolumnen visas värdet 0. E-postmallen har ännu inte länkats.
   * en händelse bearbetades men vars bekräftelse är felaktig. Kolumnen visar ett värde som inte är 0. **[!UICONTROL Number of errors]** Om du vill veta när den här händelsen ska behandlas igen läser du i **[!UICONTROL Process requested on]** kolumnen.

* **Väntande leverans**: händelsen bearbetades och leveransmallen är länkad. E-postmeddelandet väntar på att levereras och den klassiska leveransprocessen tillämpas. Du kan öppna leveransen om du vill ha mer information. Se [Leverans](../../delivery/using/about-message-tracking.md).
* **Skickat**, **ignorerat** och **leveransfel**: dessa leveransstatus återställs via arbetsflödet **updateEventsStatus** . Mer information får du genom att öppna den relevanta leveransen.
* **Händelsen omfattas** inte: routningsfasen för meddelandecentret misslyckades. Adobe Campaign hittade till exempel inte e-postmeddelandet som fungerar som en mall för händelsen.
* **Händelsen har upphört att gälla**: det maximala antalet sändningsförsök har uppnåtts. Händelsen betraktas som null.
