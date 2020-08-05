---
title: Bästa praxis för kampanjleverans
seo-title: Bästa praxis
page-status-flag: never-activated
uuid: a540efc7-105d-4c7f-a2ee-ade4d22b3445
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
discoiquuid: 0cbc4e92-482f-4dac-a1fb-b738e7127938
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4548eda6f87566398ddf19131b777012cbf8917b
workflow-type: tm+mt
source-wordcount: '4361'
ht-degree: 3%

---


# Bästa praxis {#delivery-best-practices}

Lär dig de bästa metoderna för leveransdesign och leverans med Adobe Campaign.

## Optimera leveransen {#optimize-delivery}

Innan du ens börjar skapa leveranser kan du vidta flera åtgärder för att skydda och optimera sändningsprocessen uppströms.

I följande avsnitt beskrivs god praxis och rekommenderade procedurer för optimal konfiguration av Adobe Campaign. Om du följer dessa rutiner minimeras problem som kan uppstå längre fram i kedjan.

### Plattformsprestanda

Flera faktorer kan direkt påverka serverprestanda och göra plattformen långsammare:

* Antal och typ av personaliseringselement: personalisering i e-post hämtar data från databasen för varje mottagare. Om det finns många personaliseringselement ökar detta mängden data som behövs för att förbereda leveransen.  Läs mer om personalisering i [det här avsnittet](../../delivery/using/about-personalization.md)

* Serverbelastningen: när marknadsföringsservern hanterar många olika uppgifter samtidigt kan prestandan försämras. Marknadsföringsservern måste koordinera alla inkommande och utgående data för alla leveranser för att säkerställa att data är korrekta och i tid.

   **TIPS** - Undvik detta genom att samordna schemaläggningen av leveranser med övriga medlemmar i teamet för att säkerställa bästa möjliga prestanda.

