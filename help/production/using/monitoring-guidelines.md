---
title: Riktlinjer för övervakning
description: I detta avsnitt presenteras allmänna riktlinjer för övervakningen av Campaign Classic.
page-status-flag: never-activated
uuid: cf0d782d-47bf-40ae-ab6f-d1d47fa15792
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: introduction
discoiquuid: 8b33e6af-15c3-4b30-8ad6-d76a1f33be21
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7d944973e10c4df166325049b947e359853a2353
workflow-type: tm+mt
source-wordcount: '699'
ht-degree: 0%

---


# Riktlinjer för övervakning {#monitoring-guidelines}

## Instansövervakningsinstrumentpanel {#instance-monitoring-dashboard}

Fliken, som är tillgänglig från Campaign Classic hemsida, är den viktigaste startpunkten som hjälper dig att övervaka instansen. **[!UICONTROL Monitoring]**

Här finns en kontrollpanel med information om vad som händer i din instans:  status (version av bygge, installerade paket osv.), systemindikatorer, loggar, arbetsflöden som körs, status för senaste skickade leveranser osv.

Detaljerad information finns [här](../../production/using/monitoring-processes.md).

![](assets/monitoring_tab.png)

## Övervaka Campaign Classic-processer {#monitoring-campaign-classic-processes}

Det finns fler sätt att övervaka olika Campaign-processer. Mer information finns i avsnitten nedan.

<table>
<tr><td><img src="assets/do-not-localize/instance_icon.svg" width="60px"><p><a href="#monitoring-instance">Övervaka instansen</a></p></td>
<td><img src="assets/do-not-localize/workflow_icon.svg" width="60px"><p><a href="#moniroting-workflows">Övervaka arbetsflöden</a></p></td>
<td><img src="assets/do-not-localize/database_icon.svg" width="60px"><p><a href="#monitoring-database">Övervaka databasen</a></p></td>
<td><img src="assets/do-not-localize/delivery_icon.svg" width="60px"><p><a href="#monitoring-deliveries">Bildskärmsleveranser</a></p></td></tr>
</table>

### Övervaka instansen {#monitoring-instance}

**Automatiska övervakningsverktyg**

