---
product: campaign
title: Transaktionsmeddelandens arkitektur
description: Detta avsnitt beskriver Adobe Campaign Classic transaktionsmeddelandearkitektur och de tillgängliga kanalerna för att leverera transaktionsmeddelanden
feature: Transactional Messaging, Message Center, Architecture
exl-id: 0a059397-b037-405b-b9c1-94a4a072674d
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1103'
ht-degree: 1%

---

# Transaktionsmeddelandens arkitektur {#transactional-messaging-architecture}



Transaktionsmeddelanden bygger på en specifik arkitektur som består av flera instanser:

* En **kontrollinstans** som meddelandemallarna skapas på.

* En eller flera **körningsinstanser** som tar emot händelser och levererar meddelanden.

![](assets/messagecenter_diagram.png)

| Kontrollinstans | Körningsinstans |
|--- |--- |
| Adobe Campaign-användare loggar in på kontrollinstansen för att: <ul><li>Skapa mallar för transaktionsmeddelanden</li><li>Generera förhandsgranskning av meddelande med hjälp av en startvärdeslista</li><li>Visa rapporter</li><li>Övervaka körningsinstanser</li></ul> | Körningsinstanser finns här för att: <ul><li>Ta emot händelser</li><li>Länka dem till mallar för transaktionsmeddelanden</li><li>Skicka ett personligt meddelande till varje mottagare</li></ul> |

## Installera instanser {#installing-instances}

Du måste vidta flera försiktighetsåtgärder när du installerar Transactional-meddelandepaket. Adobe rekommenderar att du arbetar i en testmiljö innan du börjar producera något. Du måste också ha en kompatibel Adobe Campaign-licens. Kontakta er kontoansvarige på Adobe för mer information.

>[!IMPORTANT]
>
>Kontrollinstansen och körningsinstansen/körningsinstanserna måste vara installerade på olika datorer. De kan inte dela samma Campaign-instans.

