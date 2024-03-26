---
product: campaign
title: Konfiguration av teknisk e-post
description: Lär dig hur du konfigurerar Campaign för att styra utdata för dina instanser när du levererar e-postmeddelanden
feature: Installation, Deliverability
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
badge-v7-prem: label="lokal och hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 515adad2-6129-450a-bb9e-fc80127835af
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '3100'
ht-degree: 0%

---

# Tekniska e-postkonfigurationer{#email-deliverability}



## Översikt {#overview}

I följande avsnitt ges en översikt över den konfiguration som krävs för att styra utdata från Adobe Campaign-instanser när e-postmeddelanden levereras.

>[!NOTE]
>
>Vissa konfigurationer kan bara utföras av Adobe för distributioner som hanteras av Adobe, till exempel för att få åtkomst till server- och instanskonfigurationsfilerna. Mer information om de olika distributionerna finns i [Värdmodeller](../../installation/using/hosting-models.md) avsnitt eller till [den här sidan](../../installation/using/capability-matrix.md).

Mer information om koncept och bästa metoder för slutprodukter med Adobe Campaign finns i [section](../../delivery/using/about-deliverability.md).

En djupdykning i vad som kan levereras, inklusive alla tekniska rekommendationer om hur man på ett effektivt sätt kan skicka och ta emot e-post via en Adobe-plattform, finns i [Adobe Deliverability Best Practice Guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=sv).

## Verksamhetsprincip {#operating-principle}

Det går att styra utdata från en eller flera Adobe Campaign-instanser för att begränsa antalet e-postmeddelanden som skickas beroende på en domän. Du kan till exempel begränsa utdata till 20 000 per timme i **yahoo.com** adresser, medan 100 000 meddelanden per timme konfigureras för alla andra domäner.

Meddelandeutdata måste kontrolleras för varje IP-adress som används av leveransservrarna (**mta**). Flera **mta** som delas upp på flera datorer och tillhör olika Adobe Campaign-instanser kan dela samma IP-adress för e-postleverans: en process måste skapas för att koordinera användningen av dessa IP-adresser.

Det här är vad **stat** gör: den vidarebefordrar alla anslutningsbegäranden och meddelanden som ska skickas till e-postservrarna för en uppsättning IP-adresser. Statistikservern håller reda på leveranser och kan aktivera eller inaktivera sändning baserat på angivna kvoter.

![](assets/s_ncs_install_mta.png)

* Statistikservern (**stat**) är länkad till en Adobe Campaign-bas för att läsa in dess konfiguration.
* Leveransservrarna (**mta**) använder du en UDP för att kontakta en statistikserver som inte alltid tillhör sin egen instans.

### Leveransservrar {#delivery-servers}

The **mta** distribuerar meddelanden till **mtachild** underordnade moduler. Varje **mtachild** förbereder meddelanden innan en auktorisering begärs från statistikservern och skickar dem.

Stegen är följande:

1. The **mta** väljer giltiga meddelanden och tilldelar dem en tillgänglig **mtachild**.
1. The **mtachild** läser in all information som krävs för att skapa meddelandet (innehåll, anpassningselement, bilagor, bilder osv.) och vidarebefordrar meddelandet till **E-posttrafikschaper**.
1. Så snart som e-posttrafikbladet får statistikserverns tillstånd (**smtp-status**) skickas meddelandet till mottagaren.

![](assets/s_ncs_install_email_traffic_shaper.png)

### E-postserverstatistik och begränsningar {#email-server-statistics-and-limitations}

Statistikservern underhåller följande statistik för varje e-postserver som tar emot meddelanden:

* Antal öppna anslutningar vid tidpunkt,
* Antal meddelanden som skickats under den senaste timmen,
* Frekvens för lyckade/avvisade anslutningar.
* Antal anslutningar till servrar som inte kan nås.

Samtidigt läser modulen in en lista med begränsningar för vissa e-postservrar:

* Maximalt antal samtidiga anslutningar.
* Maximalt antal meddelanden per timme.
* Maximalt antal meddelanden per anslutning.

### Hantera IP-adresser {#managing-ip-addresses}

Statistikservern kan kombinera flera instanser eller flera datorer med samma offentliga IP-adress. Den är därför inte länkad till en viss instans, men den måste kontakta en instans för att återställa begränsningar per domän.

