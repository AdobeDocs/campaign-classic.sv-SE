---
product: campaign
title: Riktlinjer för övervakning
description: Upptäck riktlinjer och bästa praxis för att övervaka instans och processer i Campaign
feature: Monitoring
exl-id: ca0c33c5-7350-462a-bc65-4cab51e529d9
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '743'
ht-degree: 18%

---

# Riktlinjer för övervakning {#monitoring-guidelines}



## Instansövervakningsinstrumentpanel {#instance-monitoring-dashboard}

Fliken **[!UICONTROL Monitoring]**, som du kommer åt från Campaign Classicens hemsida, är startpunkten som du kan använda för att övervaka instansen.

Här finns en kontrollpanel med information om vad som händer i instansen: status (version av bygge, installerade paket, osv.), systemindikatorer, loggar, arbetsflöden som körs, status för senaste skickade leveranser osv.

Detaljerad information finns [här](../../production/using/monitoring-processes.md).

![](assets/monitoring_tab.png)

## Övervaka Campaign Classicens processer {#monitoring-campaign-classic-processes}

<table>
<tr><td><img src="assets/do-not-localize/icon_system.svg" width="60px"><p><a href="#monitoring-instance">Övervaka instansen</a></p></td>
<td><img src="assets/do-not-localize/icon_workflows.svg" width="60px"><p><a href="#monitoring-workflows">Övervaka arbetsflöden</a></p></td>
<td><img src="assets/do-not-localize/icon_send.svg" width="60px"><p><a href="#monitoring-deliveries">Bildskärmsleveranser</a></p></td>
<td><img src="assets/do-not-localize/icon_database.svg" width="60px"><p><a href="#monitoring-database">Övervaka databasen</a></p></td></tr>
</table>

Det finns fler sätt att övervaka olika Campaign-processer. De innehåller flera sätt att övervaka dina instanser för att säkerställa att systemet är felfritt och till slut felsöka problem som kan uppstå när du ställer in arbetsflöden, skickar leveranser osv.

### Övervaka instansen {#monitoring-instance}

<img src="assets/do-not-localize/icon_system.svg" width="60px">

**Automatiska övervakningsverktyg**

