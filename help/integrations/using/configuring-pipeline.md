---
title: Konfigurera integreringen
seo-title: Konfigurera integreringen
description: Konfigurera integreringen
seo-description: null
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 39d6da007d69f81da959660b24b56ba2558a97ba
workflow-type: tm+mt
source-wordcount: '924'
ht-degree: 0%

---


# Konfigurerar pipeline {#configuring-pipeline}

Autentiseringsparametrar som kund-ID, privat nyckel och autentiseringsslutpunkt konfigureras i instanskonfigurationsfilerna.
Listan med utlösare som ska bearbetas konfigureras i ett alternativ. Det är i JSON-format.
Utlösaren bearbetas omedelbart med Javascript-kod. Den sparas i en databastabell utan vidare bearbetning i realtid.
Utlösarna används för målanpassning av ett kampanjarbetsflöde som skickar e-post. Kampanjen är konfigurerad så att en kund som har båda utlösarhändelserna får ett e-postmeddelande.

## Förutsättningar {#prerequisites}

För användning [!DNL Experience Cloud Triggers] i Campaign krävs:

* Adobe Campaign version 6.11 build 8705 eller senare.
* Adobe Analytics Ultimate, Premium, Foundation, OD, Select, Prime, Mobile Apps, Select eller Standard.

Nödvändiga konfigurationer är:

* Skapar en privat nyckelfil och skapar sedan autentiseringsprogrammet som är registrerat med nyckeln.
* Konfiguration av utlösare i Adobe Analytics.

Adobe Analytics-konfigurationen ligger utanför det här dokumentets räckvidd.

Adobe Campaign kräver följande uppgifter från Adobe Analytics:

* Namnet på autentiseringsprogrammet.
* IMSOrgId, identifieraren för Experience Cloud-kunden.
* Namnen på utlösarna som konfigurerats i Analytics.
* Namn och format för datafälten som ska stämma av med marknadsföringsdatabasen.

En del av den här konfigurationen är en anpassad utveckling som kräver följande:

* Arbetskunskaper om JSON-, XML- och Javascript-parsning i Adobe Campaign.
* Arbetskunskaper i API:erna för QueryDef och Writer.
* Aktuella krypterings- och autentiseringsfunktioner med privata nycklar.

>[!NOTE]
>
>Eftersom redigering av JS-koden kräver tekniska färdigheter, försök inte utan rätt förståelse. <br>Utlösare sparas i en databastabell. Därför kan marknadsförare på ett säkert sätt använda utlösardata i riktade arbetsflöden.

## Autentiserings- och konfigurationsfiler {#authentication-configuration}

Autentisering krävs eftersom Pipeline finns i Adobe Experience Cloud.
Om marknadsföringsservern finns på plats måste den autentiseras för att ha en säker anslutning när den loggar in på Pipeline.
Den använder ett par offentliga och privata nycklar. Den här processen fungerar på samma sätt som en användare/ett lösenord, men är bara säkrare.

### IMSOrgId {#imsorgid}

IMSOrgId är identifieraren för kunden i Adobe Experience Cloud.
Ange det i instansfilen serverConf.xml, under attributet IMSOrgId.
Exempel:

```
<redirection IMSOrgId="C5E715(…)98A4@AdobeOrg" (…)
```

### Nyckelgenerering {#key-generation}

Nyckeln är ett par filer. Det är i RSA-format och 4 096 byte långt. Den kan genereras med ett verktyg med öppen källkod, till exempel OpenSSL. Varje gång verktyget körs skapas en ny tangent slumpmässigt.
För enkelhetens skull anges stegen nedan:

* ```openssl genrsa -out <private_key.pem> 4096```

* ```openssl rsa -pubout -in <private_key.pem> -out <public_key.pem>```

Exempel: private_key.pem-fil:

```
----BEGIN RSA PRIVATE KEY----
MIIEowIBAAKCAQEAtqcYzt5WGGABxUJSfe1Xy8sAALrfVuDYURpdgbBEmS3bQMDb
(…)
64+YQDOSNFTKLNbDd+bdAA+JoYwUCkhFyvrILlgvlSBvwAByQ2Lx
----END RSA PRIVATE KEY----
```

Exempel på filen public_key.pem:

```
----BEGIN PUBLIC KEY----
MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAtqcYzt5WGGABxUJSfe1X
(…)
EwIDAQAB
----END PUBLIC KEY----
```

>[!NOTE]
>
>Tangenter ska inte genereras av PuttyGen, OpenSSL är det bästa alternativet.

### Autentisera klientframtagning i Adobe Experience Cloud {#oauth-client-creation}

Ett program av typen JWT måste skapas genom att logga in på Adobe Analytics i rätt organisationskonto under **[!UICONTROL Admin]** > **[!UICONTROL User Management]** > **[!UICONTROL Legacy Oath application]**.

Följ de här stegen:

