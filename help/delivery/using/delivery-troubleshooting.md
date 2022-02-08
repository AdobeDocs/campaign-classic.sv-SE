---
product: campaign
title: Felsökning av leverans
description: Lär dig mer om leveransresultat och hur du felsöker problem med leveransövervakning
exl-id: 37b1d7fb-7ceb-4647-9aac-c8a80495c5bf
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '791'
ht-degree: 1%

---

# Felsökning av leverans {#delivery-troubleshooting}

![](../../assets/common.svg)

I det här avsnittet beskrivs vanliga problem som du kan stöta på när du skickar leveranser och hur du felsöker dem.

Se även till att du följer de bästa metoderna och checklistorna som finns i [den här sidan](delivery-performances.md) för att säkerställa att leveranserna fungerar bra.

**Relaterade ämnen:**

* [Leveransstatus](delivery-statuses.md)
* [Kontrollpanel för leverans](delivery-dashboard.md)
* [Förstå leveransfel](understanding-delivery-failures.md)

## Långsamma leveranser {#slow-deliveries}

När du klickat på **[!UICONTROL Send]** verkar leveransen ta längre tid än vanligt. Detta kan bero på olika element:

* Vissa e-postleverantörer kan ha lagt till dina IP-adresser i en blockeringslista. I så fall bör du kontrollera dina utskick och läsa [det här avsnittet](about-deliverability.md).

* Leveransen kan vara för stor för att kunna bearbetas snabbt. Detta kan inträffa med hög JavaScript-anpassning eller om leveransen väger mer än 60 kbit. Se Adobe Campaign [Bästa praxis](delivery-best-practices.md) om du vill veta mer om riktlinjer för innehåll.

* Begränsning kan ha inträffat i Adobe Campaign MTA. Detta orsakas av:

   * Väntade meddelanden (**[!UICONTROL quotas met]** meddelande): Kvoter som deklarerats av de deklarativa MX-regler som definierats i Campaign har uppfyllts. Mer information om det här meddelandet finns i [den här sidan](deliverability-faq.md). Mer information om MX-regler finns i [det här avsnittet](../../installation/using/email-deliverability.md#about-mx-rules).

   * Väntade meddelanden (**[!UICONTROL dynamic flow control]** meddelande): Kampanj-MTA har påträffat fel vid försök att leverera meddelanden för en viss Internet-leverantör, vilket gör att det tar för lång tid att undvika en alltför hög feltäthet och därmed riskerar att blocklist.

* Ett systemproblem kan förhindra servrar från att samverka: detta kan göra hela sändningsprocessen långsammare. Kontrollera servrarna för att se till att det inte finns några minnes- eller resursproblem som kan påverka Campaign när personaliseringsdata hämtas till exempel.

## Schemalagda leveranser {#scheduled-deliveries-}

Om leveranser inte utförs vid exakt schemalagt datum kan det bero på en skillnad mellan serverns tidszon. Mellankällinstansen och produktionsinstansen kan finnas i olika tidszoner.

Om exempelvis mellanleverantörsinstansen ligger i Brisbane-tidszonen och produktionsinstansen ligger i Darwin-tidszonen ligger båda tidszonerna en halvtimme från varandra, skulle du i granskningsloggen tydligt se att om leveransen är planerad till produktion kl. 11.56 skulle samma leverans som är planerad till mitten vara kl. 12.26, vilket har en skillnad på en halvtimme.

## Misslyckad status {#failed-status}

Om status för en e-postleverans är **[!UICONTROL Failed]**, kan den länkas till ett problem med personaliseringsblock. Personaliseringsblock i en leverans kan generera fel när scheman inte matchar leveransmappningen, till exempel.

Leveransloggar är viktiga för att lära sig varför en leverans misslyckades. Här följer möjliga fel som du kan identifiera från leveransloggar:

* Mottagarmeddelanden misslyckas med felet &quot;Onåbar&quot; som anger:

   ```
   Error while compiling script 'content htmlContent' line X: `[table]` is not defined. JavaScript: error while evaluating script 'content htmlContent
   ```

   Orsaken till problemet är nästan alltid en personalisering inom HTML som försöker anropa ett register eller fält som inte har definierats eller mappats i den överordnade målsättningen eller i leveransens målmappning.

   För att rätta till detta måste arbetsflödes- och leveransinnehållet granskas för att avgöra specifikt vilken personalisering som försöker anropa tabellen i fråga och om tabellen kan mappas eller inte. Därifrån kan man antingen ta bort anropet till den här tabellen i HTML eller åtgärda mappningen till leveransen genom att gå mot en lösning.

* I distributionsmodellen där flera leverantörer är installerade kan följande meddelande visas i leveransloggarna:

   ```
   Error during the call of method 'AppendDeliveryPart' on the mid sourcing server: 'Communication error with the server: please check this one is correctly configured. Code HTTP 408 'Service temporarily unavailable'.
   ```

   Orsaken är kopplad till prestandaproblem. Det innebär att marknadsinstansen lägger för mycket tid på att bygga upp data innan den skickas till servern med mellanlagring.

   För att lösa detta rekommenderar vi att du utför ett vakuum och indexerar om databasen. Mer information om databasunderhåll finns i [det här avsnittet](../../production/using/recommendations.md).

   Du bör också starta om alla arbetsflöden med en schemalagd aktivitet och alla arbetsflöden med statusen misslyckades. Se [det här avsnittet](../../workflow/using/scheduler.md).

* När en leverans misslyckas kan följande fel visas i leveransloggarna:

   ```
   DLV-XXXX The count of message prepared (123) is greater than the number of messages to send (111). Please contact support.
   ```

   Vanligtvis innebär det här felet att det finns ett anpassningsfält eller -block i e-postmeddelandet som har fler än ett värde för mottagaren. Ett personaliseringsblock används och hämtar mer än en post för en viss mottagare.

   Du löser detta genom att kontrollera vilka personaliseringsdata som används och sedan kontrollera målet för mottagare som har fler än en post för något av dessa fält. Du kan också använda en **[!UICONTROL Deduplication]** aktiviteten i målarbetsflödet före leveransaktiviteten för att kontrollera att det bara finns ett personaliseringsfält åt gången. Mer information om borttagning av dubbletter finns i [den här sidan](../../workflow/using/deduplication.md).

* En del leveranser kan misslyckas med felet &quot;Onåbar&quot; som anger:

   ```
   Inbound email bounce (rule 'Auto_replies' has matched this bounce).
   ```

   Det innebär att leveransen lyckades, men Adobe Campaign fick ett automatiskt svar från mottagaren (t.ex. ett frånvaromeddelande) som matchade e-postreglerna för inkommande e-post för &#39;Auto_responses&#39;.

   E-postadressen för automatiskt svar ignoreras av Adobe Campaign och mottagarens adress skickas inte till karantän.