Flera automatiska metoder är tillgängliga. för att hjälpa dig att övervaka instansen. Du kan till exempel skapa e-postrapporter med identifierade avvikelser, hämta en lista med indikatorer i XML-format osv. [Klicka här](../../production/using/monitoring-processes.md#automatic-monitoring) för mer information.

**Verifieringskedja**

Med granskningsspåret kan du visualisera den fullständiga historiken över ändringar som rör alternativ, arbetsflöden och scheman i instansen. [Klicka här](../../production/using/audit-trail.md) för mer information.

**Kontrollpanelen**

På Kontrollpanelen kan du hantera flera inställningar för instansen: hantera URL-behörigheter, kontrollera instansinformation som serverns build-versioner osv. Du kan också övervaka det tillgängliga utrymmet på de SFTP-servrar som är anslutna till din instans. [Klicka här](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=sv) för mer information.

>[!NOTE]
>
>Kontrollpanelen är tillgänglig för alla administratörsanvändare. Stegen för att bevilja administratörsåtkomst till en användare finns på [den här sidan](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=sv#discover-control-panel).
>
>Observera att din instans måste lagras på AWS och uppgraderas med den [senaste GA-versionen](../../rn/using/rn-overview.md). Läs om hur du kontrollerar din version i [det här avsnittet](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version). Följ stegen på [den här sidan](https://experienceleague.adobe.com/docs/control-panel/using/faq.html?lang=sv) för att kontrollera om instanser har AWS som värd.

### Övervaka arbetsflöden {#monitoring-workflows}

<img src="assets/do-not-localize/icon_workflows.svg" width="60px">

**Värmekarta för arbetsflöde**

Workflow HeatMap ger en visuell representation av alla arbetsflöden som körs på din instans. Det gör att du enkelt kan övervaka inläsningen av instansen och planera arbetsflödena utifrån detta. [Klicka här](../../workflow/using/heatmap.md) för mer information.

**Verifieringskedja**

Med granskningsspåret kan du visualisera alla ändringar som har gjorts i arbetsflöden samt deras aktuella tillstånd. [Klicka här](../../production/using/audit-trail.md).

**Felsökning av arbetsflöden**

Du kan utföra specifika åtgärder när du stöter på problem med arbetsflödeskörningen. [Klicka här](../../production/using/workflow-execution.md) för mer information

**Övervakning av arbetsflödesstatus**

Utöver heatmap-kartan kan du skapa ett arbetsflöde där du kan övervaka statusen för en uppsättning arbetsflöden och skicka återkommande meddelanden till arbetsledare. [Klicka här](../../workflow/using/supervising-workflows.md) för mer information.

**Allmänna riktlinjer**

Du kan förbättra prestandan genom att följa riktlinjer och bästa praxis när du använder arbetsflöden. Mer information finns i följande avsnitt:
* [Bästa tillvägagångssätt när du använder arbetsflöden](../../workflow/using/workflow-best-practices.md)
* [Övervaka arbetsflödeskörning](../../workflow/using/monitoring-workflow-execution.md)

### Övervaka leveranser {#monitoring-deliveries}

<img src="assets/do-not-localize/icon_send.svg" width="60px">

**SMTP-rapporter**

SMTP-rapporter visar leveransstatistik och SMTP-fel per domän. [Läs mer](../../production/using/monitoring-processes.md)

**Bästa praxis**

[Bästa tillvägagångssätt för leverans och design](../../delivery/using/delivery-best-practices.md) kan hjälpa dig att förbättra prestanda.

**Felsökning vid leverans**
Specifika åtgärder kan utföras vid problem med leveranser:
* [Leveransproblem](../../production/using/performance-and-throughput-issues.md#deliverability_issues)
* [Bildvisningsproblem](../../production/using/image-display-issues.md)
* [Problem med leveransresultat](../../delivery/using/delivery-performances.md)
* [Tillfälliga filer utfärdas](../../production/using/temporary-files.md) - *endast på lokala värdmodeller*

### Övervaka databasen {#monitoring-database}

<img src="assets/do-not-localize/icon_database.svg" width="60px">

**Arbetsflöde för databasrensning**

Med hjälp av arbetsflödet för att rensa databas kan du ta bort föråldrade data från databasen. Vi rekommenderar att du undviker exponentiell tillväxt i databasen. [Klicka här](../../production/using/database-cleanup-workflow.md) för mer information.

**Felsökning av databasprestanda**

Specifika åtgärder kan utföras när problem med databasprestanda påträffas. [Klicka här](../../production/using/database-performances.md) för mer information.

**Databasunderhåll**

*Endast lokala och hybridvärdmodeller*

Vi rekommenderar att du regelbundet utför databasunderhåll för att undvika överförbrukning av diskutrymme, vilket påverkar databasåtkomsten. [Klicka här](../../production/using/recommendations.md) för mer information.

**Säkerhetskopiering och återställning**

*Endast lokala och hybridvärdmodeller*

Säkerhetskopiering är nödvändigt för att undvika dataförlust i händelse av problem (oavsett om det är fysiskt eller systemrelaterat) på en dator. [Klicka här](../../production/using/backup.md) om du vill ha mer information. Återställningsproceduren beskrivs i [det här avsnittet](../../production/using/restoration.md).

## Tekniska principer för Campaign Classic {#campaign-classic-technical-principles}

Tekniska resurser finns i Campaign Classicens dokumentation. Vi rekommenderar att du lär dig mer om dessa ämnen innan du utför någon teknisk åtgärd på din instans.

**Värdmodeller och funktioner**

* [Värdmodeller för Campaign Classic](../../installation/using/hosting-models.md)
* [Funktioner för värdmodeller](../../installation/using/capability-matrix.md)

**Serverkonfiguration**

*Endast lokala och hybridvärdmodeller*

* [Serverkonfigurationer](../../installation/using/configuring-campaign-server.md)
* [Serverconf.xml, filkonfiguration](../../installation/using/the-server-configuration-file.md)
* [Serverkonfiguration för leverans](../../installation/using/email-deliverability.md)
* [Kommandorader för att skapa en instans och deklarera en databas](../../installation/using/command-lines.md)

**Allmänna principer**

* [Campaign Classicens arkitektur](../../production/using/general-architecture.md)
* [Moduler för Campaign Classic](../../production/using/operating-principle.md)
* [Alternativ för Campaign Classic](../../installation/using/configuring-campaign-options.md)
* [Så här ställer du in modulernas automatiska start](../../production/using/administration.md)
* [Princip för kampanjkonfiguration](../../production/using/configuration-principle.md)
* [Felsökningsrutiner](../../production/using/performance-and-throughput-issues.md)