1. Markera **[!UICONTROL Service Account (JWT Assertion)]**.
1. Ange **[!UICONTROL Application Name]**.
1. Registrera **[!UICONTROL Public key]**.
1. Välj utlösarens **[!UICONTROL Scopes]**.

   ![](assets/triggers_5.png)

1. Klicka på **[!UICONTROL Create]** och kontrollera **[!UICONTROL Application ID]** och **[!UICONTROL Application Secret]** skapa.

   ![](assets/triggers_6.png)

### Registrering av programnamn i Adobe Campaign Classic {#application-name-registration}

Program-ID för den autentiseringsklient som skapas måste konfigureras i Adobe Campaign. Du kan göra det genom att redigera instanskonfigurationsfilen i elementet pipelined, särskilt attributet appName.

Exempel:

```
<pipelined autoStart="true" appName="applicationID" authPrivateKey="@qQf146pexBksGvo0esVIDO(…)"/>
```

### Nyckelkryptering {#key-encription}

Om du vill använda den i en pipeline måste den privata nyckeln krypteras. Krypteringen görs med Javascript-funktionen cryptString och måste utföras på samma instans som i pipeline.

Ett exempel på kryptering med privat nyckel med JavaScript finns på den här [sidan](../../integrations/using/pipeline-troubleshooting.md).

Den krypterade privata nyckeln måste registreras i Adobe Campaign. Du kan göra det genom att redigera instanskonfigurationsfilen i elementet pipelined, särskilt attributet authPrivateKey.

Exempel:

```
<pipelined autoStart="true" appName="applicationID" authPrivateKey="@qQf146pexBksGvo0esVIDO(…)"/>
```

### Automatisk processstart i pipeline {#pipelined-auto-start}

Processen med rörledning måste startas automatiskt.
Om du vill göra det anger du elementet i konfigurationsfilen till autostart=&quot;true&quot;:

```
<pipelined autoStart="true" appName="applicationID" authPrivateKey="@qQf146pexBksGvo0esVIDO(…)"/>
```

### Omstart av process i pipeline {#pipelined-restart}

Den kan också startas manuellt med kommandoraden:

```
nlserver start pipelined@instance
```

En omstart krävs för att ändringarna ska börja gälla:

```
nlserver restart pipelined@instance
```

Om det uppstår fel söker du efter fel i standardutdata (om du började manuellt) eller i den förberedda loggfilen. Mer information om hur du löser problem finns i avsnittet Felsökning i det här dokumentet.

### Konfigurationsalternativ för pipeline {#pipelined-configuration-options}

| Alternativ | Beskrivning |
|:-:|:-:|
| appName | ID för OAuth-programmet (program-ID) som är registrerat i Adobe Analytics (där den offentliga nyckeln överfördes): Admin > Användarhantering > Äldre Oath-program. Se det här[avsnittet](../../integrations/using/configuring-pipeline.md#oauth-client-creation). |
| authGatewayEndpoint | URL för att hämta gateway-token. <br> Standard: https://api.omniture.com |
| authPrivateKey | Privat nyckel (offentlig del som överförts till Adobe Analytics (se detta avsnitt). AES krypterad med alternativet XtkSecretKey: xtk.session.EncryptPassword(&quot;PRIVATE_KEY&quot;); |
| disableAuth | Inaktivera autentisering (anslutning utan gatewaytoken accepteras bara av vissa slutpunkter i utvecklingsprojektet) |
| discoverPipelineEndpoint | URL för att identifiera den slutpunkt för Pipeline Services som ska användas för den här klienten. Standard: https://producer-pipeline-pnw.adobe.net |
| dumpStatePeriodSec | Perioden mellan två dumpar av processens interna tillstånd i var/INSTANCE/pipelined.json interna tillstånd är även tillgänglig på begäran på http://INSTANCE/pipelined/status (port 7781). |
| forceradPipelineEndpoint | Inaktivera identifieringen av PipelineServicesEndpoint och framtvinga den |
| monitorServerPort | Den rörliga processen lyssnar på den här porten och tillhandahåller processens interna tillstånd på http://INSTANCE/pipelined/status (port 7781). |
| pointerFlushMessageCount | När det här antalet meddelanden bearbetas sparas förskjutningarna i databasen. Standardvärdet är 1000 |
| pekareFlushPeriodSec | Efter den här perioden sparas förskjutningarna i databasen. Standardvärdet är 5 (sek) |
| processingJSThreads | Antal dedikerade trådar som bearbetar meddelanden med anpassade JS-anslutningar. Standard är 4 |
| processingThreads | Antal dedikerade trådar som bearbetar meddelanden med inbyggd kod. Standard är 4 |
| retryPeriodSec | Fördröjning mellan återförsök (om det finns behandlingsfel). Standardvärdet är 30 (sekunder) |
| retryValiditySec | Ignorera meddelandet om det inte har bearbetats korrekt efter den här perioden (för många försök). Standardvärdet är 300 (sekunder) |
