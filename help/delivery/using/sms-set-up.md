---
product: campaign
title: Konfigurera kampanj-SMS-kanal
description: Lär dig konfigurera SMS-kanalen i Campaign
feature: SMS
role: User, Developer, Admin
exl-id: a2783a5e-6d38-41a1-b5c6-24ab489116f8
source-git-commit: 41296a0acaee93d31874bf58287e51085c6c1261
workflow-type: tm+mt
source-wordcount: '1739'
ht-degree: 26%

---

# Konfigurera SMS-kanal på en fristående instans {#setting-up-sms-channel}

Om du vill skicka till en mobiltelefon behöver du:

1. Ett externt konto som anger en koppling och typ av meddelande.

   Observera att äldre anslutningar nu är inaktuella. De föråldrade funktionerna är fortfarande tillgängliga, men de kommer inte att förbättras ytterligare eller stödjas. Läs mer [på den här sidan](../../rn/using/deprecated-features.md).

1. En leveransmall där det här externa kontot refereras.

>[!NOTE]
>
> För SMS-leveranser bör typologin använda en specifik SMS-tillhörighet som skapats i **en** dedikerad programserverbehållare. [Läs mer](../../installation/using/configure-delivery-settings.md#managing-outbound-smtp-traffic-with-affinities)

## Skapa ett externt SMPP-konto {#creating-an-smpp-external-account}

>[!IMPORTANT]
>
>Om du använder samma konto och lösenord för flera externa SMS-konton kan det leda till konflikter och överlappning mellan kontona. Se sidan [SMS-felsökning](troubleshooting-sms.md#external-account-conflict).

Om du vill skicka ett SMS till en mobiltelefon måste du först skapa ett externt SMPP-konto.
Mer information om SMS-protokoll och inställningar finns på [sidan](sms-protocol.md).

Gör så här:

1. Klicka på ikonen **[!UICONTROL New]** i noden **[!UICONTROL Platform]** > **[!UICONTROL External accounts]** i trädet.
1. Definiera kontotypen som **Routning**, kanalen som **Mobil (SMS)** och leveransläget som **Massleverans**.

   ![](assets/extended_smpp_create_account.png)

1. Markera rutan **[!UICONTROL Enabled]**.
1. Välj **[!UICONTROL Extended generic SMPP]** i listrutan **[!UICONTROL Connector]** på fliken **[!UICONTROL Mobile]**.

   ![](assets/extended_smpp_connector.png)

   >[!CAUTION]
   >
   > Från och med version 20.2 är äldre anslutningar borttagna och stöds inte. Vi rekommenderar att du använder **[!UICONTROL Extended generic SMPP]**-anslutningen. Mer information om hur du migrerar till den rekommenderade anslutningen finns på [sidan](unsupported-connector-migration.md).

1. Med alternativet **[!UICONTROL Enable verbose SMPP traces in the log file]** kan du dumpa all SMPP-trafik i loggfiler. Det här alternativet måste vara aktiverat för att kunna felsöka anslutningen och jämföra med den trafik som leverantören ser.

1. Kontakta din SMS-tjänstleverantör som förklarar hur du fyller i de olika externa kontofälten på fliken **[!UICONTROL Connection settings]**.

   Kontakta sedan din leverantör, beroende på vilken som valts, som ger dig värdet att ange i fältet **[!UICONTROL SMSC implementation name]**.

   Du kan definiera antalet anslutningar till providern per underordnat MTA-objekt. Som standard är den inställd på 1.

1. Som standard uppfyller antalet tecken i ett SMS GSM-standarden.

   SMS-meddelanden som använder GSM-kodning kan innehålla högst 160 tecken eller 153 tecken per SMS för meddelanden som skickas i flera delar.

   >[!NOTE]
   >
   >Vissa tecken räknas som två (klammerparenteser, eurosymbolen osv.).
   >
   >Nedan visas en lista över tillgängliga GSM-tecken.

   Om du vill kan du tillåta teckentranskribering genom att markera motsvarande ruta.

   ![](assets/extended_smpp_transliteration.png)

   Mer information om detta finns i [det här avsnittet](#about-character-transliteration).

1. På fliken **[!UICONTROL Throughput and delays]** kan du ange maximal genomströmning för utgående meddelanden (&quot;MT&quot;, Mobile Terminated) i MT per sekund. Om du anger &quot;0&quot; i motsvarande fält är dataflödet obegränsat.

   Samtliga fältvärden som motsvarar varaktighet måste fyllas i som sekunder.

1. På fliken **[!UICONTROL Mapping of encodings]** kan du definiera kodningar.

   Mer information om detta finns i [det här avsnittet](#about-text-encodings).

1. Alternativet **[!UICONTROL Send full phone number]** är inaktiverat som standard på fliken **[!UICONTROL SMSC specificities]**. Aktivera det inte om du vill respektera SMPP-protokollet och bara överföra siffror till servern för SMS-providern (SMSC).

   Eftersom vissa leverantörer kräver att&quot;+&quot;-prefixet används, bör du kontakta din leverantör och föreslå att du aktiverar det här alternativet om det behövs.

   Med kryssrutan **[!UICONTROL Enable TLS over SMPP]** kan du kryptera SMPP-trafik. Se denna [sida](sms-protocol.md) för mer information om detta.

1. Om du konfigurerar en **[!UICONTROL Extended generic SMPP]**-anslutning kan du konfigurera automatiska svar.

   Mer information om detta finns i [det här avsnittet](#automatic-reply).

## SMS-teckentranskribering {#about-character-transliteration}

Teckentranskribering kan ställas in i ett externt SMPP-konto för mobil leverans, på fliken **[!UICONTROL Mobile]**.

Transkriberingen ersätter ett tecken i ett SMS med ett annat om det tecknet inte beaktas av GSM-standarden.

* Om transkriberingen är **[!UICONTROL authorized]** ersätts varje tecken som inte beaktas av ett GSM-tecken när meddelandet skickas. Bokstaven &quot;ë&quot; kommer exempelvis att ersättas med &quot;e&quot;.  Meddelandet ändras därför något men teckengränsen förblir densamma.
* När transkriberingen är **[!UICONTROL not authorized]** skickas varje meddelande som innehåller tecken som inte tas med i beräkningen i binärt format (Unicode): alla tecken skickas därför som de är. SMS-meddelanden som använder Unicode är dock begränsade till 70 tecken (eller 67 tecken per SMS för meddelanden som skickas i flera delar).  Om det maximala antalet tecken överskrids skickas flera meddelanden vilket kan medföra extra kostnader.

>[!IMPORTANT]
>
>Om du infogar anpassningsfält i innehållet i SMS-meddelandet kan det medföra tecken som GSM-kodningen inte tar hänsyn till.

Som standard är teckentranskribering inaktiverat.  Om du vill att samtliga tecken i SMS-meddelanden ska behållas som de är bör du inte aktivera det här alternativet.

Om dina SMS-meddelanden innehåller många tecken som genererar Unicode-meddelanden kan du välja att aktivera det här alternativet för att begränsa kostnaderna för att skicka meddelanden.

I följande tabell visas de tecken som GSM-standarden tar hänsyn till. Alla tecken som infogats i meddelandetexten, förutom de som nämns nedan, konverterar hela meddelandet till binärt format (Unicode) och begränsar det därför till 70 tecken.

**Grundläggande tecken**

<table> 
 <tbody> 
  <tr> 
   <td> @ </td> 
   <td> <img height="21px" src="assets/delta.png" /> </td> 
   <td> SP </td> 
   <td> 0 </td> 
   <td> ○ </td> 
   <td> P </td> 
   <td> as </td> 
   <td> p </td> 
  </tr> 
  <tr> 
   <td> £ </td> 
   <td> _ </td> 
   <td> ! </td> 
   <td> 1 </td> 
   <td> A </td> 
   <td> Q </td> 
   <td> a </td> 
   <td> q </td> 
  </tr> 
  <tr> 
   <td> $ </td> 
   <td> <img height="21px" src="assets/phi.png" /> </td> 
   <td> " </td> 
   <td> 2 </td> 
   <td> B </td> 
   <td> R </td> 
   <td> b </td> 
   <td> r </td> 
  </tr> 
  <tr> 
   <td> ¥ </td> 
   <td> <img height="21px" src="assets/gamma.png" /> </td> 
   <td> # </td> 
   <td> 3 </td> 
   <td> C </td> 
   <td> S </td> 
   <td> c </td> 
   <td> s </td> 
  </tr> 
  <tr> 
   <td> É </td> 
   <td> <img height="21px" src="assets/delta.png" /> </td> 
   <td> ¤ </td> 
   <td> 4 </td> 
   <td> D </td> 
   <td> T </td> 
   <td> d </td> 
   <td> t </td> 
  </tr> 
  <tr> 
   <td> é </td> 
   <td> <img height="21px" src="assets/omega.png" /> </td> 
   <td> % </td> 
   <td> 5 </td> 
   <td> E </td> 
   <td> U </td> 
   <td> e </td> 
   <td> u </td> 
  </tr> 
  <tr> 
   <td> ñ </td> 
   <td> <img height="21px" src="assets/pi.png" /> </td> 
   <td> &amp; </td> 
   <td> 6 </td> 
   <td> F </td> 
   <td> V </td> 
   <td> f </td> 
   <td> v </td> 
  </tr> 
  <tr> 
   <td> Maximum </td> 
   <td> <img height="21px" src="assets/psi.png" /> </td> 
   <td> ' </td> 
   <td> 7 </td> 
   <td> G </td> 
   <td> B </td> 
   <td> g </td> 
   <td> w </td> 
  </tr> 
  <tr> 
   <td> systemkrav </td> 
   <td> <img height="21px" src="assets/sigma.png" /> </td> 
   <td> ( </td> 
   <td> 8 </td> 
   <td> H </td> 
   <td> X </td> 
   <td> h </td> 
   <td> x </td> 
  </tr> 
  <tr> 
   <td> else </td> 
   <td> <img height="21px" src="assets/theta.png" /> </td> 
   <td> ) </td> 
   <td> 9 </td> 
   <td> I </td> 
   <td> Y </td> 
   <td> i </td> 
   <td> y </td> 
  </tr> 
  <tr> 
   <td> LF </td> 
   <td> <img height="21px" src="assets/xi.png" /> </td> 
   <td> * </td> 
   <td> : </td> 
   <td> J </td> 
   <td> Z </td> 
   <td> j </td> 
   <td> z </td> 
  </tr> 
  <tr> 
   <td> Ø </td> 
   <td> ESC </td> 
   <td> + </td> 
   <td> ; </td> 
   <td> K </td> 
   <td> Ä </td> 
   <td> k </td> 
   <td> ä </td> 
  </tr> 
  <tr> 
   <td> ø </td> 
   <td> AE </td> 
   <td> , </td> 
   <td> &lt; </td> 
   <td> L </td> 
   <td> Ö </td> 
   <td> l </td> 
   <td> ö </td> 
  </tr> 
  <tr> 
   <td> CR </td> 
   <td> æ </td> 
   <td> - </td> 
   <td> = </td> 
   <td> M </td> 
   <td> Ð </td> 
   <td> m </td> 
   <td> ñ </td> 
  </tr> 
  <tr> 
   <td> Å </td> 
   <td> ß </td> 
   <td> . </td> 
   <td> &gt; </td> 
   <td> N </td> 
   <td> Ü </td> 
   <td> n </td> 
   <td> ä </td> 
  </tr> 
  <tr> 
   <td> å </td> 
   <td> É </td> 
   <td> / </td> 
   <td> ? </td> 
   <td> O </td> 
   <td> § </td> 
   <td> o </td> 
   <td> à </td> 
  </tr> 
 </tbody> 
</table>

SP: Blanksteg

ESC: Escape

LF: Radmatning

CR: Radretur

**Avancerade tecken (räknas två gånger)**

^ { } `[ ~ ]` | €

## Textkodning {#about-text-encodings}

När du skickar ett SMS kan Adobe Campaign använda en eller flera textkodningar.  Varje kodning har en egen specifik teckenuppsättning och avgör antalet tecken som får plats i ett SMS.

När du konfigurerar ett nytt externt SMPP-mobilleveranskonto kan du definiera **[!UICONTROL Mapping of encodings]** på fliken **[!UICONTROL Mobile]**: i fältet **[!UICONTROL data_coding]** kan Adobe Campaign kommunicera vilken kodning som används för SMSC.

>[!NOTE]
>
>Mappningen mellan **data_coding**-värdet och den kodning som faktiskt används är standardiserad.  Vissa SMSC har dock en egen specifik mappning: i det här fallet måste din **Adobe Campaign**-administratör deklarera den här mappningen. Kontakta din leverantör för mer information.

Du kan deklarera **data_codings** och tvinga fram kodningen om det behövs. Om du vill göra det anger du en enda kodning i tabellen.

* När ingen mappning av kodningar har definierats får kopplingen ett generiskt beteende:

   * Den försöker då använda GSM-kodning som den tilldelar värdet **data_coding = 0**.
   * Om GSM-kodningen misslyckas används **UCS2**-kodning som värdet **data_coding = 8** tilldelas till.

* När du definierar de kodningar som du vill använda samt de länkade **[!UICONTROL data_coding]**-fältvärdena, kommer Adobe Campaign att försöka använda den första kodningen i listan och sedan följande, om den första kodningen visar sig vara omöjlig.

>[!IMPORTANT]
>
>Deklarationsordningen är viktig: Vi rekommenderar att du placerar listan i stigande ordning **för omkostnader** så att du kan välja kodningar som gör att du får plats med så många tecken som möjligt i varje SMS.
>
>Deklarera bara de kodningar som du vill använda.  Om en del av de kodningar som SMSC tillhandahåller inte stämmer överens med ditt användningsändamål ska de inte tas upp i listan.

## Automatiskt svar {#automatic-reply}

När du konfigurerar en utökad allmän SMPP-anslutning kan du konfigurera automatiska svar.

När en prenumerant svarar på ett SMS-meddelande som skickades till dem via Adobe Campaign och deras meddelande innehåller ett nyckelord som &quot;STOP&quot;, kan du konfigurera meddelanden som automatiskt skickas tillbaka till dem i avsnittet **[!UICONTROL Automatic reply sent to the MO]**.

>[!NOTE]
>
>Nyckelorden är inte skiftlägeskänsliga.

För varje nyckelord anger du en kort kod, vilket är ett nummer som vanligtvis används för att skicka leveranser och som fungerar som avsändarnamn, och anger sedan meddelandet som ska skickas till prenumeranten.

Du kan även länka en åtgärd till ditt automatiska svar: **[!UICONTROL Send to quarantine]** eller **[!UICONTROL Remove from quarantine]**. Om en mottagare t.ex. skickar nyckelordet &quot;STOP&quot; får han/hon automatiskt en bekräftelse på att han/hon inte längre är prenumererad och skickas till karantän.

![](assets/extended_smpp_reply.png)

Om du länkar åtgärden **[!UICONTROL Remove from quarantine]** till ett automatiskt svar tas mottagarna som skickar motsvarande nyckelord automatiskt bort från karantänen.

Mottagarna visas i tabellen **[!UICONTROL Non deliverables and addresses]** som är tillgänglig via menyn **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]**.

* Om du vill skicka samma svar oavsett den korta koden lämnar du kolumnen **[!UICONTROL Short code]** tom.
* Om du vill skicka samma svar oavsett nyckelordet lämnar du kolumnen **[!UICONTROL Keyword]** tom.
* Om du vill utföra en åtgärd utan att skicka ett svar lämnar du kolumnen **[!UICONTROL Response]** tom. På så sätt kan du till exempel ta bort en användare som svarar med ett annat meddelande än&quot;STOP&quot; från karantänen.

Om du har flera externa konton som använder den utökade generiska SMPP-anslutningen med samma leverantörskonto kan följande problem uppstå: när du skickar ett svar på en kort kod kan den tas emot på någon av dina externa kontoanslutningar. Det automatiska svaret som skickas kunde därför inte vara det förväntade meddelandet.
Du kan undvika detta genom att använda någon av följande lösningar, beroende på vilken leverantör du använder:

* Skapa ett leverantörskonto för varje externt konto.
* Använd fältet **[!UICONTROL System type]** från fliken **[!UICONTROL Mobile]** > **[!UICONTROL Connection settings]** för att skilja på kortkoderna. Fråga leverantören ett annat värde för varje konto.

  ![](assets/extended_smpp_system-type.png)

Stegen för att konfigurera ett externt konto med den utökade generiska SMPP-anslutningen beskrivs i avsnittet [Skapa ett externt SMPP-konto](#creating-an-smpp-external-account).

## Ändra leveransmallen {#changing-the-delivery-template}

Adobe Campaign förser dig med en mall för att leverera till mobiler. Den här mallen är tillgänglig i noden **[!UICONTROL Resources > Templates > Delivery templates]**. Mer information finns i avsnittet [Om mallar](about-templates.md).

Om du vill leverera via SMS-kanal måste du skapa en mall där kanalkopplingen refereras.

För att behålla den inbyggda leveransmallen rekommenderar vi att du duplicerar den och sedan konfigurerar den.

I exemplet nedan skapar vi en mall för att leverera meddelanden via det SMPP-konto som aktiverats tidigare. Så här gör du:

1. Gå till noden **[!UICONTROL Delivery templates]**.
1. Högerklicka på mallen **[!UICONTROL Send to mobiles]** och välj **[!UICONTROL Duplicate]**.

   ![](assets/s_user_mobile_template_change_01.png)

1. Ändra mallens etikett, till exempel **Skickat till mobiler (SMPP)**.

   ![](assets/s_user_mobile_template_change_02.png)

1. Klicka på **[!UICONTROL Properties]**.
1. På fliken **[!UICONTROL General]** väljer du ett routningsläge som motsvarar det externa konto som du skapade i föregående steg.

   ![](assets/s_user_mobile_template_change_03.png)

1. Klicka på **[!UICONTROL Save]** för att skapa mallen.

   ![](assets/s_user_mobile_template_list.png)

Du har nu ett externt konto och en leveransmall som gör att du kan leverera via SMS.
