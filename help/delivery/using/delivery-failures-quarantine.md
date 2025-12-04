---
product: campaign
title: Leveransfel och karantänhantering
description: Lär dig mer om leveransfel och hantera karantäner i Campaign Classic v7
feature: Monitoring, Deliverability
role: User
exl-id: 86c7169a-2c71-4c43-8a1a-f39871b29856
source-git-commit: 2ebae2b84741bf26dd44c872702dbf3b0ebfc453
workflow-type: tm+mt
source-wordcount: '1559'
ht-degree: 1%

---

# Leveransfel och karantänhantering {#delivery-failures-quarantine}

>[!NOTE]
>
>Omfattande vägledning om leveransfel och karantänhantering finns i dokumentationen för Campaign v8. Det här innehållet gäller både Campaign Classic v7- och Campaign v8-användare:
>
>* [Om leveransfel](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} - omfattar feltyper, felorsaker, synkrona/asynkrona fel, felhantering och felsökning
>* [Karantänhantering](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"} - Omfattar karantän jämfört med blockeringslista, tröskelvärden för mjuka fel, karantänrapporter och adressborttagning
>
>Den här sidan dokumenterar **Campaign Classic v7-specifik konfiguration** för hantering av studsade e-postmeddelanden och karantän i hybriddistributioner och på plats.

## Förstå leveransfel

Vanliga koncept, feltyper och felsökningsanvisningar för leveransfel finns i [dokumentationen om leveransfel för Campaign v8 ](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}.

## Konfigurera studsmeddelanden {#bounce-mail-config}

Följande konfigurationsalternativ är tillgängliga för **hybriddistributioner i Campaign Classic v7** för hantering av studentpostbearbetning.

### Konfiguration av studentpostlåda {#bounce-mailbox-configuration}

Konfigurationen av studspostlådan för lokala installationer beskrivs i [det här avsnittet](../../installation/using/deploying-an-instance.md#managing-bounced-emails).

Asynkrona felmeddelanden samlas in av Adobe Campaign-plattformen via studspostlådan och kvalificeras av inMail-processen för att utöka listan med regler för e-posthantering.

>[!NOTE]
>
>För användare av hanterade molntjänster i Campaign v8 utförs och hanteras studspostlådans konfiguration av Adobe. Ingen konfiguration krävs.

### Hantering av studentkvalificering {#bounce-mail-qualification-management}

För lokala installationer och värdbaserade/hybridinstallationer som använder den äldre Campaign MTA får Adobe Campaign-leveransservern ett felmeddelande från meddelandeservern eller fjärr-DNS-servern när leveransen av ett e-postmeddelande misslyckas. Listan med fel består av strängar som finns i meddelandet som returneras av fjärrservern. Feltyper och orsaker tilldelas till varje felmeddelande.

Den här listan är tillgänglig via noden **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Delivery log qualification]**. Det innehåller alla regler som Adobe Campaign använder för att kvalificera leveransfel. Den är inte uttömmande och uppdateras regelbundet av Adobe Campaign och kan även hanteras av användaren.

![](assets/tech_quarant_rules_qualif.png)

Meddelandet som returneras av fjärrservern vid den första förekomsten av den här feltypen visas i kolumnen **[!UICONTROL First text]** i tabellen **[!UICONTROL Delivery log qualification]**. Om den här kolumnen inte visas klickar du på knappen **[!UICONTROL Configure list]** längst ned till höger i listan för att markera den.

![](assets/tech_quarant_rules_qualif_text.png)

Adobe Campaign filtrerar det här meddelandet för att ta bort variabelinnehållet (t.ex. ID:n, datum, e-postadresser, telefonnummer osv.) och visar det filtrerade resultatet i kolumnen **[!UICONTROL Text]**. Variablerna ersätts med **`#xxx#`**, förutom adresser som ersätts med **`*`**.

Med den här processen kan du sammanföra alla fel av samma typ och undvika flera poster för liknande fel i tabellen för leveransloggskvalificering.

>[!NOTE]
>
>Fältet **[!UICONTROL Number of occurrences]** visar antalet förekomster av meddelandet i listan. Den är begränsad till 100 000 förekomster. Du kan redigera fältet om du till exempel vill återställa det.

Studsade e-postmeddelanden kan ha följande kvalificeringsstatus:

* **[!UICONTROL To qualify]**: Det gick inte att kvalificera studsmeddelandet. Kvalificering måste tilldelas slutkundsteamet för att garantera effektiv plattformsleverans. Så länge den inte är kvalificerad används studentposten inte för att utöka listan över regler för e-posthantering.
* **[!UICONTROL Keep]**: studsmeddelandet har kvalificerats och kommer att användas av arbetsflödet **Uppdatera för leverans** som ska jämföras med befintliga regler för e-posthantering och berika listan.
* **[!UICONTROL Ignore]**: studsmeddelandet ignoreras av Campaign MTA, vilket innebär att den här studsen aldrig kommer att leda till att mottagarens adress sätts i karantän. Den kommer inte att användas av arbetsflödet **Uppdatera för levererbarhet** och kommer inte att skickas till klientinstanser.

![](assets/deliverability_qualif_status.png)

>[!NOTE]
>
>Om en Internet-leverantör skulle råka ut för ett avbrott markeras e-post som skickas via Campaign felaktigt som studsar. För att korrigera detta måste du uppdatera studskompetens. Mer information finns på [den här sidan](update-bounce-qualification.md).

### Regelkonfiguration för e-posthantering {#email-management-rules}

E-postregler nås via noden **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]**. Regler för e-posthantering visas i fönstrets nedre del.

