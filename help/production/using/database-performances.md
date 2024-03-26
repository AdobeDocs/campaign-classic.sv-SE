---
product: campaign
title: Databasprestanda
description: Databasprestanda
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
badge-v7-prem: label="lokal och hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 33dcfd4b-51fd-44f4-98e0-23eafb79d7da
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 7%

---

# Databasprestanda{#database-performances}



De flesta prestandaproblem är kopplade till databasunderhåll. Här är fyra huvudtips som hjälper dig att hitta orsaken till långsamma prestanda:

* Konfiguration
* Installation och konfigurering av Adobe Campaign-plattformen
* Databasunderhåll
* Realtidsdiagnos

## Konfiguration {#configuration}

Kontrollera att den ursprungliga Adobe Campaign-plattformskonfigurationen fortfarande är giltig och, om det behövs, omvärdera kundens behov i fråga om leveransbarhet eller databasstorlek. Vi rekommenderar även att du kör en fullständig maskinvarukontroll (CPU-, RAM-, IO-system).

>[!NOTE]
>
>Du kan referera till [Adobe Campaign guide för maskinvarustorlek](https://helpx.adobe.com/se/campaign/kb/hardware-sizing-guide.html) för insikter.

## Plattformskonfiguration {#platform-configuration}

Felaktig konfiguration kan påverka plattformens prestanda. Vi rekommenderar att du kontrollerar nätverkskonfigurationen, alternativen för plattformsleverans och MTA-konfigurationen i **serverConf.xml** -fil.

## Databasunderhåll {#database-maintenance}

**Åtgärd för databasrensning**

Kontrollera att databasrensningen fungerar. Om du vill göra det läser du loggfilerna för att se om de innehåller några fel. Mer information om detta finns i [det här avsnittet](../../production/using/database-cleanup-workflow.md).

**Underhållsplaner**

Kontrollera att databasunderhållet är korrekt schemalagt och att det körs. Kontakta databasadministratören om du vill veta mer om:

* Deras underhållsplan
* Underhållsplaner som körts tidigare
* Visa skriptloggarna

Mer information om detta finns i [det här avsnittet](../../production/using/recommendations.md).

>[!IMPORTANT]
>
>Om du använder en mellanleverantörskonfiguration är det viktigt att databaserna upprätthålls regelbundet. När marknadsföringsinstansen analyserar en leverans på marknadsföringsplattformen skickar den information till mellanleverantörsinstansen. Om processen går långsammare kommer marknadsinstansen att påverkas.

**Hantera arbetsregister**

Kontrollera antal och storlek på arbetsregister. När de överskrider en viss storlek påverkas databasens prestanda. De här tabellerna skapas av arbetsflöden och leveranser. De finns kvar i databasen medan arbetsflöden och leveranser är aktiva. Om du vill begränsa storleken på arbetsregister kan du utföra följande åtgärder:

* Stoppa eller ta bort leveranser med följande status: **[!UICONTROL Failed]**, **[!UICONTROL In progress]**, **[!UICONTROL Ready for delivery]**, eller **[!UICONTROL Paused]**.
* Stoppa eller ta bort arbetsflöden som pausats på grund av ett fel.
* Stoppa alla arbetsflöden som används för tester som inte innehåller en **[!UICONTROL End]** verksamhet och vars status därför kvarstår **[!UICONTROL Paused]**.

>[!IMPORTANT]
>
>Om operationen tar lång tid och frigör mycket utrymme innebär detta att det krävs ett djupgående underhåll (ombyggnad av index osv.). Mer information om detta finns i [det här avsnittet](../../production/using/recommendations.md).

**Adobe Campaign processövervakning**

Beroende på Adobe Campaign installationsinställningar kan två verktyg användas för plattformsövervakning:

* Instansproduktionssidan. Mer information finns i [Manuell övervakning](../../production/using/monitoring-processes.md#manual-monitoring).
* The *netreport* skript. Mer information finns i [Automatisk övervakning via Adobe Campaign-skript](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts).

## Specifikationer {#specifics}

Det kan bli nödvändigt att köra en realtidsdiagnos för att identifiera orsaken till problemet. Börja med att kontrollera process- och plattformsloggfilerna och övervaka sedan databasaktiviteten medan problemet återskapas. Var särskilt uppmärksam på följande:

* Planen för utförande av underhåll
* SQL-frågor som körs
* Huruvida externa processer körs samtidigt (rensning, import, sammanställd beräkning osv.).
