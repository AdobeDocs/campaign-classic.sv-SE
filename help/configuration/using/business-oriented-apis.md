---
title: Verksamhetsorienterade API:er
seo-title: Verksamhetsorienterade API:er
description: Verksamhetsorienterade API:er
seo-description: null
page-status-flag: never-activated
uuid: ddb6e5cf-dfe0-4dc9-ac5b-fab21827b874
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: api
discoiquuid: e7b3ffca-c85f-498d-89b4-23fcff59de49
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Verksamhetsorienterade API:er{#business-oriented-apis}

Business API är specifikt för varje typ av objekt. De har en effekt på:

* Leveranser:

   * Skapa en leveransåtgärd, se [SubmitDelivery (nms:delivery)](#submitdelivery--nms-delivery-),
   * skicka en kampanj (starta, pausa, stoppa, skicka bevis),
   * återställer leveransloggar.

* Arbetsflöden:

   * starta ett arbetsflöde,
   * verifiera processer osv.

      Se [SOAP-metoder i JavaScript](../../configuration/using/soap-methods-in-javascript.md).

* Innehållshantering
* Prenumerationshantering, se [Prenumerera (nms:subscription)](#subscribe--nms-subscription-) och [Avsluta prenumeration (nms:subscription)](#unsubscribe--nms-subscription-).
* Dataprocesser: import, export.

I det här avsnittet beskrivs användningen av tjänsterna &quot;Subscribe&quot;, &quot;Unsubscribe&quot; och &quot;SubmitDelivery&quot;.

>[!CAUTION]
>
>[Kampanjens JSAPI-dokumentation](http://docs.campaign.adobe.com/doc/AC/en/jsapi/index.html) innehåller ytterligare information om SOAP-anrop och användning av Javascript i Adobe Campaign, samt en fullständig referens till alla metoder och funktioner som används i programmet.

## Prenumerera (nms:subscription) {#subscribe--nms-subscription-}

Med den här tjänsten kan du prenumerera på en mottagare av en informationstjänst och uppdatera mottagarprofilen.

Följande parametrar krävs för att anropa tjänsten:

* autentisering,
* prenumerationstjänstens interna namn,
* ett XML-dokument som innehåller mottagarinformationen (från schemat &quot;nms:mottagare&quot;),
* ett booleskt värde för att skapa mottagare om det inte redan finns ett.

Beskrivning av prenumerationsmetoden i schemat nms:subscription:

```
<method name="Subscribe" static="true">
  <parameters>
     <param name="serviceName" type="string"  desc="List of information service names (comma separated)"/>
     <param name="recipient" type="DOMElement" desc="Recipient"/>
     <param name="create" type="Boolean" desc="Create recipient if it does not exist"/>
   </parameters>
</method>
```

Definitionen av avstämningsnyckeln måste anges via attributet _**key** för `<recipient>` elementet i XML-dokumentet. Innehållet i det här attributet är en kommaavgränsad XPath-lista.

Anropet returnerar inga data, förutom fel.

### Exempel {#examples}

Prenumeration med mottagaravstämningsnyckeln på e-postadressen: XML-indatadokumentet måste referera till e-postadressen och definitionen av nyckeln i det här fältet.

```
<recipient _key="email" email= "john.doe@adobe.com"/>
```

Uppdaterar både mottagaren och prenumerationen.

```
<recipient _key="email, [folder-id]" email= "john.doe@adobe.com" folder-id="1305" firstName="John" lastName="Doe"/>
```

### Exempel på SOAP-meddelanden {#example-of-soap-messages}

* Fråga:

   ```
   <?xml version='1.0' encoding='ISO-8859-1'?>
   <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
     <SOAP-ENV:Body>
       <m:Subscribe xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
         <sessiontoken xsi:type='xsd:string'/>
         <service xsi:type='xsd:string'>SVC1</service>
         <content xsi:type='' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
           <recipient _key="@email" email= "john.doe@adobe.com/>
         </content>
         <create xsi:type='xsd:boolean'>true</create>
       </m:Subscribe>
     </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

* Svar:

   ```
   <?xml version='1.0' encoding='ISO-8859-1'?>
   <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
     <SOAP-ENV:Body>
       <m:SubscribeResponse xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
       </m:SubscribeResponse>
     </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

## Avbeställ prenumerationen (nms:subscription) {#unsubscribe--nms-subscription-}

Med den här tjänsten kan du avbeställa en mottagares prenumeration från en informationstjänst och uppdatera mottagarprofilen.

Följande parametrar krävs för att anropa tjänsten:

* autentisering,
* Internt namn på tjänsten som du vill avbeställa,
* ett XML-dokument som innehåller mottagarinformationen (från schemat &quot;nms:mottagare&quot;),

Beskrivning av metoden &quot;Unsubscribe&quot; i schemat &quot;nms:subscription&quot;:

```
<method name="Unsubscribe" static="true">
  <parameters>
    <param name="serviceName" type="string" desc="List of information service names (comma separated)"/>
    <param name="recipient" type="DOMElement"  desc="Recipient"/>
  </parameters>
</method>
```

Definitionen av avstämningsnyckeln måste anges via attributet _key för elementet `<recipient>` i XML-dokumentet. Innehållet i det här attributet är en kommaavgränsad XPath-lista.

Om mottagaren inte finns i databasen eller inte prenumererar på den berörda informationstjänsten utför tjänsten ingen åtgärd och genererar inget fel.

>[!NOTE]
>
>Om tjänstnamnet inte anges som en parameter, svartlistas mottagaren automatiskt (@blackList=&quot;1&quot;).

Anropet returnerar inga data, förutom fel.

### Exempel på SOAP-meddelanden {#example-of-soap-messages-1}

Fråga:

```
<?xml version='1.0' encoding='ISO-8859-1'?>
<SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
  <SOAP-ENV:Body>
    <m:Unsubscribe xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
    <sessiontoken xsi:type='xsd:string'/>
    <service xsi:type='xsd:string'>SVC1</service>
    <content xsi:type='' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
      <recipient _key="@email" email= "john.doe@adobe.com/>
    </content>
  </m:Unsubscribe>
</SOAP-ENV:Body>
```

Svar:

```
<?xml version='1.0' encoding='ISO-8859-1'?>
<SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
  <SOAP-ENV:Body>
    <m:UnsubscribeResponse xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
    </m:UnsubscribeResponse>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

## SubmitDelivery (nms:delivery) {#submitdelivery--nms-delivery-}

Med den här tjänsten kan du skapa och skicka en leveransåtgärd.

Följande parametrar krävs för att anropa tjänsten:

* autentisering,
* leveransmallens interna namn,
* ett valfritt XML-dokument som innehåller ytterligare leveransdata.

Detta API får inte anropas i volym eftersom prestandaproblem kan uppstå.

Beskrivning av metoden i dess schema:

```
<method name="SubmitDelivery" static="true">
  <parameters>
    <param name="scenarioName" type="string" inout="in" desc="Internal name of the delivery template"/>
    <param name="content" type="DOMElement"  inout="in" desc="XML content of the delivery template" />
  </parameters>
</method>
```

En leveransmall måste skapas från Adobe Campaign-klientkonsolen. Den innehåller de parametrar som är gemensamma för alla leveranser (avsändarens adress eller meddelandets giltighetstid).

XML-indatadokumentet är ett leveransmallfragment som följer strukturen i schemat nms:delivery. Den kommer att innehålla alla ytterligare data som inte kan definieras statiskt i leveransmallen (t.ex. en lista över mottagare som ska anges som mål).

Anropet returnerar inga data, förutom fel.

### XML-dokumentexempel {#xml-document-example}

Det här exemplet är baserat på en anpassad leveransmall från en extern datakälla (en fil i det här fallet). Konfigurationen beskrivs i sin helhet i leveransmallen, så allt som återstår att skicka när anropet görs är innehållet i filen från `<externalsource>` elementet.

```
<delivery>
  <targets fromExternalSource="true">
    <externalSource>
      MsgId|ClientId|Title|Name|FirstName| Mobile|Email| Market_segment|Product_affinity1 |Product_affinity2|Product_affinity3| Product_affinity4| Support_Number|Amount|Threshold1|000001234|M.| Doe|John|0650201020| john.doe@adobe.com
|1| A1|A2|A3|A4|E12|120000|100000
    </externalSource>
  </target>
</delivery>
```

Om du inte har någon leveransmall kan du använda följande exempel:

```
<delivery>
<targets fromExternalSource="true" targetMode="1" noReconciliation="true" addressField="Email" >  
    <fileFormat active="true">  
      <source format="text" type="text">  
        <dataSourceConfig >  
          <dataSourceColumn label="Email" name="Email" type="string"/>  
        </dataSourceConfig>  
      </source>  
      <destination type="xtkDataStore"/>  
    </fileFormat>  
    <externalSource><![CDATA[not-a-repicipient@domain.com]]></externalSource>  
  </targets> 
</delivery> 
```