Flera automatiska metoder är tillgängliga. som hjälper dig att övervaka instansen. Du kan till exempel skapa e-postrapporter med identifierade avvikelser, hämta en lista med indikatorer i XML-format osv. [Klicka här](../../production/using/monitoring-processes.md#automatic-monitoring) om du vill ha mer information.

**Granskningsspår**

Med granskningsspåret kan du visualisera den fullständiga historiken över ändringar som rör alternativ, arbetsflöden och scheman i instansen. [Klicka här](../../production/using/audit-trail.md) om du vill ha mer information.

**Kontrollpanelen**

På Kontrollpanelen kan du hantera flera inställningar för din instans: hantera URL-behörigheter, kontrollera instansinformation som serverns build-versioner osv. Du kan också övervaka det tillgängliga utrymmet på de SFTP-servrar som är anslutna till din instans. [Klicka här](https://docs.adobe.com/content/help/en/control-panel/using/control-panel-home.html) om du vill ha mer information.

>[!NOTE]
>
>Observera att Kontrollpanelen endast är tillgänglig för administratörsanvändare och för alla kunder som använder Adobe Managed Services.

### Övervaka arbetsflöden {#monitoring-workflows}

**Värmekarta för arbetsflöde**

Workflow HeatMap ger en visuell representation av alla arbetsflöden som körs på din instans. Det gör att du enkelt kan övervaka inläsningen av instansen och planera arbetsflödena utifrån detta. [Klicka här](../../workflow/using/heatmap.md) om du vill ha mer information.

**Granskningsspår**

Med granskningsspåret kan du visualisera alla ändringar som har gjorts i arbetsflöden samt deras aktuella tillstånd. [Klicka här](../../production/using/audit-trail.md).

**Felsökning av arbetsflöden**

Du kan utföra specifika åtgärder när du stöter på problem med arbetsflödeskörningen. [Klicka här](../../production/using/workflow-execution.md) för mer information

**Övervakning av arbetsflödesstatus**

Utöver heatmap-kartan kan du skapa ett arbetsflöde där du kan övervaka statusen för en uppsättning arbetsflöden och skicka återkommande meddelanden till arbetsledare. [Klicka här](../../workflow/using/supervising-workflows.md) om du vill ha mer information.

**Allmänna riktlinjer**

Du kan förbättra prestandan genom att följa riktlinjer och bästa praxis när du använder arbetsflöden. Mer information finns i följande avsnitt:
* [Bästa tillvägagångssätt när du använder arbetsflöden](../../workflow/using/workflow-best-practices.md)
* [Övervaka körning av arbetsflöde](../../workflow/using/monitoring-workflow-execution.md)

### Övervaka leveranser {#monitoring-deliveries}

**SMTP-rapporter**

SMTP-rapporter visar leveransstatistik och SMTP-fel per domän. [Klicka här](../../production/using/monitoring-processes.md) om du vill ha mer information.

**God praxis**

[De bästa sätten att skicka och designa](http://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html) kan hjälpa er att förbättra deras prestanda.

**Felsökning** av leveranser Specifika åtgärder kan utföras när du stöter på leveransproblem:
* [Leveransproblem](../../production/using/performance-and-throughput-issues.md#deliverability_issues)
* [Bildvisningsproblem](../../production/using/image-display-issues.md)
* [Problem med leveransresultat](../../delivery/using/monitoring-a-delivery.md#performance_issues)
* [Temporära filproblem](../../production/using/temporary-files.md) - endast *på lokala värdmodeller*

### Övervaka databasen {#monitoring-database}

**Arbetsflöde för databasrensning**

Med hjälp av arbetsflödet för att rensa databas kan du ta bort föråldrade data från databasen. Vi rekommenderar att du undviker exponentiell tillväxt i databasen. [Klicka här](../../production/using/database-cleanup-workflow.md) om du vill ha mer information.

**Felsökning av databasprestanda**

Specifika åtgärder kan utföras när problem med databasprestanda påträffas. [Klicka här](../../production/using/database-performances.md) om du vill ha mer information.

**Databasunderhåll**

*enbart lokala och hybridhosting-modeller*

Vi rekommenderar att du regelbundet utför databasunderhåll för att undvika överförbrukning av diskutrymme, vilket påverkar databasåtkomsten. [Klicka här](../../production/using/recommendations.md) om du vill ha mer information.

**Säkerhetskopiering och återställning**

*enbart lokala och hybridhosting-modeller*

Säkerhetskopiering är nödvändigt för att undvika dataförlust i händelse av problem (oavsett om det är fysiskt eller systemrelaterat) på en dator. [Klicka här](../../production/using/backup.md) om du vill ha mer information. Återställningsproceduren beskrivs i [detta avsnitt](../../production/using/restoration.md).

## Campaign Classic tekniska principer {#campaign-classic-technical-principles}

Tekniska resurser finns i Campaign Classic dokumentation. Vi rekommenderar att du lär dig mer om dessa ämnen innan du utför någon teknisk åtgärd på din instans.

**Värdmodeller och funktioner**

* [Värdmodeller för Campaign Classic](../../installation/using/hosting-models.md)
* [Funktioner för värdmodeller](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html)

**Serverkonfiguration**

*Endast lokala och hybridhosting-modeller*

* [Obligatoriska serverkonfigurationer](../../installation/using/campaign-server-configuration.md)
* [Serverconf.xml, filkonfiguration](../../installation/using/the-server-configuration-file.md)
* [Serverkonfiguration för leverans](../../installation/using/email-deliverability.md)
* [Kommandorader för att skapa en instans och deklarera en databas](../../installation/using/command-lines.md)

**Allmänna principer**

* [Campaign Classic-arkitektur](../../production/using/general-architecture.md)
* [Campaign Classic-moduler](../../production/using/operating-principle.md)
* [Alternativ för Campaign Classic](../../installation/using/configuring-campaign-options.md)
* [Så här ställer du in modulernas automatiska start](../../production/using/administration.md)
* [Princip för kampanjkonfiguration](../../production/using/configuration-principle.md)
* [Felsökningsprocedurer](../../production/using/performance-and-throughput-issues.md)
