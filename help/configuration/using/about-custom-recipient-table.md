---
product: campaign
title: Om anpassad mottagartabell
description: Om anpassad mottagartabell
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Custom Resources
exl-id: d8cea496-b3f3-420a-bf6e-b7cbb321b30d
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '667'
ht-degree: 2%

---

# Använd en anpassad mottagartabell{#about-custom-recipient-table}



I det här avsnittet beskrivs principerna för hur du använder en anpassad (eller extern) mottagartabell.

Som standard har Adobe Campaign en inbyggd mottagartabell som färdiga funktioner och processer är länkade till. Den inbyggda mottagartabellen har ett antal fördefinierade fält och tabeller som enkelt kan utökas med hjälp av en tilläggstabell.

Om den här tilläggsmetoden ger stor flexibilitet för att utöka en tabell kan inte antalet fält eller länkar i den minskas. Om du använder en tabell som inte är standard, eller en &quot;extern mottagartabell&quot;, får du större flexibilitet men det krävs vissa försiktighetsåtgärder när du implementerar den.

Med den här funktionen kan Adobe Campaign bearbeta data från en extern databas: dessa data kommer att användas som en uppsättning profiler för leveranser. Implementeringen av den här processen innefattar flera precisioner som kan vara relevanta beroende på kundens behov. Till exempel:

* Ingen uppdateringsström till och från Adobe Campaign-databasen: data från den här tabellen kan uppdateras direkt via den databasmotor som är värd för den.
* Inga ändringar i processerna som körs på den befintliga databasen.
* Använda en profildatabas med en icke-standardstruktur: möjlighet att leverera till profiler som sparats i olika tabeller med olika strukturer, med en enda instans.
* Inga ändringar eller inget underhåll krävs vid uppdatering av Adobe Campaign-databasen.
* Den inbyggda mottagartabellen är värdelös om du inte behöver de flesta tabellfälten eller om databasmallen inte är centrerad på mottagarna.
* För att vara effektiv krävs en tabell med få fält om du har ett stort antal profiler. Den inbyggda mottagartabellen har för många fält för det här specifika fallet.

I det här avsnittet beskrivs de huvudpunkter som gör att du kan mappa befintliga tabeller i Adobe Campaign och konfigurationen som ska användas för att köra leveranser baserat på valfri tabell. Slutligen beskrivs hur man ger användarna tillgång till gränssnitt som är lika praktiska som de som finns i den inbyggda mottagartabellen. För att förstå det material som presenteras i detta avsnitt krävs god kunskap om principerna för skärm och schemadesign.

## Recommendations och begränsningar {#recommendations-and-limitations}

Användningen av en anpassad mottagartabell har följande begränsningar:

* Adobe Campaign har inte stöd för flera mottagarscheman, vilket kallas målinriktningsscheman, som är länkade till samma sändnings- och/eller spårningsloggscheman. Detta kan i annat fall leda till avvikelser i dataavstämningen efteråt.

   Bilden nedan visar den nödvändiga relationsstrukturen för varje anpassat mottagarschema:
   ![](assets/custom_recipient_limitation.png)

   Vi rekommenderar:

   * Dedikerar **[!UICONTROL nms:BroadLogRcp]** och **[!UICONTROL nms:TrackingLogRcp]** scheman till användningsklara **[!UICONTROL nms:Recipientschema]**. Dessa två loggtabeller ska inte länkas till någon annan anpassad mottagartabell.
   * Definiera dedikerade anpassade sändnings- och spårningsloggscheman för varje nytt anpassat mottagarschema. Detta kan du göra automatiskt när du ställer in målmappningen, se [Målmappning](../../configuration/using/target-mapping.md).

* Du kan inte använda standarden **[!UICONTROL Services and Subscriptions]** som ingår i produkten.

   Detta innebär den övergripande operationen som beskrivs i [det här avsnittet](../../delivery/using/managing-subscriptions.md) är inte tillämpligt.

* Länken med **[!UICONTROL visitor]** tabellen fungerar inte.

   Därför ska du använda **[!UICONTROL Social Marketing]** -modulen måste du konfigurera lagringssteget så att det refererar till rätt tabell.

   På samma sätt måste standardmallen för inledande meddelandeöverföring anpassas när hänvisningsfunktioner används.

* Du kan inte lägga till profiler manuellt i en lista.

   Därför beskrivs det förfarande som beskrivs i [det här avsnittet](../../platform/using/creating-and-managing-lists.md) är inte tillämpligt utan ytterligare konfiguration.

   >[!NOTE]
   >
   >Du kan fortfarande skapa mottagarlistor med hjälp av arbetsflöden. Mer information finns i [Skapa en profillista med ett arbetsflöde](../../configuration/using/creating-a-profile-list-with-a-workflow.md).

Vi rekommenderar också att du kontrollerar standardvärdena som används i de olika färdiga konfigurationerna: Beroende på vilka funktioner som används måste flera anpassningar göras.

Exempel:

* Vissa standardrapporter, särskilt de som tillhandahålls av **Interaktion** och **Mobila program** måste utvecklas. Se [Hantera rapporter](../../configuration/using/managing-reports.md) -avsnitt.
* Standardkonfigurationerna för vissa arbetsflödesaktiviteter refererar till standardmottagartabellen (**[!UICONTROL nms:recipient]**): dessa konfigurationer måste ändras när de används för en extern mottagartabell. Se [Hantera arbetsflöden](../../configuration/using/managing-workflows.md) -avsnitt.
* Standarden **[!UICONTROL Unsubscription link]** Personaliseringsblocket måste anpassas.
* Målmappningen för standardleveransmallarna måste ändras.
* V4-formulär är inte kompatibla med en extern mottagartabell: du måste använda webbprogram.