Om du behöver använda flera kanaler måste du installera och konfigurera relaterade paket innan du installerar Transactional-meddelandepaket. Mer information finns i [Lägg till en leveranskanal](#adding-a-delivery-channel).

## Kontrollinstans {#control-instance}

Om du vill installera kontrollinstansen på datorn väljer du paketet **[!UICONTROL Transactional message control]** via menyn **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** . Mer information finns i [Installera Campaign Classicens standardpaket](../../installation/using/installing-campaign-standard-packages.md).

![](assets/messagecenter_install_controlinstance_001.png)

De detaljerade stegen för att konfigurera kontrollinstansen visas i [det här avsnittet](../../message-center/using/configuring-instances.md#control-instance).

### Stöd för flera kontrollinstanser {#supporting-several-control-instances}

>[!IMPORTANT]
>
>Delning av ett körningskluster med flera kontrollinstanser stöds endast i lokala miljöer.

Det går att dela ett körningskluster mellan flera kontrollinstanser. Om du till exempel hanterar flera specialiserade butiker kan du konfigurera en kontrollinstans per varumärke och länka alla till samma körningskluster.

![](assets/messagecenter_diagram_2.png)

>[!NOTE]
>
>Mer information om nödvändig konfiguration finns i [Använd flera kontrollinstanser](../../message-center/using/configuring-instances.md#using-several-control-instances).

## Körningsinstans {#execution-instance}

Om du vill installera en körningsinstans på datorn väljer du paketet **[!UICONTROL Transactional message execution]** via menyn **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** . Mer information finns i [Installera Campaign Classicens standardpaket](../../installation/using/installing-campaign-standard-packages.md).

![](assets/messagecenter_install_executioninstance_001.png)

De detaljerade stegen för att konfigurera en körningsinstans visas i [det här avsnittet](../../message-center/using/configuring-instances.md#execution-instance).

## Tillgängliga leveranskanaler

E-postkanalen är som standard tillgänglig. Om du vill leverera dina transaktionsmeddelanden i flera kanaler kan du lägga till andra kanaler (mobilkanal, mobilappskanal osv.).

>[!IMPORTANT]
>
>Lägga till en leveranskanal (mobilkanal, mobilappskanal osv.) måste utföras innan du installerar Transactional-meddelandepaketet.

### Lägg till en leveranskanal {#adding-a-delivery-channel}

Adobe rekommenderar att du **alltid lägger till leveranskanalpaketet innan du installerar Transactional message-paketet**.

Om du har påbörjat ett transaktionsmeddelandeprojekt i e-postkanalen och sedan bestämmer dig under projektet för att lägga till en ny kanal, kan du följa stegen nedan.

>[!NOTE]
>
>Den här proceduren gäller endast kunder som använder en Windows NLServer som är installerad på samma dator som de arbetar på.

1. Installera den kanal du behöver, till exempel **Mobile-kanalen**, med hjälp av guiden för paketimport (**[!UICONTROL Tools > Advanced > Import package... > Adobe Campaign Package]**).
1. Utför en filimport (**[!UICONTROL Tools > Advanced > Import package... > File]**) och markera filen **dataItems **`[Your language]`**packagemessageCenter.xml**.
1. I **[!UICONTROL XML content of the data to import]** sparar du bara den leveransmall som motsvarar den tillagda kanalen. Om du till exempel har lagt till **mobilkanalen** ska du bara behålla elementet **entities** som motsvarar **[!UICONTROL Mobile transactional message]** (smsTriggerMessage). Om du har lagt till **Mobile App Channel** ska du bara behålla **iOS-transaktionsmeddelandet** (iosTriggerMessage) och **Android-transaktionsmeddelandet** (androidTriggerMessage).

   ![](assets/messagecenter_install_channel.png)

<!--## Transactional messages and inbound Interaction {#transactional-messages-and-inbound-interaction}

When combined with the Inbound Interaction module, transactional messaging enables you to insert a marketing offer dedicated to the recipient into the message.

>[!NOTE]
>
>The Interaction module is detailed in [Interaction](../../interaction/using/interaction-and-offer-management.md).

To use transactional messaging with Interaction, you need to apply the following configurations:

* Install the **Interaction** package onto the control instance and configure your offer catalog.

  >[!IMPORTANT]
  >
  >Do not replicate the offers onto the execution instances.

* The event must include an identifier linked to the recipients, for personalizing offers. The **@externalId** attribute must contain the value of this identifier. **Interaction** is configured by default to identify the recipient of the primary key:

  ```
  <rtEvent type="order_confirmation" email="john.doe@adobe.com" externalId="1242"> 
  ```

  You can configure **Interaction** so that identification takes place in the field of your choice, for example on the email address:

  ```
  <rtEvent type="order_confirmation" email="john.doe@adobe.com" externalId="john.doe@yahoo.com"> 
  ```

Create your delivery templates the way you would for an email campaign:

* Add the offer to your transactional message template.
* Check the preview, send a proof and publish the template.

You also have to enable the unitary mode on your offer spaces. For more on this, refer to [this section](../../interaction/using/creating-offer-spaces.md).-->

### Push-transaktionsmeddelanden {#transactional-messaging-and-push-notifications}

I kombination med mobilappskanalmodulen kan du med transaktionsmeddelanden skicka transaktionsmeddelanden via meddelanden på mobila enheter.

>[!NOTE]
>
>Mobilappskanalen beskrivs i [det här avsnittet](../../delivery/using/about-mobile-app-channel.md).

Om du vill använda transaktionsmeddelandemoduler med Mobile App Channel måste du använda följande konfigurationer:

1. Installera paketet **Mobile App Channel** på instans av kontroll och körning.
1. Replikera Adobe Campaign-tjänsten av typen **Mobilprogram** samt de mobilprogram som den innehåller i körningsinstanserna.

Händelsen måste innehålla följande element:

* Mobilenhets-ID (**registrationId** för Android och **deviceToken** för iOS). Detta ID representerar den adress som meddelandet ska skickas till.
* Länken till mobilprogrammet eller integreringsnyckeln (**uid**) som gör att du kan återställa anslutningsinformation som är specifik för programmet.
* Kanalen som meddelandet skickas till (**önskadKanal**): 41 för iOS och 42 för Android
* Alla data som är användbara för personalisering

Här är ett exempel på en händelse som innehåller den här informationen:

```
<SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
   <SOAP-ENV:Body>
     <urn:PushEvent>
         <urn:sessiontoken>mc/</urn:sessiontoken>
         <urn:domEvent>

              <rtEvent wishedChannel="41" type="DELIVERY" registrationToken="2cefnefzef758398493srefzefkzq483974">
                <mobileApp _operation="none" uuid="com.adobe.NeoMiles"/>
                <ctx>
                    <deliveryTime>1:30 PM</deliveryTime>
                    <url>http://www.adobe.com</url>
                </ctx>
              </rtEvent>

         </urn:domEvent>
     </urn:PushEvent>           
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

>[!NOTE]
>
>Meddelandemallar skapas inte på samma sätt.

### Transactional messaging and LINE {#transactional-messaging-and-line}

I kombination med LINE Channel kan du med transaktionsmeddelanden skicka meddelanden i realtid på LINE-appen som är installerad på konsumentmobilenheter. Detta används för att skicka välkomstmeddelandet när en LINE-användare lägger till varumärkets sida.

Om du vill använda transaktionsmeddelandemodulen med LINE behövs följande element för konfigurationen på din **marketing** -instans och din **execution** -instans:

* Installera paketet **[!UICONTROL LINE Connect]** på båda instanserna.
* Installera paketet **[!UICONTROL Transactional message control]** på din marknadsföringsinstans och paketet **[!UICONTROL Transactional message execution]** på körningsinstansen.
* Skapa ett **externt LINE-konto** och **tjänst** på båda instanserna med samma namn för att de ska synkroniseras. Mer information om hur du skapar ett externt LINE-konto och -tjänst finns i [det här avsnittet](../../delivery/using/line-channel.md#setting-up-line-channel).

Från **[!UICONTROL Explorer]** i **[!UICONTROL Platform]** > **[!UICONTROL External account]** måste du sedan konfigurera olika externa konton för båda instanserna:

1. Skapa ett **[!UICONTROL External database]** externt konto i din **körningsinstans** med följande konfiguration:

   ![](assets/line_config_mc.png)

   * **[!UICONTROL Label]** och **[!UICONTROL Internal name]** : namnge det externa kontot efter behov.
   * **[!UICONTROL Type]** : välj **[!UICONTROL External database]** .
   * **[!UICONTROL Enabled]**-rutan måste vara markerad.

   Från kategorin **[!UICONTROL Connection]**:

   * **[!UICONTROL Type]** : välj databasserver, t.ex. PostgresSQL.
   * **[!UICONTROL Server]** : Ange URL-adressen till databasservern.
   * **[!UICONTROL Account]** : Ange ditt databaskonto.

     >[!NOTE]
     >
     >Databasanvändaren måste ha läsbehörighet för följande tabeller för FDA-anslutningen: XtkOption, NmsVisitor, NmsVisitorSub, NmsService, NmsBroadLogRtEvent, NmsBroadLogBatchEvent, NmsTrackingLogRtEvent, NmsTrackingLogBatchEvent, NmsRt Event, NmsBatchEvent, NmsBroadLogMsg, NmsTrackingUrl, NmsDelivery, NmsWebTrackingLogXtkFolder.

   * **[!UICONTROL Password]** : Ange lösenordet för ditt databaskonto.
   * **[!UICONTROL Database]** : Ange databasnamnet för körningsinstansen.
   * **[!UICONTROL Target of an HTTP relay to remote database's account]**-rutan måste vara markerad.

1. Skapa ett **[!UICONTROL External Database]**-konto i din **marketing**-instans med följande konfiguration.

   ![](assets/line_config_mc_1.png)

   * **[!UICONTROL Label]** och **[!UICONTROL Internal name]** : namnge det externa kontot efter behov.
   * **[!UICONTROL Type]** : välj **[!UICONTROL External database]** .
   * Rutan Aktiverad måste vara markerad.

   Från kategorin **[!UICONTROL Connection]**:

   * **[!UICONTROL Type]** : välj **[!UICONTROL HTTP relay to remote Database]** .
   * **[!UICONTROL Server]** : Ange kampanjens server-URL för körningsinstansen.
   * **[!UICONTROL Account]** : Ange kontot som används för att komma åt din körningsinstans.
   * **[!UICONTROL Password]** : Ange lösenordet för kontot som används för att komma åt din körningsinstans.
   * **[!UICONTROL Data Source]** : ange följande syntax **`nms:extAccount:ID`** för ditt externa databaskonto i körningsinstansen.

1. Skapa ett **[!UICONTROL Execution instance]** externt konto i din **marketing**-instans med följande konfiguration för att skapa arbetsflödet för datasynkronisering:

   ![](assets/line_config_mc_2.png)

   * **[!UICONTROL Label]** och **[!UICONTROL Internal name]** : namnge det externa kontot efter behov.
   * **[!UICONTROL Type]** : välj **[!UICONTROL Execution instance]** .
   * Rutan Aktiverad måste vara markerad.

   Från kategorin **[!UICONTROL Connection]**:

   * **[!UICONTROL URL]** : Ange körningsinstansens URL.
   * **[!UICONTROL Account]** : Ange det konto som används för att komma åt din körningsinstans.
   * **[!UICONTROL Password]** : Ange lösenordet för kontot som används för att komma åt din körningsinstans.

   Från kategorin **[!UICONTROL Account connection method]**:

   * **[!UICONTROL Method]** : välj **[!UICONTROL Federated Data Access (FDA)]** .
   * **[!UICONTROL FDA account]** : välj ditt FDA-konto i listrutan.
   * Klicka på knappen **[!UICONTROL Create the archiving workflow]**.
   * Klicka på knappen **[!UICONTROL Create data synchronization workflow]** för att skapa arbetsflödet för synkronisering av LINE-data.

1. Du kan nu börja [skapa transaktionsmeddelanden](../../message-center/using/creating-the-message-template.md).
