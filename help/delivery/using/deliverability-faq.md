---
title: Viktiga punkter vid hantering av leveranser i Adobe Campaign Classic
description: Vilka är de viktigaste punkterna att kontrollera vid hantering av leveranser i Adobe Campaign Classic?
page-status-flag: never-activated
uuid: 2681042b-3018-42ae-b252-2367b56616bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 6a394eeb-fbe1-4712-bb13-db5d7965fb73
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 15581517df8d2f397285bbadebd83b7f4539dfd7
workflow-type: tm+mt
source-wordcount: '1324'
ht-degree: 0%

---


# Felsökning av slutprodukter{#deliverability-faq}

Har du något leveransproblem? Du kan hitta lösningen här.

## MX-regelfel {#mx-rule-error}

**Vad betyder felmeddelandet&quot;kvoter har uppfyllts&quot;?**

Det här meddelandet anger att du har nått kvotgränsen för en viss MX och att du måste vänta för att kunna skicka ytterligare ett e-postmeddelande till den här providern.

I Adobe Campaign finns en konfiguration för hur många e-postmeddelanden per timme som kan skickas. Denna konfiguration måste användas med vaksamhet, eftersom det nummer som definieras i instansen avser antalet anslutningar som görs med Internet-leverantören och inte antalet e-postmeddelanden som faktiskt skickas.

Det innebär att en anslutning kan använda en MX-regel utan att skicka ett e-postmeddelande. I det här fallet måste en konfiguration med en IP-adress eller en domän med dåligt rykte försöka med flera anslutningar innan ett e-postmeddelande skickas. För varje försök används ett meddelande per timkredit. Resultatet av marknadsföringskampanjen kommer att få en betydande effekt.

