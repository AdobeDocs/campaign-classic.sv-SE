---
title: Databasprestanda
seo-title: Databasprestanda
description: Databasprestanda
seo-description: null
page-status-flag: never-activated
uuid: 47ff7532-1fe7-47c2-bc3b-0f46d3a4a288
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 6358c8fd-2b75-4462-acd1-887ee44d3110
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 34cd6e6cf5652c9e2163848c2b1ef32f53ee6ca4

---


# Databasprestanda{#database-performances}

De flesta prestandaproblem är kopplade till databasunderhåll. Här är fyra huvudtips som hjälper dig att hitta orsaken till långsamma prestanda:

* Konfiguration,
* Installation och konfigurering av Adobe Campaign-plattformen,
* Databasunderhåll.
* Realtidsdiagnos.

## Konfiguration {#configuration}

Kontrollera att den ursprungliga Adobe Campaign-plattformskonfigurationen fortfarande är giltig och, om det behövs, omvärdera kundens behov i fråga om tillgänglighet eller databasstorlek. Vi rekommenderar även att du kör en fullständig maskinvarukontroll (CPU-, RAM-, IO-system).

>[!NOTE]
>
>I [Adobe Campaign Harware Sizing Guide](https://helpx.adobe.com/campaign/kb/hardware-sizing-guide.html) hittar du information om detta.

## Plattformskonfiguration {#platform-configuration}

Felaktig konfiguration kan påverka plattformens prestanda. Vi rekommenderar att du kontrollerar nätverkskonfigurationen, alternativen för plattformsleverans och MTA-konfigurationen i **filen serverConf.xml** .

## Databasunderhåll {#database-maintenance}

**Åtgärd för databasrensning**

Kontrollera att databasrensningen fungerar. Om du vill göra det läser du loggfilerna för att se om de innehåller några fel. Mer information finns i [det här avsnittet](../../production/using/database-cleanup-workflow.md).

**Underhållsplaner**

Kontrollera att databasunderhållet är korrekt schemalagt och att det körs. Kontakta databasadministratören om du vill veta mer om:

* underhållsschema,
* underhållsplaner som tidigare har genomförts,
* visa skriptloggarna.

Mer information finns i [det här avsnittet](../../production/using/recommendations.md).

>[!CAUTION]
>
>Om du använder en mellanleverantörskonfiguration är det viktigt att databaserna upprätthålls regelbundet. När marknadsföringsinstansen analyserar en leverans på marknadsföringsplattformen skickar den information till mellanleverantörsinstansen. Om processen går långsammare kommer marknadsinstansen att påverkas.

**Hantera arbetsregister**

Kontrollera antal och storlek på arbetsregister. När de överskrider en viss storlek påverkas databasens prestanda. De här tabellerna skapas av arbetsflöden och leveranser. De finns kvar i databasen medan arbetsflöden och leveranser är aktiva. Om du vill begränsa storleken på arbetsregister kan du utföra följande åtgärder:

* stoppa eller ta bort leveranser med följande status: **[!UICONTROL Failed]** , **[!UICONTROL In progress]** , **[!UICONTROL Ready for delivery]** eller **[!UICONTROL Paused]** .
* stoppa eller ta bort arbetsflöden som pausats på grund av ett fel,
* stoppa alla arbetsflöden som används för tester som inte innehåller någon **[!UICONTROL End]** aktivitet och vars status därför kvarstår **[!UICONTROL Paused]** .

>[!CAUTION]
>
>Om operationen tar lång tid och frigör mycket utrymme innebär detta att det krävs ett djupgående underhåll (ombyggnad av index osv.). Mer information finns i [det här avsnittet](../../production/using/recommendations.md).

**Processövervakning för Adobe Campaign**

Beroende på installationsinställningarna för Adobe Campaign kan två verktyg användas för plattformsövervakning:

* produktionssidan för instansen. Mer information finns i [Manuell övervakning](../../production/using/monitoring-processes.md#manual-monitoring).
* Netreport-skriptet. Mer information finns i [Automatisk övervakning via skript](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts)i Adobe Campaign.

## Specifikationer {#specifics}

Det kan bli nödvändigt att köra en realtidsdiagnos för att identifiera orsaken till problemet. Börja med att kontrollera process- och plattformsloggfilerna och övervaka sedan databasaktiviteten medan problemet återskapas. Var särskilt uppmärksam på följande:

* planen för utförande av underhåll,
* SQL-frågor som körs,
* huruvida externa processer körs samtidigt (rensning, import, sammanställd beräkning osv.).

