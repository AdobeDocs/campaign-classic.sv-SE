---
solution: Campaign Classic
product: campaign
title: Konfigurera flermärkesförsäljning
description: Konfigurera flermärkesförsäljning
audience: message-center
content-type: reference
topic-tags: instance-configuration
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 2%

---


# Konfigurera flermärkesförsäljning{#configuring-multibranding}

I det här avsnittet beskrivs en lösning för att konfigurera spårning och spegla sidadresser per varumärke för transaktionsmeddelanden i Adobe Campaign.

## Förutsättningar {#prerequisites}

* Alla värdar måste läggas till i instansens konfigurationsfil (`config-<instance>.xml`).
* Varje varumärke måste tilldelas en underdomän.
* Du måste ha ett HTTPS-certifikat för alla varumärken om webbspårningen görs på HTTPS-sidor.

## Vanlig process {#typical-process}

Om du vill konfigurera multibranding måste du konfigurera både körningsinstanser och kontrollinstans. Följ stegen nedan i körningsinstanserna:

1. Skapa ett externt konto per varumärke.

   >[!NOTE]
   >
   >Ett externt konto för en körningsinstanstyp visas i avsnittet [Kontrollinstans](../../message-center/using/creating-a-shared-connection.md#control-instance).

1. Utöka schemat nms:extAccount för att lägga till spårnings-URL:

   ```
   <attribute advanced="true" desc="URL of the tracking servers" label="Tracking server URL"
   length="100" name="trackingURL" type="string"/>
   ```

   >[!NOTE]
   >
   >Utökning av ett befintligt schema visas i avsnittet [Utöka ett schema](../../configuration/using/extending-a-schema.md).

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

I kontrollinstansen måste du länka leveransmallar och externa konton. För att göra detta måste du:

1. Skapa ett externt konto per varumärke med samma interna namn som definieras i steg 1.
1. Skapa en standardleveransmall per varumärke.
1. I leveransmallens **[!UICONTROL Properties]** anger du routningen till varumärkesets externa konto.

