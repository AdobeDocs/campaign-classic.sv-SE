---
product: campaign
title: Simuleringar i Campaign
description: Kom igång med Campaign-simuleringar
role: User, Data Engineer
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
feature: Campaigns
exl-id: 709c64a8-34bf-43fa-a820-238295fb26b8
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '1252'
ht-degree: 1%

---

# Simuleringar i Campaign{#campaign-simulations}

## Om simuleringar {#about-simulations}

Med Campaign Optimization kan ni testa effektiviteten i en kampanjplan med hjälp av simuleringar. Detta gör att ni kan mäta den potentiella framgången för en kampanj: genererade intäkter, målvolym baserat på de typologiregler som tillämpas osv.

Med simulering kan du övervaka och jämföra effekterna av leveranser.

>[!NOTE]
>
>Leveranser som förberetts i testläge påverkar inte varandra, t.ex. när en kampanj bedöms i distribuerad marknadsföring, eller så länge leveranserna inte är schemalagda i den preliminära kalendern.\
>Detta innebär att tryck- och kapacitetsregler endast tillämpas på leveranser i **[!UICONTROL Target estimation and message personalization]** läge. Leveranser i **[!UICONTROL Estimation and approval of the provisional target]** och in **[!UICONTROL Target evaluation]** Läget beaktas inte.\
>Leveransläget väljs i **[!UICONTROL Typology]** underflik för leveransegenskaperna.

![](assets/simu_campaign_select_delivery_mode.png)

## Konfigurera en simulering {#setting-up-a-simulation}

### Skapa en simulering {#creating-a-simulation}

Så här skapar du en simulering:

1. Öppna **[!UICONTROL Campaigns]** klickar du på **[!UICONTROL More]** -länken i **[!UICONTROL Create]** -avsnittet och välj **[!UICONTROL Simulation]** alternativ.

   ![](assets/simu_campaign_opti_01.png)

1. Ange mallen och namnet på simuleringen. Klicka **[!UICONTROL Save]** för att skapa simuleringen.

   ![](assets/simu_campaign_opti_02.png)

1. Klicka på **[!UICONTROL Edit]** för att konfigurera den.

   ![](assets/simu_campaign_opti_edit.png)

1. I **[!UICONTROL Scope]** anger du de leveranser du vill ta hänsyn till för den här simuleringen. Klicka på **[!UICONTROL Add]** och ange vilket leveranssätt som ska användas.

   ![](assets/simu_campaign_opti_edit_scope.png)

   Du kan antingen välja varje leverans en i taget eller sortera dem efter kampanj, program eller plan.

   >[!NOTE]
   >
   >Om du väljer leveranser via en plan, ett program eller en kampanj kan Adobe Campaign automatiskt uppdatera listan med leveranser som ska beaktas när en simulering startas. Om du vill göra det går du till **[!UICONTROL Refresh the selection of deliveries each time the simulation is started]** alternativ.
   >  
   >Om du inte gör detta kommer alla leveranser som inte är tillgängliga i planen, programmet eller kampanjen när simuleringen skapas inte att tas med i beräkningen: leveranser som läggs till senare kommer att ignoreras.

   ![](assets/simu_campaign_opti_edit_scope_update.png)

1. Markera de element som ska ingå i simuleringsomfånget. Om det behövs markerar du flera element med hjälp av SKIFT- och CTRL-tangenterna.

   ![](assets/simu_campaign_opti_edit_scope_select.png)

   Klicka **[!UICONTROL Finish]** för att godkänna markeringen.

   Du kan kombinera utvalda leveranser och leveranser som hör till planer, program eller kampanjer manuellt.

   ![](assets/simu_campaign_opti_edit_scope_save.png)

   Om det behövs kan du använda ett dynamiskt villkor via **[!UICONTROL Edit the dynamic condition...]** länk.

   Klicka **[!UICONTROL Save]** för att godkänna konfigurationen.

   >[!NOTE]
   >
   >Endast leveranser vars mål har beräknats beaktas vid beräkning av simuleringar (status: **Mål klart** eller **Leverera färdigt**).

1. I **[!UICONTROL Calculations]** väljer du till exempel en analysdimension som mottagarschemat.

   ![](assets/simu_campaign_opti_dimension.png)