* Arbetsflödets körning: övervakning av arbetsflödena är avgörande för att undvika problem med plattformens prestanda. Följ riktlinjerna som visas [i det här dokumentet](../../workflow/using/workflow-best-practices.md#execution-and-performance).

* Som värdkund kan ni utnyttja funktionerna [i](https://docs.adobe.com/content/help/en/control-panel/using/discover-control-panel/key-features.html) Campaign Control Panel för att övervaka plattformen med [prestandaövervakningsfunktioner](https://docs.adobe.com/content/help/en/control-panel/using/performance-monitoring/about-performance-monitoring.html) .

### Kontrollerar nätverkskonfiguration {#network-config}

Om du vill optimera leveransen när du hanterar e-post i stora volymer och undvika att ta fel för en skräppost, kontrollerar du att du har en giltig nätverkskonfiguration som inte försöker dölja serverns identitet.

**Tips**:  Använd en transparent avsändaradress som motsvarar ert varumärkes webbplats. Exempel: företaget TravelAgency hanterar hotellkedjan Valentino. Företaget äger domänen valentino.com för sin webbplats. För att marknadsföra alla hjärtans dag-hotell i Paris använder man underdomänen paris.valentino.com. Därför kan en relevant avsändaradress vara hotel@paris.valentino.com.

### Leveranshantering {#deliverability-management}

Om du vill nå mottagarnas inkorg utan att studsa eller markeras som skräppost måste du förbättra leveransfrekvensen för dina meddelanden.

* Vad är leverans?

   * Det avser de faktorer i ett e-postmeddelande som avgör om det kan accepteras av en mottagares server. Internet-leverantörer (Internet Service Providers) filtrerar bort e-postmeddelanden som de identifierar som SPAM eller blockerar bilder från hämtning. Om de fastställer att en viss domän skickar för många e-postmeddelanden, kommer de att ange en gräns för hur många e-postmeddelanden de accepterar från den avsändaren.

   * När du kontrollerar om e-postmeddelandet kan levereras vill du fokusera på fyra huvudkategorier: datakvalitet, meddelande och innehåll, utskick av infrastruktur och anseende. Mer information finns i [det här avsnittet](../../delivery/using/about-deliverability.md).

* Använd de rekommendationer som beskrivs [i det här dokumentet](../../delivery/using/deliverability-key-points.md).

* Kontakta din Adobe-representant om du behöver hjälp.

### Karantänhantering {#quarantine-management}

Det ligger i ditt bästa intresse att upprätthålla goda karantänhanteringsprocesser.

När du börjar skicka e-post på en ny plattform kan du använda en lista med adresser som inte är fullständigt kvalificerade. Om du skickar till ogiltiga adresser eller till honeypoadresser (postlådor som bara skapats för att lura skräppost) börjar detta minska din plattforms anseende. Goda rutiner för hantering av karantäner hjälper till att upprätthålla adresskvaliteten, undvika blockeringslista från leverantörer av internetåtkomst, minska felfrekvensen och snabba upp leveranser och dataflöde.

**Tips**

* Om du har en lista med ogiltiga adresser rekommenderar Adobe att du importerar den till karantäntabellen via **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Non deliverables and addresses]**.

* Mottagare vars adresser sätts i karantän exkluderas som standard vid leveransanalysen: de inte är riktade. Detta snabbar upp leveranserna eftersom felfrekvensen avsevärt påverkar leveranshastigheten. En e-postadress kan sättas i karantän när inkorgen är full eller om adressen inte finns. [Lär dig mer](#identifying-quarantined-addresses-for-a-delivery)

* Adobe Campaign hanterar felaktiga adresser beroende på vilken typ av fel som returneras. Mer information om detta hittar du i [det här avsnittet](../../delivery/using/understanding-quarantine-management.md).


* Vissa internetleverantörer betraktar automatisk e-post som skräppost om antalet ogiltiga adresser är för högt.  Med karantän kan du därför undvika att läggas till i en blockeringslista av dessa leverantörer.

* Hantering av karantäner minskar också SMS-sändningskostnaderna eftersom felaktiga telefonnummer utesluts från leveranser.

### Mekanisk för dubbel anmälan {#double-opt-in}

För att undvika att skicka meddelanden till ogiltiga adresser, begränsa felaktig kommunikation och förbättra avsändarens anseende rekommenderar Adobe att du använder en dubbel anmälningsmekanism för bekräftelse efter prenumeration. Detta säkerställer att mottagaren prenumererar avsiktligt.

Detaljerad information om hur denna mekanism ska implementeras finns i [detta avsnitt](../../web/using/use-cases--web-forms.md).

## Använd mallar {#use-templates}

Leveransmallar ger ökad effektivitet genom färdiga scenarier för de flesta vanliga typer av aktiviteter. Med mallar kan marknadsförarna driftsätta nya kampanjer med minimal anpassning på kortare tid.

Läs mer om leveransmallar i [det här avsnittet](../../delivery/using/creating-a-delivery-template.md).

### Kom igång med leveransmallar {#gs-templates}

Med en [leveransmall](../../delivery/using/creating-a-delivery-template.md) kan du definiera en uppsättning tekniska och funktionella egenskaper som passar dina behov och som kan återanvändas för framtida leveranser. Sedan kan ni spara tid och standardisera leveranser vid behov.

När du hanterar flera varumärken i Adobe Campaign rekommenderar Adobe att du har en underdomän per varumärke. En bank kan till exempel ha flera underdomäner som motsvarar var och en av dess regionala myndigheter. Om en bank äger domänen bluebank.com kan dess underdomäner vara @ny.bluebank.com, @ma.bluebank.com, @ca.bluebank.com osv. Med en leveransmall per underdomän kan ni alltid använda rätt förkonfigurerade parametrar för varje varumärke, vilket undviker fel och sparar tid.

**Tips**:  För att undvika konfigurationsfel i Campaign Standarden rekommenderar vi att du duplicerar en inbyggd mall och ändrar dess egenskaper i stället för att skapa en ny mall.

### Konfigurera adresser

* Avsändarens adress är obligatorisk för att tillåta att ett e-postmeddelande skickas.

* En del Internet-leverantörer (Internet Service Providers) kontrollerar avsändarens adress innan de accepterar meddelanden.

* En felformaterad adress kan leda till att den nekas av den mottagande servern. Du måste se till att rätt adress anges.

* Adressen måste uttryckligen identifiera avsändaren. Domänen måste ägas av och registreras hos avsändaren.

* Adobe rekommenderar att du skapar e-postkonton som motsvarar adresserna som angetts för leveranser och svar. Kontakta systemadministratören för meddelanden.

Följ stegen nedan för att konfigurera adresser i Campaign-gränssnittet:

1. Klicka på [länken i](../../delivery/using/creating-a-delivery-template.md)leveransmallen **[!UICONTROL From]** . I **[!UICONTROL Email header parameters]** fönstret fyller du i följande fält:

   ![](assets/d_best_practices_email_header.png)

1. I **[!UICONTROL Sender address]** fältet kontrollerar du att adressdomänen är densamma som den underdomän som du delegerade till Adobe. Du kan ändra den del som föregår @ men inte domänadressen.

1. I **[!UICONTROL From]** fältet använder du ett namn som mottagarna lätt kan identifiera, till exempel ert varumärke, för att öka öppningshastigheten för era leveranser. Om du vill förbättra mottagarens upplevelse ytterligare kan du lägga till en persons namn, till exempel&quot;Emma from Megastore&quot;.

1. I **[!UICONTROL Reply address text]** fälten används avsändarens adress som standard för svar. Adobe rekommenderar dock att man använder en befintlig riktig adress som till exempel kundtjänst för ert varumärke. Om en mottagare skickar ett svar kan kundtjänst hantera det.

### Konfigurera en kontrollgrupp

När leveransen har skickats kan du jämföra beteendet hos de uteslutna mottagarna med mottagarna som tog emot leveransen. Sedan kan ni mäta effektiviteten i era kampanjer. Läs mer om kontrollgrupper i [det här avsnittet](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).

Om du vill konfigurera en kontrollgrupp klickar du på **[!UICONTROL To]** länken. Välj **[!UICONTROL Select target]** fliken i **[!UICONTROL Control group]** fönstret. Du kan extrahera en del av målet, till exempel ett slumpmässigt urval på 5 %.

![](assets/d_best_practices_control_group.png)

### Använd typografi för att tillämpa filter eller kontrollregler

En typologi innehåller kontrollregler som tillämpas under analysfasen innan ett meddelande skickas.

Ändra standardtypologin efter behov på fliken **[!UICONTROL Typology]** för mallens egenskaper.

Om du till exempel vill ha bättre kontroll över utgående trafik kan du definiera vilka IP-adresser som kan användas genom att definiera en tillhörighet per underdomän och skapa en typologi per tillhörighet. Tillhörigheterna definieras i instansens konfigurationsfil. Kontakta Adobe Campaign-administratören.

For more on typologies, refer to [this section](../../campaign/using/about-campaign-typologies.md).

## Designa och personalisera {#design-and-personalize}

När du utformar meddelandeinnehållet bör du undvika vanliga problem som kan hindra dig från att utföra leveransen. Oftast är möjliga fel relaterade till [personalisering](../../delivery/using/about-personalization.md), [formatering](../../delivery/using/defining-the-email-content.md#message-content) och [bilder](../../delivery/using/defining-the-email-content.md#adding-images).

### Optimera personalisering {#optimize-personalization}

För att undvika vanliga problem som kan hindra dig från att utföra leveransen och för att förbättra mottagarnas upplevelse kan du anpassa dina meddelanden med Adobe Campaign.

Du kan använda mottagarnas data som lagras i Adobe Campaign-databasen eller som samlats in via spårning, landningssidor, prenumerationer osv.
Grundläggande om anpassning presenteras i [det här avsnittet](../../delivery/using/personalization-fields.md).

Se till att meddelandeinnehållet är rätt utformat för att undvika fel, som vanligtvis är relaterade till personalisering.

**Tips**: I personaliseringsfält som kommer från externa filer från tredjepartsleverantörer kan externt HTML-innehåll vara fel. Du undviker detta genom att kontrollera syntaxen, användning av taggar, tecken osv. En personaliseringstagg för Adobe Campaign har till exempel alltid följande format: &lt;%=table.field%>. Mer information finns i [det här avsnittet](../../delivery/using/about-personalization.md).

Felaktig användning av parametrar i personaliseringsblock kan vara ett problem. Variabler i JavaScript bör till exempel användas enligt följande:

    &lt;%
    
    var brand = &quot;xxx&quot;
    
    %>

Mer information om personaliseringsblock finns i [det här avsnittet](../../delivery/using/personalization-blocks.md).

Ni kan förbereda personaliseringsdata i ett arbetsflöde för att förbättra analysen av leveransförberedelser. Detta bör användas särskilt om personaliseringsdata kommer från en extern tabell via FDA (Federated Data Access). Det här alternativet beskrivs i det här [avsnittet](../../delivery/using/personalization-fields.md#optimizing-personalization)

### Skapa optimerat innehåll {#optimize-content}

När du skapar e-postmeddelanden bör du tänka på de allmänna bästa metoderna nedan.

* Behåll designen enkel

* Tänk på mobilanvändare

* Undvik helt bildbaserade e-postmeddelanden

* Använda e-postsäkra teckensnitt

* Koda specialtecken

**Subject line** - Work on [subject line](../../delivery/using/defining-the-email-content.md#message-content) to improve open rate:

* Undvik för långa motiv. Använd högst 50 tecken

* Undvik att använda upprepade ord som &quot;free&quot; eller &quot;offer&quot; som kan betraktas som spam

* Undvik versaler och specialtecken som &quot;!&quot;, &quot;£&quot;, &quot;€&quot;, &quot;$&quot;

**Spegelsida** - inkludera alltid en länk för spegelsida. Önskad position är högst upp i e-postmeddelandet. [Lär dig mer](../../delivery/using/sending-messages.md#generating-the-mirror-page)

**Länk** för att avbryta prenumerationen - länken för att avbryta prenumerationen är nödvändig. Den måste vara synlig och giltig och formuläret måste vara funktionellt. När meddelandet analyseras kontrollerar en [typologiregel](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies) som standard om en avanmälningslänk har inkluderats och genererar en varning om den saknas.

**Tips**: Eftersom mänskliga fel alltid är möjliga bör du kontrollera att länken för avanmälan fungerar korrekt före varje gång du skickar. När du t.ex. skickar ett bevis ska du kontrollera att länken är giltig, att formuläret är online och att fältet för att inte längre kontakta den här mottagaren har ändrats till Ja.

Lär dig hur du infogar en länk för avanmälan [i det här avsnittet](../../delivery/using/personalization-blocks.md#personalization-blocks-example).

**E-poststorlek** - För att undvika prestandaproblem och leveransproblem är den rekommenderade maxstorleken för ett e-postmeddelande cirka **35 kB**. Om du vill kontrollera meddelandestorleken går du till **[!UICONTROL Preview]** fliken och väljer en testprofil. När meddelandet har genererats visas meddelandestorleken i det övre högra hörnet.

Tänk på följande om du vill hålla din e-post under gränsen:

* Ta bort överflödiga eller oanvända format

* Flytta en del av e-postinnehållet till en landningssida

* Minimera koden

Kontrollera att du har testat alla ändringar innan du skickar det

**SMS-längd**

Som standard uppfyller antalet tecken i ett SMS-meddelande GSM-standarden (Global System for Mobile Communications). SMS-meddelanden som använder GSM-kodning kan innehålla högst 160 tecken eller 153 tecken per SMS för meddelanden som skickas i flera delar.

Transkriberingen ersätter ett tecken i ett SMS med ett annat om det tecknet inte beaktas av GSM-standarden. Observera att om du infogar anpassningsfält i innehållet i SMS-meddelandet kan det medföra tecken som GSM-kodningen inte tar hänsyn till. Du kan godkänna teckentranskribering genom att markera motsvarande ruta på fliken SMPP-kanalinställningar i motsvarande **[!UICONTROL External account]**.
Läs mer [i det här avsnittet](../../delivery/using/sms-channel.md#creating-an-smpp-external-account).

**Tips**:

* Om du vill behålla alla tecken i SMS-meddelanden som de är, ska du inte aktivera transkribering för att t.ex. inte ändra egennamn.

* Om dina SMS-meddelanden innehåller många tecken som inte beaktas av GSM-standarden kan du aktivera transkribering för att begränsa kostnaderna för att skicka meddelanden.

Läs mer [i det här avsnittet](../../delivery/using/sms-channel.md#about-character-transliteration).

### Arbeta med formatering {#formatting}

Kontrollera följande element för att undvika vanliga formateringsfel:

* Korrekt **datumformatering**: Adobe Campaign tillhandahåller datumformateringsfunktioner för JavaScript-mallar och XSL-formatmallar. [Lär dig mer](../../delivery/using/formatting.md#date-display)

* Användning av **tillåtna tecken** i e-postmeddelanden: listan med giltiga tecken för e-postadresser definieras i alternativet XtkEmail_Characters. Lär dig hur du får tillgång till Campaign-alternativ [i det här avsnittet](../../installation/using/configuring-campaign-options.md). För att specialtecken ska kunna hanteras på rätt sätt måste Adobe Campaign vara installerat i Unicode.

* Konfiguration av **e-postautentisering**: Kontrollera att e-posthuvudena innehåller DKIM-signaturen. Med DKIM-autentisering (Domain Keys Identified Mail) kan den mottagande e-postservern verifiera att ett meddelande verkligen skickades av den person eller enhet som det hävdades ha skickats av och om meddelandeinnehållet ändrades mellan den tidpunkt det ursprungligen skickades (och DKIM &quot;signerade&quot;) och den tidpunkt det togs emot. Den här standarden använder vanligtvis domänen i sidhuvudet Från eller Avsändare. Mer information om detta hittar du i [det här avsnittet](../../delivery/using/technical-recommendations.md#dkim).

* **Responsiv e-postdesign** säkerställer att ett e-postmeddelande återges optimalt för den enhet där det öppnas.

   * Använd responsiv e-post-HTML i stället för webb-HTML.

   * Använd förhandsgranskningsläget och skicka provtryck för att testa återgivningen på så många enheter som möjligt.

   * Modulen Adobe Campaign Classic Digital Content Editor (DCE) innehåller responsiva designformaterade mallar för mobiler som är tillgängliga via **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Content templates]**. Läs mer [i den här artikeln](https://theblog.adobe.com/responsive-email-design-101/).



### Hantera bilder {#manage-images}

Följ riktlinjerna nedan när det gäller att använda bilder.

* **Förhindra att bilder blockeras** - Vissa e-postklienter blockerar bilder som standard, och vissa användare ändrar sina inställningar för att blockera bilder för att spara vid dataanvändning. Om bilderna inte hämtas kan därför hela meddelandet gå förlorat. Så här undviker du:

   * Balansera innehållet med bild och text. Undvik helt bildbaserade e-postmeddelanden.

   * Om texten måste finnas i en bild använder du alt- och titeltext för att vara säker på att meddelandet når fram. Formatera din alt-/titeltext för att förbättra utseendet.

   * Undvik att använda bakgrundsbilder eftersom de inte stöds av vissa e-postklienter.

* **Gör bilderna responsiva** - Försök att göra bilderna responsiva och ändra storlek. Observera att detta kan ha en kostnadseffekt eftersom det tar längre tid att bygga.

* **Använd absoluta bildreferenser** - För att vara tillgängliga utifrån måste de bilder som används i e-postmeddelanden och offentliga resurser som är länkade till kampanjer finnas på en externt tillgänglig server.

   * Du kan kontrollera om instanskonfigurationen aktiverar offentlig resurshantering. [Lär dig mer](../../installation/using/deploying-an-instance.md#managing-public-resources)

   * I leveransguiden kan du importera en HTML-sida som innehåller bilder eller infoga bilder direkt med HTML-redigeraren via **[!UICONTROL Image]** -ikonen. [Lär dig mer](../../delivery/using/defining-the-email-content.md#adding-images)

   * Om bilderna inte visas kontrollerar du att bilderna är tillgängliga på servern. Det gör du genom att klicka på fliken Källa i leveransfönstret. Hitta bilderna och kopiera och klistra in URL:en för varje bild i en webbläsare. Om bilderna inte visas kontaktar du IT-administratören eller tredjepartsleverantören som tillhandahåller ditt leveransinnehåll.

### Förhandsgranska meddelandet {#preview-msg}

Adobe rekommenderar att du förhandsgranskar ditt meddelande för att kontrollera hur det är anpassat och hur mottagarna ser det.

* I leveransguiden kan du på **[!UICONTROL Preview]** underfliken visa återgivningen av varje innehåll för en mottagare. Anpassningsfälten och de villkorliga elementen i innehållet ersätts med motsvarande information för den valda profilen. [Lär dig mer](../../delivery/using/defining-the-email-content.md#message-content)

* En automatisk skräppostkontroll utförs under varje förhandsgranskning. På **[!UICONTROL Preview]** underfliken ska du kontrollera [SpamAssassin](../../delivery/using/spamassassin.md) spam-poäng.  Klicka **[!UICONTROL More...]** om du vill veta mer om varningen.  Innan du gör det kontrollerar du att SpamAssets är korrekt installerat och konfigurerat på Adobe Campaign programserver. [Lär dig mer](../../installation/using/configuring-spamassassin.md)

## Definiera rätt mål {#define-the-right-target}

Målgruppen är följande: skapa listor noggrant, testa e-postmeddelanden på populära e-postklienter och mobila enheter och se till att e-postlistorna är aktuella (utan okända eller föråldrade adresser). Du kan också skicka korrektur som hjälper dig att konfigurera en komplett valideringscykel.

Läs mer om målpopulationer [i det här avsnittet](../../delivery/using/steps-defining-the-target-population.md)

### Rikta er till rätt målgrupp {#target-the-right-audience}

När innehållet är klart måste du noga definiera vem som ska få meddelandet.

För att leveransen ska bli framgångsrik vill ni skicka det mest relevanta personaliserade innehållet till rätt mottagare. Med Adobe Campaign kan ni skapa det mest korrekta målet: kan du välja mottagare utifrån deras ålder, lokalisering, vad de har köpt, om de har klickat på en länk i en tidigare leverans osv. Med Adobe Campaign kan du även definiera testprofiler, kontrollgrupper och startadresser för att vara säker på att målet är korrekt.

### Målmappningar {#target-mappings}

I Campaign Classic är leveransmallarna som standard avsedda för **mottagare**. Adobe Campaign erbjuder andra målmappningar för leveranser som du kan ändra efter behov.

Du kan till exempel leverera till besökare vars profiler har samlats in via sociala nätverk eller till besökare som prenumererar på en informationstjänst.

Dessa mappningar presenteras [i det här avsnittet](../../delivery/using/selecting-a-target-mapping.md).

Du kan också skapa och använda en anpassad målmappning. Mer information om detta hittar du i [det här avsnittet](../../configuration/using/target-mapping.md).

### Externa mottagare {#external-recipients}

Du kan leverera till mottagare som lagras i en extern fil i stället för att sparas i databasen. Läs mer [i det här avsnittet](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients).

### Skicka till prenumeranterna {#send-to-subscribers}

Om du vill skicka meddelanden till prenumeranterna på ett nyhetsbrev kan du rikta dem direkt till motsvarande informationstjänst. Läs mer [i det här avsnittet](../../delivery/using/managing-subscriptions.md#delivering-to-the-subscribers-of-a-service).


### Testa mottagare och startadresser {#test-recipients-seed-addresses}

Om du vill testa leveransen använder du korrektur innan du skickar till huvudmålet.

Se till att du väljer rätt korrekturmottagare eftersom de validerar formuläret och meddelandets innehåll. Stegen för att definiera korrekturmottagare visas [i det här avsnittet](../../delivery/using/steps-defining-the-target-population.md#selecting-the-proof-target).

Seed-adresser används för målmottagare som inte matchar de definierade målvillkoren för att testa en leverans innan den skickas till huvudmålet. De presenteras [i detta avsnitt](../../delivery/using/about-seed-addresses.md).

### Deduplicera adresser {#deduplicate-addresses}

Det är viktigt att undvika att ha dubbla e-postadresser, eftersom detta kan påverka ditt mål:

* Samma meddelande kan skickas mer än en gång när ett mål delas.

* Om en mottagare säger upp prenumerationen efter att ha fått ett meddelande kommer deras duplicerade profil fortfarande att få framtida meddelanden.

Borttagning av dubbletter skyddar det avsändande anseendet och garanterar en god karantänhantering.

Läs mer [i det här fallet](../../workflow/using/deduplication.md#example--identify-the-duplicates-before-a-delivery).


### Indexera e-postadresser {#index-addresses}

För att optimera prestanda för SQL-frågor som används i programmet kan ett index deklareras från huvudelementet i dataschemat.

Stegen för att lägga till ett index till e-postadressen beskrivs [i det här avsnittet](../../configuration/using/database-mapping.md#indexed-fields).

## Utför alla kontroller innan du skickar {#perform-all-checks}

När meddelandet är klart ser du till att innehållet visas korrekt på alla enheter och att det inte innehåller fel som personalisering eller brutna länkar.

Innan du skickar meddelandet måste du se till att parametrarna och konfigurationen stämmer överens med leveransen.

### Varför validering är avgörande {#validation-is-key}

Innan du skickar en leverans måste du se till att mottagarna får det meddelande som du verkligen vill skicka. För att göra detta måste du validera meddelandets innehåll och leveransparametrar.

Med det här steget kan du identifiera eventuella fel och åtgärda dem innan du levererar till huvudmålet.

Stegen för validering av leverans beskrivs [i det här avsnittet](../../delivery/using/steps-validating-the-delivery.md).

### Inkorgsåtergivning {#inbox-and-email-rendering}

Med inkorgsåtergivning kan du förhandsgranska meddelanden på större e-postklienter, skanna innehåll och anseende, upptäcka hur mottagarna läser meddelanden.

**Tips**:

* Du kan visa det skickade meddelandet i olika sammanhang där det kan tas emot: webbpost, meddelandetjänst, mobil osv.

* Återgivningsfunktioner för inkorgen är avgörande för att du ska kunna identifiera om dina e-postkampanjer fungerar som de ska med filtren hos viktiga internetleverantörer (Internet Service Providers) och webbposttjänster. Sådana verktyg skickar en kopia av ett e-postmeddelande till ett nätverk av testinkorgar, så att du kan se hur meddelandet kommer att visas, eller återges, i alla dessa tjänster. De kan även innehålla rapporter och kodkorrigeringsalternativ som hjälper dig att snabbt identifiera och göra korrigeringar som förbättrar leveransen.

Läs mer [i det här avsnittet](../../delivery/using/inbox-rendering.md).

### Korrekturmeddelanden {#proof-messages}

Genom att skicka korrektur kan du kontrollera länken för avanmälan, spegelsidan och alla andra länkar, validera meddelandet, verifiera att bilder visas, upptäcka eventuella fel osv. Du kanske också vill kontrollera din design och återgivning på olika enheter.

Läs mer [i det här avsnittet](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### Ställ in A/B-testleveranser {#a-b-testing-deliveries}

Om du har flera innehåll för en e-postleverans kan du använda A/B-testning för att ta reda på vilken version som har störst påverkan på målpopulationen.

**Tips**:

* Skicka olika versioner till vissa mottagare

* Välj den som har högst framgångsfrekvens och skicka den till resten av ditt mål

Läs mer [i det här avsnittet](../../workflow/using/a-b-testing.md).

### Se till att ditt meddelande levereras {#make-sure-your-message-is-delivered}

Som ett sista steg kan du maximera dina chanser och utnyttja kraften i Adobe Campaign Classic för att säkerställa att ditt budskap verkligen kommer att levereras till de relevanta mottagarna.

**Gå igenom en valideringsprocess** - Du kan definiera en fullständig valideringsprocess där Adobe Campaign-operatorer och -grupper deltar för att validera både mål- och meddelandeinnehållet. Detta kommer att säkerställa full övervakning och kontroll av kampanjens olika processer: målgruppsanpassning, innehåll, budget, extrahering och utskick av ett bevis. Beroende på deras behörigheter meddelas användare, får korrektur och kan validera eller avvisa meddelandet. Läs mer [i det här avsnittet](../../campaign/using/marketing-campaign-approval.md#approval-process).

**Använd vågor** - Du kan stegvis öka volymen som skickas med vågor. På så sätt undviker du att meddelanden markeras som skräppost eller när du vill begränsa antalet meddelanden per dag. Med vågor kan du dela upp leveranser i flera grupper i stället för att skicka stora mängder meddelanden samtidigt. Läs mer [i det här avsnittet](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves).

**Prioritera meddelanden** - Du kan ange avsändarordning för leveranser genom att ange prioritetsnivå. För att göra detta:

1. Redigera leveransegenskaperna och välj **[!UICONTROL Delivery]** fliken.

1. Definiera prioritetsnivån för leveransen på en skala från **[!UICONTROL Very low]** till **[!UICONTROL Very high]**.

>[!NOTE]
>
>Det går inte att definiera ordningen för att skicka meddelanden från en leverans.

**Konfigurera IP-tillhörigheter** - För att få bättre kontroll över utgående SMTP-trafik kan du hantera tillhörigheter genom att definiera vilka specifika IP-adresser som kan användas för varje tillhörighet. På så sätt kan du begränsa antalet e-postmeddelanden för specifika leveranser till maskiner eller utdatameddelanden. Du kan till exempel använda en affinitet per land eller underdomän. Du kan sedan skapa en typologi per land och länka varje tillhörighet till motsvarande typologi.

Du kan:

* Definiera IP-tillhörigheterna i konfigurationsfilen serverConf.xml. [Lär dig mer](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities)

* Deklarera de IP-adresser som kan användas för varje IPAfinity-element. [Lär dig mer](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

* I den [typologi](../../campaign/using/about-campaign-typologies.md) du väljer använder du **[!UICONTROL Managing affinities with IP addresses]** fältet för att länka leveranser till leveransservern (MTA) som hanterar tillhörigheten. [Lär dig mer](../../campaign/using/applying-rules.md#control-outgoing-smtp-traffic).

* När e-postmeddelandet har skickats kontrollerar du huvudet för att verifiera vilken IP-adress som leveransen skickades från. E-postadministratören bör hjälpa dig att få fram rubrikinformationen.

>[!NOTE]
>
>De flesta av dessa steg kan bara utföras av en expertanvändare.

**Använd typologier** - Du kan använda typologiregler för att exkludera delar av målet baserat på specifika kriterier. Detta garanterar att de meddelanden som skickas bäst uppfyller kundernas behov och förväntningar, i enlighet med företagets kommunikationspolicy. Du kan till exempel filtrera de mottagare som är minderåriga från målet i nyhetsbrevet. Läs mer [i det här exemplet](../../campaign/using/filtering-rules.md).

**Undvik bifogade filer** - Bifogade filer är fortfarande en av de vanligaste vektorerna för spridning av skadlig kod, särskilt när de skickas satsvis. Inkludera en säker länk till dokumentet i stället för att bifoga det. Detta garanterar ett extra säkerhetslager för att förhindra oavsiktlig omdistribution och minskar avsevärt riskerna för att meddelandet kommer att refuseras vid inkommande e-postgatewayar av meddelandestorlek eller säkerhetsskäl.

## Spåra och övervaka {#track-and-monitor}

Klickade du på knappen Skicka? Låt oss se vad som händer. När leveransen har skickats kan du med Adobe Campaign hålla reda på skickade meddelanden och se hur mottagarna svarar på leveransen. Detta hjälper er att förbättra era framtida utskick och optimera era nästa kampanjer.

### Övervaka leveranser {#monitoring-deliveries}

För att kunna styra era kampanjer måste ni se till att meddelandet verkligen har levererats till mottagarna.

På kontrollpanelen för kampanjleverans kan du kontrollera bearbetade meddelanden och leveransgranskningsloggar.
Du kan också styra status för meddelandena i leveransloggarna. [Lär dig mer](../../delivery/using/monitoring-a-delivery.md#delivery-dashboard).

Vad händer om leveranserna inte skickas och deras status förblir **Väntande**?

* Körningsprocessen väntar på att vissa resurser ska vara tillgängliga. MTA har kanske inte startats.
Kontrollera att mta@instance startas på dina MTA-servrar och starta MTA-modulen om det behövs. [Lär dig mer](../../production/using/administration.md).

* Leveransen kan ha en tillhörighet som inte har konfigurerats på den sändande instansen.
Tips: Kontrollera konfigurationen för trafikhantering (IP-tillhörighet). Mer information finns i Kontrollera utgående SMTP-trafik.

>[!NOTE]
>
>Dessa steg kan bara utföras av en expertanvändare.

### Spårning {#tracking-deliveries}

Om du vill veta mer om mottagarnas beteende kan du spåra hur de reagerar på en leverans: mottagning, öppning, klickningar på länkar, avbeställningar osv. I Campaign Classic visas den här informationen på fliken Spårning för mottagarna som leveransmålet gäller och på fliken Spårning för leveransen. I Campaign Standard visas den på fliken Spårningsloggar för leveransen.

**Tips**: Spårning av meddelanden är aktiverat som standard. Om du vill konfigurera URL-adresser väljer du alternativet Visa URL-adresser i det nedre avsnittet av leveransguiden. För varje URL för meddelandet kan du välja om spårning ska aktiveras.

Mer information finns i avsnittet [Konfigurera spårning](../../delivery/using/how-to-configure-tracked-links.md) och i beskrivningen av [spårningsindikatorer](../../reporting/using/delivery-reports.md#tracking-indicators) .

### Leveransprestanda {#delivery-performances}

Om du vill mäta den hastighet med vilken meddelandena levereras kan du styra leveransflödet. Kriterierna är antalet meddelanden som skickas per timme och storleken på meddelandena (i bitar per sekund). Mer information finns i [Leveransflöde](../../reporting/using/global-reports.md#delivery-throughput).

**Tips**:

* Behåll inte leveranser i felaktigt tillstånd för instansen eftersom detta bevarar tillfälliga tabeller och påverkar prestandan.

* Ta bort leveranser som inte längre behövs och inaktiva mottagare från databasen för att upprätthålla adresskvaliteten.

* Försök inte schemalägga stora leveranser tillsammans. Observera att det kan ta 5 till 10 minuter att sprida belastningen jämnt över systemet.

### Felsökning av leverans {#delivery-troubleshooting}

Specifika åtgärder kan utföras vid problem med leveranser:

* [Leveransproblem](../../production/using/performance-and-throughput-issues.md#deliverability_issues)

* [Bildvisningsproblem](../../production/using/image-display-issues.md)

* [Problem med leveransresultat](../../delivery/using/monitoring-a-delivery.md#performance_issues)

* [Temporära filproblem](../../production/using/temporary-files.md) - endast *lokala kunder*
