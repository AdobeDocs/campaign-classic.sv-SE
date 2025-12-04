---
product: campaign
title: Övervaka era leveranser i Campaign-gränssnittet
description: Lär dig hur du får tillgång till listan över leveranser och använder kontrollpanelen för leverans för att övervaka dina leveranser
feature: Monitoring
role: User, Developer
exl-id: 44ecc8c6-6584-43eb-96b4-7d8463053123
source-git-commit: eac670cd4e7371ca386cee5f1735dc201bf5410a
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# Övervaka era leveranser i Campaign-gränssnittet {#delivery-dashboard}

>[!NOTE]
>
>Omfattande vägledning om hur du får åtkomst till leveranslistan och använder kontrollpanelen för leverans finns i [dokumentationen för Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard). Det här innehållet gäller både Campaign Classic v7- och Campaign v8-användare.
>
>Den här sidan innehåller **Campaign Classic v7-specifika anpassningar** för hybriddistributioner och lokala distributioner.

Övervakning av leveranser är nödvändigt för att säkerställa att era kampanjer är effektiva och når era kunder.

Mer information om hur du får åtkomst till leveranslistan, använder kontrollpanelsflikarna för leverans och övervakar leveranser finns i [Leveranserna för Campaign v8 Monitor i dokumentationen för Campaign-gränssnittet](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}.

## Anpassa leveransloggar {#use-case}

För **hybriddistributioner** i Campaign Classic v7 kan du anpassa leveransloggar genom att utöka scheman. I det här avsnittet visas hur du lägger till avsändarens IP-adresser i leveransloggarna.

>[!NOTE]
>
>Den här anpassningen kräver schemautbyggnadsfunktioner som är tillgängliga i lokala distributioner. Användare av hanterade molntjänster för Campaign v8 bör kontakta Adobe kundtjänst för att få anpassade leveransloggfält.
>
>Den här ändringen är annorlunda om du använder en enda instans eller en mellankällinstans. Innan du utför ändringen kontrollerar du att du är ansluten till e-postsändningsinstansen.

### Steg 1: Utöka schemat

Om du vill lägga till **publicID** i leveransloggarna måste du utöka schemat först. Du kan fortsätta enligt följande.

1. Skapa ett schematillägg, under **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data Schemas]** > **[!UICONTROL New]**.

   Mer information om schematillägg finns på [den här sidan](../../configuration/using/extending-a-schema.md).

1. Välj **[!UICONTROL broadLogRcp]** om du vill utöka mottagarens leveransloggar (nms) och definiera ett anpassat namnområde. I det här fallet blir det&quot;cus&quot;:

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

1. Klicka på menyn **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Update database structure...]**.

   ![](assets/update-database-structure.png)

1. I fönstret **[!UICONTROL Edit tables]** kontrolleras tabellen **[!UICONTROL NmsBroadLogRcp]** (eller tabellen **[!UICONTROL broadLogMid]** om du befinner dig i en MID-källmiljö) enligt nedan:

   ![](assets/edit-tables.png)

   >[!IMPORTANT]
   >
   >Kontrollera alltid att det inte finns några andra ändringar förutom tabellen **[!UICONTROL NmsBroadLoGRcp]** (eller tabellen **[!UICONTROL broadLogMid]** om du befinner dig i en mellankällkodsmiljö). Om så är fallet avmarkerar du andra tabeller.

1. Klicka på **[!UICONTROL Next]** för att validera. Följande skärm visas:

   ![](assets/update-script.png)

1. Klicka på **[!UICONTROL Next]** och sedan på **[!UICONTROL Start]** för att börja uppdatera databasstrukturen. Indexuppbyggnaden startar. Det här steget kan vara långt, beroende på antalet rader i tabellen **[!UICONTROL NmsBroadLogRcp]**.

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
>Mer information om hur du konfigurerar listor i Campaign Classic-gränssnittet finns på [den här sidan](../../platform/using/adobe-campaign-workspace.md).

Nedan visas vad du bör se på fliken **[!UICONTROL Delivery]** efter ändringar:

![](assets/logs-with-ip.png)

## Relaterade ämnen

* [Övervaka leveranser i Campaign-gränssnittet](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"} (Campaign v8-dokumentation)
* [Leveransstatus](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-statuses){target="_blank"} (dokumentation för kampanj v8)
* [Om leveransfel](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (dokumentation för Campaign v8 - utförlig guide för både v7 och v8)
* [Karantänhantering](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"} (Campaign v8-dokumentation - omfattande guide för både v7 och v8)
* [Bounce mail configuration](understanding-delivery-failures.md) (v7 hybrid/lokal)
* [Karantänkonfiguration](understanding-quarantine-management.md) (v7-hybridteknik/lokal)
