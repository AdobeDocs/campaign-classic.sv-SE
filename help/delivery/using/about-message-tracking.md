---
product: campaign
title: Kom igång med spårning
description: Läs mer om de allmänna riktlinjerna för spårning i Adobe Campaign
feature: Monitoring, Email
role: User
exl-id: 43779505-9917-4e99-af25-b00a9d29a645
source-git-commit: ba53107ce06c0484070cbe0943ba439d33d5f710
workflow-type: tm+mt
source-wordcount: '1267'
ht-degree: 2%

---

# Kom igång med meddelandespårning {#get-started-tracking}

>[!IMPORTANT]
>
>**Allmän spårningsvägledning** som gäller både Campaign Classic v7 och Campaign v8 finns i [Meddelandespårningsdokumentationen för Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/tracking){target="_blank"}:
>
>* [Konfigurera spårade länkar](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/tracked-links){target="_blank"}
>* [Konfigurera alternativ för URL-spårning](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/url-tracking){target="_blank"}
>* [Spåra anpassade länkar](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/personalized-links){target="_blank"}
>* [Åtkomstspårningsloggar](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/tracking-logs){target="_blank"}
>* [Testspårning](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/testing-tracking){target="_blank"}
>* [Rapporter om spårning](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/reporting/delivery-reports#tracking-indicators){target="_blank"}
>
>**Den här sidan innehåller endast Campaign Classic v7-specifika spårningsfunktioner**, främst för hybriddistributioner och lokala distributioner.

## Spårningsfunktioner

### Spårningskonfiguration {#configure-tracking}

För Campaign Classic v7 **hybriddistributioner/lokala distributioner** måste du konfigurera spårning på instansnivå innan du använder den.

>[!NOTE]
>
>För Hanterade molntjänster i Campaign v8 utförs spårningskonfigurationen av Adobe.

**Verksamhetsprincip**

Innan du använder spårning måste du först konfigurera den för din instans. Konfigurationen måste utföras på Adobe Campaign programservrar och webbservrar.

I Campaign finns det två typer av spårning:

* **Webbspårning**: I det här läget kan du spåra besök på webbplatsens sidor
* **Meddelandespårning**: I det här läget kan du spåra meddelandeleveranser och mottagarnas beteende

Spårningsläget väljs under installationen. För lokala installationer måste spårningskonfigurationen definieras på instansnivå. [Läs mer](../../installation/using/deploying-an-instance.md#operating-principle)

**Spårningsserver**

Om du vill konfigurera spårning måste instansen deklareras och registreras hos spårningsservern(arna). Spårningsservern används för att registrera och hämta information om URL:er som mottagarna klickat på.

För lokala installationer är spårningsservern vanligtvis en webbserver som kör Adobe Campaign webbprogram. URL:en för spårningsservern måste definieras i din instanskonfiguration. [Läs mer](../../installation/using/deploying-an-instance.md#tracking-server)

**Sparar spårning**

När spårning har konfigurerats och URL:erna har fyllts i måste spårningsservern registreras. Registreringen gör det möjligt för Adobe Campaign att spara spårningsinformation och tillhandahålla rapporter och statistik om spårade aktiviteter.

För lokala installationer lagras spårningsinformation i databasen och hämtas via tekniska arbetsflöden. Det tekniska arbetsflödet **Spårning** bearbetar och lagrar spårningsdata som samlats in från omdirigeringsservern. [Läs mer](../../installation/using/deploying-an-instance.md#saving-tracking)

### Spårning av webbprogram {#web-application-tracking}

<img src="assets/do-not-localize/icon-web-app.svg" width="60px">

>[!NOTE]
>
>**Spårning av webbprogram är specifikt för Campaign Classic v7** och är inte tillgängligt i Campaign v8.

**Spåra en webbapplikation**

Du kan också spåra och mäta besök på webbprogramsidor med hjälp av spårningstaggar. Den här funktionaliteten kan användas för alla webbapplikationstyper som formulär och landningssidor. [Läs mer](../../web/using/tracking-a-web-application.md)

**Välj att inte delta i spårning av webbapplikation**

Med avanmälan om spårning av webbprogram kan du sluta spåra webbbeteenden för slutanvändare som avanmäler sig från beteendespårning. Du kan inkludera möjligheten att visa en banderoll i webbprogram eller landningssidor så att användarna kan välja bort den. [Läs mer](../../web/using/web-application-tracking-opt-out.md)

## Felsökning av spårning {#tracking-troubleshooting}

<img src="assets/do-not-localize/icon-troubleshooting.svg" width="60px">

Följande felsökningstips gäller för **hybriddistributioner i Campaign Classic v7/på plats**. Viss information kan också gälla för Campaign v8-distributioner på plats. Kontakta din Adobe-representant om du behöver hjälp med de hanterade molntjänsterna för Campaign v8.

Grundläggande felsökningssteg för spårning i Campaign v8 finns i [Felsökningsspårning i dokumentationen för Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/tracking-logs#troubleshooting){target="_blank"}.

### Grundläggande kontroller {#basic-checks}

**Kontrollera att spårningsloggsprocessen körs**

Den här processen läser från det delade minnet för IIS/webbservern och skriver omdirigeringsloggarna.

Du kommer åt den från hemsidan genom att välja fliken Övervakning i din instans. Du kan också köra följande kommando på instansen: `<user>@<instance>:~$ nlserver pdump`

Om spårningsprocessen inte visas i listan startar du den med följande kommando på instansen: `<user>@<instance>:~$ nlserver start trackinglogd`

**Kontrollera att det tekniska arbetsflödet för spårning har körts nyligen**

Du hittar det tekniska arbetsflödet för spårning i mapparna Administration > Produktion > Tekniska arbetsflöden.

### Avancerad felsökning {#advanced-troubleshooting}

+++Arbetsflödet för spårning misslyckas

>[!NOTE]
>
>Endast för Windows

Den skadade loggfilen för spårning ../nl6/var/&lt;instance_name>/redir/log/0x0000 kan stoppa spårningsarbetsflödet. Om du enkelt vill identifiera skadade rader och ta bort dem för att återuppta arbetsflödet för spårning kan du använda kommandona nedan.

**Jag vet i vilken fil den skadade raden är**

I så fall kan skadade rader hittas i loggfilen 0x000000000A0000.log, men samma process kan tillämpas på en uppsättning filer - en i taget.

```
$ cd {install directory}/var/{instance name}/redir/log
$ cat 0x00000000000A0000.log | sed -nE '/^[[:alnum:]]{2}x[[:alnum:]]*\t[0-9T:\.-]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[[:alnum:]]*\t[[:alnum:]-]*\t[[:print:]]*\t[[:print:]]*\t[[:print:]]*\t([0-9a-fA-F\.:]*|[0-9a-fA-F\.:]*\t[[:print:]]*|[0-9a-fA-F\.:]*,[[:print:]]*)$/!p'
```

Du kan sedan stoppa arbetsflödet för spårning, ta bort skadade rader och starta om arbetsflödet.

**Jag vet inte i vilken fil den skadade raden är**

1. Använd följande kommandorad för att checka in alla spårningsfiler.

   ```
   $ cd {install directory}/var/{instance name}/redir/log
   $ cat *.log | sed -nE '/^[[:alnum:]]{2}x[[:alnum:]]*\t[0-9T:\.-]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[0-9a-fA-F]*\t[[:alnum:]]*\t[[:alnum:]-]*\t[[:print:]]*\t[[:print:]]*\t[[:print:]]*\t([0-9a-fA-F\.:]*|[0-9a-fA-F\.:]*\t[[:print:]]*|[0-9a-fA-F\.:]*,[[:print:]]*)$/!p'
   ```

1. Kommandot visar alla skadade rader. Exempel:

   ```
   50x000000000FD7EC86 2017-06-24T21:00:50.96 1f506d71 1aeab4b6 1af77020 0 e5155671-4ab7-4ce4-a763-3b82dda6d881 h
   Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.95 Safari/537.36 52.46.20.64
   ```

   >[!NOTE]
   >
   >Radretur har lagts till före användaragenten för att ge bättre läsbarhet och inte återge effektiv återgivning.

1. Kör ett grep-kommando för att hitta motsvarande fil.

   ```
   $ grep -Rn <Log Id>
   # for example:
   $ grep -Rn 50x000000000FD7EC86
   ```

1. Hitta felloggen med filnamnet och radnumret. Exempel:

   ```
   ./0x000000000FD7E000.log:3207:50x000000000FD7EC86 2017-06-24T21:00:50.96 1f506d71 1aeab4b6 1af77020 0 e5155671-4ab7-4ce4-a763-3b82dda6d881 h
   Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.95 Safari/537.36 52.46.20.64
   ```

   >[!NOTE]
   >
   >En vagnretur har lagts till före användaragenten för att ge bättre läsbarhet och inte återge effektiv återgivning.

Du kan sedan stoppa arbetsflödet för spårning, ta bort skadade rader och starta om arbetsflödet.

+++

+++Spårning av länkar misslyckas ibland

När du försöker komma åt spårningslänkarna visas följande meddelande:

`Requested URL '/r/ id=h787bc0,281a4d8,281a4da&p1=1' cannot be found`

1. Gå till URL:en för &lt;redirection_server>/r/test och kontrollera om build-numret och localhost returnerades av begäran.

1. Kontrollera konfigurationen reserveServer i filen serverConf.xml för spårningsservern. Den här konfigurationen bör vara i omdirigeringsläge.

   ```
   <redirection>
      <spareServer _operation="update" enabledIf="$(hostname)!='test-rt1'" id="1"
      url="http://test-rt1:8080"/>
      <spareServer _operation="insert" enabledIf="$(hostname)!='test-rt4'" id="4"
      url="http://test-rt4:8080"/>
      <spareServer _operation="insert" enabledIf="$(hostname)!='test-rt3'" id="3"
      url="http://test-rt3:8080"/>
      <spareServer _operation="insert" enabledIf="$(hostname)!=test-rt2'" id="2"
      url="http://test-rt2:8080"/>
   </redirection>
   ```

1. Kontrollera manuellt om filen &lt;deliveryID>.xml finns på datorn i katalogen .../nl6/var/&lt;instance_name>/redir/url/&lt;YYYY> (YYYY representerar leveransår).

1. Kontrollera manuellt om &lt;trackingUrlId> kan hittas i filen &lt;deliveryID>.xml.

1. Kontrollera manuellt förekomst av broadcastID i relaterad leverans-ID.

1. Kontrollera &lt;deliveryID>.xml-filbehörigheter i katalogen .../nl6/var/&lt;instance_name>/redir/url/year.

   De bör ha minst 644 behörigheter så att Apache kan läsa spårnings-URL:er för att omdirigera begärd länk.

+++

+++Uppdatera alternativet NmsTracking_Pointer

Följ de här stegen när du uppdaterar alternativet NmsTracking_Pointer:

1. Stoppa arbetsflödet för spårning.

1. Stoppa spårningsloggtjänsten.

1. Uppdatera alternativet NmsTracking_Pointer till önskat värde.

1. Starta om spårningstjänsten.

1. Starta om arbetsflödet för spårning.

+++

+++Spårning fungerar inte med en del WebMail

Du kan anpassa uppföljningsformeln för klickningar och ange en anpassad Adobe Analytics-spårningsformel.

Den sortens anpassning måste göras med försiktighet för att undvika att lägga till extra radmatade tecken. Alla radmatade tecken som finns utanför JavaScript-uttrycket finns i den slutliga formeln.

Den här typen av extra radbrytningstecken i spårnings-URL:en kommer att leda till problem i vissa webMail-filer (AOL, GMail osv.).

**Första exemplet:**

* Felaktig syntax

  ```
  <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe Analytics
  var pattern = new RegExp("(nl611\.test15|google\.com)", 'i')
  if( $(urlstring).match(pattern) && delivery.FCP == false )
  {
  %>
  &cid=<%= message.delivery.internalName %>&bid=<%= message.id.toString().toLowerCase() %><% } %>
  ```

* Korrigera syntax

  ```
  <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe Analytics
  var pattern = new RegExp("(nl611\.test15|google\.com)", 'i')
  if( $(urlstring).match(pattern) && delivery.FCP == false )
  {
  %>&cid=<%= message.delivery.internalName %>&bid=<%= message.id.toString().toLowerCase() %><% } %>
  ```

Du kan ersätta JavaScript-uttrycket med en fast sträng STRING för att förstå var den extra raden finns.

```
// Incorrect
STRING1
&cid=STRING2&bid=STRING3

// Correct
STRING1&cid=STRING2&bid=STRING3
```

**Andra exemplet**

* Felaktig syntax

  ```
  <%@ include option='NmsTracking_ClickFormula' %>
  <% // Parameters expected by Adobe Analytics
  var pattern = new RegExp("(vistaprint|entryUrl)", 'i')
  if( $(urlstring).match(pattern) && delivery.FCP == false )
  {%>&cid=<%= message.delivery.internalName%>&bid=<%= message.id.toString().toLowerCase()%>&SHPID=<%= message.recipient.factShopper.shopper_id %><% }
  
  %>
  ```

* Korrigera syntax

  ```
  <%@ include option='NmsTracking_ClickFormula' %><% // Parameters expected by Adobe Analytics
  var pattern = new RegExp("(vistaprint|entryUrl)", 'i')
  if( $(urlstring).match(pattern) && delivery.FCP == false )
  {%>&cid=<%= message.delivery.internalName%>&bid=<%= message.id.toString().toLowerCase()%>&SHPID=<%= message.recipient.factShopper.shopper_id %><% }
  
  %>
  ```

Du kan ersätta JavaScript-uttrycket med en fast sträng STRING för att förstå var den extra raden finns.

```
// Incorrect
STRING1&cid=STRING2&bid=STRING3&SHPID=STRING4

// Correct
STRING1&cid=STRING2&bid=STRING3&SHPID=STRING4
```

+++

+++Hämtningen av spårningsloggar är för långsam

När instansen inte hämtar loggar för direkt spårning utan från en fjärransluten Adobe Campaign Classic-server, hämtas loggarna via SOAP-anropet GetTrackingLogs, som definieras i RemoteTracking-schemat.

Med ett alternativ i filen serverConf.xml kan du ange antalet loggar som hämtas samtidigt med den här metoden: logCountPerRequest.

Standardvärdet för logCountPerRequest är 1000, det kan i vissa fall visa sig vara för litet. Godkända värden måste vara mellan 0 och 10 000.

+++

+++Spårningsloggar kunde inte länkas till mottagare

I Adobe Campaign Classic ska en målmappning vara unik i termer av mottagarschema jämfört med utsändnings-/spårningsloggscheman.

![](assets/tracking-troubleshooting.png)

Det är inte möjligt att använda flera målscheman med samma spårningsloggschema eftersom spårningsarbetsflödet inte kan avstämma data med mål-ID.

Om du inte vill använda den körklara målmappningen med nms:recipient rekommenderar vi följande metoder:

* Om du vill använda en anpassad målinriktningsdimension måste du skapa ett anpassat brushlog-/spårningsloggschema med nms:broadlog som mall (t.ex. nms:broadLogRcp, nms:broadLogSvc osv.).

* Om du vill använda OOB trackingLogRcp/broadLogRcp måste måldimensionen vara nms:recipient och filtreringsdimensionen kan vara ett anpassat schema.

+++