Leveransstatistik finns för varje mål-MX och för varje käll-IP. Om måldomänen till exempel har 5 MX och plattformen kan använda tre olika IP-adresser, kan servern hantera upp till 15 serier med indikatorer för den här domänen.

Källans IP-adress matchar den offentliga IP-adressen, dvs. adressen som den visas av fjärre-postservern. Den här IP-adressen kan skilja sig från adressen för datorn som är värd för **mta**, om det finns en NAT-router. Detta är orsaken till varför statistikservern använder en identifierare som matchar den offentliga IP-adressen (**publicId**). Associationen mellan den lokala adressen och identifieraren deklareras i **serverConf.xml** konfigurationsfil. Alla parametrar som är tillgängliga i **serverConf.xml** finns listade i [section](../../installation/using/the-server-configuration-file.md).

## Leveransstyrning {#delivery-output-controlling}

För att kunna leverera meddelanden till e-postservrar **E-posttrafikschaper** -komponenten begär en anslutning från statistikservern. När begäran har godkänts öppnas anslutningen.

Innan meddelanden skickas begär modulen &#39;tokens&#39; från servern. Dessa består vanligtvis av minst 10 tokens, vilket minskar antalet frågor till servern.

Servern sparar all statistik som hör till anslutningar och leveranser. Vid omstart förloras informationen tillfälligt: varje klient sparar en lokal kopia av sin sändningsstatistik och returnerar den till servern regelbundet (varannan minut). Servern kan sedan samla in data på nytt.

I följande avsnitt beskrivs hur ett meddelande behandlas av **E-posttrafikschaper** -komponenten.

### Meddelandeleverans {#message-delivery}

När ett meddelande skickas kan du få tre möjliga resultat:

