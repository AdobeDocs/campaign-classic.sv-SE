---
title: Övervaka leverans
seo-title: Övervaka leverans
description: Övervaka leverans
seo-description: null
page-status-flag: never-activated
uuid: 7cb409eb-a01c-4b4d-bb62-760e0bafdc8a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
discoiquuid: 3aab3d47-76fd-4c68-add4-9c14240c936e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: fcedad248169f53e716f2bd8b1b141fbf1f4d189
workflow-type: tm+mt
source-wordcount: '2602'
ht-degree: 0%

---


# Övervaka leverans{#monitoring-a-delivery}

Kontrollpanelen för **leverans** är avgörande för att du ska kunna övervaka leveranser och eventuella problem som uppstår när meddelanden skickas.

**Relaterade ämnen:**

* [Om leveransfel](../../delivery/using/understanding-delivery-failures.md)
* [Om karantänhantering](../../delivery/using/understanding-quarantine-management.md)
* [Bästa praxis](https://helpx.adobe.com/campaign/kb/delivery-best-practices.html)
* [Hantera leveranser](../../delivery/using/about-deliverability.md)

## Kontrollpanel för leverans {#delivery-dashboard}

Om du vill visa information om en leverans redigerar du den, visar kontrollpanelen och klickar på de tillgängliga flikarna.

Det går inte längre att ändra tabbinnehållet när leveransen har skickats.

![](assets/s_ncs_user_del_details.png)

### Sammanfattning av leverans {#delivery-summary}

Fliken **[!UICONTROL Summary]** innehåller leveransegenskaperna: leveransstatus, kanal som används, information om avsändare, ämne, information om exekvering. Mer information finns i [Antal skickade](#number-of-messages-sent)meddelanden.

Med hjälp av **[!UICONTROL reports]** länken kan du titta på en uppsättning rapporter om leveransåtgärden: allmän leveransrapport, detaljerad rapport, leveransrapport, distribution av felmeddelanden, öppningsfrekvens, klick och transaktioner osv. Innehållet på den här fliken kan konfigureras enligt dina krav. For more information, refer to [this section](../../reporting/using/delivery-reports.md).

### Leveransloggar och historik {#delivery-logs-and-history}

Fliken visar en historik över förekomsterna i den här leveransen. **[!UICONTROL Delivery]** Den innehåller leveransloggarna, dvs. en lista över skickade meddelanden och deras status samt tillhörande meddelanden.

För en leverans kan du till exempel bara visa mottagare med en misslyckad leverans eller en adress i karantän. Det gör du genom att klicka på **[!UICONTROL Filters]** knappen och välja **[!UICONTROL By state]**. Välj sedan läget i listrutan.

![](assets/s_ncs_user_delivery_delivery_tab.png)

Olika statusvärden visas på [den här sidan](#delivery-statuses).

>[!NOTE]
>
>Med hjälp av **[!UICONTROL Display the mirror page for this message...]** länken kan du visa spegelsidan för innehållet i den leverans som har valts i listan i ett nytt fönster. Spegelsidan är bara tillgänglig för leveranser för vilka HTML-innehåll har definierats. Mer information finns i [Generera spegelsidan](../../delivery/using/sending-messages.md#generating-the-mirror-page).

### Spårningsloggar {#tracking-logs}

På **[!UICONTROL Tracking]** fliken visas spårningshistoriken för leveransen. På den här fliken visas spårningsdata för skickade meddelanden, d.v.s. alla URL:er som ska spåras av Adobe Campaign. Spårningsdata uppdateras varje timme.

>[!NOTE]
>
>Om spårning inte är aktiverat för en leverans visas inte den här fliken.

Spårningskonfigurationen utförs i rätt steg i leveransguiden. Se [Konfigurera spårade länkar](../../delivery/using/how-to-configure-tracked-links.md).

**[!UICONTROL Tracking]** data tolkas i leveransrapporterna. Se [det här avsnittet](../../reporting/using/delivery-reports.md).

![](assets/s_ncs_user_delivery_tracking_tab.png)

### Leveransgranskning {#delivery-audit-}

Fliken innehåller leveransloggen och alla meddelanden som rör korrektur **[!UICONTROL Audit]** . Med **[!UICONTROL Refresh]** knappen kan du uppdatera data. Använd knappen **[!UICONTROL Filters]** för att definiera ett filter för data.

Med särskilda ikoner kan du identifiera fel och varningar. Se [Analysera leveransen](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery).

På **[!UICONTROL Proofs]** underfliken kan du visa en lista med de korrektur som har skickats.

![](assets/s_ncs_user_delivery_log_tab.png)

Du kan ändra den information som visas i det här fönstret (och den på **[!UICONTROL Delivery]** - och **[!UICONTROL Tracking]** -flikarna) genom att markera kolumnerna som ska visas. Det gör du genom att klicka på **[!UICONTROL Configure list]** ikonen i det nedre högra hörnet. Mer information om hur du konfigurerar listvisning finns i [det här avsnittet](../../platform/using/adobe-campaign-workspace.md#configuring-lists).

### Synkronisering av kontrollpanel för leverans {#delivery-dashboard-synchronization}

Från kontrollpanelen för leverans vill du kontrollera de bearbetade meddelandena och leveransloggarna för att vara säker på att leveransen har skickats.

Vissa indikatorer eller status kan vara felaktiga eller inte aktuella. Lösningen kan vara:

* Om leveransstatusen är felaktig kontrollerar du att alla nödvändiga godkännanden har gjorts för leveransen eller att arbetsflödena **[!UICONTROL operationMgt]** och **[!UICONTROL deliveryMgt]** körs utan fel. Detta kan också bero på leveransen med en tillhörighet som inte har konfigurerats på den sändande instansen.
* Om leveransindikatorerna fortfarande är noll och du använder en mellanleverantörskonfiguration bör du kontrollera det **[!UICONTROL Mid-sourcing (delivery counters)]** tekniska arbetsflödet. Starta om det inte har status **[!UICONTROL Started]**. Sedan kan du försöka beräkna om indikatorerna genom att högerklicka på leveransen i Adobe Campaign Explorer och välja **[!UICONTROL Actions]** > **[!UICONTROL Recompute delivery and tracking indicators]**. Mer information om spårningsindikatorer finns i det här [avsnittet](../../reporting/using/delivery-reports.md#tracking-indicators).
* Om leveransräknaren inte stämmer överens med leveransräknaren kan du försöka beräkna om indikatorerna genom att högerklicka på leveransen i Adobe Campaign Explorer och välja **[!UICONTROL Actions]** > **[!UICONTROL Recompute delivery and tracking indicators]** för att synkronisera om. Mer information om spårningsindikatorer finns i det här [avsnittet](../../reporting/using/delivery-reports.md#tracking-indicators).
* Om leveransräknaren inte är uppdaterad för medelstora distributioner kontrollerar du att det tekniska arbetsflödet körs. **[!UICONTROL Mid-Sourcing (Delivery counters)]** Mer information finns på den här [sidan](../../installation/using/mid-sourcing-deployment.md).

Du kan också spåra leveranser med olika rapporter via kontrollpanelen för leverans. For more on this, refer to this [section](../../reporting/using/delivery-reports.md).

## Prestandaproblem {#performance-issues}

### Checklista {#checklist-}

Om leveransresultaten är felaktiga kan du kontrollera:

* **Leveransens** storlek: Stora leveranser kan ta längre tid att slutföra. MTA-underordnade är konfigurerade att hantera en standardbatchstorlek, som fungerar för de flesta instanser, men som måste kontrolleras när leveranserna är konstant långsamma.
* **Målet för leveransen**: Förbud mot leveransprestanda påverkas av mjuka studsfel som hanteras enligt konfigurationen för nya försök. Ju fler fel, desto fler försök.
* **Den totala plattformsbelastningen**: När flera stora leveranser skickas kan den övergripande plattformen påverkas. Du kan även kontrollera IP-adressens anseende och leveransproblem. Mer information finns i Adobe Campaign [Deliverability best practices guide](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) och på [den här sidan](../../delivery/using/about-deliverability.md).

Plattforms- och databasunderhåll kan också påverka leveransresultaten. For more on this, refer to [this page](../../production/using/database-performances.md).

### Långsamma leveranser {#slow-deliveries}

När du har klickat på **[!UICONTROL Send]** knappen verkar leveransen ta längre tid än vanligt. Detta kan bero på olika element:

* Vissa e-postleverantörer kan ha svartlistat dina IP-adresser. I så fall kontrollerar du dina utskick och läser [detta för att komma igång](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) .
* Leveransen kan vara för stor för att kunna bearbetas snabbt. Detta kan inträffa vid hög JavaScript-anpassning eller om leveransen väger mer än 60 kbit/s. Mer information om riktlinjer för innehåll finns i Adobe Campaign [Delivery best practices](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html) .
* Begränsning kan ha inträffat i Adobe Campaign MTA. Detta orsakas av:

   * Väntade meddelanden (**[!UICONTROL quotas met]** meddelande): Kvoter som deklarerats av de deklarativa MX-regler som definierats i Campaign har uppfyllts. Mer information om det här meddelandet finns på [den här sidan](https://helpx.adobe.com/campaign/kb/acc-deliverability-faq.html#FAQ). Mer information om MX-regler finns på [den här sidan](../../delivery/using/technical-recommendations.md#mx-rules).
   * Väntade meddelanden (**[!UICONTROL dynamic flow control]** meddelande): Kampanj-MTA har stött på fel vid försök att leverera meddelanden för en viss Internet-leverantör, vilket gör att det tar för lång tid att undvika en alltför hög feltäthet och därmed riskerar att bli svartlistad.

* Ett systemproblem kan förhindra servrar från att samverka: detta kan göra hela sändningsprocessen långsammare. Kontrollera servrarna för att se till att det inte finns några minnes- eller resursproblem som kan påverka Campaign när personaliseringsdata hämtas till exempel.

### Bästa tillvägagångssätt för prestanda {#best-practices-performance}

* Behåll inte leveranser i felaktigt tillstånd för instansen eftersom detta bevarar tillfälliga tabeller och påverkar prestandan.

* Ta bort leveranser som inte längre behövs.

* Inaktiva mottagare de senaste 12 månaderna som ska tas bort från databasen för att upprätthålla adresskvaliteten.

* Försök inte schemalägga stora leveranser tillsammans. Det finns ett mellanrum på 5-10 minuter för att sprida belastningen jämnt över systemet. Samordna schemaläggningen av leveranser med övriga medlemmar i teamet för att säkerställa bästa möjliga prestanda. När marknadsföringsservern hanterar många olika uppgifter samtidigt kan prestandan försämras.

* Håll storleken på era e-postmeddelanden så låg som möjligt. Den rekommenderade maximala storleken för ett e-postmeddelande är cirka 35 kB. Storleken på en e-postleverans genererar en viss volym på de avsändande servrarna.

* För stora leveranser, som leveranser till över en miljon mottagare, behövs utrymme i utskicksköerna. Detta är inget problem för servern, men om det kombineras med dussintals andra stora leveranser som alla går ut samtidigt kan det medföra en fördröjning.

* Personalisering i e-postmeddelanden hämtar data från databasen för varje mottagare. Om det finns många personaliseringselement ökar detta mängden data som behövs för att förbereda leveransen.

* Indexadresser. För att optimera prestanda för SQL-frågor som används i programmet kan ett index deklareras från huvudelementet i dataschemat.

>[!NOTE]
>
>Internetleverantörer inaktiverar adresser efter en tids inaktivitet. Avvisade meddelanden skickas till avsändare för att informera dem om den nya statusen.

## Leveransstatus {#delivery-statuses}

När du skickar en leverans kan du stöta på följande status på kontrollpanelen för leverans:

<table> 
 <thead> 
  <tr> 
   <th> Status<br /> </th> 
   <th> Definitioner och lösningar<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Ej tillämpligt<br /> </td> 
   <td> Leveransen har tagits med i beräkningen av servern (MTA) men har inte bearbetats.<br /> </td> 
  </tr> 
  <tr> 
   <td> Ignorerad<br /> </td> 
   <td> Leveransen skickades inte till mottagaren på grund av ett fel med hans adress. Den var antingen svartlistad, i karantän, inte tillhandahållen eller en dubblett. <br /> </td> 
  </tr> 
  <tr> 
   <td> Skickat<br /> </td> 
   <td> Leveransen skickades korrekt till meddelandeleverantören (men mottagaren tog inte nödvändigtvis emot den).<br /> </td> 
  </tr> 
  <tr> 
   <td> Misslyckades<br /> </td> 
   <td> Leveransen kunde inte nå mottagaren på grund av en ogiltig adress eller en fullständig inkorg, till exempel. Den kan även länkas till ett problem med personaliseringsblock eftersom de kan generera fel när scheman inte matchar leveransmappningen. Se <a href="#failed-status" target="_blank">Misslyckad status</a><br /> </td> 
  </tr> 
  <tr> 
   <td> Tjänsteleverantören har tagit hänsyn till<br /> </td> 
   <td> SMS-tjänstleverantören tog emot leveransen.<br /> </td> 
  </tr> 
  <tr> 
   <td> Mottaget på mobilen<br /> </td> 
   <td> Mottagaren tog emot SMS på sin mobila enhet.<br /> </td> 
  </tr> 
  <tr> 
   <td> Väntande<br /> </td> 
   <td> Leveransen är klar att skickas och kommer att bearbetas av leveransservern (MTA). Se <a href="#pending-status" target="_blank">Väntande status</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> Leveransen har avbrutits<br /> </td> 
   <td> Leveransen avbröts av en operator.<br /> </td> 
  </tr> 
  <tr> 
   <td> Förberedd<br /> </td> 
   <td> Mellanliggande status används endast för externa anslutningar som mobilkanalen. Den följer statusen Väntande och är den externa kopplingen som avgör följande status.<br /> </td> 
  </tr> 
  <tr> 
   <td> Skickat till tjänsteleverantören<br /> </td> 
   <td> Leveransen skickades till SMS-tjänstleverantören men har inte tagits emot än.<br /> </td> 
  </tr> 
 </tbody> 
</table>

Om du vill veta hur du kan optimera leveransen av Adobe Campaign-e-postmeddelanden kan du läsa Adobe Campaign [Deliverability best practices guide](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) och [den här sidan](../../delivery/using/about-deliverability.md).

### Väntande status {#pending-status}

När du har bekräftat leveransen ser du att leveransstatus är **[!UICONTROL Pending]**. Den här statusen innebär att körningsprocessen väntar på att vissa resurser ska vara tillgängliga.

Statusen **[!UICONTROL Pending]** kan först innebära att leveransen har schemalagts och väntar tills det angivna datumet. Mer information finns i avsnittet [Leveransplanering](../../delivery/using/steps-sending-the-delivery.md#scheduling-the-delivery-sending) .

Om leveransen inte skickas och dess status kvarstår **[!UICONTROL Pending]** kan det bero på:

* MTA-agenten (Message Transfert Agent) som kör moduler och processer på leveransservern och som hanterar e-postutskick kanske inte har startats eller behöver startas om. Gör så här om du vill kontrollera detta och starta modulen om det behövs:

   * Kontrollera att dina `mta@<instance>` moduler har startats på dina MTA-servrar.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (X.Y.Z YY.R build nnnn@SHA1) of DD/MM/YYYY
   [...]
   mta@<INSTANCENAME> (9268) - 23.0 Mb
   [...]
   ```

   * Om MTA inte finns med i listan startar du det med följande kommando:

   ```
   nlserver start mta@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >Ersätt `<INSTANCENAME>` med namnet på din instans (produktion, utveckling osv.). Instansnamnet identifieras via konfigurationsfilerna: `[path of application]nl6/conf/config-<INSTANCENAME>.xml`

* Leveransen kan ha en tillhörighet som inte har konfigurerats på den sändande servern. I det här fallet kontrollerar du konfigurationen för trafikhanteringen (IP-tillhörighet) och använder fältet **[!UICONTROL Managing affinities with IP addresses]** för att länka leveranser till den MTA som hanterar tillhörigheten. For more information on affinities, refer to [this section](../../installation/using/configuring-campaign-server.md#personalizing-delivery-parameters).
* När leveransförberedelsen är väntande kan det finnas för många kampanjer som körs, vilket blockerar statusuppdateringen av leveransen. Du löser det genom att gå till **[!UICONTROL Options]** och öka värdet för **[!UICONTROL NmsOperation_LimitConcurrency]** (standardvärdet är 10). Kör inte fler kampanjer än det värde som tilldelats det här specifika alternativet.

### Misslyckad status {#failed-status}

Om status för en e-postleverans är **[!UICONTROL Failed]** kan den länkas till ett problem med personaliseringsblock. Personaliseringsblock i en leverans kan generera fel när scheman inte matchar leveransmappningen, till exempel.

Leveransloggar är viktiga för att lära sig varför en leverans misslyckades. Här följer möjliga fel som du kan identifiera från leveransloggar:

* Om det inte går att nå mottagarmeddelanden med felet &quot;Oåtkomligt&quot;: **Fel vid kompilering av skript &#39;content htmlContent&#39; rad X:`[table]`är inte definierad. JavaScript: fel vid utvärdering av skript &#39;content htmlContent**&#39; är orsaken till problemet nästan alltid en personalisering inom HTML som försöker anropa en tabell eller ett fält som inte har definierats eller mappats i den överordnade målsättningen eller i leveransens målmappning.

   För att rätta till detta måste arbetsflödes- och leveransinnehållet granskas för att avgöra specifikt vilken personalisering som försöker anropa tabellen i fråga och om tabellen kan mappas eller inte. Därifrån är det antingen vägen till lösningen att ta bort anropet till den här tabellen i HTML-koden eller att åtgärda mappningen till leveransen.

* I distributionsmodellen där flera leverantörer är installerade kan följande meddelande visas i leveransloggarna: **Ett fel uppstod när metoden AppendDeliveryPart skulle anropas på mittkällservern: &#39;Kommunikationsfel med servern: kontrollera att den här är korrekt konfigurerad. Kod HTTP 408 &#39;Tjänsten är inte tillgänglig för tillfället&#39;**.

   Orsaken är kopplad till prestandaproblem. Det innebär att marknadsinstansen lägger för mycket tid på att bygga upp data innan den skickas till servern med mellanlagring.

   För att lösa detta rekommenderar vi att du utför ett vakuum och indexerar om databasen. Mer information om databasunderhåll finns i [det här avsnittet](../../production/using/recommendations.md).

   Du bör också starta om alla arbetsflöden med en schemalagd aktivitet och alla arbetsflöden med statusen misslyckades. Se [det här avsnittet](../../workflow/using/scheduler.md).

* När en leverans misslyckas kan följande fel visas i leveransloggarna: **DLV-XXXX Antalet förberedda meddelanden (123) är större än antalet meddelanden som ska skickas (111). Kontakta supporten.**

   Vanligtvis innebär det här felet att det finns ett anpassningsfält eller -block i e-postmeddelandet som har fler än ett värde för mottagaren. Ett personaliseringsblock används och hämtar mer än en post för en viss mottagare.

   Du löser detta genom att kontrollera vilka personaliseringsdata som används och sedan kontrollera målet för mottagare som har fler än en post för något av dessa fält. Du kan också använda en aktivitet i målarbetsflödet före leveransaktiviteten för att kontrollera att det bara finns ett personaliseringsfält åt gången. **[!UICONTROL Deduplication]** Mer information om borttagning av dubbletter finns på [den här sidan](../../workflow/using/deduplication.md).

* En del leveranser kan misslyckas med felet &quot;Onåbar&quot; som anger: &quot;Studsa inkommande e-post (regeln &quot;Auto_responses&quot; har matchat detta studs). Det innebär att leveransen lyckades, men Adobe Campaign fick ett automatiskt svar från mottagaren (t.ex. ett frånvaromeddelande) som matchade de inkommande e-postreglerna för autosvar. Adobe Campaign ignorerar e-postmeddelandet om automatiskt svar och mottagarens adress skickas inte till karantän.

**Relaterade ämnen:**

* [Leveransloggar och historik](#delivery-logs-and-history)
* [Om leveransfel](../../delivery/using/understanding-delivery-failures.md)
* [Typ av leveransfel och orsaker](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)

## Antal skickade meddelanden {#number-of-messages-sent}

Du kan komma åt leveranser från leveranslistan via trädnoden **[!UICONTROL Campaign Management > Deliveries]** .

Som standard innehåller listan över leveranser namnen och statusvärdena för leveranser som skapas i den valda noden. Här visas även antalet meddelanden som ska skickas, bearbetas och skickas.

* Antalet **[!UICONTROL Messages to send]** motsvarar antalet mottagare som valts efter analys och före leverans.
* Antalet meddelanden i **[!UICONTROL Success]** kolumnen motsvarar antalet meddelanden som har skickats av servern och tagits emot av mottagarna.
* Antalet **[!UICONTROL Processed]** meddelanden motsvarar antalet mottagna meddelanden plus antalet meddelanden med fel.

På kontrollpanelen för leverans kan du spåra antalet skickade meddelanden.

>[!NOTE]
>
>Vid stora leveranser kanske du vill uppdatera dessa värden. Det gör du genom att markera leveransen i fråga och sedan högerklicka på den. Välj **[!UICONTROL Action > Recompute delivery and tracking indicators...]** och använd sedan guiden för att uppdatera informationen.

## Schemalagda leveranser {#scheduled-deliveries-}

Om leveranser inte utförs vid exakt schemalagt datum kan det bero på en skillnad mellan serverns tidszon. Mellankällinstansen och produktionsinstansen kan finnas i olika tidszoner.

Om exempelvis mellanleverantörsinstansen ligger i Brisbane-tidszonen och produktionsinstansen ligger i Darwin-tidszonen ligger båda tidszonerna en halvtimme från varandra, skulle du i granskningsloggen tydligt se att om leveransen är planerad till produktion kl. 11.56 skulle samma leverans som är planerad till mitten vara kl. 12.26, vilket har en skillnad på en halvtimme.
