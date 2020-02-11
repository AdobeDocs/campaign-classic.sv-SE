---
title: Tekniska rekommendationer för förbättrad leverans med Adobe Campaign Classic
description: Upptäck tekniker, konfigurationer och verktyg som ni kan använda för att förbättra leveransgraden med Adobe Campaign Classic.
page-status-flag: never-activated
uuid: 71be1087-e5ff-4a7a-85ca-36803839e72f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: fc95538b-b54d-44ec-81aa-f51b62982699
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0291f464c2b4db51e1e56cefe83aa9e751e680a9

---


# Tekniska rekommendationer{#technical-recommendations}

Flera tekniker, konfigurationer och verktyg som du kan använda för att förbättra din leveransgrad visas nedan.

## Konfiguration {#configuration}

### Omvänd DNS {#reverse-dns}

 Adobe Campaign kontrollerar om en omvänd DNS anges för en IP-adress och att detta korrekt pekar tillbaka till IP-adressen.

En viktig punkt i nätverkskonfigurationen är att se till att rätt omvänd DNS har definierats för var och en av IP-adresserna för utgående meddelanden. Det innebär att det för en viss IP-adress finns en omvänd DNS-post (PTR-post) med matchande DNS-post (A-post) som repeterar den ursprungliga IP-adressen.