Därför är&quot;kvoter uppfyllda&quot; inte bara ett konfigurationsproblem, utan kan även kopplas till rykte. Det är viktigt att analysera felmeddelanden i [SMTP-loggen](../../production/using/monitoring-processes.md#smtp-errors-per-domain).

Mer information om MX-konfiguration finns i [det här avsnittet](../../installation/using/email-deliverability.md#mx-configuration).

## Samma felmeddelande för en Internet-leverantör {#same-error-for-an-isp}

**Varför får jag alltid samma felmeddelande för en viss Internet-leverantör?**

Om du alltid får samma felmeddelande för en Internet-leverantör, kan din e-postadress eller IP-adress ha identifierats som defekt av Internet-leverantören. Utför följande rekommendationer:
* Kontrollera om du får en stor andel fel kopplade till obefintliga e-postadresser (okända **** användare).
* Uppdatera dina prenumerationsformulär för att upptäcka eventuella fel i de angivna domännamnen (till exempel: gmaul.com eller yaho.com).
* Om du märker fel som anger att dina meddelanden har deklarerats som skräppost, eller att dina meddelanden alltid är blockerade, kan du försöka utesluta mottagare som inte har öppnat eller klickat i något av dina meddelanden de senaste 12 månaderna från målet.

Om problemet kvarstår kontaktar du de kommersiella tjänsterna eller leveranstjänsterna, Adobe Campaign Client Care eller Adobe Campaign-supporten.

## Svartlistning kontra karantän {#blacklisting-versus-quarantine}

* **Vad är skillnaden mellan en svartlistad e-postadress och en e-postadress i karantän?**

   * Statusen **[!UICONTROL Blacklisted]** är ett resultat av en feedbackslinga (när en person rapporterar ett meddelande som skräppost).

   * Statusen **[!UICONTROL Quarantined]** är ett resultat av en mjuk eller hård studsa.
   Mer information finns i [det här avsnittet](../../delivery/using/understanding-quarantine-management.md#quarantine-vs-blacklisting).

* **Vad betyder de olika anledningarna till karantänfel?**

   Här följer tio möjliga orsaker: inte definierad, okänd användare, ogiltig domän, svartlistad adress, nekad, fel ignorerad, ej tillgänglig, konto inaktiverat, postlåda full, inte ansluten.

   Mer information finns i [Om karantänhantering](../../delivery/using/understanding-quarantine-management.md).

## Osvartlistning {#unblacklisting}

* **En av mina mottagare blev svartlistad av misstag. Hur avlistar jag dem så att jag kan börja skicka dem igen?**

   * Gå till **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**.
   * I informationen för motsvarande post anger du värdet för **[!UICONTROL Status]** fältet till **[!UICONTROL Valid]**.
   * Spara posten.

* **Hur kan jag ta reda på om en av mina IP-adresser är svartlistad? Hur avsvartlistar jag mina IP-adresser?**

   Om du vill kontrollera om din IP-adress är svartlistad kan du använda olika webbplatser för att verifiera den:
   * [https://mxtoolbox.com/](https://mxtoolbox.com/)
   * [https://whatismyipaddress.com/blacklist-check](https://whatismyipaddress.com/blacklist-check)
   * [https://www.blacklistalert.org/](https://www.blacklistalert.org/)
   I allmänhet returnerar resultatet av IP-adresskontrollen en lista som innehåller information om svartlistan och även namnet på den webbplats som svartlistade IP-adressen.

   Genom att klicka på motsvarande länk kan du komma åt webbplatsinformationen. Sedan kan du begära att din webbplats avlistas från den webbplats som svartlistade IP-adressen.

   >[!NOTE]
   >
   >Borttagningsprocessen kan variera beroende på webbplatsen. Vissa webbplatser kräver att du skapar ett konto, medan andra bara behöver du ange IP-adressen.

## God praxis {#best-practices}

Nedan följer några tips som kan hjälpa dig att identifiera och åtgärda leveransproblem.

### Identifiera ett leveransproblem {#identify-deliverability-issue}

Följande element kan dra uppmärksamheten till dig:

* Postads- eller kampanjstatistik: avbeställning, missbruk, klagomål och/eller avhoppsfrekvens är högre än vanligt.
* Prenumerationsaktivitet: öppnas, klickningar och/eller transaktioner är lägre än vanligt.
* Seed-konton visar filtrerade eller olevererade utskick.

### Hypotetiskt möjliga orsaker {#potential-causes}

Ställ följande frågor för att identifiera möjliga orsaker till leveransproblemet:

* Har det nyligen skett en förändring i listsegmenteringen?
* Har jag skaffat några nya datakällor?
* Skickade jag oavsiktligt en karantänfil?
* Kan problemet bero på mitt meddelandeinnehåll?
* Skickas jag ofta tillräckligt för att behålla värma IP-adresser?
* Segmenterar jag mina utskick efter aktivitet/engagemang, eller skickar jag fullständiga filer?
* Vad är det &quot;säkra&quot; segmentet i min fil i termer av senaste användning?
* Har jag strategier för omaktivering och återbekräftelse för segment som inte definieras som säkra?

### Åtgärda problemet {#address-issue}

**Klagomål**

Klagomålen definieras av prenumeranter som **rapporterar e-post som skräppost** genom att klicka på motsvarande knapp i sin inkorg.

Om ditt leveransproblem har orsakats av klagomål:
* Du måste försöka avgöra varför mottagarna klagar.
* Du kanske också vill flytta länken för att avbryta prenumerationen till det övre av e-postmeddelandet. Detta uppmuntrar prenumeranter att avbryta prenumerationen i stället för att klaga på skräppostknappen.

Avsändare kan samla in en mängd information från sina [feedback-slingor](../../delivery/using/technical-recommendations.md#feedback-loop) :
* Det är viktigt att lagra data och leta efter mönster i saker som anmälningskälla, hur länge adressen har prenumererats eller till och med vissa beteendedemografiska profiler.
* Klagomål kan ofta identifiera en riskfylld datakälla eller ett risksegment i filen. Risky definieras som den som mest sannolikt klagar, vilket kan skada anseendet, och i sin tur antalet inkorgar.

Klagomålen kommer också från prenumeranter som inte längre vill ha e-post:
* Detta kan ofta bero på för många meddelanden, att de som prenumererar inte uppfattade meddelandet, att de inte förväntade sig meddelandet eller inte minns att de valde.
* Det är också viktigt att utföra en granskning för att säkerställa att alla insamlingspunkter är tydliga och att det inte finns några förkryssade kryssrutor i inköpsplatserna.
* Du bör också skicka ett välkomstmeddelande när prenumeranter väljer att gå med för att ange tonen och förklara hur ofta de kan förvänta sig att få e-postmeddelanden från dig.

**Datasäkerhet**

**Hårda studsar** inträffar när du skickar till en **adress** som inte kan levereras hos en Internet-leverantör. En adress kan vara olevererbar av många orsaker, till exempel:
* Felstavad adress. Detta kan åtgärdas med en datavalideringstjänst i realtid eller genom att kräva en bekräftad anmälan innan marknadsföringsmeddelanden skickas till den adressen.
* Felaktig lista eller datakälla. Om det kommer från en ny källa kontrollerar du hur adresserna samlades in och att det fanns behörighet.
* Posta till en adress som vid ett tillfälle var aktiv, men som har stängts eller avslutats efter en inaktivitetsperiod.

**Engagemang**

Förutom klagomål och informationskvalitet fokuserar internetleverantörer mer än någonsin på **positivt engagemang** för att fatta leveransbeslut. De vill se om era prenumeranter öppnar era e-postmeddelanden eller tar bort dem utan att läsa dem. Eftersom de inte delar dessa data med avsändare måste vi använda den information vi har och översätta öppningar/klick/transaktioner som engagemang.

Som en del av det pågående anseendeunderhållet är det viktigt att förstå hur engagerade prenumeranter finns på er lista och utveckla en **riskhierarki** för senaste nytt för prenumeranterna i varje fil. Senaste tid definieras som senaste öppnings-/klicknings-/transaktionsdatum eller registreringsdatum. Tidsramen kan skilja sig åt lodrätt. Så här gör du:

1. Fastställ aktiva (&quot;säkra&quot;) segment för varje vertikal. Detta är vanligtvis prenumeranter som har varit aktiva under de senaste 3-6 månaderna.
1. Minska frekvensen för inaktivitet.
1. Skapa en [omengagemangsserie](../../delivery/using/re-engagement-best-practices.md) för måttliga riskinaktioner. Det är normalt 6-9 månader utan engagemang.
1. Utveckla en bekräftelsekampanj för riskinaktivitet. Detta är vanligtvis prenumeranter som inte har interagerat med ett e-postmeddelande på 9-12 månader.
1. Slutligen anger du en avlämningsregel och tar bort prenumeranter som inte har öppnat e-postmeddelanden på&quot;x&quot; månader. Vi rekommenderar vanligtvis 12+ månader, men det kan skilja sig åt beroende på försäljnings- och köpcykel.
