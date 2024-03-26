---
product: campaign
title: Kontrollpanel för leverans
description: Läs mer om hur du använder kontrollpanelen för leverans för att övervaka leveranser
badge-v7: label="v7" type="Informative" tooltip="Gäller Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Monitoring
role: User, Data Engineer
exl-id: 44ecc8c6-6584-43eb-96b4-7d8463053123
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '1189'
ht-degree: 3%

---

# Kontrollpanel för leverans {#delivery-dashboard}


The **kontrollpanel för leverans** är nyckeln för att övervaka leveranser och eventuella problem som uppstår när meddelanden skickas.

Du kan hämta information om en leverans och redigera den om det behövs. Observera att tabbinnehållet inte längre kan ändras när leveransen har skickats.

Här är den information du kan övervaka med hjälp av flera flikar som är tillgängliga på kontrollpanelen:

* [Leveranssammanfattning](#delivery-summary)
* [Leveransrapporter](#delivery-reports)
* [Leveransloggar, spegelsidor, undantag](#delivery-logs-and-history)
* [Loggar och historik för leveransspårning](#tracking-logs)
* [Leveransåtergivning](#delivery-rendering)
* [Leveransgranskning](#delivery-audit-)

![](assets/s_ncs_user_del_details.png)

**Relaterade ämnen:**

* [Förstå leveransfel](understanding-delivery-failures.md)
* [Förstå karantänshantering](understanding-quarantine-management.md)
* [God praxis för leverans](delivery-best-practices.md)
* [Hantera leveranser](about-deliverability.md)

## Leveranssammanfattning {#delivery-summary}

The **[!UICONTROL Summary]** -fliken innehåller information om leveransstatus: leveransstatus, kanal som används, information om avsändare, ämne, information om utförande.

## Leveransrapporter {#delivery-reports}

The **[!UICONTROL Reports]** -länk, som du kommer åt från **[!UICONTROL Summary]** kan du titta på en uppsättning rapporter som rör leveransåtgärden: allmän leveransrapport, detaljerad rapport, leveransrapport, distribution av misslyckade meddelanden, öppningsfrekvens, klick och transaktioner osv.

Innehållet på den här fliken kan konfigureras enligt dina krav. Mer information om leveransrapporter finns i [det här avsnittet](../../reporting/using/delivery-reports.md).

![](assets/delivery-report.png)

## Leveransloggar, historik och undantag {#delivery-logs-and-history}

The **[!UICONTROL Delivery]** -fliken innehåller en historik över förekomsterna i den här leveransen. Den innehåller leveransloggarna, dvs. en lista över skickade meddelanden och deras status samt tillhörande meddelanden.

För en leverans kan du till exempel bara visa mottagare med en misslyckad leverans eller en adress i karantän. Klicka på **[!UICONTROL Filters]** knapp och markera **[!UICONTROL By state]**. Välj sedan läget i listrutan. Olika statusvärden visas i [den här sidan](delivery-statuses.md).

>[!NOTE]
>
>Listan som visar leveransloggarna kan anpassas som alla listor i Campaign Classicen. Du kan till exempel lägga till en kolumn för att veta vilken IP-adress som skickade varje e-post i en leverans. Mer information finns i användningsexemplet i [det här avsnittet](#use-case).

![](assets/s_ncs_user_delivery_delivery_tab.png)

The **[!UICONTROL Display the mirror page for this message...]** kan du visa spegelsidan för innehållet i den leverans som valts i listan i ett nytt fönster.

Spegelsidan är bara tillgänglig för leveranser för vilka HTML-innehåll har definierats. Mer information finns i [Generera spegelsidan](sending-messages.md#generating-the-mirror-page).

![](assets/s_ncs_user_wizard_miror_page_link.png)

## Loggar och historik för leveransspårning {#tracking-logs}

The **[!UICONTROL Tracking]** På -fliken visas spårningshistoriken för leveransen. På den här fliken visas spårningsdata för skickade meddelanden, d.v.s. alla URL:er som spåras av Adobe Campaign. Spårningsdata uppdateras varje timme.

>[!NOTE]
>
>Om spårning inte är aktiverat för en leverans visas inte den här fliken.

Spårningskonfigurationen utförs i rätt steg i leveransguiden. Se [Konfigurera spårade länkar](how-to-configure-tracked-links.md).

**[!UICONTROL Tracking]** data tolkas i leveransrapporterna. Se [det här avsnittet](../../reporting/using/delivery-reports.md).

![](assets/s_ncs_user_delivery_tracking_tab.png)

## Inkorgsåtergivning {#delivery-rendering}

The **[!UICONTROL Inbox rendering]** Med -fliken kan du förhandsgranska meddelandet i de olika sammanhang som det kan tas emot i och kontrollera kompatibiliteten i de flesta datorer och program.

På så sätt kan du se till att ditt meddelande visas för mottagarna på ett optimalt sätt på en mängd olika webbklienter, webbmejl och enheter.

Mer information om inkorgsåtergivning finns i [den här sidan](inbox-rendering.md)

![](assets/s_tn_inbox_rendering_tokens.png)

## Leveransgranskning {#delivery-audit-}

The **[!UICONTROL Audit]** -fliken innehåller leveransloggen och alla meddelanden som rör korrekturet.

The **[!UICONTROL Refresh]** kan du uppdatera data. Använd **[!UICONTROL Filters]** för att definiera ett filter på data.

Med särskilda ikoner kan du identifiera fel och varningar. Se [Analyserar leveransen](steps-validating-the-delivery.md#analyzing-the-delivery).

The **[!UICONTROL Proofs]** kan du visa en lista med de korrektur som har skickats.

![](assets/s_ncs_user_delivery_log_tab.png)

Du kan ändra den information som visas i det här fönstret (och i **[!UICONTROL Delivery]** och **[!UICONTROL Tracking]** genom att markera de kolumner som ska visas. Klicka på **[!UICONTROL Configure list]** ikonen i det nedre högra hörnet. Mer information om hur du konfigurerar listvisning finns i [det här avsnittet](../../platform/using/adobe-campaign-workspace.md#configuring-lists).

## Synkronisering av kontrollpanel för leverans {#delivery-dashboard-synchronization}

Från kontrollpanelen för leverans vill du kontrollera de bearbetade meddelandena och leveransloggarna för att vara säker på att leveransen har skickats.

Vissa indikatorer eller status kan vara felaktiga eller inte aktuella. Lösningen kan vara:

* Om leveransstatusen är felaktig kontrollerar du att alla nödvändiga godkännanden har gjorts för leveransen eller att **[!UICONTROL operationMgt]** och **[!UICONTROL deliveryMgt]** arbetsflöden körs utan fel. Detta kan också bero på leveransen med en tillhörighet som inte har konfigurerats på den sändande instansen.

* Om leveransindikatorerna fortfarande är noll och om du använder en mellanleverantörskonfiguration ska du kontrollera **[!UICONTROL Mid-sourcing (delivery counters)]** tekniskt arbetsflöde. Starta det om dess status inte är **[!UICONTROL Started]**. Du kan sedan försöka beräkna om indikatorerna genom att högerklicka på leveransen i Adobe Campaign Explorer och välja **[!UICONTROL Actions]** > **[!UICONTROL Recompute delivery and tracking indicators]**. Mer information om spårningsindikatorer finns i [section](../../reporting/using/delivery-reports.md#tracking-indicators).

* Om leveransräknaren inte matchar leveransadressen kan du försöka beräkna om indikatorerna genom att högerklicka på leveransadressen i Adobe Campaign Explorer och välja **[!UICONTROL Actions]** > **[!UICONTROL Recompute delivery and tracking indicators]** för att omsynkronisera. Mer information om spårningsindikatorer finns i [section](../../reporting/using/delivery-reports.md#tracking-indicators).

* Om leveransräknaren inte är uppdaterad för medelstora installationer bör du kontrollera att **[!UICONTROL Mid-Sourcing (Delivery counters)]** det tekniska arbetsflödet körs. Se denna [sida](../../installation/using/mid-sourcing-deployment.md) för mer information om detta.

Du kan också spåra leveranser med olika rapporter via kontrollpanelen för leverans. Mer information om detta hittar du i det här [avsnittet](../../reporting/using/delivery-reports.md).

## Användningsfall: Lägga till avsändarens IP-adresser i loggarna {#use-case}

I det här avsnittet får du lära dig hur du lägger till information i leveransloggarna om IP-adressen som skickade varje e-postmeddelande i en leverans.

>[!NOTE]
>
>Den här ändringen är annorlunda om du använder en enda instans eller en mellankällinstans. Innan du utför ändringen kontrollerar du att du är ansluten till e-postsändningsinstansen.

### Steg 1: Utöka schemat

Lägg till **publicID** i leveransloggarna måste du utöka schemat först. Du kan fortsätta enligt följande.

1. Skapa ett schematillägg under **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data Schemas]** > **[!UICONTROL New]**.

   Mer information om schematillägg finns i [den här sidan](../../configuration/using/extending-a-schema.md).

1. Välj **[!UICONTROL broadLogRcp]** för att utöka mottagarens leveransloggar (nms) och definiera ett anpassat namnutrymme. I det här fallet blir det&quot;cus&quot;:

   ![](assets/schema-parameters.png)

   >[!NOTE]
   >
   >Om instansen finns i Mid-sourcing måste du arbeta med schemat för bredaLogMid.

1. Lägg till det nya fältet i tillägget. I det här exemplet måste du ersätta:

   ```
   <element img="nms:broadLog.png" label="Recipient delivery logs" labelSingular="Recipient delivery log" name="broadLogRcp"/>
   ```

   av:

   ```
   <element img="nms:broadLog.png" label="Recipient delivery logs" labelSingular="Recipient delivery log" name="broadLogRcp">
   <attribute desc="Outbound IP identifier" label="IP identifier"
   name="publicId" type="long"/>
   </element>
   ```

   ![](assets/edit-schema.png)

### Steg 2: Uppdatera databasstrukturen

När ändringarna är klara måste du uppdatera databasstrukturen så att den anpassas till den logiska beskrivningen.

Gör så här:

1. Klicka på **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Update database structure...]** -menyn.

   ![](assets/update-database-structure.png)

1. I **[!UICONTROL Edit tables]** fönster, **[!UICONTROL NmsBroadLogRcp]** tabellen är markerad (eller **[!UICONTROL broadLogMid]** tabell (om du arbetar i en mellankällmiljö), enligt nedan:

   ![](assets/edit-tables.png)

   >[!IMPORTANT]
   >
   >Se alltid till att det inte finns några andra ändringar förutom **[!UICONTROL NmsBroadLoGRcp]** tabell (eller **[!UICONTROL broadLogMid]** om du arbetar i en miljö där flera leverantörer arbetar). Om så är fallet avmarkerar du andra tabeller.

1. Klicka **[!UICONTROL Next]** för att validera. Följande skärm visas:

   ![](assets/update-script.png)

1. Klicka **[!UICONTROL Next]** sedan **[!UICONTROL Start]** för att börja uppdatera databasstrukturen. Indexuppbyggnaden startar. Det här steget kan vara långt, beroende på antalet rader i **[!UICONTROL NmsBroadLogRcp]** tabell.

   ![](assets/start-database-update.png)

>[!NOTE]
>
>När uppdateringen av databasens fysiska struktur har slutförts måste du koppla från och ansluta igen så att dina ändringar beaktas.

### Steg 3: Validera ändringen

För att bekräfta att allt fungerade som det ska måste du uppdatera skärmen med leveransloggar.

Det gör du genom att öppna leveransloggarna och lägga till kolumnen&quot;IP-identifierare&quot;.

![](assets/list-config.png)

>[!NOTE]
>
>Mer information om hur du konfigurerar listor i Campaign Classicens gränssnitt finns i [den här sidan](../../platform/using/adobe-campaign-workspace.md).

Nedan visas vad du bör se i **[!UICONTROL Delivery]** tabb efter ändringar:

![](assets/logs-with-ip.png)