1. Sedan kan du lägga till uttryck.

   ![](assets/simu_campaign_opti_dimension_02.png)

### Körningsinställningar {#execution-settings}

The **[!UICONTROL General]** -fliken i simuleringen kan du ange körningsinställningar:

* The **[!UICONTROL Schedule execution for down-time]** alternativet skjuter upp simuleringsöppningen till en mindre upptagen tidsperiod, baserat på vald prioritetsnivå. Simuleringar använder stora databasresurser, vilket är orsaken till varför icke-brådskande simuleringar ska schemaläggas att köras på natten, till exempel.
* The **[!UICONTROL Priority]** är den nivå som tillämpas på simuleringen för att fördröja dess utlösande åtgärd.
* **[!UICONTROL Save SQL queries in the log]**. Med SQL-loggar kan du diagnostisera en simulering om den avslutas med fel. De kan också hjälpa dig att ta reda på varför en simulering är för långsam. Dessa meddelanden visas efter simuleringen i **[!UICONTROL SQL logs]** underflik i **[!UICONTROL Audit]** -fliken.

## Kör en simulering {#executing-a-simulation}

### Starta en simulering {#starting-a-simulation}

När simuleringsomfånget har definierats kan du köra det.

Det gör du genom att öppna kontrollpanelen för simulering och klicka på **[!UICONTROL Start simulation]**.

![](assets/simu_campaign_opti_start.png)

När körningen är klar öppnar du simuleringen och klickar på **[!UICONTROL Results]** för att visa de mål som beräknats för varje leverans.

![](assets/simu_campaign_opti_results.png)

1. The **[!UICONTROL Deliveries]** på underfliken anges alla leveranser som har beaktats vid simuleringen. Den visar två antal:

   * The **[!UICONTROL Initial count]** är målet så som det beräknats under uppskattningen av leveransen.
   * The **[!UICONTROL Final count]** är antalet mottagare som räknas efter simulering.

     Skillnaden mellan inledande och avslutande antal återspeglar tillämpningen av de olika regler eller filter som konfigurerats före simuleringen.

     Om du vill veta mer om den här beräkningen kan du redigera **[!UICONTROL Exclusions]** underflik.

1. The **[!UICONTROL Exclusions]** på underfliken kan du visa exkluderingen.

   ![](assets/simu_campaign_opti_14.png)

