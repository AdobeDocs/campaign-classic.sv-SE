---
product: campaign
title: Förstå karantänshantering
description: Förstå karantänshantering
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
exl-id: cfd8f5c9-f368-4a31-a1e2-1d77ceae5ced
source-git-commit: 98380c18b915cfebc980e68f9840f9d8919eaca4
workflow-type: tm+mt
source-wordcount: '2614'
ht-degree: 14%

---

# Förstå karantänshantering{#understanding-quarantine-management}

![](../../assets/common.svg)

## Om karantäner {#about-quarantines}

Adobe Campaign hanterar en lista med adresser i karantän. Mottagare vars adress sätts i karantän exkluderas som standard vid leveransanalys och anges inte som mål. En e-postadress kan sättas i karantän när till exempel postlådan är full eller om adressen inte finns. Under alla omständigheter uppfyller karantänförfarandet de särskilda regler som beskrivs nedan.

>[!NOTE]
>
>Detta avsnitt gäller för onlinekanaler: e-post, SMS, push-meddelanden.

### Optimera leveransen genom karantäner {#optimizing-your-delivery-through-quarantines}

De profiler vars e-postadresser eller telefonnummer är i karantän exkluderas automatiskt vid förberedelse av meddelanden (se [Identifiera karantänadresser vid en leverans](#identifying-quarantined-addresses-for-a-delivery)).  Detta snabbar upp leveranserna eftersom felfrekvensen avsevärt påverkar leveranshastigheten.

Vissa internetleverantörer betraktar automatisk e-post som skräppost om antalet ogiltiga adresser är för högt.  Med karantän kan du därför undvika att läggas till i blockeringslista av dessa leverantörer.

Dessutom bidrar karantäner till att minska SMS-kostnaderna genom att utesluta felaktiga telefonnummer från leveranser. Mer information om de bästa sätten för att skydda och optimera leveranser finns på [den här sidan](delivery-best-practices.md) .

### Karantän mot blockeringslista {#quarantine-vs-denylist}

**Karantän** gäller bara en adress, inte själva profilen.    Det innebär att om två profiler har samma e-postadress så påverkas båda om adressen sätts i karantän.

På samma sätt kan en profil vars e-postadress sätts i karantän uppdatera sin profil och ange en ny adress. Den kan sedan användas av leveransåtgärder igen.

Att vara på **blockeringslista**&#x200B;å andra sidan resulterar det i att profilen inte längre används som mål för någon leverans, t.ex. efter en avanmälan (avanmälan).

>[!NOTE]
>
>När en användare svarar på ett SMS-meddelande med ett nyckelord som&quot;STOP&quot; för att avanmäla sig från SMS-leveranser, läggs deras profil inte till blockeringslista, som i avanmälningsprocessen via e-post. Profilens telefonnummer skickas till karantänen så att användaren fortsätter att ta emot e-postmeddelanden.

## Identifiera adresser i karantän {#identifying-quarantined-addresses}

Adresser i karantän kan användas för en viss leverans eller för hela plattformen.

### Identifiera adresser i karantän för en leverans {#identifying-quarantined-addresses-for-a-delivery}

Adresser i karantän för en viss leverans listas i leveransloggarna på kontrollpanelen under leveransförberedelsefasen (se [Leveransloggar och historik](delivery-dashboard.md#delivery-logs-and-history)).

### Identifiera adresser i karantän för hela plattformen {#identifying-quarantined-addresses-for-the-entire-platform}

Administratörer kan lista adresserna i karantän för hela plattformen från **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]** nod.

>[!NOTE]
>
>Den här menyn listar element i karantän för **e-post**, **SMS** och **push-meddelanden** .

Följande information finns för varje adress:

![](assets/tech_quarant_npai.png)

>[!NOTE]
>
>Ökningen av antalet karantän är en normal effekt som har samband med databasens slitage. Om en e-postadress till exempel anses ha en livslängd på tre år och mottagartabellen ökar med 50 % varje år, kan ökningen av antalet karantän beräknas enligt följande:
>
>Slutet av år 1: (1*0.33)/(1+0.5)=22 %.
Slutet av år 2: ((1,22*0,33)+0,33)/(1,5+0,75)=32,5 %.

### Identifiera adresser i karantän i leveransrapporter {#identifying-quarantined-addresses-in-delivery-reports}

Följande rapporter innehåller information om adresserna i karantän:

* För varje leverans visas **[!UICONTROL Delivery summary]** rapporten visar antalet adresser i karantän i leveransmålet. Den visar:

   * Antalet adresser som placerats i karantän under leveransanalysen.

   * Antalet adresser som placerats i karantän efter leveransåtgärden.

* The **[!UICONTROL Non-deliverables and bounces]** rapporten innehåller information om adresserna i karantän, typer av fel som uppstått osv. samt felinformation per domän.

Du kan söka efter den här informationen för alla leveranser av plattformen (**[!UICONTROL Home page > Reports]**) eller för en viss leverans. Du kan också skapa anpassade rapporter och välja vilken information som ska visas.

### Identifiera adresser i karantän för en mottagare {#identifying-quarantined-addresses-for-a-recipient}

Du kan slå upp status för e-postadressen för alla mottagare. Det gör du genom att markera mottagarprofilen och klicka på knappen **[!UICONTROL Deliveries]** -fliken. För alla leveranser till den mottagaren kan du ta reda på om adressen misslyckades, placerades i karantän under analysen osv. För varje mapp kan du bara visa mottagare vars e-postadress är i karantän. Om du vill göra det använder du **[!UICONTROL Quarantined email address]** programfilter.

![](assets/tech_quarant_recipients_filter.png)

### Ta bort en adress i karantän {#removing-a-quarantined-address}

Om det behövs kan du ta bort en adress manuellt från karantänlistan. Dessutom tas adresser som matchar specifika villkor automatiskt bort från karantänlistan av **[!UICONTROL Database cleanup]** arbetsflöde.

Så här tar du bort en adress manuellt från karantänlistan:

* Du kan ändra dess status till **[!UICONTROL Valid]** från **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]** nod.

   ![](assets/tech_quarant_error_status.png)

* Du kan också ändra dess status till **[!UICONTROL Allowlisted]**. I det här fallet finns adressen kvar på karantänlistan, men den kommer att riktas systematiskt, även om ett fel inträffar.

Adresserna tas automatiskt bort från karantänlistan i följande fall:

* Adresser i en **[!UICONTROL With errors]** status kommer att tas bort från karantänlistan efter en slutförd leverans.
* Adresser i en **[!UICONTROL With errors]** status tas bort från karantänlistan om den senaste mjuka studsen inträffade för mer än 10 dagar sedan. Mer information om mjuk felhantering finns i [det här avsnittet](#soft-error-management).
* Adresser i en **[!UICONTROL With errors]** status som studsade med **[!UICONTROL Mailbox full]** felet tas bort från karantänlistan efter 30 dagar.

Status ändras sedan till **[!UICONTROL Valid]**.

>[!IMPORTANT]
Mottagare med en adress i en **[!UICONTROL Quarantine]** eller **[!UICONTROL On denylist]** status tas aldrig bort, även om de får ett e-postmeddelande.

Du kan ändra antalet fel och perioden mellan två fel. Om du vill göra det ändrar du motsvarande inställningar i distributionsguiden (**[!UICONTROL Email channel]** > **[!UICONTROL Advanced parameters]**). Mer information om distributionsguiden finns i [det här avsnittet](../../installation/using/deploying-an-instance.md).

## Villkor för att skicka en adress till karantän {#conditions-for-sending-an-address-to-quarantine}

Adobe Campaign hanterar karantän enligt typ av leveransfel och den orsak som tilldelats vid kvalificering av felmeddelanden (se [E-poststudsar](understanding-delivery-failures.md#bounce-mail-qualification)) och [Typ av leveransfel och orsaker](understanding-delivery-failures.md#delivery-failure-types-and-reasons).

* **Ignorerad avvikelse**: ignorerade avvikelser skickar ingen adress till karantänen.
* **Kritisk avvikelse**: motsvarande e-postadress skickas omedelbart till karantänen.
* **Icke-kritisk avvikelse**: En icke-kritiskt avvikelse skickar inte en adress till karantän omedelbart men ökar dock felräknaren.  Mer information finns i [Mjuk felhantering](#soft-error-management).

Om en användare kvalificerar ett e-postmeddelande som skräppost ([feedback-slinga](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#feedback-loops)) dirigeras meddelandet automatiskt om till en teknisk brevlåda som hanteras av Adobe. Användarens e-postadress skickas sedan automatiskt till karantänen.

I listan över adresser i karantän visas **[!UICONTROL Error reason]** anger varför den valda adressen placerades i karantän. Karantänen i Adobe Campaign är skiftlägeskänslig.    Se till att importera e-postadresser med små bokstäver så att inte e-postadresserna fortsätter att ta emot meddelanden.

![](assets/tech_quarant_error_reasons.png)

### Mjuk felhantering {#soft-error-management}

I motsats till hårda fel skickar inte mjuka fel en adress direkt till karantän, utan i stället ökar de en felräknare.

* När felräknaren når gränsvärdet sätts adressen i karantän.
* I standardkonfigurationen anges tröskelvärdet till fem avvikelser, där två avvikelser klassas som viktiga om de inträffar med minst 24 timmars mellanrum.        Adressen sätts i karantän vid den femte avvikelsen.    
* Tröskelvärdet för felräknaren kan ändras.  Mer information finns i [Försök igen efter ett tillfälligt leveransfel](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure).

Felräknaren initieras om om det senaste allvarliga felet inträffade för mer än 10 dagar sedan. Adressstatusen ändras sedan till **Giltig** och tas bort från listan över karantäner av **Databasrensning** arbetsflöde.

## Kantlinjer för push-meddelanden {#push-notification-quarantines}

Karantänmekanismen för push-meddelanden är globalt densamma som den allmänna processen. Se [Om karantäner](#about-quarantines). Vissa fel hanteras dock på olika sätt för push-meddelanden. För vissa mjuka fel utförs till exempel inga försök inom samma leverans. Specifikationerna för push-meddelanden anges nedan. Mekanismen för återförsök (antal återförsök, frekvens) är densamma som för e-postmeddelanden.

Objekten som sätts i karantän är enhetstoken.

### iOS karantän {#ios-quarantine}

HTTP/V2-protokollet tillåter direkt feedback och status för varje push-leverans. Om HTTP/V2-protokollkopplingen används anropas inte längre feedbacktjänsten av **[!UICONTROL mobileAppOptOutMgt]** arbetsflöde. En token betraktas som oregistrerad när ett mobilprogram avinstalleras eller installeras om.

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
   <td> Målenhet aktiverad<br /> </td> 
   <td> OK<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Målenhet avstängd<br /> </td> 
   <td> OK<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Användaren inaktiverar meddelanden för programmet<br /> </td> 
   <td> OK<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Skapande/analys av meddelande - nyttolasten är för stor<br /> </td> 
   <td> Fel<br /> </td> 
   <td> Nyttolasten är för lång<br /> </td> 
   <td> Mjuk<br /> </td> 
   <td> Avvisad<br /> </td> 
   <td> Nej<br /> </td> 
  </tr> 
  <tr> 
   <td> Fas för att skapa/analysera meddelanden - oväntat problem med innehållsformat<br /> </td> 
   <td> Fel<br /> </td> 
   <td> Olika felmeddelanden enligt felet<br /> </td> 
   <td> Mjuk<br /> </td> 
   <td> Odefinierad<br /> </td> 
   <td> Nej<br /> </td> 
  </tr> 
  <tr> 
   <td> Certifikatproblem (lösenord, fel osv.) och testa anslutningen till APN-problemet<br /> </td> 
   <td> Fel<br /> </td> 
   <td> Olika felmeddelanden enligt felet<br /> </td> 
   <td> Mjuk<br /> </td> 
   <td> Avvisad<br /> </td> 
   <td> Nej<br /> </td> 
  </tr> 
  <tr> 
   <td> Nätverksanslutningen bröts under sändning<br /> </td> 
   <td> Fel<br /> </td> 
   <td> Anslutningsfel<br /> </td> 
   <td> Odefinierad<br /> </td> 
   <td> Onåbar<br /> </td> 
   <td> Ja<br /> </td> 
  </tr> 
  <tr> 
   <td> Avvisning av APN-meddelande: Avregistrering<br /> användaren har tagit bort programmet eller token har gått ut<br /> </td> 
   <td> Fel<br /> </td> 
   <td> Oregistrerad<br /> </td> 
   <td> Hård<br /> </td> 
   <td> Okänd användare<br /> </td> 
   <td> Nej<br /> </td> 
  </tr> 
  <tr> 
   <td> Avvisning av APN-meddelande: alla andra fel<br /> </td> 
   <td> Fel<br /> </td> 
   <td> Felavvisande orsak kommer att finnas i felmeddelandet<br /> </td> 
   <td> Mjuk<br /> </td> 
   <td> Avvisad<br /> </td> 
   <td> Nej<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Android-karantän {#android-quarantine}

**För Android V1**

För varje meddelande får Adobe Campaign synkrona fel direkt från FCM-servern. Adobe-kampanjen hanterar dem i farten och genererar hårda eller mjuka fel beroende på hur allvarligt felet är, och nya försök kan utföras:

* Nyttolastlängden har överskridits, anslutningsproblem, problem med tjänsttillgänglighet: återförsök utförd, mjukt fel, felorsak **[!UICONTROL Refused]**.
* Enhetskvoten har överskridits: inget nytt försök, mjukt fel, felorsak: **[!UICONTROL Refused]**.
* Ogiltig eller oregistrerad token, oväntat fel, problem med avsändarkontot: inget nytt försök, hårt fel, felorsaken är **[!UICONTROL Refused]**.

The **[!UICONTROL mobileAppOptOutMgt]** arbetsflödet körs var 6:e timme för att uppdatera **AppSubscriptionRcp** tabell. Fältet för tokens som har deklarerats som oregistrerade eller inte längre giltiga **Handikappade** är inställd på **True** och prenumerationen som är länkad till denna enhetstoken exkluderas automatiskt från framtida leveranser.

Under leveransanalysen läggs alla enheter som är undantagna från målet automatiskt till i **excludeLogAppSubRcp** tabell.

>[!NOTE]
Här är olika typer av fel för kunder som använder Baidu-kontakten:
* Anslutningsproblem i början av leveransen: feltyp **[!UICONTROL Undefined]**, felorsak **[!UICONTROL Unreachable]**, återförsök utförs.
* Förlorad anslutning under leverans: mjukt fel, felorsak **[!UICONTROL Refused]**, återförsök utförs.
* Synkront fel returnerades av Baidu under sändning: allvarligt fel, felorsak **[!UICONTROL Refused]**, inga nya försök utförs.
Adobe Campaign kontaktar Baidu-servern var 10:e minut för att hämta det skickade meddelandets status och uppdaterar sändningarna. Om ett meddelande deklareras som skickat anges meddelandets status i utsändningsloggarna till **[!UICONTROL Received]**. Om Baidu deklarerar ett fel ställs statusen in på **[!UICONTROL Failed]**.

**För Android V2**

Android V2-karantänmekanismen använder samma process som Android V1, samma gäller för prenumerations- och exkluderingsuppdateringen. Mer information finns i [Android V1](#android-quarantine) -avsnitt.

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
   <td> Fas för skapande/analys av meddelanden: ogiltiga nyckelord som används i anpassade fält<br /> </td> 
   <td> Fel<br /> </td> 
   <td> Följande nyckelord kan inte användas: {1}<br /> </td> 
   <td> Mjuk<br /> </td> 
   <td> </td> 
   <td> Nej<br /> </td> 
  </tr> 
  <tr> 
   <td> Fas för skapande/analys av meddelanden: nyttolasten är för stor<br /> </td> 
   <td> Fel<br /> </td> 
   <td> Meddelandet är för stort: {1} bitar, medan endast {2} är behöriga<br /> </td> 
   <td> Mjuk<br /> </td> 
   <td> Avvisad<br /> </td> 
   <td> Nej<br /> </td> 
  </tr> 
  <tr> 
   <td> Nätverksanslutningen bröts under sändning<br /> </td> 
   <td> Fel<br /> </td> 
   <td> Inget svar från tjänsten Firebase Cloud Messaging på adressen: {1}<br /> </td> 
   <td> Mjuk<br /> </td> 
   <td> Onåbar<br /> </td> 
   <td> Ja<br /> </td> 
  </tr> 
  <tr> 
   <td> Avvisning av FCM-meddelande: FCM-servern är inte tillgänglig för tillfället (till exempel med timeout). <br /> </td> 
   <td> Fel<br /> </td> 
   <td> Tjänsten Firebase Cloud Messaging är inte tillgänglig för tillfället<br /> </td> 
   <td> Mjuk<br /> </td> 
   <td> Onåbar<br /> </td> 
   <td> Ja<br /> </td> 
  </tr> 
  <tr> 
   <td> Avvisning av FCM-meddelande: Fel vid autentisering av avsändarkontot<br /> </td> 
   <td> Fel<br /> </td> 
   <td> Det gick inte att identifiera utvecklarkontot. Kontrollera ditt ID och lösenord<br /> </td> 
   <td> Mjuk<br /> </td> 
   <td> Avvisad<br /> </td> 
   <td> Nej<br /> </td> 
  </tr> 
  <tr> 
   <td> Avvisning av FCM-meddelande: Enhetskvoten har överskridits<br /> </td> 
   <td> Fel<br /> </td> 
   <td> </td> 
   <td> Mjuk<br /> </td> 
   <td> Avvisad<br /> </td> 
   <td> Ja<br /> </td> 
  </tr> 
  <tr> 
   <td> Avvisning av FCM-meddelande: Ogiltig registrering/är inte registrerad<br /> </td> 
   <td> Fel<br /> </td> 
   <td> </td> 
   <td> Hård<br /> </td> 
   <td> Okänd användare<br /> </td> 
   <td> Nej<br /> </td> 
  </tr> 
  <tr> 
   <td> Avvisning av FCM-meddelande: Alla andra fel<br /> </td> 
   <td> Fel<br /> </td> 
   <td> Felkoden har returnerats från Firebase Cloud Messaging-servern: {1} </td> 
   <td> </td> 
   <td> Avvisad<br /> </td> 
   <td> Nej<br /> </td> 
  </tr> 
    <tr> 
   <td> Avvisning av FCM-meddelande: Ogiltigt argument<br /> </td> 
   <td> Fel<br /> </td> 
   <td> INVALID_ARGUMENT </td> 
   <td> Ignorerad</td> 
   <td> Odefinierad<br /> </td> 
   <td> Nej<br /> </td> 
  </tr>
    <tr> 
   <td> Avvisning av FCM-meddelande: Autentiseringsfel från tredje part<br /> </td> 
   <td> Fel<br /> </td> 
   <td> THIRD_PARTY_AUTH_ERROR </td> 
   <td> Ignorerad</td>
   <td> Avvisad<br /> </td> 
   <td> Ja<br /> </td> 
  </tr>
    <tr> 
   <td> Avvisning av FCM-meddelande: Avsändarens ID matchar inte<br /> </td> 
   <td> Fel<br /> </td> 
   <td> SENDER_ID_MISMATCH </td> 
   <td> Mjuk</td>
   <td> Okänd användare<br /> </td> 
   <td> Nej<br /> </td> 
  </tr>
    <tr> 
   <td> Avvisning av FCM-meddelande: Oregistrerad<br /> </td> 
   <td> Fel<br /> </td>
   <td> OREGISTRERAD </td> 
   <td> Hård</td> 
   <td> Okänd användare<br /> </td> 
   <td> Nej<br /> </td> 
  </tr>
    <tr> 
   <td> Avvisning av FCM-meddelande: Intern<br /> </td> 
   <td> Fel<br /> </td> 
   <td> INTERN </td> 
   <td> Ignorerad</td> 
   <td> Avvisad<br /> </td> 
   <td> Ja<br /> </td> 
  </tr>
    <tr> 
   <td> Avvisning av FCM-meddelande: Otillgänglig<br /> </td> 
   <td> Fel<br /> </td> 
   <td> OTILLGÄNGLIG</td> 
   <td> Ignorerad</td> 
   <td> Avvisad<br /> </td> 
   <td> Ja<br /> </td> 
  </tr>
    <tr> 
   <td> Avvisning av FCM-meddelande: oväntad felkod<br /> </td> 
   <td> Fel<br /> </td> 
   <td> oväntad felkod</td> 
   <td> Ignorerad</td> 
   <td> Avvisad<br /> </td> 
   <td> Nej<br /> </td> 
  </tr>
  <tr> 
   <td> Autentisering: Anslutningsproblem<br /> </td> 
   <td> Fel<br /> </td> 
   <td> Det går inte att ansluta till autentiseringsservern </td> 
   <td> Ignorerad</td>
   <td> Avvisad<br /> </td> 
   <td> Ja<br /> </td> 
  </tr>
    <tr> 
   <td> Autentisering: Oauktoriserad klient eller omfång i begäran.<br /> </td> 
   <td> Fel<br /> </td> 
   <td> unauthorized_client </td> 
   <td> Ignorerad</td>
   <td> Avvisad<br /> </td> 
   <td> Nej<br /> </td> 
  </tr>
    <tr> 
   <td> Autentisering: Klienten är inte behörig att hämta åtkomsttoken med den här metoden, eller så är klienten inte auktoriserad för något av de begärda scopen.<br /> </td> 
   <td> Fel<br /> </td> 
   <td> unauthorized_client </td> 
   <td> Ignorerad</td>
   <td> Avvisad<br /> </td> 
   <td> Nej<br /> </td> 
  </tr>
    <tr> 
   <td> Autentisering: Åtkomst nekad<br /> </td> 
   <td> Fel<br /> </td>
   <td> access_deny</td> 
   <td> Ignorerad</td>
   <td> Avvisad<br /> </td> 
   <td> Nej<br /> </td> 
  </tr>
    <tr> 
   <td> Autentisering: Ogiltig e-postadress<br /> </td> 
   <td> Fel<br /> </td> 
   <td> invalid_grant </td> 
   <td> Ignorerad</td> 
   <td> Avvisad<br /> </td> 
   <td> Nej<br /> </td> 
  </tr>
    <tr> 
   <td> Autentisering: Ogiltig JWT<br /> </td> 
   <td> Fel<br /> </td> 
   <td> invalid_grant </td> 
   <td> Ignorerad</td> 
   <td> Avvisad<br /> </td> 
   <td> Nej<br /> </td> 
  </tr>
    <tr> 
   <td> Autentisering: Ogiltig JWT-signatur<br /> </td> 
   <td> Fel<br /> </td> 
   <td> invalid_grant </td> 
   <td> Ignorerad</td> 
   <td> Avvisad<br /> </td> 
   <td> Nej<br /> </td> 
  </tr>
    <tr> 
   <td> Autentisering: Ogiltig publik för OAuth-scope eller ID-token har angetts<br /> </td> 
   <td> Fel<br /> </td> 
   <td> unauthorized_client</td> 
   <td> Ignorerad</td> 
   <td> Avvisad<br /> </td> 
   <td> Nej<br /> </td> 
  </tr>
    <tr> 
   <td> Autentisering: OAuth-klient inaktiverad<br /> </td> 
   <td> Fel<br /> </td> 
   <td> disabled_client</td> 
   <td> Ignorerad</td> 
   <td> Avvisad<br /> </td> 
   <td> Nej<br /> </td> 
  </tr>
 </tbody> 
</table>

## SMS-karantän {#sms-quarantines}

**För standardanslutningar**

Karantänmekanismen för SMS-meddelanden är globalt densamma som den allmänna processen. Se [Om karantäner](#about-quarantines). Specifikationerna för SMS anges nedan.

>[!NOTE]
The **[!UICONTROL Delivery log qualification]** tabellen gäller inte för **Utökad allmän SMPP** koppling.

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
   <td> Skickat till providern<br /> </td> 
   <td> Skickat<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Mottaget på mobilen<br /> </td> 
   <td> Mottaget<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Ett fel returnerades av providern<br /> </td> 
   <td> Fel<br /> </td> 
   <td> Fel vid mottagning av data (SR eller MO)<br /> </td> 
   <td> Mjuk<br /> </td> 
   <td> Onåbar<br /> </td> 
  </tr> 
  <tr> 
   <td> Ogiltig MT-bekräftelse<br /> </td> 
   <td> Fel<br /> </td> 
   <td> Felet {1} uppstod när bekräftelseramen för sändningsfrågan bearbetades<br /> </td> 
   <td> Mjuk<br /> </td> 
   <td> Onåbar<br /> </td> 
  </tr> 
  <tr> 
   <td> Fel när MT skickades<br /> </td> 
   <td> Fel<br /> </td> 
   <td> Fel när meddelanden skickades<br /> </td> 
   <td> Mjuk<br /> </td> 
   <td> Onåbar<br /> </td> 
  </tr> 
 </tbody> 
</table>

**För den utökade generiska SMPP-anslutningen**

När SMPP-protokollet används för att skicka SMS-meddelanden hanteras felhanteringen på ett annat sätt. Mer information om den utökade allmänna SMPP-anslutningen finns i [den här sidan](sms-set-up.md#creating-an-smpp-external-account).

SMPP-kopplingen hämtar data från SR-meddelandet (statusrapport) som returneras med reguljära uttryck (regex) för att filtrera innehållet. Dessa data matchas sedan mot informationen i **[!UICONTROL Delivery log qualification]** tabell (tillgänglig via **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** meny).

Innan en ny typ av fel har kvalificerats anges felorsaken alltid till **Avvisad** som standard.

>[!NOTE]
Feltyperna och orsakerna till felet är desamma som för e-postmeddelanden. Se [Typ av leveransfel och orsaker](understanding-delivery-failures.md#delivery-failure-types-and-reasons).
Be leverantören om en lista över status- och felkoder för att ange korrekta feltyper och orsaker till felet i tabellen för leveransloggens kvalificeringsregister.

Exempel på ett genererat meddelande:

```
SR Generic DELIVRD 000|#MESSAGE#
```

* Alla felmeddelanden börjar med **SR** för att skilja mellan SMS-felkoder och e-postfelkoder.
* Andra delen (**Allmän** i det här exemplet) refererar felmeddelandet till namnet på SMSC-implementeringen som definieras i **[!UICONTROL SMSC implementation name]** fält för SMS-externt konto. Läs [den här sidan](sms-set-up.md#creating-an-smpp-external-account).

   Eftersom samma felkod kan ha olika innebörd för varje provider kan du med det här fältet veta vilken provider som genererade felkoden. Du kan sedan hitta felet i den aktuella providerns dokumentation.

* Den tredje delen (**LEVERERA** i det här exemplet) motsvarar felmeddelandet statuskoden som hämtats från SR med statusextraheringsregex som definierats i det externa SMS-kontot.

   Denna region anges i **[!UICONTROL SMSC specificities]** fliken för det externa kontot. Läs [den här sidan](sms-set-up.md#creating-an-smpp-external-account).

   ![](assets/tech_quarant_error_regex.png)

   Regexen extraherar som standard **stat:** fält enligt definitionen i **Tillägg B** i **Specifikation för SMPP 3.4**.

* Fjärde delen (**000** i det här exemplet) motsvarar felmeddelandet den felkod som extraheras från SR med den felkodsextraheringsregex som definieras i det externa SMS-kontot.

   Denna region anges i **[!UICONTROL SMSC specificities]** fliken för det externa kontot. Läs [den här sidan](sms-set-up.md#creating-an-smpp-external-account).

   Regexen extraherar som standard **err:** fält enligt definitionen i **Tillägg B** i **Specifikation för SMPP 3.4**.

* Allt som kommer efter rörlighetssymbolen (|) visas bara i **[!UICONTROL First text]** kolumn i **[!UICONTROL Delivery log qualification]** tabell. Det här innehållet ersätts alltid av **#MESSAGE#** när meddelandet har normaliserats. Med den här processen undviker du att ha flera poster för liknande fel och den är samma som för e-postmeddelanden. Mer information finns i [E-poststudsar](understanding-delivery-failures.md#bounce-mail-qualification).

Den utökade generiska SMPP-anslutningen använder en heuristisk metod för att hitta rimliga standardvärden: om statusen börjar med **DELIV** anses det vara en framgång eftersom det matchar de vanliga statusvärdena **LEVERERA** eller **LEVERERAD** används av de flesta leverantörer. All annan status leder till ett allvarligt fel.
