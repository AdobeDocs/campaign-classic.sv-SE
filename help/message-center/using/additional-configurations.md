---
product: campaign
title: Ytterligare konfigurationer
description: Lär dig hur du konfigurerar ytterligare konfigurationer för transaktionsmeddelanden i Adobe Campaign Classic
feature: Transactional Messaging, Message Center
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 4d25d740-db57-4d18-8cae-2dd49c4a786e
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '793'
ht-degree: 4%

---

# Ytterligare konfigurationer {#mc-additional-configurations}



## Övervaka gränsvärden {#monitoring-thresholds}

Du kan konfigurera varningströskeln (orange) och aviseringströskeln (rött) för de indikatorer som visas i **meddelandecentrets servicenivå** och **meddelandecentrets behandlingstid** rapporter (se [Åtkomstrapporter för transaktionsmeddelanden](../../message-center/using/about-transactional-messaging-reports.md)).

Gör så här:

1. Öppna distributionsguiden på **körningsinstansen**.

1. Gå till sidan **[!UICONTROL Message Center]**.

1. Använd pilarna för att ändra tröskelvärdena.

   ![](assets/messagecenter_monitor_events_001.png)

>[!NOTE]
>
>Antalet väntande händelser i kö visas i avsnittet [Systemindikatorer](../../production/using/monitoring-processes.md#system-indicators) på sidan för processövervakning i Adobe Campaign. Mer information om distributionsguiden finns i [det här avsnittet](../../installation/using/deploying-an-instance.md#deployment-assistant).

## Rensa händelser {#purging-events}

Du kan använda [distributionsguiden](../../production/using/database-cleanup-workflow.md#deployment-assistant) för att konfigurera hur länge data ska lagras i databasen.

Händelserensning utförs automatiskt av [arbetsflödet för databasrensning](../../production/using/database-cleanup-workflow.md). Det här arbetsflödet tömmer händelser som tagits emot och lagrats på körningsinstanser och händelser som arkiverats på en kontrollinstans.

Använd pilarna för att ändra inställningarna för tömning.

Inställningar för händelserensning på en kontrollinstans:

![](assets/messagecenter_delete_events_001.png)

Inställningar för händelserensning på en körningsinstans:

![](assets/messagecenter_delete_events_002.png)

Mer information om arbetsflödet för databasrensning finns i [det här avsnittet](../../production/using/database-cleanup-workflow.md).


## Tekniska arbetsflöden {#technical-workflows}

Du måste se till att de tekniska arbetsflödena för kontrollinstansen och de olika körningsinstanserna verkligen har skapats och startats innan du distribuerar några transaktionsmeddelandemallar.

De olika tekniska arbetsflödena för transaktionsmeddelanden (Message Center) är uppdelade mellan kontrollinstansen och körningsinstansen/instanserna.

### Styra instansarbetsflöden {#control-instance-workflows}

Om du har en eller flera instanser registrerade för körning i kontrollinstansen måste du skapa ett arkiveringsarbetsflöde för varje **[!UICONTROL Message Center execution instance]** externt konto. Klicka på knappen **[!UICONTROL Create the archiving workflow]** för att skapa och starta arbetsflödet.

![](assets/messagecenter_archiving_002.png)

Dessa arbetsflöden kan sedan nås från mappen **Administration > Produktion > Meddelandecenter**. Arkiveringsarbetsflödena startas automatiskt när de har skapats.

<!--**Minimal architecture**

Once the control and execution modules are installed on the same instance, you must create the archiving workflow using the deployment wizard. Click the **[!UICONTROL Create the archiving workflow]** button to create and start the workflow.

![](assets/messagecenter_archiving_001.png)-->

### Arbetsflöden för körningsinstanser {#execution-instance-workflows}

På körningsinstansen/instanserna kan du komma åt de tekniska arbetsflödena för transaktionsmeddelanden från mappen **Administration > Produktion > Meddelandecenter**. Du behöver bara starta dem. Arbetsflödena i listan är:

* **[!UICONTROL Processing batch events]** (internt namn: **[!UICONTROL batchEventsProcessing]**): Med det här arbetsflödet kan du dela upp grupphändelser i en kö innan de länkas till en meddelandemall.
* **[!UICONTROL Processing real time events]** (internt namn: **[!UICONTROL rtEventsProcessing]**): Med det här arbetsflödet kan du dela upp realtidshändelser i en kö innan de länkas till en meddelandemall.
* **[!UICONTROL Update event status]** (internt namn: **[!UICONTROL updateEventStatus]**): Med det här arbetsflödet kan du tilldela en status till händelsen.

  Följande händelselägen är tillgängliga:

   * **[!UICONTROL Pending]** : händelsen finns i kön. Ingen meddelandemall har ännu tilldelats den.
   * **[!UICONTROL Pending delivery]** : händelsen finns i kön, en meddelandemall har tilldelats den och bearbetas av leveransen.
   * **[!UICONTROL Sent]** : den här statusen kopieras från leveransloggarna. Det betyder att leveransen har skickats.
   * **[!UICONTROL Ignored by the delivery]** : den här statusen kopieras från leveransloggarna. Det betyder att leveransen ignorerats.
   * **[!UICONTROL Delivery failed]** : den här statusen kopieras från leveransloggarna. Det betyder att leveransen misslyckats.
   * **[!UICONTROL Event not taken into account]** : händelsen kunde inte länkas till en meddelandemall. Händelsen kommer inte att bearbetas.

### Arbetsflödesschema för arkivering

Undvik att ändra schemat för **arkiveringsarbetsflödet** som körs på kontrollinstansen. Annars kan vissa spårningsdata som hämtas från körningsinstansen gå förlorade.

Om du ändrar arbetsflödesschemat för arkivering måste du också ändra schemat för **spårningsarbetsflöde** i körningsinstansen så att det matchar arbetsflödesschemat för arkivering i kontrollinstansen.

## Konfigurera multibranding {#configuring-multibranding}

I det här avsnittet beskrivs en lösning för att konfigurera spårning och spegla sidadresser per varumärke för transaktionsmeddelanden i Adobe Campaign.

### Förhandskrav {#prerequisites}

* Alla värdar måste läggas till i konfigurationsfilen för instansen (`config-<instance>.xml`).
* Varje varumärke måste tilldelas en underdomän.
* Du måste ha ett HTTPS-certifikat för alla varumärken om webbspårningen görs på HTTPS-sidor.

Om du vill konfigurera multibranding måste du konfigurera både körningsinstanser och kontrollinstans.

### Körningsinstans {#execution-instance}

Följ stegen nedan på körningsinstansen/körningsinstanserna:

1. Skapa ett externt konto per varumärke.

   >[!NOTE]
   >
   >Lär dig hur du skapar ett externt konto av typen körningsinstans i [det här avsnittet](../../message-center/using/configuring-instances.md#control-instance).

1. Utöka schemat nms:extAccount för att lägga till spårnings-URL:

   ```
   <attribute advanced="true" desc="URL of the tracking servers" label="Tracking server URL"
   length="100" name="trackingURL" type="string"/>
   ```

   >[!NOTE]
   >
   >Lär dig hur du utökar ett befintligt schema i avsnittet [Utöka ett schema](../../configuration/using/extending-a-schema.md).

1. Ändra formuläret nms:extAccount:

   ```
   <container label="Message domain branding" type="frame">
        <static type="help"> These parameters are used to override the DNS alias and addresses used during message delivery. When not populated, the values of the 'NmsServer_MirrorPageUrl' and 'NmsEmail_DefaultErrorAddr' options are used.</static>
        <input xpath="@mirrorURL"/>
        <input xpath="@trackingURL"/>
        <input img="nms:sendemail.png" menuId="deliveryMenuBuilder" type="scriptEdit">
               xpath="errorAddress"/>
      </container>
   ```

1. Ändra alternativen NmsTracking_OpenFormula och NmsTracking_ClickFormula om du vill använda det externa kontot i stället för ett globalt alternativ.

   Om du vill göra det ersätter du:

   ```
   <%@ include option='NmsTracking_ServerUrl' %>
   ```

   med:

   ```
   <%@ value object="provider" xpath="@trackingURL" %>
   ```

   >[!IMPORTANT]
   >
   >Dessa ändringar kan leda till konflikter vid uppgradering. Du kan behöva sammanfoga dessa formler manuellt med deras nya version.

### Kontrollinstans {#control-instance}

I kontrollinstansen måste du länka leveransmallar och externa konton.

Gör så här:

1. Skapa ett externt konto per varumärke med samma interna namn som definierats i [körningsinstansen](#execution-instance) (steg 1).

1. Skapa en [leveransmall](../../delivery/using/about-templates.md) per varumärke.

1. I leveransmallens **[!UICONTROL Properties]** anger du routningen till varumärkesets externa konto.
