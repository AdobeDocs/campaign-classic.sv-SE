---
title: Webbtjänstsamtal
seo-title: Webbtjänstsamtal
description: Webbtjänstsamtal
seo-description: null
page-status-flag: never-activated
uuid: 7defe0e4-bb4a-4f6a-b6e8-e2ffac73b4c1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: api
discoiquuid: 6934c165-6d27-4ce5-8607-170f299b4702
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c51a51f175e9f3fe5a55f2b5f57872057f70909d
workflow-type: tm+mt
source-wordcount: '954'
ht-degree: 0%

---


# Webbtjänstsamtal{#web-service-calls}

## Allmän information {#general-information}

Alla API-metoder presenteras i form av webbtjänster. På så sätt kan du hantera alla Adobe Campaign-funktioner via SOAP-anrop, som är startpunkten för programservern Adobe Campaign. Adobe Campaign-konsolen använder bara SOAP-anrop.

Med webbtjänster kan du skapa många program från ett tredjepartssystem:

* Synkrona aviseringar, meddelanden och mallkörning i realtid från ett back office- eller transaktionssystem.
* Utveckling av specialgränssnitt med förenklad funktionalitet (webbgränssnitt osv.).
* Matning och sökning av data i databasen, med iakttagande av handelsregler och som förblir isolerade från den underliggande fysiska modellen.

## Definition av webbtjänster {#definition-of-web-services}

Definitionen av de webbtjänster som implementeras på programservern i Adobe Campaign är tillgänglig från datamappningarna.

En webbtjänst beskrivs i datamappningens grammatik och är tillgänglig från **`<methods>`** elementet.

```
<methods>
  <method name="GenerateForm" static="true">
    <help>Generates the form in Mail or Web mode</help>
    <parameters>
      <param name="formName" type="string" desc="Name of form"/>
      <param name="mailMode" type="boolean" desc="Generate a form of type Mail"/>
      <param name="result" type="string" inout="out" desc="Result "/>
    </parameters>
  </method>
</methods>
```

Här finns ett exempel på definitionen av metoden **GenerateForm**.

Beskrivningen av tjänsten börjar med `<method>` elementet. Listan över metodens parametrar fylls i från `<parameters>` elementet. Varje parameter anges med ett namn, en typ (Boolean, sträng, DOMElement osv.) och en beskrivning. Med attributet &quot;inout&quot; med värdet &quot;out&quot; kan du ange att parametern &quot;result&quot; finns i SOAP-anropets utdata.

Förekomsten av attributet&quot;static&quot; (med värdet&quot;true&quot;) beskriver metoden som statisk, vilket betyder att alla parametrar för metoden måste deklareras.

En const-metod har implicit ett XML-dokument i det associerade schemats format som indata.

En fullständig beskrivning av elementet `<method>` i ett Adobe Campaign-schema finns i kapitlet &quot;Schemareferenser&quot; under  <a href="../../configuration/using/elements-and-attributes.md#method--element" target="_blank">  `<method>`    -element.

Exempel på &quot;const&quot;-typ &quot;ExecuteQuery&quot;-metoden från schemat &quot;xtk:queryDef&quot;:

```
<method name="ExecuteQuery" const="true">
  <help>Retrieve data from a query</help>
  <parameters>
    <param desc="Output xml document" name="output" type="DOMDocument" inout="out"/>
  </parameters>
</method>
```

Indataparametern för den här metoden är ett XML-dokument i formatet för schemat &quot;xtk:queryDef&quot;.

## Beskrivning av webbtjänst: WSDL {#web-service-description--wsdl}

Det finns en WSDL-fil (Web Service Description Library) för varje tjänst. I den här XML-filen används ett språk för att beskriva tjänsten och ange tillgängliga metoder, parametrar och servern som ska kontaktas för att tjänsten ska kunna köras.

### WSDL-filgenerering {#wsdl-file-generation}

Om du vill generera en WSDL-fil måste du ange följande URL från en webbläsare:

