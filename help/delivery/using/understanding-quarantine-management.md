---
product: campaign
title: Förstå karantänhantering
description: Förstå karantänhantering
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Monitoring, Deliverability
role: User
exl-id: cfd8f5c9-f368-4a31-a1e2-1d77ceae5ced
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '2987'
ht-degree: 7%

---

# Förstå karantänhantering{#understanding-quarantine-management}

Adobe Campaign hanterar en lista med adresser i karantän. Mottagare vars adress sätts i karantän exkluderas som standard vid leveransanalys och anges inte som mål. En e-postadress kan sättas i karantän, till exempel när postlådan är full eller om adressen inte finns. Under alla omständigheter uppfyller karantänförfarandet de särskilda regler som beskrivs nedan.

>[!NOTE]
>
>Det här avsnittet gäller för onlinekanaler: e-post, SMS, push-meddelanden.

## Optimera leveransen genom karantänhantering {#optimizing-your-delivery-through-quarantines}

Profilerna vars e-postadresser eller telefonnummer är i karantän exkluderas automatiskt vid meddelandeförberedelsen (se [Identifiera adresser i karantän för en leverans](#identifying-quarantined-addresses-for-a-delivery)). Detta snabbar upp leveranserna eftersom felfrekvensen avsevärt påverkar leveranshastigheten.

Vissa internetleverantörer betraktar automatisk e-post som skräppost om antalet ogiltiga adresser är för högt.  Med karantän kan du därför undvika att läggas till i blockeringslista av dessa leverantörer.

Dessutom bidrar karantäner till att minska SMS-kostnaderna genom att utesluta felaktiga telefonnummer från leveranser.

Mer information om de bästa sätten för att skydda och optimera leveranser finns på [den här sidan](delivery-best-practices.md).

### Karantän mot blockeringslista {#quarantine-vs-denylist}

Karantän och blockeringslista gäller inte för samma objekt:

* **Karantän** gäller bara för en **adress** (eller telefonnummer osv.), inte för själva profilen. En profil vars e-postadress är placerad i karantän kan till exempel uppdatera sin profil och ange en ny adress. Därefter kan den användas av leveransåtgärder igen. Om två profiler råkar ha samma telefonnummer, påverkas båda om numret sätts i karantän.

  Adresserna eller telefonnumren i karantän visas i [exkluderingsloggarna](#identifying-quarantined-addresses-for-a-delivery) (för en leverans) eller i [karantänlistan](#identifying-quarantined-addresses-for-the-entire-platform) (för hela plattformen).

* Om du däremot befinner dig på **blockeringslista**, leder det till att **profile** inte längre anges som mål för leveransen, till exempel efter en avanmälan (avanmälan) för en viss kanal. Om en profil på blockeringslista för e-postkanalen till exempel har två e-postadresser, kommer båda adresserna inte att levereras.

  Du kan kontrollera om det finns en profil på blockeringslista för en eller flera kanaler under **[!UICONTROL No longer contact]** på fliken **[!UICONTROL General]** i profilen. Se [det här avsnittet](../../platform/using/editing-a-profile.md#general-tab).

>[!NOTE]
>
>Karantänen innehåller en **[!UICONTROL Denylisted]**-status, som används när mottagarna rapporterar ditt meddelande som skräppost eller svarar på ett SMS-meddelande med ett nyckelord som &quot;STOP&quot;. I så fall skickas profilens adress eller telefonnummer till karantän med statusen **[!UICONTROL Denylisted]**. Mer information om hur du hanterar SMS-meddelanden för STOP finns i [det här avsnittet](../../delivery/using/sms-send.md#processing-inbound-messages).

## Identifiera adresser i karantän {#identifying-quarantined-addresses}

Adresser i karantän kan användas för en viss leverans eller för hela plattformen.

### Identifiera adresser i karantän för en leverans {#identifying-quarantined-addresses-for-a-delivery}

Adresser i karantän för en viss leverans listas under leveransförberedelsefasen i leveransloggarna på kontrollpanelen (se [Leveransloggar och historik](delivery-dashboard.md#delivery-logs-and-history)).

### Identifiera adresser i karantän för hela plattformen {#identifying-quarantined-addresses-for-the-entire-platform}

Administratörer kan lista adresserna i karantän för hela plattformen från noden **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**.

>[!NOTE]
>
>Den här menyn listar element i karantän för **e-post**, **SMS** och **push-meddelanden** .

Följande information finns för varje adress:

![](assets/tech_quarant_npai.png)

>[!NOTE]
>
>Ökningen av antalet karantän är en normal effekt som har samband med databasens slitage. Om en e-postadress till exempel anses ha en livslängd på tre år och mottagartabellen ökar med 50 % varje år, kan ökningen av antalet karantän beräknas enligt följande:
>
>Slut på år 1: (1&#42;0.33)/(1+0.5)=22 %.
>
>Slut på år 2: ((1.22&#42;0.33)+0.33)/(1.5+0.75)=32,5 %.

### Identifiera adresser i karantän i leveransrapporter {#identifying-quarantined-addresses-in-delivery-reports}

Följande rapporter innehåller information om adresserna i karantän:

* För varje leverans visar rapporten **[!UICONTROL Delivery summary]** antalet adresser i karantän i leveransmålet. Den visar:

   * Antalet adresser som placerats i karantän under leveransanalysen.

   * Antalet adresser som placerats i karantän efter leveransåtgärden.

* Rapporten **[!UICONTROL Non-deliverables and bounces]** innehåller information om adresserna i karantän, typer av fel som uppstått osv. samt felinformation per domän.

Du kan söka efter den här informationen för alla leveranser av plattformen (**[!UICONTROL Home page > Reports]**) eller för en viss leverans. Du kan också skapa anpassade rapporter och välja vilken information som ska visas.

### Identifiera adresser i karantän för en mottagare {#identifying-quarantined-addresses-for-a-recipient}

Du kan slå upp status för e-postadressen för alla mottagare. Det gör du genom att markera mottagarprofilen och klicka på fliken **[!UICONTROL Deliveries]**. För alla leveranser till den mottagaren kan du ta reda på om adressen misslyckades, placerades i karantän under analysen osv. För varje mapp kan du bara visa mottagare vars e-postadress är i karantän. Använd programfiltret **[!UICONTROL Quarantined email address]** om du vill göra det.

![](assets/tech_quarant_recipients_filter.png)


## Villkor för att skicka en adress till karantän {#conditions-for-sending-an-address-to-quarantine}

Adobe Campaign hanterar karantän enligt typ av leveransfel och den orsak som tilldelats vid kvalificering av felmeddelanden (se [Bedragning av e-postkvalificering](understanding-delivery-failures.md#bounce-mail-qualification) och [Leveransfel och orsaker](understanding-delivery-failures.md#delivery-failure-types-and-reasons)).

* **Ignorerad avvikelse**: ignorerade avvikelser skickar ingen adress till karantänen.
* **Kritisk avvikelse**: motsvarande e-postadress skickas omedelbart till karantänen.
* **Icke-kritisk avvikelse**: En icke-kritiskt avvikelse skickar inte en adress till karantän omedelbart men ökar dock felräknaren.  Mer information finns i [Mjuk felhantering](#soft-error-management).

Om en användare kvalificerar ett e-postmeddelande som en skräppost ([feedbackslinga](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#feedback-loops)) dirigeras meddelandet automatiskt om till en teknisk postlåda som hanteras av Adobe. Användarens e-postadress skickas sedan automatiskt till karantänen med status **[!UICONTROL Denylisted]**.    Den här statusen avser endast adressen, profilen finns inte på blockeringslista, så att användaren fortsätter att ta emot SMS-meddelanden och push-meddelanden.

>[!NOTE]
>
>Karantänen i Adobe Campaign är skiftlägeskänslig.    Se till att importera e-postadresser med små bokstäver så att inte e-postadresserna fortsätter att ta emot meddelanden.

I listan över adresser i karantän (se [Identifiera adresser i karantän för hela plattformen](#identifying-quarantined-addresses-for-the-entire-platform)) visar fältet **[!UICONTROL Error reason]** varför den valda adressen placerades i karantän.

![](assets/tech_quarant_error_reasons.png)

### Mjuk felhantering {#soft-error-management}

I motsats till hårda fel skickar inte mjuka fel en adress direkt till karantän, utan i stället ökar de en felräknare.

Försök utförs igen under [leveranstiden](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period). När felräknaren når gränsvärdet sätts adressen i karantän.    Mer information finns i [Försök igen efter ett tillfälligt leveransfel](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure).

Felräknaren initieras om om det senaste allvarliga felet inträffade för mer än 10 dagar sedan. Adressstatusen ändras sedan till **Giltig** och tas bort från listan över karantäner i arbetsflödet för [Databasrensning](../../production/using/database-cleanup-workflow.md).


Om du har uppgraderat till [Förbättrat MTA](sending-with-enhanced-mta.md) för värdbaserade eller hybridinstallerade installationer, baseras nu det maximala antalet försök som ska utföras om **[!UICONTROL Erroneous]**-statusen är och den minsta fördröjningen mellan försök på hur bra en IP fungerar både historiskt och för närvarande på en viss domän.

För lokala installationer och värdbaserade/hybridinstallationer som använder det äldre Campaign MTA kan ni ändra antalet fel och perioden mellan två fel. Det gör du genom att ändra motsvarande inställningar i [distributionsguiden](../../installation/using/deploying-an-instance.md) (**[!UICONTROL Email channel]** > **[!UICONTROL Advanced parameters]**) eller [på leveransnivå](../../delivery/using/steps-sending-the-delivery.md#configuring-retries).


## Ta bort en adress från karantän {#removing-a-quarantined-address}

### Automatiska uppdateringar {#unquarantine-auto}

Adresser som matchar specifika villkor tas automatiskt bort från karantänlistan av arbetsflödet [Databasrensning](../../production/using/database-cleanup-workflow.md).

Adresserna tas automatiskt bort från karantänlistan i följande fall:

* Adresser med statusen **[!UICONTROL With errors]** tas bort från karantänlistan efter en slutförd leverans.
* Adresser med statusen **[!UICONTROL With errors]** tas bort från karantänlistan om den senaste mjuka studsen inträffade för mer än 10 dagar sedan. Mer information om mjuk felhantering finns i [det här avsnittet](#soft-error-management).
* Adresser i en **[!UICONTROL With errors]**-status som studsade med felet **[!UICONTROL Mailbox full]** tas bort från karantänlistan efter 30 dagar.

Deras status ändras sedan till **[!UICONTROL Valid]**.

>[!IMPORTANT]
>
>Mottagare med en adress i en **[!UICONTROL Quarantine]**- eller **[!UICONTROL Denylisted]**-status tas aldrig bort, även om de får ett e-postmeddelande.

### Manuella uppdateringar {#unquarantine-manual}

Du kan också ta bort karantänen för en adress manuellt. Om du vill ta bort en adress manuellt från karantänlistan ändrar du dess status till **[!UICONTROL Valid]** från noden **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**.

![](assets/tech_quarant_error_status.png)

### Massuppdateringar {#unquarantine-bulk}

Du kan behöva göra satsvisa uppdateringar i karantänlistan, t.ex. om en Internet-leverantör är i ett driftstopp. I så fall markeras e-postmeddelanden felaktigt som studsar eftersom de inte kan levereras till mottagaren. Dessa adresser måste tas bort från karantänlistan.

Om du vill utföra det här skapar du ett arbetsflöde och lägger till en **[!UICONTROL Query]**-aktivitet i karantäntabellen för att filtrera bort alla påverkade mottagare. När de har identifierats kan de tas bort från karantänlistan och inkluderas i framtida e-postleveranser för kampanjer.

Nedan följer de rekommenderade riktlinjerna för den här frågan:

* För Campaign Classic v7-miljöer med regelinformation för inkommande e-post i fältet **[!UICONTROL Error text]** i karantänlistan:

   * **Feltext (karantäntext)** innehåller &quot;Momen_Code10_InvalidRecipient&quot;
   * **E-postdomänen (@domain)** är lika med domain1.com ELLER **E-postdomänen (@domain)** är lika med domain2.com ELLER **E-postdomän (@domain)** är lika med domain3.com
   * **Uppdatera status (@lastModified)** på eller efter `MM/DD/YYYY HH:MM:SS AM`
   * **Uppdatera status (@lastModified)** på eller före `MM/DD/YYYY HH:MM:SS PM`

* För Campaign Classic v7-instanser med SMTP-studssvarsinformation i fältet **[!UICONTROL Error text]** i karantänlistan:

   * **Feltext (karantäntext)** innehåller &quot;550-5.1.1&quot; OCH **Feltexten (karantäntext)** innehåller &quot;support.ISP.com&quot;

  där &quot;support.ISP.com&quot; kan vara: &quot;support.apple.com&quot; eller &quot;support.google.com&quot;, till exempel

   * **Uppdatera status (@lastModified)** på eller efter `MM/DD/YYYY HH:MM:SS AM`
   * **Uppdatera status (@lastModified)** på eller före `MM/DD/YYYY HH:MM:SS PM`

När du har en lista över berörda mottagare lägger du till en **[!UICONTROL Update data]**-aktivitet för att ange deras e-postadressstatus till **[!UICONTROL Valid]** så att de tas bort från karantänlistan i arbetsflödet **[!UICONTROL Database cleanup]**. Du kan även ta bort dem från karantäntabellen.

## Kantlinjer för push-meddelanden {#push-notification-quarantines}

Karantänmekanismen för push-meddelanden är globalt densamma som den allmänna processen. Vissa fel hanteras dock på olika sätt för push-meddelanden. För vissa mjuka fel utförs till exempel inga försök inom samma leverans. Specifikationerna för push-meddelanden anges nedan. Mekanismen för återförsök (antal återförsök, frekvens) är densamma som för e-post.

Objekten som sätts i karantän är enhetstoken.

### iOS karantän {#ios-quarantine}

HTTP/V2-protokollet tillåter direkt feedback och status för varje push-leverans. Om HTTP/V2-protokollkopplingen används anropas inte längre feedbacktjänsten av arbetsflödet **[!UICONTROL mobileAppOptOutMgt]**. En token betraktas som oregistrerad när ett mobilprogram avinstalleras eller installeras om.

Synkront, om APN:er returnerar status &quot;unregistered&quot; för ett meddelande, sätts måltoken omedelbart i karantän.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Scenario</strong><br /> </td> 
   <td> <strong>Status</strong><br /> </td> 
   <td> <strong>Felmeddelande</strong><br /> </td> 
   <td> <strong>Feltyp</strong><br /> </td> 
   <td> <strong>Felorsak</strong><br /> </td> 
   <td> <strong>Försök igen</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Målenheten är påslagen <br /> </td> 
   <td> OK<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Målenheten är avstängd <br /> </td> 
   <td> OK<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Användaren inaktiverar meddelanden för programmet <br /> </td> 
   <td> OK<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Fas för att skapa/analysera meddelanden - nyttolasten är för stor<br /> </td> 
   <td> Fel <br /> </td> 
   <td> Nyttolasten är för lång <br /> </td> 
   <td> Mjuk<br /> </td> 
   <td> Avvisad<br /> </td> 
   <td> Nej<br /> </td> 
  </tr> 
  <tr> 
   <td> Fas för att skapa/analysera meddelanden - oväntat innehållsformatproblem<br /> </td> 
   <td> Fel <br /> </td> 
   <td> Olika felmeddelanden enligt felet <br /> </td> 
   <td> Mjuk<br /> </td> 
   <td> Odefinierad<br /> </td> 
   <td> Nej<br /> </td> 
  </tr> 
  <tr> 
   <td> Certifikatproblem (lösenord, fel osv.) och testanslutning till APN-problem<br /> </td> 
   <td> Fel <br /> </td> 
   <td> Olika felmeddelanden enligt felet <br /> </td> 
   <td> Mjuk<br /> </td> 
   <td> Avvisad<br /> </td> 
   <td> Nej<br /> </td> 
  </tr> 
  <tr> 
   <td> Nätverksanslutningen bröts under sändning av <br /> </td> 
   <td> Fel <br /> </td> 
   <td> Anslutningsfel <br /> </td> 
   <td> Odefinierad<br /> </td> 
   <td> Onåbar<br /> </td> 
   <td> Ja<br /> </td> 
  </tr> 
  <tr> 
   <td> Avvisning av APN-meddelande: Avregistrering<br /> har tagits bort av användaren eller så har token upphört att gälla<br /> </td> 
   <td> Fel <br /> </td> 
   <td> Oregistrerad<br /> </td> 
   <td> Hård<br /> </td> 
   <td> Okänd användare: <br /> </td> 
   <td> Nej<br /> </td> 
  </tr> 
  <tr> 
   <td> Meddelandeavvisande för APN: alla andra fel <br /> </td> 
   <td> Fel <br /> </td> 
   <td> Felavvisandeorsaken kommer att finnas i felmeddelandet <br /> </td> 
   <td> Mjuk<br /> </td> 
   <td> Avvisad<br /> </td> 
   <td> Nej<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Android karantän {#android-quarantine}

**För Android v1**

För varje meddelande får Adobe Campaign synkrona fel direkt från FCM-servern. Adobe-kampanjen hanterar dem i farten och genererar hårda eller mjuka fel beroende på hur allvarligt felet är, och nya försök kan utföras:

* Nyttolastlängden har överskridits, anslutningsproblem, problem med tjänsttillgänglighet: återförsök utförd, mjukt fel, felorsak är **[!UICONTROL Refused]**.
* Enhetskvoten har överskridits: inga nya försök, inget mjukt fel, felorsaken är **[!UICONTROL Refused]**.
* Ogiltig eller oregistrerad token, oväntat fel, problem med avsändarkontot: inget nytt försök, hårt fel, felorsaken är **[!UICONTROL Refused]**.

Arbetsflödet **[!UICONTROL mobileAppOptOutMgt]** körs var sjätte timme för att uppdatera tabellen **AppSubscriptionRcp**. För tokens som deklarerats som oregistrerade eller inte längre giltiga ställs fältet **Inaktiverad** in på **Sant** och prenumerationen som är länkad till den enhetstoken exkluderas automatiskt från framtida leveranser.

Under leveransanalysen läggs alla enheter som är undantagna från målet automatiskt till i tabellen **excludeLogAppSubRcp** .

>[!NOTE]
>
>Här är olika typer av fel för kunder som använder Baidu-kontakten:
>
>* Anslutningsproblem i början av leveransen: feltyp **[!UICONTROL Undefined]**, felorsak **[!UICONTROL Unreachable]**, nytt försök utförs.
>* Anslutningen bröts under en leverans: mjukt fel, felorsak **[!UICONTROL Refused]**, nytt försök utförs.
>* Synkront fel returnerades av Baidu under sändning: hårt fel, felorsak **[!UICONTROL Refused]**, inga nya försök utförs.
>
>Adobe Campaign kontaktar Baidu-servern var 10:e minut för att hämta det skickade meddelandets status och uppdaterar sändningarna. Om ett meddelande deklareras som skickat anges meddelandets status i utsändningsloggarna till **[!UICONTROL Received]**. Om Baidu deklarerar ett fel anges statusen till **[!UICONTROL Failed]**.

**För Android V2**

Android V2-karantänmekanismen använder samma process som Android V1, samma sak gäller för prenumerations- och exkluderingsuppdateringen. Mer information finns i avsnittet [Android V1](#android-quarantine).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Scenario</strong><br /> </td> 
   <td> <strong>Status</strong><br /> </td> 
   <td> <strong>Felmeddelande</strong><br /> </td> 
   <td> <strong>Feltyp</strong><br /> </td> 
   <td> <strong>Felorsak</strong><br /> </td> 
   <td> <strong>Försök igen</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Fas för skapande/analys av meddelanden: ogiltiga nyckelord används i anpassade fält <br /> </td> 
   <td> Fel <br /> </td> 
   <td> Följande nyckelord kan inte användas: {1}<br /> </td> 
   <td> Mjuk<br /> </td> 
   <td> </td> 
   <td> Nej<br /> </td> 
  </tr> 
  <tr> 
   <td> Fas för att skapa/analysera meddelanden: nyttolasten är för stor <br /> </td> 
   <td> Fel <br /> </td> 
   <td> Meddelandet är för stort: {1} bitar, endast {2} är auktoriserade<br /> </td> 
   <td> Mjuk<br /> </td> 
   <td> Avvisad<br /> </td> 
   <td> Nej<br /> </td> 
  </tr> 
  <tr> 
   <td> Nätverksanslutningen bröts under sändning av <br /> </td> 
   <td> Fel <br /> </td> 
   <td> Inget svar från tjänsten Firebase Cloud Messaging på adressen: {1}<br /> </td> 
   <td> Mjuk<br /> </td> 
   <td> Onåbar<br /> </td> 
   <td> Ja<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM-meddelandeavvisande: FCM-servern är inte tillgänglig för tillfället (till exempel med timeout). <br /> </td> 
   <td> Fel <br /> </td> 
   <td> Tjänsten Firebase Cloud Messaging är inte tillgänglig för tillfället<br /> </td> 
   <td> Mjuk<br /> </td> 
   <td> Onåbar<br /> </td> 
   <td> Ja<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM-meddelandeavvisande: Fel vid autentisering av avsändarkontot <br /> </td> 
   <td> Fel <br /> </td> 
   <td> Det gick inte att identifiera utvecklarkontot. Kontrollera ditt ID och lösenord <br /> </td> 
   <td> Mjuk<br /> </td> 
   <td> Avvisad<br /> </td> 
   <td> Nej<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM-meddelandeavvisande: Enhetskvoten har överskridits <br /> </td> 
   <td> Fel <br /> </td> 
   <td> </td> 
   <td> Mjuk<br /> </td> 
   <td> Avvisad<br /> </td> 
   <td> Ja<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM-meddelandeavvisande: Ogiltig registrering/inte registrerad<br /> </td> 
   <td> Fel <br /> </td> 
   <td> </td> 
   <td> Hård<br /> </td> 
   <td> Okänd användare: <br /> </td> 
   <td> Nej<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM-meddelandeavvisande: Alla andra fel <br /> </td> 
   <td> Fel <br /> </td> 
   <td> Firebase Cloud Messaging-servern returnerade en oväntad felkod: {1} </td> 
   <td> </td> 
   <td> Avvisad<br /> </td> 
   <td> Nej<br /> </td> 
  </tr> 
    <tr> 
   <td> FCM-meddelandeavvisande: Ogiltigt argument <br /> </td> 
   <td> Fel <br /> </td> 
   <td> INVALID_ARGUMENT </td> 
   <td> Ignorerad</td> 
   <td> Odefinierad<br /> </td> 
   <td> Nej<br /> </td> 
  </tr>
    <tr> 
   <td> FCM-meddelandeavvisande: Autentiseringsfel från tredje part <br /> </td> 
   <td> Fel <br /> </td> 
   <td> THIRD_PARTY_AUTH_ERROR </td> 
   <td> Ignorerad</td>
   <td> Avvisad<br /> </td> 
   <td> Ja<br /> </td> 
  </tr>
    <tr> 
   <td> FCM-meddelandeavvisande: Avsändarens ID matchar inte<br /> </td> 
   <td> Fel <br /> </td> 
   <td> SENDER_ID_MISMATCH </td> 
   <td> Mjuk</td>
   <td> Okänd användare: <br /> </td> 
   <td> Nej<br /> </td> 
  </tr>
    <tr> 
   <td> FCM-meddelandeavvisande: Avregistrerad<br /> </td> 
   <td> Fel <br /> </td>
   <td> OREGISTRERAD </td> 
   <td> Hård</td> 
   <td> Okänd användare: <br /> </td> 
   <td> Nej<br /> </td> 
  </tr>
    <tr> 
   <td> FCM-meddelandeavvisande: Intern<br /> </td> 
   <td> Fel <br /> </td> 
   <td> INTERN </td> 
   <td> Ignorerad</td> 
   <td> Avvisad<br /> </td> 
   <td> Ja<br /> </td> 
  </tr>
    <tr> 
   <td> FCM-meddelandeavvisande: Otillgänglig<br /> </td> 
   <td> Fel <br /> </td> 
   <td> OTILLGÄNGLIG</td> 
   <td> Ignorerad</td> 
   <td> Avvisad<br /> </td> 
   <td> Ja<br /> </td> 
  </tr>
    <tr> 
   <td> FCM-meddelandeavvisande: oväntad felkod <br /> </td> 
   <td> Fel <br /> </td> 
   <td> oväntad felkod</td> 
   <td> Ignorerad</td> 
   <td> Avvisad<br /> </td> 
   <td> Nej<br /> </td> 
  </tr>
  <tr> 
   <td> Autentisering: Anslutningsproblem <br /> </td> 
   <td> Fel <br /> </td> 
   <td> Det går inte att ansluta till autentiseringsservern </td> 
   <td> Ignorerad</td>
   <td> Avvisad<br /> </td> 
   <td> Ja<br /> </td> 
  </tr>
    <tr> 
   <td> Autentisering: Oauktoriserad klient eller omfång i begäran.<br /> </td> 
   <td> Fel <br /> </td> 
   <td> unauthorized_client </td> 
   <td> Ignorerad</td>
   <td> Avvisad<br /> </td> 
   <td> Nej<br /> </td> 
  </tr>
    <tr> 
   <td> Autentisering: Klienten saknar behörighet att hämta åtkomsttoken med den här metoden, eller klienten har inte behörighet för de begärda scopen.<br /> </td> 
   <td> Fel <br /> </td> 
   <td> unauthorized_client </td> 
   <td> Ignorerad</td>
   <td> Avvisad<br /> </td> 
   <td> Nej<br /> </td> 
  </tr>
    <tr> 
   <td> Autentisering: Åtkomst nekad<br /> </td> 
   <td> Fel <br /> </td>
   <td> access_deny</td> 
   <td> Ignorerad</td>
   <td> Avvisad<br /> </td> 
   <td> Nej<br /> </td> 
  </tr>
    <tr> 
   <td> Autentisering: Ogiltig e-postadress <br /> </td> 
   <td> Fel <br /> </td> 
   <td> invalid_grant </td> 
   <td> Ignorerad</td> 
   <td> Avvisad<br /> </td> 
   <td> Nej<br /> </td> 
  </tr>
    <tr> 
   <td> Autentisering: Ogiltig JWT<br /> </td> 
   <td> Fel <br /> </td> 
   <td> invalid_grant </td> 
   <td> Ignorerad</td> 
   <td> Avvisad<br /> </td> 
   <td> Nej<br /> </td> 
  </tr>
    <tr> 
   <td> Autentisering: Ogiltig JWT-signatur <br /> </td> 
   <td> Fel <br /> </td> 
   <td> invalid_grant </td> 
   <td> Ignorerad</td> 
   <td> Avvisad<br /> </td> 
   <td> Nej<br /> </td> 
  </tr>
    <tr> 
   <td> Autentisering: Ogiltig OAuth-scope eller angiven ID-tokenpublik<br /> </td> 
   <td> Fel <br /> </td> 
   <td> unauthorized_client</td> 
   <td> Ignorerad</td> 
   <td> Avvisad<br /> </td> 
   <td> Nej<br /> </td> 
  </tr>
    <tr> 
   <td> Autentisering: OAuth-klienten inaktiverad<br /> </td> 
   <td> Fel <br /> </td> 
   <td> disabled_client</td> 
   <td> Ignorerad</td> 
   <td> Avvisad<br /> </td> 
   <td> Nej<br /> </td> 
  </tr>
 </tbody> 
</table>

## SMS-karantän {#sms-quarantines}

**För standardanslutningar**

Karantänmekanismen för SMS-meddelanden är globalt densamma som den allmänna processen. Se [Om karantän](#about-quarantines). Specifikationerna för SMS anges nedan.

>[!NOTE]
>
>Tabellen **[!UICONTROL Delivery log qualification]** gäller inte för den allmänna SMPP **-anslutningen** Extended.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Scenario</strong><br /> </td> 
   <td> <strong>Status</strong><br /> </td> 
   <td> <strong>Felmeddelande</strong><br /> </td> 
   <td> <strong>Feltyp</strong><br /> </td> 
   <td> <strong>Felorsak</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Skickat till providern <br /> </td> 
   <td> Skickat <br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Mottaget på mobilen <br /> </td> 
   <td> Mottaget <br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Ett fel returnerades av providern <br /> </td> 
   <td> Fel <br /> </td> 
   <td> Ett fel uppstod när data togs emot (SR eller MO)<br /> </td> 
   <td> Mjuk<br /> </td> 
   <td> Onåbar<br /> </td> 
  </tr> 
  <tr> 
   <td> Ogiltig MT-bekräftelse <br /> </td> 
   <td> Fel <br /> </td> 
   <td> Felet {1} uppstod när bekräftelseramen för sändningsfrågan <br /> bearbetades </td> 
   <td> Mjuk<br /> </td> 
   <td> Onåbar<br /> </td> 
  </tr> 
  <tr> 
   <td> Ett fel uppstod när MT<br /> skickades </td> 
   <td> Fel <br /> </td> 
   <td> Fel när meddelanden <br /> skickades </td> 
   <td> Mjuk<br /> </td> 
   <td> Onåbar<br /> </td> 
  </tr> 
 </tbody> 
</table>

**För den utökade allmänna SMPP-anslutningen**

När SMPP-protokollet används för att skicka SMS-meddelanden hanteras felhanteringen på ett annat sätt. Mer information om den utökade allmänna SMPP-anslutningen finns på [den här sidan](sms-set-up.md#creating-an-smpp-external-account).

SMPP-kopplingen hämtar data från SR-meddelandet (statusrapport) som returneras med reguljära uttryck (regex) för att filtrera innehållet. Dessa data matchas sedan mot informationen i tabellen **[!UICONTROL Delivery log qualification]** (som är tillgänglig via menyn **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]**).

Innan en ny typ av fel kvalificeras är felorsaken alltid inställd på **Refused** som standard.

>[!NOTE]
>
>Feltyperna och orsakerna till felet är desamma som för e-postmeddelanden. Se [Leveransfeltyper och orsaker](understanding-delivery-failures.md#delivery-failure-types-and-reasons).
>
>Be leverantören om en lista över status- och felkoder för att ange korrekta feltyper och orsaker till felet i tabellen för leveransloggens kvalificeringsregister.

Exempel på ett genererat meddelande:

```
SR Generic DELIVRD 000|#MESSAGE#
```

* Alla felmeddelanden börjar med **SR** för att skilja mellan SMS-felkoder och e-postfelkoder.
* Den andra delen (**Allmänt** i det här exemplet) av felmeddelandet refererar till namnet på SMSC-implementeringen, som definieras i fältet **[!UICONTROL SMSC implementation name]** i det externa SMS-kontot. Läs [den här sidan](sms-set-up.md#creating-an-smpp-external-account).

  Eftersom samma felkod kan ha olika innebörd för varje provider kan du med det här fältet veta vilken provider som genererade felkoden. Du kan sedan hitta felet i den aktuella providerns dokumentation.

* Den tredje delen (**DELIVRD** i det här exemplet) av felmeddelandet motsvarar statuskoden som hämtats från SR med statusextraheringsregex som definierats i det externa SMS-kontot.

  Den här regionen anges på fliken **[!UICONTROL SMSC specificities]** i det externa kontot. Läs [den här sidan](sms-set-up.md#creating-an-smpp-external-account).

  ![](assets/tech_quarant_error_regex.png)

  Regex extraherar som standard fältet **stat:** enligt definitionen i avsnittet **Bilaga B** i specifikationen **SMPP 3.4**.

* Den fjärde delen (**000** i det här exemplet) av felmeddelandet motsvarar den felkod som extraheras från SR med hjälp av den felkodsextraheringsregex som definierats i det externa SMS-kontot.

  Den här regionen anges på fliken **[!UICONTROL SMSC specificities]** i det externa kontot. Läs [den här sidan](sms-set-up.md#creating-an-smpp-external-account).

  Regex extraherar som standard fältet **err:** enligt definitionen i avsnittet **Bilaga B** i specifikationen **SMPP 3.4**.

* Allt som kommer efter lodstreck (|) visas bara i kolumnen **[!UICONTROL First text]** i tabellen **[!UICONTROL Delivery log qualification]**. Det här innehållet ersätts alltid av **#MESSAGE#** efter att meddelandet har normaliserats. Med den här processen undviker du att ha flera poster för liknande fel och den är samma som för e-postmeddelanden. Mer information om detta finns i [Studsa e-postkvalificering](understanding-delivery-failures.md#bounce-mail-qualification).

Den utökade generiska SMPP-anslutningen använder en heuristisk metod för att hitta rimliga standardvärden: om statusen börjar med **DELIV** betraktas den som lyckad eftersom den matchar de vanliga statusvärdena **DELIVRD** eller **DELIVERED** som används av de flesta leverantörer. All annan status leder till ett allvarligt fel.