1. The **[!UICONTROL Alerts]** underfliken grupperar alla varningsmeddelanden som genereras under simuleringen. Varningsmeddelanden kan skickas vid kapacitetsöverbelastning (om antalet mottagare som är mål överstiger den angivna kapaciteten, till exempel).
1. The **[!UICONTROL Exploration of the exclusions]** Med subtab kan du skapa en resultatanalystabell. Användaren måste ange variabler i axeln abscissa/ordinates.

   Ett exempel på hur analystabellen skapas finns i slutet av [Utforska resultat](#exploring-results).

### Visa resultat {#viewing-results}

#### Granskning {#audit}

The **[!UICONTROL Audit]** använder du för att övervaka simuleringskörning. The **[!UICONTROL SQL Logs]** subtab är användbar för expertanvändare. Körningsloggar visas i SQL-format. Dessa loggar visas bara om **[!UICONTROL Save SQL queries in the log]** har valts i **[!UICONTROL General]** innan simuleringskörning.

![](assets/simu_campaign_opti_11.png)

#### Utforska resultat {#exploring-results}

The **[!UICONTROL Exploration of the exclusions]** Med subtab kan du analysera data från en simulering.

Beskrivande analys är detaljerad i [det här avsnittet](../../reporting/using/about-adobe-campaign-reporting-tools.md).

## Resultat av en simulering {#results-of-a-simulation}

Indikatorerna i **[!UICONTROL Log]** och **[!UICONTROL Results]** -flikarna ger en första översikt över simuleringsresultaten. Öppna **[!UICONTROL Reports]** -fliken.

### Rapporter {#reports}

Om du vill analysera resultatet av en simulering redigerar du dess rapporter: de visar undantag och orsaker.

Följande rapporter tillhandahålls som standard:

* **[!UICONTROL Detail of simulation exclusions]** : Den här rapporten innehåller en detaljerad förteckning över orsaker till uteslutning för alla berörda leveranser.
* **[!UICONTROL Simulation summary]** : Denna rapport visar vilka populationer som uteslutits från simuleringen under de olika leveranserna.
* **[!UICONTROL Summary of exclusions linked to the simulation]** : den här rapporten innehåller ett diagram över undantag som orsakas av simuleringen tillsammans med den tillämpade typologiregeln och ett diagram som visar exkluderingsförhållandet per regel.

>[!NOTE]
>
>Du kan skapa nya rapporter och lägga till dem i de som erbjuds. Mer information om detta finns i [det här avsnittet](../../reporting/using/about-adobe-campaign-reporting-tools.md).

Klicka på **[!UICONTROL Reports]** länk till målsimuleringen via kontrollpanelen.

![](assets/campaign_opt_reporting_edit_from_board.png)

Du kan även redigera rapporter med **[!UICONTROL Reports]** -länk som är tillgänglig från kontrollpanelen för simuleringar.

### Jämför simuleringar {#comparing-simulations-}

Varje gång en simulering körs ersätter resultatet alla tidigare resultat: du kan inte visa och jämföra resultat från en körning med en annan.

Om du vill jämföra resultaten måste du använda rapporter. I Adobe Campaign kan du spara en rapporthistorik och visa den igen senare. Den här historiken sparas under simuleringens livscykel.

**Exempel:**

1. Skapa en simulering av en leverans som typologi **A** används på.
1. I **[!UICONTROL Reports]** kan du redigera någon av de tillgängliga rapporterna, som **[!UICONTROL Detail of simulation exclusions]** till exempel.
1. Klicka på ikonen längst upp till höger i rapporten för att skapa en ny historik.

   ![](assets/campaign_opt_reporting_create_hist.png)

1. Stäng simuleringen och ändra typologikonfigurationen **A**.
1. Kör simuleringen igen och jämför resultatet med resultatet som visas i rapporten som en historik skapades för.

   ![](assets/campaign_opt_reporting_edit_hist.png)

   Du kan spara så många rapporthistorik som behövs.

### Rapporteringsaxlar {#reporting-axes}

The **[!UICONTROL Calculations]** kan du definiera rapportaxlar på målet. Dessa axlar kommer att användas vid resultatanalys (se [Utforska resultat](#exploring-results)).

>[!NOTE]
>
>Vi rekommenderar att du definierar beräkningsaxlar i simuleringsmallarna i stället för individuellt för varje simulering.\
>Simuleringsmallar sparas i **[!UICONTROL Resources > Templates > Simulation templates]** noden i Adobe Campaign-trädet.

**Exempel:**

I exemplet nedan vill vi skapa ytterligare en rapporteringsaxel baserat på mottagarnas status (&quot;Kund&quot;,&quot;Prospekt&quot; eller ingen).

1. Om du vill definiera en rapportaxel väljer du den tabell som innehåller den information som ska bearbetas i **[!UICONTROL Analysis dimension]** fält. Denna information är obligatorisk.
1. Här väljer vi segmentfältet för mottagartabellen.

   ![](assets/simu_campaign_opti_09.png)

1. Följande alternativ är tillgängliga:

   * **[!UICONTROL Generate target overlap statistics]** Med kan du återställa all överlappande statistik i simuleringsrapporten. Överlappningar är mottagare som används för minst två leveranser inom en simulering.

     >[!IMPORTANT]
     >
     >Om du väljer det här alternativet ökar simuleringskörningstiden avsevärt.

   * **[!UICONTROL Keep the simulation work table]** I kan du behålla simuleringsspår.

     >[!IMPORTANT]
     >
     >Det automatiska sparandet av dessa tabeller kräver en betydande lagringskapacitet: se till att databasen är tillräckligt stor.

När simuleringsresultatet visas visas informationen om det valda uttrycket i **[!UICONTROL Overlaps]** underflik.

Målöverlapp för leverans anger målmottagarna i minst två leveranser av en simulering.

![](assets/simu_campaign_opti_13.png)

>[!NOTE]
>
>Den här underfliken visas bara om **[!UICONTROL Generate target recovery statistics]** har aktiverats.

Informationen om rapporteringsaxlar kan behandlas i exkluderingsanalysrapporter som skapas i **[!UICONTROL Exploring exclusions]** underflik. Mer information finns i [Utforska resultat](#exploring-results).