Domänvalet för en omvänd DNS har betydelse när vissa Internet-leverantörer hanteras. I AOL accepteras endast feedbackslingor med en adress i samma domän som den omvända DNS-adressen (se [Feedback-slinga](#feedback-loop)).

Det finns ett verktyg för att verifiera konfigurationen av en domän: [https://mxtoolbox.com/SuperTool.aspx](https://mxtoolbox.com/SuperTool.aspx).

### MX-regler {#mx-rules}

MX-regler (Mail eXchanger) är de regler som hanterar kommunikation mellan en sändande server och en mottagande server.

Mer exakt används de för att styra hur snabbt Campaign MTA (Message Transfer Agent) skickar e-postmeddelanden till varje enskild e-postdomän eller Internet-leverantör (t.ex. hotmail.com, comcast.net). Dessa regler är vanligtvis baserade på gränser som offentliggjorts av Internet-leverantörer (t.ex. innehåller inte mer än 20 meddelanden per varje SMTP-anslutning).

Mer information om MX-hantering finns i det [dedikerade avsnittet](../../installation/using/email-deliverability.md#mx-configuration).

### TLS {#tls}

TLS (Transport Layer Security) är ett krypteringsprotokoll som kan användas för att säkra anslutningen mellan två e-postservrar och skydda innehållet i ett e-postmeddelande från att läsas av andra än de avsedda mottagarna.

## Autentisering {#authentication}

### SPF {#spf}

SPF (Sender Policy Framework) är en standard för e-postautentisering som gör att ägaren av en domän kan ange vilka e-postservrar som får skicka e-post för den domänens räkning. I den här standarden används domänen i e-postens &quot;Return-Path&quot;-huvud (kallas även för &quot;Envelope From&quot;-adress).

Det finns ett verktyg för att verifiera en SPF-post: [https://www.kitterman.com/spf/validate.html](https://www.kitterman.com/spf/validate.html)

SPF är en teknik som i viss utsträckning gör att du kan kontrollera att domännamnet som används i ett e-postmeddelande inte är falskt. När ett meddelande tas emot från en domän tillfrågas domänens DNS-server. Svaret är en kort post (SPF-posten) som anger vilka servrar som har behörighet att skicka e-post från den här domänen. Om vi antar att bara ägaren av domänen har möjlighet att ändra den här posten, kan vi tänka oss att den här metoden inte tillåter att avsändaradressen förfalskas, åtminstone inte delen från höger om&quot;@&quot;.

I den slutliga [RFC 4408-specifikationen](https://www.rfc-editor.org/info/rfc4408)används två element i meddelandet för att avgöra vilken domän som betraktas som avsändare: Den domän som anges av SMTP-kommandot &quot;HELO&quot; (eller &quot;EHLO&quot;) och den domän som anges av adressen för huvudet &quot;Return-Path&quot; (eller &quot;MAIL FROM&quot;), som också är studsadressen. Olika överväganden gör det möjligt att endast ta hänsyn till ett av dessa värden. vi rekommenderar att du ser till att båda källorna anger samma domän.

Om du kontrollerar SPF-filen utvärderas giltigheten för avsändarens domän:

* **Ingen**: Ingen utvärdering kunde göras.
* **Neutral**: Domänen som efterfrågas aktiverar inte utvärdering.
* **Godkänd**: Domänen anses vara autentisk.
* **Misslyckades**: Domänen är förfalskad och meddelandet bör avvisas.
* **SoftFail**: Domänen är antagligen förfalskad, men meddelandet bör inte avvisas enbart på grundval av detta resultat.
* **TempError**: Ett tillfälligt fel stoppade utvärderingen. Meddelandet kan avvisas,
* **PermError**: SPF-posterna för domänen är ogiltiga.

Det är värt att notera att det kan ta upp till 48 timmar att ta hänsyn till poster gjorda på DNS-servernivå. Den här fördröjningen beror på hur ofta DNS-cachen för de mottagande servrarna uppdateras.

### DKIM {#dkim}

DKIM-autentisering (DomainKeys Identified Mail) är en efterföljare till SPF och använder kryptografi med offentlig nyckel som gör att den mottagande e-postservern kan verifiera att ett meddelande verkligen skickades av den person eller enhet som det hävdades ha skickats av, och huruvida meddelandeinnehållet ändrades mellan den tidpunkt då det ursprungligen skickades (och DKIM &quot;signerade&quot;) och den tidpunkt det togs emot. Den här standarden använder vanligtvis domänen i huvudet Från eller Avsändare. 1024b är den rekommenderade krypteringsstorleken enligt Best Practices för att säkerställa att DKIM:s säkerhetsnivå är korrekt. Lägre DKIM-nycklar anses inte giltiga av de flesta åtkomstleverantörer.

DKIM kommer från en kombination av DomainKeys, Yahoo! och Cisco identifierade autentiseringsprinciper för Internet Mail och används för att kontrollera avsändardomänens autenticitet och garantera meddelandets integritet.

DKIM ersatte **DomainKeys** -autentisering.

>[!IMPORTANT]
>
>För värdbaserade eller hybridbaserade installationer, om du har uppgraderat till Enhanced MTA, signerar DKIM e-postautentisering av Förbättrat MTA. DKIM-signering av den inbyggda Campaign MTA inaktiveras i **[!UICONTROL Domain management]** tabellen som en del av den förbättrade MTA-uppgraderingen.
>
>Mer information om Adobe Campaign Enhanced MTA finns i det här [dokumentet](https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html).

DKIM kräver vissa förutsättningar:

* **Säkerhet**: Kryptering är en viktig del av DKIM och för att försäkra sig om att DKIM:s säkerhetsnivå sedan våren 2013 är 1024b den rekommenderade krypteringsstorleken. Lägre DKIM-nycklar anses inte giltiga av de flesta åtkomstleverantörer.
* **Anseende**: anseendet baseras på IP-adressen och/eller domänen, men den mindre transparenta DKIM-väljaren är också ett nyckelelement som ska beaktas. Det är viktigt att du väljer väljaren: Undvik att behålla&quot;standardinställningen&quot; som kan användas av alla och därför har ett mycket svagt rykte. Du måste implementera en annan väljare för **kundlojalitet jämfört med kundvärvning** och för autentisering.
* **Adobe Campaign-alternativdeklaration**: i Adobes kampanj baseras den privata nyckeln för DKIM på en DKIM-väljare och en domän. Det går för närvarande inte att skapa flera privata nycklar för samma domän/underdomän med olika väljare. Det går inte att definiera vilken väljardomän/underdomän som ska användas för autentisering i varken plattformen eller e-postmeddelandet. Plattformen kommer att välja en av de privata nycklarna, vilket innebär att autentiseringen har en stor chans att misslyckas.

>[!NOTE]
>
>* Om du har konfigurerat DomainKeys för din Adobe Campaign-instans behöver du bara välja **dhelm** i domänhanteringsreglerna. Om inte följer du samma konfigurationssteg (privat/offentlig nyckel) som för DomainKeys.
>* Du behöver inte aktivera både DomainKeys och DKIM för samma domän som DKIM är en förbättrad version av DomainKeys.
>* Följande domäner validerar för närvarande DKIM: AOL, Gmail.


### DMARC {#dmarc}

DMARC (Domain-based Message Authentication, Reporting and Conformance) är den senaste formen av e-postautentisering, och den förlitar sig på både SPF- och DKIM-autentisering för att avgöra om ett e-postmeddelande godkänns eller misslyckas. DMARC är unikt och kraftfullt på två mycket viktiga sätt:

* Överensstämmelse - Avsändaren kan instruera Internet-leverantörer om vad de ska göra med meddelanden som inte kan autentiseras (t.ex. inte acceptera det).
* Rapportering - Den ger avsändaren en detaljerad rapport som visar alla meddelanden som inte kunde verifieras av DMARC, tillsammans med domänen Från och IP-adressen som används för varje. Detta gör att ett företag kan identifiera legitim e-post som inte kan autentiseras och som behöver någon typ av &quot;fix&quot; (t.ex. lägga till IP-adresser i sin SPF-post) samt källorna till och förekomsten av nätfiskeförsök i sina e-postdomäner.

DMARC kan utnyttja de rapporter som genererats av [250ok](https://250ok.com/).

<!--#### Configuring the application {#configuring-the-application}

To define the domain used for the HELO command, edit the instance's configuration file (conf/config-instance.xml) and define a "localDomain" attribute as follows:

```
<serverConf>
  <shared>
    <dnsConfig localDomain="mydomain.net"/>
  </shared>
</serverConf>
```

The MAIL FROM domain is the domain used in technical bounce messages. This address is defined in the deployment wizard or via the NmsEmail_DefaultErrorAddr option.

#### DNS configuration {#dns-configuration}

An SPF record can currently be defined on a DNS server as a TXT type record (code 16) or an SPF type record (code 99). An SPF record takes the form of a character string. For example:

```
v=spf1 ip4:12.34.56.78/32 ip4:12.34.56.79/32 ~all
```

defines the 2 IP addresses 12.34.56.78 and 12.34.56.79 as authorized to send emails for the domain. **~all** means that any other address should be interpreted as a SoftFail.

Recommendations for defining an SPF record:

* Add **~all** (SoftFail) or **-all** (Fail) at the end to reject all servers other than those defined. Without this, servers will be able to forge this domain (with a Neutral evaluation).
* Do not add **ptr** (openspf.org recommends against this as costly and unreliable).-->

## Feedback-slinga {#feedback-loop}

En feedback-slinga fungerar genom att på Internet-nivå deklarera en given e-postadress för ett intervall av IP-adresser som används för att skicka meddelanden. Internet-leverantören skickar till den här postlådan, på ungefär samma sätt som för studsmeddelanden, de meddelanden som rapporteras av mottagarna som skräppost. Plattformen bör konfigureras för att blockera framtida leveranser till användare som har klagat. Det är viktigt att du inte längre kontaktar dem även om de inte använde rätt avanmälningslänk. På grundval av dessa klagomål kommer en Internet-leverantör att svartlista en IP-adress. Beroende på Internet-leverantören kommer en klagofrekvens på ungefär 1 % att resultera i en svartlista över en IP-adress.

En standard håller på att utarbetas för att definiera formatet för meddelanden med feedback-slingor: ARF ( [Abuse Feedback Reporting Format)](https://tools.ietf.org/html/rfc6650).

Implementering av en feedbackslinga för en instans kräver:

* En postlåda som är dedikerad till instansen, som kan vara studspostlådan
* IP-adresser som är dedikerade till instansen

Implementering av en enkel feedbackslinga i Adobe Campaign använder funktionen för studsmeddelanden. Postlådan för feedbackslingan används som studspostlåda och en regel definieras för att identifiera dessa meddelanden. E-postadresserna till mottagarna som rapporterade meddelandet som skräppost läggs till i karantänlistan.

* Skapa eller ändra en studs-postregel, **Feedback_loop**, i **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]** med orsaken **Refused** och typen **Hard**.
* Om en postlåda har definierats särskilt för feedbackslingan definierar du parametrarna som ska få åtkomst till den genom att skapa ett nytt externt studentkonto i **[!UICONTROL Administration > Platform > External accounts]**.

Mekanismen fungerar omedelbart för att behandla klagomål. Om du vill vara säker på att den här regeln fungerar som den ska kan du tillfälligt inaktivera kontona så att de inte samlar in dessa meddelanden och sedan kontrollera innehållet i feedbackloopens postlåda manuellt. Kör följande kommandon på servern:

```
nlserver stop inMail@instance,
nlserver inMail -instance:instance -verbose.
```

Om du tvingas använda en enda slingadress för feedback för flera instanser måste du:

* Replikera de meddelanden som tas emot på så många postlådor som det finns instanser av,
* få varje postlåda upphämtad i en enda instans,
* Konfigurera instanserna så att de endast bearbetar de meddelanden som berör dem: instansinformationen ingår i Message-ID-huvudet i meddelanden som skickas av Adobe Campaign och finns därför även i svarsslingmeddelandena. Ange bara parametern **checkInstanceName** i instanskonfigurationsfilen (instansen verifieras inte som standard och detta kan leda till att en viss adress sätts i karantän på ett felaktigt sätt):

   ```
   <serverConf>
     <inMail checkInstanceName="true"/>
   </serverConf>
   ```

Adobe Campaigns leveranstjänst hanterar din prenumeration på tjänster för feedback-slingor för följande internetleverantörer: AOL, BlueTie, Comcast, Cox, EarthLink, FastMail, Gmail, Hotmail, HostedEmail, Libero, Mail.ru, MailTrust, OpenSRS, QQ, RoadRunner, Synacor, Telenor, Terra, UnitedOnline, USA, XS4ALL, Yahoo, Yandex, Zoho.

## List-Unsubscribe {#list-unsubscribe}

### Om List-Unsubscribe {#about-list-unsubscribe}

Det är obligatoriskt att lägga till ett SMTP-huvud med namnet **List-Unsubscribe** för att säkerställa optimal leveranshantering.

Den här rubriken kan användas som ett alternativ till ikonen&quot;Rapportera som SPAM&quot;. Den visas som en länk för avprenumeration i e-postgränssnittet.

Om du använder den här funktionen kan du skydda ditt rykte och din feedback kommer att tas som en oprenumeration.

>[!NOTE]
>
>Den här funktionaliteten finns i build 6831.

Om du vill använda List-Unsubscribe måste du ange en kommandorad som ser ut så här:

```
List-Unsubscribe: mailto: client@newsletter.example.com?subject=unsubscribe?body=unsubscribe
```

>[!IMPORTANT]
>
>Exemplet ovan baseras på mottagartabellen. Om databasimplementeringen görs från en annan tabell måste du skriva om kommandoraden med rätt information.

Följande kommandorad kan användas för att skapa en dynamisk **List-Unsubscribe**:

```
List-Unsubscribe: mailto: %=errorAddress%?subject=unsubscribe%=message.mimeMessageId%
```

Gmail, Outlook.com och Microsoft Outlook har stöd för den här metoden och en avanmälningsknapp är tillgänglig direkt i gränssnittet. Den här tekniken minskar antalet klagomål.

![](assets/s_tn_del_msn_unsubscribe_list.png)

![](assets/s_tn_del_gmail_unsubscribe_list.png)

Du kan implementera **List-Unsubscribe** genom att:

* direkt lägga till kommandoraden i leveransmallen - se [det här avsnittet](#adding-a-command-line-in-a-delivery-template),
* eller, skapa en typologiregel - se [det här avsnittet](#creating-a-typology-rule).

### Lägga till en kommandorad i en leveransmall {#adding-a-command-line-in-a-delivery-template}

Kommandoraden måste läggas till i det extra avsnittet i e-postmeddelandets SMTP-huvud.

Detta kan göras i varje e-postmeddelande eller i befintliga leveransmallar. Du kan också skapa en ny leveransmall som innehåller den här funktionen.

### Skapa en typologiregel {#creating-a-typology-rule}

Regeln måste innehålla skriptet som genererar kommandoraden och den måste inkluderas i e-postrubriken.

>[!NOTE]
>
>Vi rekommenderar att du skapar en typologiregel: funktionen för att avbryta prenumerationen läggs automatiskt till i varje e-postmeddelande.

1. List-Unsubscribe: &lt;mailto:unsubscribe@domain.com>

   Om du klickar på länken **för att avbryta prenumerationen** öppnas användarens standardklient för e-post. Den här typologiregeln måste läggas till i en typologi som används för att skapa e-post.

1. List-Unsubscribe: `<https://domain.com/unsubscribe.jsp>`

   Om du klickar på länken **för att avbryta prenumerationen** dirigeras användaren till ditt formulär för att avbryta prenumerationen.

   Exempel:

   ![](assets/s_tn_del_unsubscribe_param.png)

## E-postoptimering {#email-optimization}

### SMTP {#smtp}

SMTP (Simple mail transfer protocol) är en Internetstandard för e-postöverföring.

SMTP-felen som inte kontrolleras av en regel visas i mappen **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Delivery log qualification]** . Dessa felmeddelanden tolkas som standard som ej nåbara felmeddelanden. De vanligaste felen måste identifieras och en motsvarande regel läggas till i **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Mail rule sets]** om du vill att feedback från SMTP-servrarna ska vara korrekt. Utan detta kommer plattformen att göra onödiga återförsök (okända användare) eller felaktigt placera vissa mottagare i karantän efter ett visst antal tester.

### Dedikerade IP-adresser {#dedicated-ips}

Adobe tillhandahåller en dedikerad IP-strategi för varje kund med en IP-förstärkning för att bygga upp ett anseende och optimera leveransresultaten.

## IP-certifiering {#ip-certification}

IP-certifiering är ett program för vitlistning och sändningsmetoder som hjälper till att säkerställa att e-post tas emot utan att blockeras av antispamfilter eller andra e-postblockeringssystem.

För närvarande erbjuder två leverantörer IP-certifiering: Return Path och Certified Senders Alliance.

Certifierade avsändare läggs till i e-postvitlistor som används av globala postlådeproviders och e-postsäkerhetsföretag. Dessa kommersiella vitlistor är baserade på ett system som gör att avsändaren kan kringgå skräppostfilter helt eller delvis eller tilldelas inkrementella punkter när de kommer in i systemet.

Programmet [Return Path Certification](https://www.validity.com/products/returnpath/certification/) har flera fördelar:

* En mätbar ökning av inkorgplaceringen hos de främsta postlådeleverantörerna som Microsoft, AOL, Yahoo, Gmail, Comcast, Orange, Mail.ru med flera
* Bra rykte och behandling vid viktiga filter som Cloudmark, SpamAssassin och Cisco Ironport
* Ett efterlevnadsteam som arbetar med övervakning dygnet runt, alla dagar, och som tillhandahåller säkerhetsvarningar och arbetar med dig genom att åtgärda eventuella kompromisser
* Data från postlådeprovidern som ger detaljerad information om nyckeltal, placering och certifieringsprestanda
* Förenklad och snabbare IP-uppvärmning, inklusive bättre rykte och erkännande vid migrering eller hämtning av en ny IP-adress

Certifieringen [Certified Senders Alliance](https://certified-senders.org/certification-process/) ger bland annat följande fördelar:

* Certifiering av avsändare av kommersiella e-postmeddelanden som kan uppfylla höga kvalitetskrav
* Förbättrad leverans och leverans av kommersiella e-postmeddelanden som ökar inkorgplaceringen och minskar skräppostfiltreringen
* Skydd mot juridiska och ekonomiska risker genom att till fullo följa rättsliga normer
* Skydda anseendet genom tidiga varningar från CSA:s anmälningskontor och dagliga rapporter om skräppostfällor

Internetleverantörer får använda dessa tjänster och antalet internetleverantörer kan variera beroende på vitlistan.

Men eftersom allt fler Internet-leverantörer bygger sina antispamfilter baserat på varje inkorgsägares beteende i stället för att analysera själva meddelandeinnehållet, kan IP-certifiering inte vara en garanti för inkorgsplacering eller till och med leverans.