![](assets/tech_quarant_rules.png)

>[!NOTE]
>
>Standardparametrarna för plattformen konfigureras i distributionsguiden. Mer information finns i [det här avsnittet](../../installation/using/deploying-an-instance.md).

Standardreglerna är följande:

>[!IMPORTANT]
>
>* Leveransservern måste startas om om parametrarna har ändrats.
>* Ändringen eller skapandet av hanteringsregler är endast till för expertanvändare.

#### Inkommande e-post {#inbound-email}

Dessa regler innehåller strängar som kan returneras av fjärrservrar och som gör att du kan kvalificera felet (**Hård**, **Mjuk** eller **Ignorerad**).

När ett e-postmeddelande misslyckas returnerar fjärrservern ett studsmeddelande till den adress som anges i plattformsparametrarna. Adobe Campaign jämför innehållet i varje studsmeddelande med strängarna i regellistan och tilldelar det sedan en av de tre feltyperna.

>[!NOTE]
>
>Användaren kan skapa egna regler. När du importerar ett paket och uppdaterar data via arbetsflödet **Uppdatera för leverans**, skrivs de regler som användaren har skapat över.

Mer information om studskompetens finns i [det här avsnittet](#bounce-mail-qualification-management).

#### Domänhantering {#domain-management}

För lokala installationer tillämpar MTA en enda **domänhanteringsregel** på alla domäner.

<!--![](assets/tech_quarant_domain_rules_02.png)-->

* Du kan välja om du vill aktivera vissa identifieringsstandarder och krypteringsnycklar eller inte för att kontrollera domännamnet, till exempel **Avsändarens ID**, **Domännycklar**, **DKIM** och **S/MIME**.
* Med parametrarna **SMTP-relä** kan du konfigurera IP-adressen och porten för en reläserver för en viss domän. Mer information om detta finns i [det här avsnittet](../../installation/using/configuring-campaign-server.md#smtp-relay).

Om dina meddelanden visar **[!UICONTROL on behalf of]** i avsändaradressen ska du se till att inte signera e-postmeddelanden med **avsändar-ID**, som är den inaktuella autentiseringsstandarden för e-post från Microsoft. Om alternativet **[!UICONTROL Sender ID]** är aktiverat avmarkerar du motsvarande ruta och kontaktar [Adobe kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). Leveransen påverkas inte.

#### MX-hantering {#mx-management}

För lokala installationer används MX-hanteringsregler för att reglera flödet av utgående e-post för en specifik domän.

<!--![](assets/tech_quarant_domain_rules_01.png)-->

Dessa regler är tillgängliga i distributionsguiden och kan anpassas:

* **[!UICONTROL MX Management]**: Den här regeln används för att styra flödet av utgående e-post för en domän. Där samplas studsmeddelanden och blockeringar som skickas där så är lämpligt.

* **[!UICONTROL Period]**: den tidsram under vilken meddelanden stryps eller blockeras.

* **[!UICONTROL Limit]**: maximalt antal meddelanden som tillåts per tidsperiod.

* **[!UICONTROL Type]**: Feltypen (hård, mjuk eller ignorerad) som används för att fastställa sändningsbeteendet. Mer information om feltypsdefinitioner finns i [Campaign v8-dokumentationen](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}.

Mer information om MX-hantering finns i [det här avsnittet](../../installation/using/email-deliverability.md#about-mx-rules).

>[!NOTE]
>
>För användare av hanterade molntjänster i Campaign v8 hanteras MX-regler och e-postflödeshantering av Adobe som en del av den hanterade infrastrukturen. Kontakta Adobe kundtjänst om du behöver justera MX-inställningarna för specifika användningsfall.

## Karantänhantering {#quarantine-management}

Omfattande riktlinjer för karantänhantering finns i [dokumentationen för karantänhantering för Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"}.

## Konfiguration av karantän {#quarantine-config}

Följande konfigurationsalternativ är tillgängliga för **hybriddistributioner i Campaign Classic v7** för att anpassa karantänbeteendet.

### Konfiguration av tröskelvärde för mjukt fel {#soft-error-threshold}

För lokala installationer som använder det gamla Campaign MTA kan du ändra antalet fel och perioden mellan två fel innan en adress sätts i karantän.

Så här konfigurerar du dessa inställningar:

1. Öppna distributionsguiden från **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Deployment wizard]**
2. Navigera till **[!UICONTROL Email channel]** > **[!UICONTROL Advanced parameters]**
3. Konfigurera:
   * **Antal fel**: Maximalt antal mjuka fel innan en adress sätts i karantän (standard: 5)
   * **Period mellan två signifikanta fel**: Tidsfönstret (i sekunder) för felräkning (standard: 86 400 sekunder = 1 dag)

När felräknaren når tröskelvärdet sätts adressen i karantän. Om det senaste allvarliga felet inträffade för mer än 10 dagar sedan initieras felräknaren om.

Mer information finns på [den här sidan](communication-channels.md) under **Leveranssändning** > **Konfigurera återförsök**.

>[!NOTE]
>
>För användare av hanterade molntjänster i Campaign v8 hanteras inställningar för nya försök och feltrösklar av Adobe utifrån IP-prestanda och domänens anseende. Ingen konfiguration krävs.

### Arbetsflöde för databasrensning {#database-cleanup-workflow}

För lokala installationer tar det tekniska arbetsflödet **[!UICONTROL Database cleanup]** automatiskt bort adresser i karantän som matchar specifika villkor.

Få åtkomst till det här arbetsflödet från **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]** > **[!UICONTROL Database cleanup]**.

Arbetsflödet tar bort adresser från karantän i följande fall:

* Adresser i statusen **[!UICONTROL With errors]** efter en slutförd leverans
* Adresser i statusen **[!UICONTROL With errors]** om den senaste mjuka studsen inträffade för mer än 10 dagar sedan
* Adresser i statusen **[!UICONTROL With errors]** med felet **[!UICONTROL Mailbox full]** efter 30 dagar

Se till att arbetsflödet körs regelbundet (rekommenderas: dagligen) för att upprätthålla karantänlistans hygien.

Mer information om databasrensning finns i [det här avsnittet](../../production/using/database-cleanup-workflow.md).

>[!NOTE]
>
>För användare av hanterade molntjänster i Campaign v8 övervakas och hanteras arbetsflödet för databasrensning av Adobe.

### Karantänsdetaljer för push-meddelanden {#push-quarantine-specifics}

För Campaign Classic v7 följer karantänmekanismen för push-meddelanden med kanalspecifika beteenden.

För push-meddelanden för **iOS** och **Android** använder karantänmekanismen enhetstoken i stället för e-postadresser. När ett mobilprogram avinstalleras eller installeras om placeras den associerade token i karantän.

Detaljerad information om karantänscenarier för push-meddelanden (iOS- och Android-feltyper, återförsöksbeteende osv.) finns i [Om leveransfel](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} -dokumentationen som innehåller omfattande feltyper för push-meddelanden.

### Specifikationer för SMS-karantän {#sms-quarantine-specifics}

För Campaign Classic v7 följer SMS-karantäner den allmänna karantänmekanismen med vissa kanalspecifika beteenden som är relaterade till telefonnummer i stället för e-postadresser.

SMS-karantänmekanismen varierar beroende på vilken koppling som används:

* **Standard SMPP-anslutningar**: Felkvalificeringsregler som definieras i **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Delivery log qualification]** gäller för SMS-leveranser.

* **Utökad generisk SMPP-anslutning**: Felhantering hanteras på olika sätt med reguljära uttryck (regex) för att tolka SR-meddelanden som returneras av SMSC-providern.

Detaljerad information om SMS-karantänscenarier och feltyper finns i [Förstå leveransfel](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} -dokumentationen som innehåller omfattande tabeller för feltyper av SMS.

## Relaterade ämnen

* [Om leveransfel](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (dokumentation för Campaign v8)
* [Karantänhantering](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"} (Campaign v8-dokumentation)
* [Bästa praxis för leverans](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} (dokumentation för Campaign v8)
* [Leveransstatus](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-statuses){target="_blank"} (dokumentation för kampanj v8)
* [Arbetsflöde för databasrensning](../../production/using/database-cleanup-workflow.md) (v7-hybrid/lokal)
* [Konfigurera leveransförsök](communication-channels.md) (v7-hybrid/lokal)
* [Uppdatera studskvalifikation](update-bounce-qualification.md) (v7-hybrid/lokal)
* [Konfiguration för e-postleverans](../../installation/using/email-deliverability.md) (v7-hybrid/lokal)
* [Distribuerar en instans](../../installation/using/deploying-an-instance.md#managing-bounced-emails) (v7-hybrid/lokal)

