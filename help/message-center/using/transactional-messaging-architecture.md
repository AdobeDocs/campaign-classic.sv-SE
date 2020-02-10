---
title: Transactional Messaging-arkitekturen i Adobe Campaign Classic
description: I det här avsnittet beskrivs transaktionsmeddelandearkitekturen för Adobe Campaign Classic.
page-status-flag: never-activated
uuid: a8fe7a37-6df7-49f4-838f-97a72e4a38f3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: introduction
discoiquuid: a910d5fe-cef4-47d8-b3bc-0055ef0d1afd
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 25ae29490f8b4c58dad499669f5bccff43de8b7a

---


# Arkitektur för transaktionsmeddelanden{#transactional-messaging-architecture}

## Om körnings- och kontrollinstanser {#about-execution-and-control-instances}

I Adobe Campaign har transaktionsfunktioner (även kallat Message Center) utformats för att stödja skalbarhet och tillhandahålla en tjänst dygnet runt. Den består av flera instanser:

* en kontrollinstans som meddelandemallarna skapas i,
* en eller flera körningsinstanser som tar emot händelser och levererar meddelanden.

Om du vill använda de här funktionerna loggar Adobe Campaign-användare in på kontrollinstansen för att skapa transaktionsmeddelandemallar, generera meddelandeförhandsvisningen med hjälp av en startlista, visa rapporter och övervaka körningsinstanser.

Körningsinstanser tar emot händelser, länkar dem till transaktionsmeddelandemallar och skickar ett personligt meddelande till varje mottagare.

![](assets/messagecenter_diagram.png)

## Stöd för flera kontrollinstanser {#supporting-several-control-instances}

>[!CAUTION]
>
>Delning av ett körningskluster med flera kontrollinstanser stöds endast i lokala miljöer.

Det går att dela ett körningskluster mellan flera kontrollinstanser. Om du till exempel hanterar flera specialiserade butiker kan du konfigurera en kontrollinstans per varumärke och länka alla till samma körningskluster.

![](assets/messagecenter_diagram_2.png)

