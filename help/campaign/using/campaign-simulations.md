---
title: Kampanjsimuleringar
seo-title: Kampanjsimuleringar
description: Kampanjsimuleringar
seo-description: null
page-status-flag: never-activated
uuid: d5a090ef-57e5-46b2-b9ad-6d4d964c8e20
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: campaign-optimization
discoiquuid: e8e7a720-c93d-491d-8768-270e47e9c898
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Kampanjsimuleringar{#campaign-simulations}

## Om simuleringar {#about-simulations}

Med Campaign Optimization kan ni testa effektiviteten i en kampanjplan med hjälp av simuleringar. Detta gör att ni kan mäta en kampanjs potentiella framgång: genererade intäkter, målvolym baserat på tillämpade typologiregler osv.

Med simulering kan du övervaka och jämföra effekterna av leveranser.

>[!NOTE]
>
>Leveranser som förberetts i testläge påverkar inte varandra, t.ex. när en kampanj bedöms i distribuerad marknadsföring, eller så länge leveranserna inte är schemalagda i den preliminära kalendern.\
>Detta innebär att tryck- och kapacitetsregler endast tillämpas på leveranser i **[!UICONTROL Target estimation and message personalization]** läge. Leveranser i **[!UICONTROL Estimation and approval of the provisional target]** och i **[!UICONTROL Target evaluation]** läge beaktas inte.\
>Leveransläget väljs på **[!UICONTROL Typology]** underfliken till leveransegenskaperna.

![](assets/simu_campaign_select_delivery_mode.png)

## Konfigurera en simulering {#setting-up-a-simulation}

### Skapa en simulering {#creating-a-simulation}

Så här skapar du en simulering:

1. Gå till **[!UICONTROL Campaigns]** universum, klicka på **[!UICONTROL More]** länken i **[!UICONTROL Create]** avsnittet och välj **[!UICONTROL Simulation]** alternativet.

   ![](assets/simu_campaign_opti_01.png)

1. Ange mallen och namnet på simuleringen. Klicka **[!UICONTROL Save]** för att skapa simuleringen.

   ![](assets/simu_campaign_opti_02.png)

1. Klicka på **[!UICONTROL Edit]** fliken för att konfigurera den.

   ![](assets/simu_campaign_opti_edit.png)

1. Ange de leveranser du vill använda för den här simuleringen på fliken **[!UICONTROL Scope]** . Det gör du genom att klicka på **[!UICONTROL Add]** knappen och ange leveransvalsläget.

   ![](assets/simu_campaign_opti_edit_scope.png)

   Du kan antingen välja varje leverans en i taget eller sortera dem efter kampanj, program eller plan.

   >[!NOTE]
   >
   >Om ni väljer leveranser via en plan, ett program eller en kampanj kan Adobe Campaign automatiskt uppdatera listan över leveranser för att ta hänsyn till varje gång en simulering startas. Markera **[!UICONTROL Refresh the selection of deliveries each time the simulation is started]** alternativet om du vill göra det.
   >  
   >Om du inte gör detta kommer alla leveranser som inte är tillgängliga i planen, programmet eller kampanjen när simuleringen skapas inte att beaktas: leveranser som läggs till senare ignoreras.

   ![](assets/simu_campaign_opti_edit_scope_update.png)

1. Välj de element som ska ingå i simuleringsomfånget. Om det behövs markerar du flera element med hjälp av SKIFT- och CTRL-tangenterna.

   ![](assets/simu_campaign_opti_edit_scope_select.png)

   Klicka **[!UICONTROL Finish]** för att godkänna markeringen.

   Du kan kombinera utvalda leveranser och leveranser som hör till planer, program eller kampanjer manuellt.

   ![](assets/simu_campaign_opti_edit_scope_save.png)

   Om det behövs kan du använda ett dynamiskt villkor via **[!UICONTROL Edit the dynamic condition...]** länken

   Klicka **[!UICONTROL Save]** för att godkänna konfigurationen.

   >[!CAUTION]
   >
   >Endast leveranser vars mål har beräknats beaktas vid beräkning av simuleringar (status: **Target ready** or **Ready to deliver**).

1. Välj en analysdimension, t.ex. mottagarschema, på fliken **[!UICONTROL Calculations]** .

   ![](assets/simu_campaign_opti_dimension.png)

1. Sedan kan du lägga till uttryck.

   ![](assets/simu_campaign_opti_dimension_02.png)

### Körningsinställningar {#execution-settings}

På fliken **[!UICONTROL General]** i simuleringen kan du ange körningsinställningar:

* Med det här alternativet **[!UICONTROL Schedule execution for down-time]** fördröjs simuleringsöppningen till en mindre upptagen tidsperiod, baserat på vald prioritetsnivå. Simuleringar använder stora databasresurser, vilket är orsaken till varför icke-brådskande simuleringar ska schemaläggas att köras på natten, till exempel.
* Värdet **[!UICONTROL Priority]** är den nivå som används för simuleringen för att fördröja dess utlösande åtgärd.
* **[!UICONTROL Save SQL queries in the log]**. Med SQL-loggar kan du diagnostisera en simulering om den avslutas med fel. De kan också hjälpa dig att ta reda på varför en simulering är för långsam. Dessa meddelanden visas efter simuleringen på **[!UICONTROL SQL logs]** fliken **[!UICONTROL Audit]** .

## Köra en simulering {#executing-a-simulation}

### Starta en simulering {#starting-a-simulation}

När simuleringsomfånget har definierats kan du köra det.

Det gör du genom att öppna kontrollpanelen för simulering och klicka på **[!UICONTROL Start simulation]**.

![](assets/simu_campaign_opti_start.png)

När körningen är klar öppnar du simuleringen och klickar på **[!UICONTROL Results]** fliken för att visa de mål som beräknats för varje leverans.

![](assets/simu_campaign_opti_results.png)

1. På **[!UICONTROL Deliveries]** underfliken visas alla leveranser som har beaktats vid simuleringen. Den visar två antal:

   * Målvärdet **[!UICONTROL Initial count]** är det som beräknats vid uppskattningen av leveransen.
   * Värdet **[!UICONTROL Final count]** är antalet mottagare som räknas efter simulering.

      Skillnaden mellan inledande och avslutande antal återspeglar tillämpningen av de olika regler eller filter som konfigurerats före simuleringen.

      Om du vill veta mer om den här beräkningen redigerar du **[!UICONTROL Exclusions]** underfliken.

1. På **[!UICONTROL Exclusions]** underfliken kan du visa en exkluderingsbrytning.

   ![](assets/simu_campaign_opti_14.png)

1. På **[!UICONTROL Alerts]** underfliken grupperas alla varningsmeddelanden som genereras under simuleringen. Varningsmeddelanden kan skickas vid kapacitetsöverbelastning (om antalet mottagare som är mål överstiger den angivna kapaciteten, till exempel).
1. På **[!UICONTROL Exploration of the exclusions]** underfliken kan du skapa en resultatanalystabell. Användaren måste ange variabler i axeln abscissa/ordinates.

   Ett exempel på hur du skapar analystabeller finns i slutet av [Utforska resultat](#exploring-results).

### Visa resultat {#viewing-results}

#### Granskning {#audit}

På fliken **[!UICONTROL Audit]** kan du övervaka simuleringskörning. Underfliken **[!UICONTROL SQL Logs]** är användbar för expertanvändare. Körningsloggar visas i SQL-format. Dessa loggar visas bara om **[!UICONTROL Save SQL queries in the log]** alternativet har valts på **[!UICONTROL General]** fliken före simuleringskörning.

![](assets/simu_campaign_opti_11.png)

#### Utforska resultat {#exploring-results}

Med **[!UICONTROL Exploration of the exclusions]** underfliken kan du analysera data som är ett resultat av en simulering.

Beskrivande analys finns i [detta avsnitt](../../reporting/using/about-adobe-campaign-reporting-tools.md).

## Resultat av en simulering {#results-of-a-simulation}

Indikatorerna på flikarna **[!UICONTROL Log]** och **[!UICONTROL Results]** ger en första översikt över simuleringsresultaten. Öppna fliken om du vill få en mer detaljerad resultatvy **[!UICONTROL Reports]** .

### Rapporter {#reports}

Om du vill analysera resultatet av en simulering redigerar du dess rapporter: de visar undantag och orsaker.

Följande rapporter tillhandahålls som standard:

* **[!UICONTROL Detail of simulation exclusions]** : Denna rapport innehåller en detaljerad förteckning över orsaker till uteslutning för alla berörda leveranser.
* **[!UICONTROL Simulation summary]** : Denna rapport visar vilka populationer som har uteslutits från simuleringen under de olika leveranserna.
* **[!UICONTROL Summary of exclusions linked to the simulation]** : I den här rapporten visas ett diagram över uteslutningar som orsakats av simuleringen tillsammans med den tillämpade typologiregeln och ett diagram över uteslutningsförhållandet per regel.

>[!NOTE]
>
>Du kan skapa nya rapporter och lägga till dem i de som erbjuds. Mer information finns i [det här avsnittet](../../reporting/using/about-adobe-campaign-reporting-tools.md).

Klicka på länken för målsimuleringen via kontrollpanelen för att få åtkomst till rapporter. **[!UICONTROL Reports]**

![](assets/campaign_opt_reporting_edit_from_board.png)

Du kan också redigera rapporter med hjälp av den **[!UICONTROL Reports]** länk som du kommer åt från simuleringspanelen.

### Jämföra simuleringar {#comparing-simulations-}

Varje gång en simulering körs ersätter resultatet eventuella tidigare resultat: du kan inte visa och jämföra resultat från en körning till en annan.

Om du vill jämföra resultaten måste du använda rapporter. Med Adobe Campaign kan du spara en rapporthistorik och visa den igen senare. Den här historiken sparas under simuleringens livscykel.

**Exempel:**

1. Skapa en simulering av en leverans som typologi **A** tillämpas på.
1. Redigera en av de tillgängliga rapporterna på **[!UICONTROL Reports]** fliken, t. **[!UICONTROL Detail of simulation exclusions]** ex.
1. Klicka på ikonen längst upp till höger i rapporten för att skapa en ny historik.

   ![](assets/campaign_opt_reporting_create_hist.png)

1. Stäng simuleringen och ändra konfigurationen för typologi **A**.
1. Kör simuleringen igen och jämför resultatet med resultatet som visas i rapporten som en historik skapades för.

   ![](assets/campaign_opt_reporting_edit_hist.png)

   Du kan spara så många rapporthistorik som behövs.

### Rapporteringsaxlar {#reporting-axes}

På fliken **[!UICONTROL Calculations]** kan du definiera rapporteringsaxlar för målet. Dessa axlar används vid resultatanalys (se [Utforska resultat](#exploring-results)).

>[!NOTE]
>
>Vi rekommenderar att du definierar beräkningsaxlar i simuleringsmallarna i stället för individuellt för varje simulering.\
>Simuleringsmallar sparas i noden **[!UICONTROL Resources > Templates > Simulation templates]** i Adobe Campaign-trädet.

**Exempel:**

I exemplet nedan vill vi skapa ytterligare en rapporteringsaxel baserat på mottagarnas status (&quot;Kund&quot;,&quot;Prospekt&quot; eller ingen).

1. Om du vill definiera en rapportaxel markerar du tabellen som innehåller den information som ska bearbetas i **[!UICONTROL Analysis dimension]** fältet. Denna information är obligatorisk.
1. Här väljer vi segmentfältet för mottagartabellen.

   ![](assets/simu_campaign_opti_09.png)

1. Följande alternativ är tillgängliga:

   * **[!UICONTROL Generate target overlap statistics]** Med kan du återställa all överlappande statistik i simuleringsrapporten. Överlappningar är mottagare som används för minst två leveranser inom en simulering.

      >[!CAUTION]
      >
      >Om du väljer det här alternativet ökar simuleringskörningstiden avsevärt.

   * **[!UICONTROL Keep the simulation work table]** I kan du behålla simuleringsspår.

      >[!CAUTION]
      >
      >Det automatiska sparandet av dessa tabeller kräver en betydande lagringskapacitet: kontrollera att databasen är tillräckligt stor.

När simuleringsresultatet visas, visas informationen om det valda uttrycket på **[!UICONTROL Overlaps]** underfliken.

Målöverlapp för leverans anger målmottagarna i minst två leveranser av en simulering.

![](assets/simu_campaign_opti_13.png)

>[!NOTE]
>
>Den här underfliken visas bara om **[!UICONTROL Generate target recovery statistics]** alternativet har aktiverats.

Informationen om rapportaxlar kan behandlas i exkluderingsanalysrapporter som skapas på **[!UICONTROL Exploring exclusions]** underfliken. Mer information finns i [Utforska resultat](#exploring-results).
