---
product: campaign
title: Om webbtjänster
description: Om webbtjänster
audience: configuration
content-type: reference
topic-tags: api
exl-id: 7aa2aef1-2eb6-48a6-82fa-4451bed66216
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 4%

---

# Om webbtjänster{#about-web-services}

![](../../assets/v7-only.svg)

## Definition av Adobe Campaign API:er {#definition-of-adobe-campaign-apis}

Adobe Campaign programserver är utformad för öppenhet och enkel integrering med allt mer mångsidiga och komplexa företagsinformationssystem.

Adobe Campaign API:er används i JavaScript i programmet och i SOAP utanför det. De utgör ett bibliotek med generiska funktioner som kan berikas. Mer information finns i [Implementera SOAP-metoder](../../configuration/using/implementing-soap-methods.md).

>[!IMPORTANT]
>
>Antalet auktoriserade motorsamtal per dag varierar beroende på ditt licensavtal. Mer information finns på [den här sidan](https://helpx.adobe.com/legal/product-descriptions/adobe-campaign-classic---product-description.html).\
>En lista över alla API:er, inklusive deras fullständiga beskrivning, finns i [den här dedikerade dokumentationen](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html).

## Förhandskrav {#prerequisites}

Innan du använder Adobe Campaign API:er måste du känna till följande:

* Javascript
* SOAP-protokoll
* Adobe Campaign datamodell

## Använda Adobe Campaign API:er {#using-adobe-campaign-apis}

Adobe Campaign använder två typer av API:er:

* Generiska data har åtkomst till API:er för att fråga efter datamodelldata. Se [Dataorienterade API:er](../../configuration/using/data-oriented-apis.md).
* Affärsspecifika API:er där du kan agera på varje objekt: leveranser, arbetsflöden, prenumerationer osv. Se [Affärsorienterade API:er](../../configuration/using/business-oriented-apis.md).

Om du vill utveckla API:er och interagera med Adobe Campaign måste du känna till datamodellen. Med Adobe Campaign kan du generera en fullständig beskrivning av basen. Se [Beskrivning av modellen](../../configuration/using/data-oriented-apis.md#description-of-the-model).

## SOAP-anrop {#soap-calls}

Med SOAP-protokollet kan du anropa API-metoder, via den avancerade klienten, tredjepartsprogram som använder webbtjänster eller JSP som använder dessa metoder internt.

![](assets/s_ncs_configuration_architecture.png)

Strukturen för ett SOAP-meddelande är följande:

* ett kuvert som definierar meddelandets struktur,
* en valfri rubrik,
* ett organ som innehåller information om samtalet och svaret,
* felhantering som definierar felvillkoret.

## Resurser och utbyten {#resources-and-exchanges}

I följande schema visas de olika resurser som används i Adobe Campaign API:er:

![](assets/s_ncs_integration_webservices_schema_pres.png)

## Exempel på ett SOAP-meddelande i metoden ExecuteQuery {#example-of-a-soap-message-on-the--executequery--method--}

I det här exemplet anropar en SOAP-fråga metoden&quot;ExecuteQuery&quot;, som tar en teckensträng som parameter för autentisering (sessionstoken) och ett XML-innehåll för beskrivningen av frågan som ska köras.

Mer information finns i [ExecuteQuery (xtk:queryDef)](../../configuration/using/data-oriented-apis.md#executequery--xtk-querydef-).

>[!NOTE]
>
>WSDL-beskrivningen av den här tjänsten har slutförts i exemplet som visas här: [Beskrivning av webbtjänst: WSDL](../../configuration/using/web-service-calls.md#web-service-description--wsdl).

### SOAP-fråga {#soap-query}

```
<?xml version='1.0' encoding='ISO-8859-1'?>
  <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
    <SOAP-ENV:Body>
      <ExecuteQuery xmlns='urn:xtk:queryDef' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
        <__sessiontoken xsi:type='xsd:string'/>
        <entity xsi:type='ns:Element' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
          <queryDef firstRows="true" lineCount="200" operation="select" schema="nms:rcpGrpRel" startLine="0" startPath="/" xtkschema="xtk:queryDef">
          ...
          </queryDef>
        </entity>
      </ExecuteQuery>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

`<soap-env:envelope>`-elementet är det första elementet i meddelandet som representerar SOAP-kuvertet.

`<soap-env:body>`-elementet är det första underordnade elementet i omslaget. Den innehåller beskrivningen av meddelandet, dvs. innehållet i frågan eller svaret.

Den metod som ska anropas anges i `<executequery>`-elementet från texten i SOAP-meddelandet.

I SOAP identifieras parametrarna i den ordning de visas. Den första parametern, `<__sessiontoken>`, tar autentiseringskedjan, den andra parametern är XML-beskrivningen för frågan från `<querydef>`-elementet.

### SOAP-svar {#soap-response}

```
<?xml version='1.0' encoding='ISO-8859-1'?>
  <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
    <SOAP-ENV:Body>
      <ExecuteQueryResponse xmlns='urn:xtk:queryDef' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
        <pdomOutput xsi:type='ns:Element' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
          <rcpGrpRel-collection><rcpGrpRel group-id="1872" recipient-id="1362"></rcpGrpRel></rcpGrpRel-collection>
        </pdomOutput>
      </ExecuteQueryResponse>
    </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

Resultatet av frågan anges från `<pdomoutput>`-elementet.

## Felhantering {#error-management}

Exempel på SOAP-felsvar:

```
<?xml version='1.0' encoding='ISO-8859-1'?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
  <SOAP-ENV:Body>
    <SOAP-ENV:Fault>
      <faultcode>SOAP-ENV:Server</faultcode>
      <faultstring>Error while executing 'Write' of the 'xtk:persist'.</faultstring> service
      <detail>ODBC error: [Microsoft][ODBC SQL Server Driver][SQL Server]Cannot insert duplicate key row in object 'XtkOption' with unique index 'XtkOption_name'. SQLSTate: 23000
ODBC error: [Microsoft][ODBC SQL Server Driver][SQL Server]The statement has been terminated. SQLSTate: 01000 Cannot save the 'Options (xtk:option)' document </detail>
    </SOAP-ENV:Fault>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

`<soap-env:fault>`-elementet i SOAP-meddelandets brödtext används för att förmedla felsignaler som uppstår under bearbetningen av webbtjänsten. Detta består av följande delelement:

* `<faultcode>` : anger feltypen. Feltyperna är:

   * &quot;VersionMismatch&quot; i händelse av inkompatibilitet med den SOAP-version som används,
   * &quot;MustUnderstand&quot; i händelse av problem i meddelandehuvudet,
   * &quot;Klient&quot; om klienten saknar viss information,
   * &quot;Server&quot; om servern har problem med att köra bearbetningen.

* `<faultstring>` : meddelande som beskriver felet
* `<detail>` : långt felmeddelande

Slutfört eller misslyckat anrop av tjänsten identifieras när elementet `<faultcode>` verifieras.

>[!IMPORTANT]
>
>Alla Adobe Campaign webbtjänster hanterar fel. Vi rekommenderar därför att du testar varje anrop för att kunna hantera returnerade fel.

Exempel på felhantering i C#:

```
try 
{
  // Invocation of method
  ...
}
catch (SoapException e)
{
  System.Console.WriteLine("Soap exception: " + e.Message);        
  if (e.Detail != null)
    System.Console.WriteLine(e.Detail.InnerText);
}
```

## Webbtjänstserverns URL (eller EndPoint) {#url-of-web-service-server--or-endpoint-}

Om du vill skicka webbtjänsten måste du kontakta den Adobe Campaign-server som implementerar motsvarande tjänstmetod.

Server-URL:en är följande:

https://serverName/nl/jsp/soaprouter.jsp

Med **`<server>`** Adobe Campaign-programservern (**nlserver web**).