1. **Lyckades**: meddelandet har skickats Meddelandet uppdateras.
1. **Meddelandet misslyckades**: den kontaktade servern avvisade meddelandet för den valda mottagaren. Resultatet matchar returkoderna 550 till 599, men undantag kan definieras.
1. **Sessionen misslyckades** (för 5.11 uppåt): om **mta** får ett svar på det här meddelandet. Meddelandet överges (se [Avbrutet meddelande](#message-abandonment)). Meddelandet skickas till en annan sökväg eller anges till väntande om inga andra sökvägar är tillgängliga (se [Meddelande väntar](#message-pending)).

   >[!NOTE]
   >
   >A **bana** är en anslutning mellan Adobe Campaign **mta** och målet **mta**. Adobe Campaign **mta** kan välja mellan flera IP-startadresser och flera IP-måldomäner.

### Avbrutet meddelande {#message-abandonment}

Övergivna meddelanden skickas tillbaka till **mta** och hanteras inte längre av **mtachild**.

The **mta** besluta om förfarandet för detta meddelande (återkrav, övergivande, karantän etc.), beroende på svarskoden och reglerna.

### Meddelande väntar {#message-pending}

Ett meddelande visas när det kommer till den aktiva kön och det inte finns några tillgängliga sökvägar.

En sökväg är vanligtvis markerad som otillgänglig under en varierande tidsperiod efter ett anslutningsfel. Otillgänglighetsperioden beror på felens frekvens och ålder.

## Statistisk serverkonfiguration {#statistics-server-configuration}

Statistikservern kan användas av flera instanser: den måste konfigureras oberoende av de instanser som ska använda den.

Börja med att definiera den Adobe Campaign-databas som ska vara värd för konfigurationen.

### Starta konfiguration {#start-configuration}

Som standard är **stat** för varje instans startas modulen. När instanserna samlas på samma dator, eller när instanser delar samma IP-adress, används en enskild statistikserver: de andra måste inaktiveras.

### Definition av serverporten {#definition-of-the-server-port}

Som standard avlyssnar statistikservern port 7777. Den här porten kan ändras i **serverConf.xml** -fil. Alla parametrar som är tillgängliga i **serverConf.xml** finns listade i [section](../../installation/using/the-server-configuration-file.md).

```
<stat port="1234"/>
```

## MX-konfiguration {#mx-configuration}

>[!IMPORTANT]
>
>För värdbaserade eller hybridinstallationer, om du har uppgraderat till [Förbättrad MTA](../../delivery/using/sending-with-enhanced-mta.md), **[!UICONTROL MX management]** regler för leveransflöde används inte längre. Den utökade MTA-servern använder sina egna MX-regler som gör att den kan anpassa din genomströmning efter domän baserat på ditt eget historiska e-postrykte och på realtidsfeedback som kommer från de domäner där du skickar e-post.

### Om MX-regler {#about-mx-rules}

>[!NOTE]
>
>Detta avsnitt och avsnitten nedan gäller endast lokala installationer och hostinginstallationer/hybridinstallationer som använder det äldre Campaign MTA.

MX-regler (Mail eXchanger) är de regler som hanterar kommunikation mellan en sändande server och en mottagande server.

Dessa regler läses in automatiskt varje morgon kl. 6.00 (servertid) för att klientinstansen ska kunna levereras regelbundet.

Beroende på materialkapaciteten och den interna policyn kommer en Internet-leverantör att acceptera ett fördefinierat antal anslutningar och meddelanden per timme. Dessa variabler kan ändras automatiskt av Internet-leverantörssystemet beroende på IP-adressens och den sändande domänens anseende. Via sin leveransplattform hanterar Adobe Campaign över 150 specifika regler av Internet-leverantören och dessutom en generisk regel för andra domäner.

Det maximala antalet anslutningar beror inte enbart på antalet offentliga IP-adresser som används av MTA.

Om du till exempel har tillåtit 5 anslutningar i MX-reglerna och har konfigurerat 2 offentliga IP:n kan du tro att du inte kan ha fler än 10 anslutningar samtidigt öppna till den här domänen. Detta är inte sant, det maximala antalet anslutningar avser en sökväg och en sökväg som är en kombination av en av våra offentliga MTA-IP:n och en offentlig IP-adress till kundens MTA.

I exemplet nedan har användaren två konfigurerade offentliga IP-adresser och domänen är yahoo.com.

```
user:~ user$ host -t mx yahoo.com
                yahoo.com mail is handled by 1 mta5.am0.yahoodns.net.
                yahoo.com mail is handled by 1 mta6.am0.yahoodns.net.
                yahoo.com mail is handled by 1 mta7.am0.yahoodns.net.
```

MX-poster för yahoo.com talar om för oss att yahoo.com har 3 Mail Exchangers. För att ansluta Peer Mail Exchanger kommer MTA att begära dess IP-adress från DNS.

```
user:~ user$ host -t a mta5.am0.yahoodns.net
                mta5.am0.yahoodns.net has address 98.136.216.26
                mta5.am0.yahoodns.net has address 98.136.217.202
                mta5.am0.yahoodns.net has address 98.138.112.38
                mta5.am0.yahoodns.net has address 66.196.118.37
                mta5.am0.yahoodns.net has address 63.250.192.46
                mta5.am0.yahoodns.net has address 66.196.118.240
                mta5.am0.yahoodns.net has address 98.136.217.203
                mta5.am0.yahoodns.net has address 98.138.112.35
```

För den här posten kan användaren kontakta 8 peer-IP-adresser. Eftersom användaren har två publika IP-adresser ger detta dem 8 * 2 = 16 kombinationer för att nå yahoo.com e-postservrar. Var och en av dessa kombinationer kallas en bana.

Den andra MX-posten visas som:

```
user:~ user$ host -t a mta6.am0.yahoodns.net
                mta6.am0.yahoodns.net has address 98.138.112.38
                mta6.am0.yahoodns.net has address 98.136.216.26
                mta6.am0.yahoodns.net has address 63.250.192.46
                mta6.am0.yahoodns.net has address 66.196.118.35
                mta6.am0.yahoodns.net has address 98.136.217.203
                mta6.am0.yahoodns.net has address 98.138.112.32
                mta6.am0.yahoodns.net has address 98.138.112.37
                mta6.am0.yahoodns.net has address 66.196.118.33
```

4 av dessa 8 IP-adresser används redan i mta5 (98.136.216.26, 98.138.112.38, 63.250.192.46 och 98.136.217.203). Med den här posten kan användaren använda fyra nya IP-adresser. Den tredje MX-posten gör detsamma.

Totalt har vi 16 fjärr-IP-adresser. I kombination med våra två lokala offentliga IP-adresser har vi 32 sökvägar för att nå yahoo.com e-postservrar.

>[!NOTE]
>
>Om 2 MX-poster refererar till samma IP-adress räknas den här som en sökväg och inte två.

Nedan följer några exempel på hur du använder MX-regler:

![](assets/s_ncs_examples_mx_rules.png)

I exemplet nedan har användaren en gräns på 10 000 meddelanden per timme för en viss domän, men MTA-flödeskapaciteten är högre än denna gräns.

I det här fallet är trafiken uppdelad i 12 perioder på 5 minuter för varje timme och den verkliga gränsen är 833 meddelanden per period.

Dessa meddelanden kommer att levereras så snabbt som möjligt.

![](assets/s_ncs_traffic_shaping.png)

### Konfigurera MX-hantering {#configuring-mx-management}

De regler som ska följas för MX anges i **[!UICONTROL MX management]** dokumentet **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]** trädnod.

Om **[!UICONTROL MX management]** dokumentet finns inte i noden, du kan skapa det manuellt. Så här gör du:

1. Skapa en ny uppsättning postregler.
1. Välj **[!UICONTROL MX management]** läge.

   ![](assets/s_ncs_install_mx_mgt_rule.png)

1. Retur **defaultMXRules** i **[!UICONTROL Internal name]** fält.

För att ändringarna ska kunna beaktas måste du starta om statistikservern.

Om du vill läsa in konfigurationen på nytt utan att starta om statistikservern använder du följande kommando på den dator som är värd för servern: `nlserver stat -reload`

>[!NOTE]
>
>Den här kommandoraden är bäst **omstart av nlserver**. Den förhindrar att statistik som samlats in innan omstarten går förlorad och undviker toppar som kan gå mot kvoter som definieras i MX-reglerna.

### Konfigurera MX-regler {#configuring-mx-rules}

The **[!UICONTROL MX management]** -dokument visar alla domäner som är länkade till en MX-regel.

Dessa regler tillämpas i sekvens: den första regeln vars MX-mask är kompatibel med MX-målfilen används.

Följande parametrar är tillgängliga för varje regel:

* **[!UICONTROL MX mask]**: domän som regeln tillämpas på. Varje regel definierar en adressmask för MX. Alla MX vars namn matchar masken är därför giltiga. Masken kan innehålla &quot;&#42;&quot; och &quot;?&quot; allmänna tecken.

  Till exempel följande adresser:

   * a.mx.yahoo.com
   * b.mx.yahoo.com
   * c.mx.yahoo.com

  är kompatibla med följande masker:

   * &#42;.yahoo.com
   * ?.mx.yahoo.com

  För e-postadressen foobar@gmail.com är domänen gmail.com och MX-posten är:

  ```
  gmail.com mail exchanger = 20 alt2.gmail-smtp-in.l.google.com.
  gmail.com mail exchanger = 10 alt1.gmail-smtp-in.l.google.com.
  gmail.com mail exchanger = 40 alt4.gmail-smtp-in.l.google.com.
  gmail.com mail exchanger = 5  gmail-smtp-in.l.google.com.
  gmail.com mail exchanger = 30 alt3.gmail-smtp-in.l.google.com.
  ```

  I det här fallet MX-regeln `*.google.com` kommer att användas. Som du ser matchar MX-regelmasken inte nödvändigtvis domänen i e-postmeddelandet. De MX-regler som används för gmail.com e-postadresser är de som används för masken `*.google.com`.

* **[!UICONTROL Range of identifiers]**: Med det här alternativet kan du ange intervallet för identifierare (publicID) som regeln gäller för. Du kan ange:

   * Ett tal: regeln gäller bara för detta publicId,
   * Ett sifferintervall (**number1-number2**): regeln gäller för alla publika ID:n mellan dessa två tal.

  >[!NOTE]
  >
  >Om fältet är tomt gäller regeln alla identifierare.

  Ett offentligt ID är en intern identifierare för en offentlig IP som används av en eller flera MTA. Dessa ID:n definieras i MTA-servrarna i **config-instance.xml** -fil.

  ![](assets/s_ncs_install_mta_ips.png)

* **[!UICONTROL Shared]**: definierar omfånget för egenskaperna för den här MX-regeln. När det här alternativet är markerat delas alla parametrar på alla IP-adresser som är tillgängliga för instansen. När alternativet är avmarkerat definieras MX-reglerna för varje IP. Det maximala antalet meddelanden multipliceras med antalet tillgängliga IP-adresser.
* **[!UICONTROL Maximum number of connections]**: maximalt antal samtidiga anslutningar till avsändarens domän.
* **[!UICONTROL Maximum number of messages]**: maximalt antal meddelanden som kan skickas på en anslutning. När meddelandena överskrider det här antalet stängs anslutningen och en ny öppnas.
* **[!UICONTROL Messages per hour]**: maximalt antal meddelanden som kan skickas på en timme till avsändarens domän.
* **[!UICONTROL Connection time out]**: tidströskel för anslutning till en domän.

  >[!NOTE]
  >
  >Windows kan utfärda en **timeout** före detta tröskelvärde, vilket beror på vilken version av Windows du har.

* **[!UICONTROL Timeout Data]**: maximal väntetid efter att meddelandeinnehållet har skickats (DATA-avsnittet i SMTP-protokollet).
* **[!UICONTROL Timeout]**: maximal väntetid för andra utbyten med SMTP-servern.
* **[!UICONTROL TLS]**: TLS-protokollet, som gör att du kan kryptera e-postleveranser, kan aktiveras selektivt. För varje MX-mask finns följande alternativ:

   * **[!UICONTROL Default configuration]**: Detta är den allmänna konfigurationen som anges i konfigurationsfilen serverConf.xml som används.

     >[!IMPORTANT]
     >
     >Vi rekommenderar inte att du ändrar standardkonfigurationen.

   * **[!UICONTROL Disabled]** : Meddelandena skickas systematiskt utan kryptering.
   * **[!UICONTROL Opportunistic]** : Meddelandeleveransen krypteras om den mottagande servern (SMTP) kan generera TLS-protokollet.

Konfigurationsexempel:

![](assets/s_ncs_install_mx_mgt_rule_details.png)

>[!NOTE]
>
>Mer information om hur du använder MX-servrar med Adobe Campaign finns i [det här avsnittet](../../installation/using/using-mx-servers.md).

### Hantera e-postformat {#managing-email-formats}

Du kan definiera formatet för skickade meddelanden så att innehållet som visas automatiskt anpassas efter domänen för varje mottagares adress.

För att göra det går du till **[!UICONTROL Management of email formats]** -dokument, som finns i **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Non deliverables management]** > **[!UICONTROL Mail rule sets]**.