[https://`<server>`/nl/jsp/schemawsdl.jsp?schema=`<schema>`

Med:

* **`<server>`**: programservern Adobe Campaign (webbserver)
* **`<schema>`**: schema-ID-nyckel (namespace:schema_name)

### Exempel på metoden ExecuteQuery i schemat xtk:queryDef {#example-on-the--executequery--method-of-schema--xtk-querydef-}

WSDL-filen genereras från URL:en:

[https://localhost/nl/jsp/schemawsdl.jsp?schema=xtk:queryDef](https://my_serveur/nl/jsp/schemawsdl.jsp?schema=xtk:queryDef)

En WSDL-beskrivning börjar med att definiera de typer som används för att skapa formulärmeddelanden, som är kopplade till portar, som är kopplade till ett protokoll av bindningar som skapar webbtjänster.

#### Typer {#types}

Typdefinitioner baseras på XML-scheman. I det här exemplet använder metoden &quot;ExecuteQuery&quot; strängen &quot;s:string&quot; och ett XML-dokument (`<s:complextype>`) som parametrar. Returvärdet för metoden (&quot;ExecuteQueryResponse&quot;) är ett XML-dokument ( `<s:complextype>`).

```
<types>
<s:schema elementFormDefault="qualified" targetNamespace="urn:xtk:queryDef">
  <s:element name="ExecuteQuery">
    <s:complexType>
      <s:sequence>
        <s:element maxOccurs="1" minOccurs="1" name="sessiontoken" type="s:string"/>
        <s:element maxOccurs="1" minOccurs="1" name="entity">
          <s:complexType>
            <s:sequence>
              <s:any/>
            </s:sequence>
          </s:complexType>
        </s:element>
      </s:sequence>
    </s:complexType>
  </s:element>
  <s:element name="ExecuteQueryResponse">
    <s:complexType>
      <s:sequence>
        <s:element maxOccurs="1" minOccurs="1" name="pdomOutput">
          <s:complexType mixed="true">
            <s:sequence>
              <s:any/>
            </s:sequence>
          </s:complexType>
        </s:element>
      </s:sequence>
    </s:complexType>
  </s:element>
```

#### Meddelanden {#messages}

Här `<message>` beskrivs namnen och typerna för en uppsättning fält som ska skickas. I metoden används två meddelanden för att skicka som en parameter (&quot;ExecuteQueryIn&quot;) och returvärdet (&quot;ExecuteQueryOut&quot;).

```
<message name="ExecuteQueryIn">
  <part element="tns:ExecuteQuery" name="parameters"/>
</message>

<message name="ExecuteQueryOut">
  <part element="tns:ExecuteQueryResponse" name="parameters"/>
</message> 
```

#### PortType {#porttype}

Meddelandena `<porttype>` kopplas till åtgärden &quot;ExecuteQuery&quot; som utlöses av frågan (&quot;input&quot;) som genererar ett svar (&quot;output&quot;).

```
<portType name="queryDefMethodsSoap">
  <operation name="ExecuteQuery">
    <input message="tns:ExecuteQueryIn"/>
    <output message="tns:ExecuteQueryOut"/>
  </operation>
</portType>
```

#### Bindning {#binding}

Delen anger `<binding>` SOAP-kommunikationsprotokollet ( `<soap:binding>` ), datatransporten i HTTP (värdet för attributet transport) och dataformatet för åtgärden ExecuteQuery. Innehållet i SOAP-kuvertet innehåller meddelandesegmenten direkt utan omformning.

```
<binding name="queryDefMethodsSoap" type="tns:queryDefMethodsSoap">
  <soap:binding style="document" transport="http://schemas.xmlsoap.org/soap/http"/>
  <operation name="ExecuteQuery">
    <soap:operation soapAction="xtk:queryDef#ExecuteQuery" style="document"/>
    <input>
      <soap:body encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" namespace="urn:xtk:queryDef" use="literal"/>
    </input>
    <output>
      <soap:body encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" namespace="urn:xtk:queryDef" use="literal"/>
    </output>
  </operation>
</binding>
```

#### Tjänst {#service}

Delen beskriver `<service>` tjänsten XtkQueryDef med dess URI på URL:en för programservern i Adobe Campaign.

```
<service name="XtkQueryDef">
  <port binding="tns:queryDefMethodsSoap" name="queryDefMethodsSoap">
    <soap:address location="https://localhost/nl/jsp/soaprouter.jsp"/>
  </port>
</service>
```

## Anslutningar {#connectivity}

Adobe Campaign har ökat säkerheten för autentiseringsmekanismer genom att införa säkerhetszoner (se kapitlet **Definiera säkerhetszoner** i [det här avsnittet](../../installation/using/configuring-campaign-server.md#defining-security-zones)) samt inställningar för sessionshantering.

Det finns två autentiseringslägen:

* **via ett anrop till inloggningsmetoden()**. Det här läget genererar en sessionstoken och en säkerhetstoken. Det är det säkraste läget och därför det mest rekommenderade.

eller

* **via inloggning + lösenord** för Adobe Campaign som skapar en sessionstoken. Sessionstoken upphör automatiskt efter en angiven period. Det här läget rekommenderas inte och kräver att säkerhetsinställningarna för vissa zoninställningar reduceras (allowUserPassword=&quot;true&quot; och sessionTokenOnly=&quot;true&quot;).

### Sessionstokensegenskaper {#session-token-characteristics}

Sessionstoken har följande egenskaper:

* en X-timmars livscykel (livscykeln kan konfigureras i filen serverConf.xml, standardperioden är 24 timmar)
* en slumpmässig konstruktion (den innehåller inte längre användarens inloggning och lösenord)
* på webben:

   * sessionstoken blir en permanent token, och tas inte bort när webbläsaren stängs
   * den placeras i en HTTP-ONLY-cookie (cookies måste aktiveras för operatorer)

### Egenskaper för säkerhetstoken {#security-token-characteristics}

Säkerhetstoken har följande egenskaper:

* den genereras från sessionstoken
* har en 24-timmars livscykel (konfigurerbar i filen serverConf.xml, standardperioden är 24 timmar)
* den lagras i Adobe Campaign-konsolen
* på webben:

   * det lagras i ett dokument.__securityToken, egenskap
   * webbadresserna uppdateras för att uppdatera säkerhetstoken
   * formulären uppdateras även via ett dolt fält som innehåller token

#### Säkerhetstokenförflyttning {#security-token-movement}

När du använder konsolen är det:

* skickas i inloggningssvaret (i HTTP-huvudet)
* används i varje fråga (i HTTP-huvudet)

Från en POST och GET HTTP:

* servern slutför länkarna med token
* servern lägger till ett dolt fält i formulär

Från ett SOAP-anrop:

* det läggs till för att ringa rubriker

### Exempel på utlysningar {#call-examples}

* Använda **HttpSoapConnection/SoapService**:

   ```
     var cnx = new HttpSoapConnection("https://serverURL/nl/jsp/soaprouter.jsp");
   var session = new SoapService(cnx, 'urn:xtk:session');
   session.addMethod("Logon", "xtk:session#Logon",
                       ["sessiontoken", "string", "Login", "string", "Password", "string", "Parameters", "NLElement"],
                       ["sessionToken", "string", "sessionInfo", "NLElement", "securityToken", "string"]);
   
   var res = session.Logon("", "admin", "pwd", <param/>);
   var sessionToken = res[0];
   var securityToken = res[2];
   
   cnx.addTokens(sessionToken, securityToken);
   var query = new SoapService(cnx, 'urn:xtk:queryDef');
   query.addMethod("ExecuteQuery", "xtk:queryDef#ExecuteQuery",
                       ["sessiontoken", "string", "entity", "NLElement"],
                       ["res", "NLElement"]);
   
   var queryRes = query.ExecuteQuery("", <queryDef operation="select" schema="nms:recipient">
             <select>
               <node expr="@email"/>
               <node expr="@lastName"/>
               <node expr="@firstName"/>
             </select>
             <where>
               <condition expr="@email = 'joe.doe@aol.com'"/>
             </where>
           </queryDef>);
   logInfo(queryRes[0].toXMLString())
   ```

* Använda **HttpServletRequest**:

>[!NOTE]
>
>De URL:er som används i följande **HttpServletRequest** -anrop måste finnas i listan över tillåtna i avsnittet url-behörigheter i **filen serverConf.xml** . Detta gäller även för serverns URL.

Inloggningskörning():

```
var req = new HttpClientRequest("https://serverURL/nl/jsp/soaprouter.jsp");
req.header["Content-Type"] = "text/xml; charset=utf-8";
req.header["SOAPAction"] =   "xtk:session#Logon";
req.method = "POST";
req.body = '<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:xtk:session">' +
  '<soapenv:Header/>' +
  '<soapenv:Body>' +
      '<urn:Logon>' +
          '<urn:sessiontoken></urn:sessiontoken>' +
          '<urn:strLogin>LOGIN_HERE</urn:strLogin>' +
          '<urn:strPassword>PASSWORD_HERE</urn:strPassword>' +
          '<urn:elemParameters></urn:elemParameters>' +
      '</urn:Logon>' +
  '</soapenv:Body>' +
'</soapenv:Envelope>';
req.execute();
         
var resp = req.response;
var xmlRes = new XML(String(resp.body).replace("<?xml version='1.0'?>",""));
var sessionToken = String(xmlRes..*::pstrSessionToken);;
var securityToken = String(xmlRes..*::pstrSecurityToken);
```

Frågekörning:

```
var req2 = new HttpClientRequest("https://serverURL/nl/jsp/soaprouter.jsp");
req2.header["Content-Type"] = "text/xml; charset=utf-8";
req2.header["SOAPAction"] =   "xtk:queryDef#ExecuteQuery";req2.header["X-Security-Token"] = securityToken;
req2.header["cookie"]           = "__sessiontoken="+sessionToken;
req2.method = "POST";
req2.body = '<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:xtk:queryDef">' +
           '<soapenv:Header/><soapenv:Body><urn:ExecuteQuery><urn:sessiontoken/><urn:entity>' +
              '<queryDef operation="select" schema="nms:recipient">' +
                '<select><node expr="@email"/><node expr="@lastName"/><node expr="@firstName"/></select>' +
                '<where><condition expr="@email = \'john.doe@aol.com\'"/></where>' +
              '</queryDef>' +
         '</urn:entity></urn:ExecuteQuery></soapenv:Body></soapenv:Envelope>';
req2.execute();
var resp2 = req2.response;
logInfo(resp2.body)
```