>[!NOTE]
>
>Mer information om nödvändig konfiguration finns i [Använda flera kontrollinstanser](../../message-center/using/creating-a-shared-connection.md#using-several-control-instances).

## Installera instanser {#installing-instances}

Du måste vidta flera försiktighetsåtgärder när du installerar Transactional-meddelandepaket. Adobe rekommenderar att du arbetar i en testmiljö innan du börjar producera något. Du måste också ha en kompatibel Adobe Campaign-licens. Kontakta er kontoansvarige på Adobe om du vill ha mer information.

>[!CAUTION]
>
>Kontrollinstansen och körningsinstansen/körningsinstanserna måste vara installerade på olika datorer. De kan inte dela samma Campaign-instans.

Om du behöver använda flera kanaler måste du installera och konfigurera relaterade paket innan du installerar Transactional-meddelandepaket. Se [Lägga till en leveranskanal](#adding-a-delivery-channel).

* Om du vill installera kontrollinstansen på datorn väljer du **[!UICONTROL Transactional message control]** modulen.

   ![](assets/messagecenter_install_controlinstance_001.png)

* Om du vill installera körningsinstansen på datorn väljer du **[!UICONTROL Transactional message execution]** modulen.

   ![](assets/messagecenter_install_executioninstance_001.png)

## Lägga till en leveranskanal {#adding-a-delivery-channel}

Lägga till en leveranskanal (mobilkanal, mobilappskanal osv.) måste utföras innan du installerar Transactional-meddelandepaketet. Om du har startat ett transaktionsmeddelandeprojekt i e-postkanalen och sedan bestämmer dig under projektet för att lägga till en ny kanal måste du följa dessa steg:

1. Installera den kanal du behöver, till exempel **mobilkanalen**, med hjälp av guiden för paketimport ( **[!UICONTROL Tools > Advanced > Import package... > Adobe Campaign Package]** ).
1. Utför en filimport ( **[!UICONTROL Tools > Advanced > Import package... > File]** ) och markera filen ****`[Your language]`**datanmspackemessageCenter.xml** .
1. I **[!UICONTROL XML content of the data to import]** behålls bara den leveransmall som motsvarar den tillagda kanalen. Om du till exempel har lagt till **mobilkanalen** ska du bara behålla **enhetselementet** som motsvarar **[!UICONTROL Mobile transactional message]** (smsTriggerMessage). Om du har lagt till **mobilappskanalen** ska du bara behålla **iOS-transaktionsmeddelandet** (iosTriggerMessage) och **Android-transaktionsmeddelandet** (androidTriggerMessage).

   ![](assets/messagecenter_install_channel.png)

## Transaktionsmeddelanden och inkommande interaktion {#transactional-messages-and-inbound-interaction}

I kombination med modulen för inkommande interaktion kan du med transaktionsmeddelanden infoga ett marknadsföringserbjudande som är dedikerat till mottagaren i meddelandet.

>[!NOTE]
>
>Interaktionsmodulen beskrivs i [Interaktion](../../interaction/using/interaction-and-offer-management.md).

Om du vill använda transaktionsmeddelanden med interaktion måste du använda följande konfigurationer:

* Installera **interaktionspaketet** på kontrollinstansen och konfigurera din erbjudandekatalog.

   >[!CAUTION]
   >
   >Replikera inte erbjudandena på körningsinstanserna.

* Händelsen måste innehålla en identifierare som är länkad till mottagarna för att kunna personalisera erbjudanden. Attributet **@externalId** måste innehålla värdet för den här identifieraren. **Interaktionen** är som standard konfigurerad för att identifiera mottagaren av primärnyckeln:

   ```
   <rtEvent type="order_confirmation" email="john.doe@adobe.com" externalId="1242"> 
   ```

   Du kan konfigurera **Interaktion** så att identifiering sker i valfritt fält, t.ex. på e-postadressen:

   ```
   <rtEvent type="order_confirmation" email="john.doe@adobe.com" externalId="john.doe@yahoo.com"> 
   ```

Skapa leveransmallar på det sätt du vill för en e-postkampanj:

* Lägg till erbjudandet i mallen för transaktionsmeddelanden.
* Kontrollera förhandsgranskningen, skicka ett korrektur och publicera mallen.

Du måste också aktivera enhetsläget för dina erbjudanden. Mer information finns i [det här avsnittet](../../interaction/using/creating-offer-spaces.md).

## Transaktionsmeddelanden och push-meddelanden {#transactional-messaging-and-push-notifications}

I kombination med mobilappskanalmodulen kan du med transaktionsmeddelanden skicka transaktionsmeddelanden via meddelanden på mobila enheter.

>[!NOTE]
>
>Mobilappskanalen beskrivs i [det här avsnittet](../../delivery/using/about-mobile-app-channel.md).

Om du vill använda transaktionsmeddelandemoduler med Mobile App Channel måste du använda följande konfigurationer:

1. Installera paketet **Mobile App Channel** på instanser för kontroll och körning.
1. Replikera Adobe Campaign-tjänsten av typen **mobilprogram** samt de mobilprogram som den innehåller i körningsinstanserna.

Händelsen måste innehålla följande element:

* Mobilenhets-ID (**registrationId** för Android och **deviceToken** för iOS). Detta ID representerar den adress som meddelandet ska skickas till.
* Länken till mobilprogrammet eller integreringsnyckeln (**uuid**) som gör att du kan återställa anslutningsinformation som är specifik för programmet.
* Den kanal som meddelandet ska skickas till (**önskadKanal**): 41 för iOS och 42 för Android
* Alla data som är användbara för personalisering

Här är ett exempel på en händelse som innehåller den här informationen:

```
<SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
   <SOAP-ENV:Body>
     <urn:PushEvent>
         <urn:sessiontoken>mc/</urn:sessiontoken>
         <urn:domEvent>

              <rtEvent wishedChannel="41" type="DELIVERY" registrationToken="2cefnefzef758398493srefzefkzq483974">
                <mobileApp _operation=”none” uuid="com.adobe.NeoMiles"/>
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

## Transactional messaging and LINE {#transactional-messaging-and-line}

I kombination med LINE Channel kan du med transaktionsmeddelanden skicka meddelanden i realtid på LINE-appen som är installerad på konsumentmobilenheter. Detta används för att skicka välkomstmeddelandet när en LINE-användare lägger till varumärkets sida.

Om du vill använda transaktionsmeddelandemodulen med LINE behövs följande element för konfigurationen på din **marknadsföringsinstans** och din **körningsinstans** :

* Installera paketet på båda instanserna **[!UICONTROL LINE Connect]** .
* Installera paketet på din marknadsinstans och **[!UICONTROL Transactional message control]** paketet på körningsinstansen **[!UICONTROL Transactional message execution]** .
* Skapa ett **externt LINE-konto** och en **tjänst** på båda instanserna med samma namn som de ska synkroniseras med. Mer information om hur du skapar ett externt LINE-konto och -tjänst finns på den här [sidan](../../delivery/using/line-channel.md#creating-a-line-account-and-an-external-account-).

Från **[!UICONTROL Explorer]** , i **[!UICONTROL Platform]** > **[!UICONTROL External account]** , måste du sedan konfigurera olika externa konton för båda instanserna:

1. Skapa ett **[!UICONTROL External database]** externt konto i din **körningsinstans** med följande konfiguration:

   ![](assets/line_config_mc.png)

   * **[!UICONTROL Label]** och **[!UICONTROL Internal name]** : namnge ditt externa konto efter behov.
   * **[!UICONTROL Type]** : välj **[!UICONTROL External database]** .
   * **[!UICONTROL Enabled]** måste vara markerad.
   Från **[!UICONTROL Connection]** kategorin:

   * **[!UICONTROL Type]** : välj databasserver, t.ex. PostgresSQL.
   * **[!UICONTROL Server]** : ange URL:en för databasservern.
   * **[!UICONTROL Account]** : ange ditt databaskonto.

      >[!NOTE]
      >
      >Databasanvändaren måste ha läsbehörighet för följande tabeller för FDA-anslutningen: XtkOption, NmsVisitor, NmsVisitorSub, NmsService, NmsBroadLogRtEvent, NmsBroadLogBatchEvent, NmsTrackingLogRtEvent, NmsTrackingLogBatchEvent, NmsRtEvent, NmsBatchEvent, NmsBroadLog Msg, NmsTrackingUrl, NmsDelivery, NmsWebTrackingLogXtkFolder.

   * **[!UICONTROL Password]** : Ange lösenordet för ditt databaskonto.
   * **[!UICONTROL Database]** : ange databasnamnet för körningsinstansen.
   * **[!UICONTROL Target of an HTTP relay to remote database's account]** måste vara markerad.


1. Skapa ett **[!UICONTROL External Database]** konto i din **marknadsföringsinstans** med följande konfiguration.

   ![](assets/line_config_mc_1.png)

   * **[!UICONTROL Label]** och **[!UICONTROL Internal name]** : namnge ditt externa konto efter behov.
   * **[!UICONTROL Type]** : välj **[!UICONTROL External database]** .
   * Rutan Aktiverad måste vara markerad.
   Från **[!UICONTROL Connection]** kategorin:

   * **[!UICONTROL Type]** : välj **[!UICONTROL HTTP relay to remote Database]** .
   * **[!UICONTROL Server]** : Ange kampanjens server-URL för körningsinstansen.
   * **[!UICONTROL Account]** : Ange kontot som används för att komma åt din körningsinstans.
   * **[!UICONTROL Password]** : Ange lösenordet för kontot som används för att komma åt din körningsinstans.
   * **[!UICONTROL Data Source]** : ange följande syntax **[!UICONTROL nms:extAccount:ID of your external database account in the execution instance]** .


1. Skapa ett **[!UICONTROL Execution instance]** externt konto i din **marknadsföringsinstans** med följande konfiguration för att skapa arbetsflödet för datasynkronisering:

   ![](assets/line_config_mc_2.png)

   * **[!UICONTROL Label]** och **[!UICONTROL Internal name]** : namnge ditt externa konto efter behov.
   * **[!UICONTROL Type]** : välj **[!UICONTROL Execution instance]** .
   * Rutan Aktiverad måste vara markerad.
   Från **[!UICONTROL Connection]** kategorin:

   * **[!UICONTROL URL]** : ange körningsinstansens URL.
   * **[!UICONTROL Account]** : ange det konto som används för att komma åt din körningsinstans.
   * **[!UICONTROL Password]** : Ange lösenordet för kontot som används för att komma åt din körningsinstans.
   Från **[!UICONTROL Account connection method]** kategorin:

   * **[!UICONTROL Method]** : välj **[!UICONTROL Federated Data Access (FDA)]** .
   * **[!UICONTROL FDA account]** : välj ditt FDA-konto i listrutan.
   * Klicka på **[!UICONTROL Create the archiving workflow]** knappen.
   * Klicka på **[!UICONTROL Create data synchronization workflow]** knappen för att skapa arbetsflödet för LINE-datasynkronisering.



1. Nu kan du börja skapa transaktionsmeddelanden. Mer information finns på den här [sidan](../../message-center/using/introduction.md).