Det här dokumentet innehåller en lista över alla fördefinierade domäner som motsvarar de japanska format som hanteras av Adobe Campaign. Mer information finns i [det här dokumentet](../../delivery/using/defining-the-email-content.md#sending-emails-on-japanese-mobiles).

![](assets/mail_rule_sets.png)

The **MIME-struktur** (Multipurpose Internet Mail Extensions) gör att du kan definiera meddelandestrukturen som ska skickas till olika e-postklienter. Det finns tre alternativ:

* **Multipart**: Meddelandet skickas i text- eller HTML-format. Om formatet HTML inte godkänns kan meddelandet fortfarande visas i textformat.

  Som standard är multipart-strukturen **multipart/option**, men det blir automatiskt **multipart/related** när en bild läggs till i meddelandet. Vissa leverantörer förväntar sig **multipart/related** som standard, **[!UICONTROL Force multipart/related]** detta format används även om ingen bild är kopplad.

* **HTML**: Ett meddelande som bara innehåller HTML skickas. Om HTML inte godkänns visas inte meddelandet.
* **Text**: Ett meddelande i textformat skickas. Fördelen med textformatmeddelanden är att de är mycket små.

Om **[!UICONTROL Image inclusion]** är aktiverat visas dessa direkt i e-postmeddelandet. Bilderna överförs sedan och URL-länkarna ersätts av innehållet.

Det här alternativet används särskilt av den japanska marknaden för **Deco-mail**, **Avböj e-post** eller **Dekoration Mail**. Mer information finns i [det här dokumentet](../../delivery/using/defining-the-email-content.md#sending-emails-on-japanese-mobiles).

>[!IMPORTANT]
>
>När du infogar bilder i ett e-postmeddelande ökar storleken avsevärt.

## Leveransserverkonfiguration {#delivery-server-configuration}

### Klocksynkronisering {#clock-synchronization}

Klockorna för alla servrar som utgör Adobe Campaign-plattformen (inklusive databasen) måste synkroniseras och deras system måste vara inställda på samma tidszon.

### Statistikserverns koordinater {#coordinates-of-the-statistics-server}

Statistikserverns adress måste anges i **mta**.

The **statServerAddress** egenskapen för **mta** -elementet i konfigurationen gör att du kan ange adress och nummer för den port som ska användas.

```
<mta statServerAddress="emailStatServer:7777">
   [...]
 </mta>
```

Om du vill använda statistikservern på samma dator måste du ange åtminstone namnet på datorn med **localhost** värde:

```
 <mta statServerAddress="localhost">
```

>[!IMPORTANT]
>
>Om fältet inte fylls i visas **mta** kommer inte att starta.

### Lista över IP-adresser som ska användas {#list-of-ip-addresses-to-use}

Konfigurationen för trafikledning finns i **mta/child/smtp** -element i konfigurationsfilen.

För varje **IPAfinity** måste du deklarera IP-adresserna som kan användas för datorn.

Exempel:

```
<IPAffinity localDomain="<domain>" name="default">
  <IP address="192.168.0.11" publicId="1" weight="5"/>
  <IP address="192.168.0.12" heloHost="revdns1.campaign.com" publicId="2" weight="5"/>
  <IP address="192.168.0.13" publicId="3" weight="1"/>
</IPAffinity>
```

Parametrarna är följande:

* **adress**: det här är IP-adressen för den MTA-värddator som ska användas.
* **heloHost**: den här identifieraren representerar IP-adressen så som den kommer att ses av SMTP-servern.

* **publicId**: den här informationen är användbar när en IP-adress delas av flera Adobe Campaign **mtas** bakom en NAT-router. Statistikservern använder den här identifieraren för att memorera anslutningen och skicka statistik mellan den här startpunkten och målservern.
* **vikt**: låter dig definiera den relativa användningsfrekvensen för adressen. Som standard har alla adresser en vikt som är lika med 1.

>[!NOTE]
>
>I filen serverConf.xml måste du verifiera att en IP-adress motsvarar en enda hjälpvärd med en unik identifierare (public_id). Den kan inte mappas till flera olika värddatorer, vilket kan leda till leveransproblem.

I det föregående exemplet, med normala villkor, distribueras adresserna enligt följande:

    * &quot;1&quot;: 5 / (5+5+1) = 45 %
    * &quot;2&quot;: 5 / (5+5+1) = 45 %
    * &quot;3&quot;: 1 / (5+5+1) = 10 %

Om till exempel den första adressen inte kan användas för ett givet MX, skickas meddelanden enligt följande:

    * &quot;2&quot;: 5 / (5+1) = 83 %
    * &quot;3&quot;: 1 / (5+1) = 17 %

* **includeDomains**: låter dig reservera den här IP-adressen för e-post som tillhör en viss domän. Det här är en lista med masker som kan innehålla ett eller flera jokertecken (&#39;&#42;&#39;). Om attributet inte anges kan alla domäner använda den här IP-adressen.

  Exempel: **includeDomains=&quot;wanadoo.com,orange.com,yahoo.&#42;&quot;**

* **excludeDomains**: utelämnar en lista över domäner för den här IP-adressen. Det här filtret används efter **includeDomains** filter.

  ![](assets/s_ncs_install_mta_ips.png)

## Optimering av e-postutskick {#email-sending-optimization}

Adobe Campaign interna arkitektur **mta** påverkar konfigurationen för optimering av e-postleverans. Här är några tips om hur du kan förbättra dina leveranser.

### Justera parametern maxWaitMessages {#adjust-the-maxwaitingmessages-parameter}

The **maxWaitMessages** parameter anger det högsta antalet meddelanden som har förberetts av **mtachild**. Meddelanden tas bara bort från den här listan när de har skickats eller övergetts.

Den här parametern är mycket viktig och särskilt viktig om meddelanden inte sorteras efter domän.

När **maxWorkingSetMb** (256) har nått tröskelvärdet och leveransservern slutar skicka meddelanden. Prestandan minskar avsevärt fram till **mtachild** börjar om. Du kan antingen öka tröskelvärdet för **maxWorkingSetMb** eller minska tröskelvärdet för **maxWaitMessages** parameter.

The **maxWorkingSetMb** parametern beräknas empiriskt genom att det maximala antalet meddelanden multipliceras med den genomsnittliga meddelandestorleken och resultatet multipliceras med 2,5. Om ett meddelande till exempel har en genomsnittlig storlek på 50 kB och **maxWaitMessages** är lika med 1 000, vilket innebär att det använda minnet i genomsnitt är 125 MB.

### Justera antalet datorer {#adjust-the-number-of-mtachild}

Antalet underordnade bör inte överstiga antalet processorer i datorn (ca. 1000 sessioner). Vi rekommenderar att du inte överskrider 8 **mtachild**. Sedan kan du öka antalet meddelanden per **child** (**maxMsgPerChild**) för att uppnå en tillräcklig livslängd.
