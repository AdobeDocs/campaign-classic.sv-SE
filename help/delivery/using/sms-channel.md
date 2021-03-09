---
solution: Campaign Classic
product: campaign
title: SMS-kanal
description: SMS-kanal
audience: delivery
content-type: reference
topic-tags: sending-messages-on-mobiles
translation-type: tm+mt
source-git-commit: f78fa94fb4fb9236222886a167a46d252497b2aa
workflow-type: tm+mt
source-wordcount: '3131'
ht-degree: 20%

---


# SMS-kanal{#sms-channel}

Med Adobe Campaign kan ni utföra massutskick av personaliserade SMS-meddelanden. Mottagarprofilerna måste innehålla minst ett mobiltelefonnummer.

>[!NOTE]
>
>I Adobe Campaign kan du även skicka meddelanden på mobilterminaler via alternativet **Adobe Campaign Mobile App Channel (NMAC)**.
> 
>Mer information finns i [Om mobilappskanalen](../../delivery/using/about-mobile-app-channel.md).

Avsnitten nedan innehåller information som är specifik för SMS-kanalen. Global information om hur du skapar en leverans finns i [det här avsnittet](../../delivery/using/steps-about-delivery-creation-steps.md).

## Konfigurera SMS-kanal {#setting-up-sms-channel}

Om du vill skicka till en mobiltelefon behöver du:

1. Ett externt konto som anger en koppling och typ av meddelande.

   Observera att följande anslutningar kommer att bli inaktuella från och med version 20.2: Generic SMPP (SMPP version 3.4 med stöd för binärt läge), Sybase365 (SAP SMS 365), CLX Communications, Tele2, O2 och iOS. Det finns fortfarande funktioner som inte längre används, men de kommer inte att förbättras ytterligare eller stödjas. Se denna [sida](https://helpx.adobe.com/se/campaign/kb/deprecated-and-removed-features.html) för mer information om detta.

1. En leveransmall där det här externa kontot refereras.

### Skapar ett SMPP-externt konto {#creating-an-smpp-external-account}

Om du vill skicka ett SMS till en mobiltelefon måste du först skapa ett externt SMPP-konto.
Mer information om SMS-protokoll och inställningar finns på den här [sidan](../../delivery/using/sms-protocol.md).

Följ stegen nedan för att göra detta:

1. Klicka på ikonen **[!UICONTROL New]** i noden **[!UICONTROL Platform]** > **[!UICONTROL External accounts]** i trädet.
1. Definiera kontotypen som **Routning**, kanalen som **Mobil (SMS)** och leveransläget som **Massleverans**.

   ![](assets/extended_smpp_create_account.png)

1. Markera rutan **[!UICONTROL Enabled]**.
1. Välj **[!UICONTROL Extended generic SMPP]** i listrutan **[!UICONTROL Connector]** på fliken **[!UICONTROL Mobile]**.

   ![](assets/extended_smpp_connector.png)

   >[!CAUTION]
   >
   > Från och med version 20.2 är äldre anslutningar borttagna och stöds inte. Vi rekommenderar att du använder **[!UICONTROL Extended generic SMPP]**-kontakten. Mer information om hur du migrerar till den rekommenderade anslutningen finns på den här [sidan](../../delivery/using/unsupported-connector-migration.md).

1. Med alternativet **[!UICONTROL Enable verbose SMPP traces in the log file]** kan du dumpa all SMPP-trafik i loggfiler. Det här alternativet måste vara aktiverat för att kunna felsöka anslutningen och jämföra med den trafik som leverantören ser.

1. Kontakta din SMS-tjänstleverantör som förklarar hur du fyller i de olika externa kontofälten på fliken **[!UICONTROL Connection settings]**.

   Kontakta sedan leverantören, beroende på vilken som valts, som ger dig värdet att ange i fältet **[!UICONTROL SMSC implementation name]**.

   Du kan definiera antalet anslutningar till providern per underordnat MTA-objekt. Som standard är den inställd på 1.

1. Som standard uppfyller antalet tecken i ett SMS GSM-standarden.

   SMS-meddelanden som använder GSM-kodning kan innehålla högst 160 tecken eller 153 tecken per SMS för meddelanden som skickas i flera delar.

   >[!NOTE]
   >
   >Vissa tecken räknas som två (parenteser, hakparanteser, eurosymbolen etc.).  
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

   Med kryssrutan **[!UICONTROL Enable TLS over SMPP]** kan du kryptera SMPP-trafik. Se denna [sida](../../delivery/using/sms-protocol.md) för mer information om detta.

1. Om du konfigurerar en **[!UICONTROL Extended generic SMPP]**-anslutning kan du konfigurera automatiska svar.

   Mer information om detta finns i [det här avsnittet](#automatic-reply).

### Om teckentransformering {#about-character-transliteration}

Teckentranskribering kan ställas in i ett externt SMPP-konto för mobil leverans, under fliken **[!UICONTROL Mobile]**.

Transkriberingen ersätter ett tecken i ett SMS med ett annat om det tecknet inte beaktas av GSM-standarden.

* Om transkriberingen är **[!UICONTROL authorized]** ersätts varje tecken som inte beaktas av ett GSM-tecken när meddelandet skickas. Bokstaven &quot;ë&quot; kommer exempelvis att ersättas med &quot;e&quot;.  Meddelandet ändras därför något men teckengränsen förblir densamma.
* När transkriberingen är **[!UICONTROL not authorized]** skickas varje meddelande som innehåller tecken som inte tas med i beräkningen i binärt format (Unicode): alla tecken skickas därför som de är. SMS-meddelanden som använder Unicode är dock begränsade till 70 tecken (eller 67 tecken per SMS för meddelanden som skickas i flera delar).  Om det maximala antalet tecken överskrids skickas flera meddelanden vilket kan medföra extra kostnader.

>[!IMPORTANT]
>
>Om du infogar anpassningsfält i innehållet av SMS-meddelandet kan det medföra tecken som GSM-kodningen inte tar hänsyn till.  

Som standard är teckentranskribering inaktiverat.  Om du vill att samtliga tecken i SMS-meddelanden ska behållas som de är bör du inte aktivera det här alternativet.

Om dina SMS-meddelanden innehåller många tecken som genererar Unicode-meddelanden kan du välja att aktivera det här alternativet för att begränsa kostnaderna för att skicka meddelanden.

I följande tabell visas de tecken som GSM-standarden tar hänsyn till. Alla tecken som infogats i meddelandetexten förutom de som nämns nedan konverterar hela meddelandet till binärt format (Unicode) och begränsar det därför till 70 tecken.  

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
   <td> è </td> 
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
   <td> ù </td> 
   <td> <img height="21px" src="assets/pi.png" /> </td> 
   <td> &amp; </td> 
   <td> 6 </td> 
   <td> F </td> 
   <td> V </td> 
   <td> f </td> 
   <td> v </td> 
  </tr> 
  <tr> 
   <td> ì </td> 
   <td> <img height="21px" src="assets/psi.png" /> </td> 
   <td> ' </td> 
   <td> 7 </td> 
   <td> G </td> 
   <td> W </td> 
   <td> g </td> 
   <td> w </td> 
  </tr> 
  <tr> 
   <td> ò </td> 
   <td> <img height="21px" src="assets/sigma.png" /> </td> 
   <td> ( </td> 
   <td> 8 </td> 
   <td> H </td> 
   <td> X </td> 
   <td> h </td> 
   <td> x </td> 
  </tr> 
  <tr> 
   <td> Ç </td> 
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
   <td> Æ </td> 
   <td> , </td> 
   <td> &lt;&gt; </td> 
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
   <td> Ñ </td> 
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
   <td> ü </td> 
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

### Om textkodning {#about-text-encodings}

När du skickar ett SMS kan Adobe Campaign använda en eller flera textkodningar.  Varje kodning har en egen specifik teckenuppsättning och avgör antalet tecken som får plats i ett SMS.

När du konfigurerar ett nytt externt SMPP-konto för mobil leverans kan du definiera **[!UICONTROL Mapping of encodings]** på fliken **[!UICONTROL Mobile]**: I fältet **[!UICONTROL data_coding]** kan Adobe Campaign kommunicera vilken kodning som används för SMSC.

>[!NOTE]
>
>Mappningen mellan **data_coding**-värdet och den kodning som faktiskt används är standardiserad.  Vissa SMSC har dock en egen specifik mappning: I det här fallet måste din **Adobe Campaign**-administratör deklarera den här mappningen. Kontakta din leverantör för mer information.

Du kan deklarera **data_codings** och tvinga kodningen om det behövs: Om du vill göra det anger du en enda kodning i tabellen.

* När ingen mappning av kodningar har definierats får kopplingen ett generiskt beteende:

   * Den försöker då använda GSM-kodning som den tilldelar värdet **data_coding = 0**.
   * Om GSM-kodningen misslyckas används **UCS2**-kodning som värdet **data_coding = 8** tilldelas till.

* När du definierar de kodningar som du vill använda samt de länkade fältvärdena för **[!UICONTROL data_coding]**, försöker Adobe Campaign använda den första kodningen i listan och sedan följande, om den första kodningen visar sig vara omöjlig.

>[!IMPORTANT]
>
>Deklarationsordningen är viktig: Vi rekommenderar att du placerar listan i stigande ordning **för omkostnader** så att du kan välja kodningar som gör att du får plats med så många tecken som möjligt i varje SMS.
>
>Deklarera bara de kodningar som du vill använda.  Om en del av de kodningar som SMSC tillhandahåller inte stämmer överens med ditt användningsändamål ska de inte tas upp i listan.

### Automatiskt svar {#automatic-reply}

När du konfigurerar en utökad allmän SMPP-anslutning kan du konfigurera automatiska svar.

När en prenumerant svarar på ett SMS-meddelande som skickades till dem via Adobe Campaign och deras meddelande innehåller ett nyckelord som &quot;STOP&quot;, kan du konfigurera meddelanden som automatiskt skickas tillbaka till dem i **[!UICONTROL Automatic reply sent to the MO]**-avsnittet.

>[!NOTE]
>
>Nyckelorden är inte skiftlägeskänsliga.

För varje nyckelord anger du en kort kod, vilket är ett nummer som vanligtvis används för att skicka leveranser och som fungerar som avsändarnamn, och anger sedan meddelandet som ska skickas till prenumeranten.

Du kan även länka en åtgärd till ditt automatiska svar: **[!UICONTROL Send to quarantine]** eller **[!UICONTROL Remove from quarantine]**. Om en mottagare t.ex. skickar nyckelordet &quot;STOP&quot; får han/hon automatiskt en bekräftelse på att han/hon inte längre är prenumererad och skickas till karantän.

![](assets/extended_smpp_reply.png)

Om du länkar **[!UICONTROL Remove from quarantine]**-åtgärden till ett automatiskt svar tas mottagarna som skickar motsvarande nyckelord automatiskt bort från karantänen.

Mottagarna visas i tabellen **[!UICONTROL Non deliverables and addresses]** som är tillgänglig via menyn **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]**.

* Om du vill skicka samma svar oavsett vilken kort kod det är lämnar du kolumnen **[!UICONTROL Short code]** tom.
* Om du vill skicka samma svar oavsett nyckelordet lämnar du kolumnen **[!UICONTROL Keyword]** tom.
* Om du vill utföra en åtgärd utan att skicka ett svar lämnar du kolumnen **[!UICONTROL Response]** tom. På så sätt kan du till exempel ta bort en användare som svarar med ett annat meddelande än&quot;STOP&quot; från karantänen.

Om du har flera externa konton som använder den utökade allmänna SMPP-anslutningen med samma leverantörskonto kan följande problem uppstå: när du skickar ett svar till en kort kod kan det tas emot på någon av dina externa kontoanslutningar. Det automatiska svaret som skickas kunde därför inte vara det förväntade meddelandet.
Du undviker detta genom att använda någon av följande lösningar, beroende på vilken leverantör du använder:

* Skapa ett leverantörskonto för varje externt konto.
* Använd fältet **[!UICONTROL System type]** från fliken **[!UICONTROL Mobile]** > **[!UICONTROL Connection settings]** för att skilja på kortkoderna. Fråga leverantören ett annat värde för varje konto.

   ![](assets/extended_smpp_system-type.png)

Stegen för att konfigurera ett externt konto med den utökade generiska SMPP-anslutningen beskrivs i avsnittet [Skapa ett SMPP-externt konto](../../delivery/using/sms-channel.md#creating-an-smpp-external-account).

### Ändra leveransmallen {#changing-the-delivery-template}

Adobe Campaign förser dig med en mall för att leverera till mobiler. Den här mallen är tillgänglig i noden **[!UICONTROL Resources > Templates > Delivery templates]**. Mer information finns i avsnittet [Om mallar](../../delivery/using/about-templates.md).

Om du vill leverera via SMS-kanal måste du skapa en mall där kanalkopplingen refereras.

För att behålla den inbyggda leveransmallen rekommenderar vi att du duplicerar den och sedan konfigurerar den.

I exemplet nedan skapar vi en mall för att leverera meddelanden via det SMPP-konto som aktiverats tidigare. Så här gör du:

1. Gå till noden **[!UICONTROL Delivery templates]**.
1. Högerklicka på mallen **[!UICONTROL Send to mobiles]** och välj **[!UICONTROL Duplicate]**.

   ![](assets/s_user_mobile_template_change_01.png)

1. Ändra mallens etikett, till exempel **Skickat till mobiler (SMPP)**.

   ![](assets/s_user_mobile_template_change_02.png)

1. Klicka på **[!UICONTROL Properties]**.
1. På fliken **[!UICONTROL General]** väljer du ett routningsläge som motsvarar det externa konto du skapade i föregående steg.

   ![](assets/s_user_mobile_template_change_03.png)

1. Klicka på **[!UICONTROL Save]** för att skapa mallen.

   ![](assets/s_user_mobile_template_list.png)

Du har nu ett externt konto och en leveransmall som gör att du kan leverera via SMS.

## Skapa en SMS-leverans {#creating-a-sms-delivery}

### Välja leveranskanal {#selecting-the-delivery-channel}

Följ stegen nedan för att skapa en ny SMS-leverans:

>[!NOTE]
>
>Globala koncept för leveransskapande beskrivs i [det här avsnittet](../../delivery/using/steps-about-delivery-creation-steps.md).

1. Skapa en ny leverans, till exempel från kontrollpanelen Leverans.
1. Välj leveransmallen **Skickat till mobiler (SMPP)** som du skapade tidigare. Mer information finns i avsnittet [Ändra leveransmallen](#changing-the-delivery-template).

   ![](assets/s_user_mobile_wizard.png)

1. Identifiera leveransen med en etikett, kod och beskrivning. Mer information om detta finns i [det här avsnittet](../../delivery/using/steps-create-and-identify-the-delivery.md#identifying-the-delivery).
1. Klicka på **[!UICONTROL Continue]** för att bekräfta informationen och visa meddelandekonfigurationsfönstret.

## Definiera SMS-innehållet {#defining-the-sms-content}

Följ stegen nedan för att skapa innehållet i SMS:et:

1. Ange innehållet i meddelandet i **[!UICONTROL Text content]**-avsnittet i guiden. Med verktygsfältsknapparna kan du importera, spara och söka i innehåll. Den sista knappen används för att infoga anpassningsfält.

   ![](assets/s_ncs_user_wizard_sms01_138.png)

   Användningen av anpassningsfält beskrivs i [Om personalisering](../../delivery/using/about-personalization.md).

1. Klicka på **[!UICONTROL Preview]** längst ned på sidan för att visa återgivningen av meddelandet med dess personalisering. Om du vill starta förhandsgranskningen väljer du en mottagare med knappen **[!UICONTROL Test personalization]** i verktygsfältet. Du kan välja en mottagare bland de definierade målen eller en annan mottagare.

   ![](assets/s_ncs_user_wizard_sms01_139.png)

   Du kan godkänna SMS-meddelandet. Du kan även visa innehållet i SMS-meddelandet på mobiltelefonskärmen till höger om innehållsredigeraren. Klicka på skärmen och använd musen för att bläddra igenom innehållet.

   ![](assets/s_ncs_user_wizard_sms01_140.png)

1. Klicka på länken **[!UICONTROL Data loaded]** för att visa information om mottagaren.

   ![](assets/s_user_mobile_wizard_sms_02.png)

   >[!NOTE]
   >
   >SMS-meddelanden är begränsade till en längd på 160 tecken om den latinska 1-teckentabellen (ISO-8859-1) används. Om meddelandet skrivs i Unicode får det inte innehålla fler än 70 tecken. Vissa specialtecken kan påverka meddelandets längd. Mer information om meddelandets längd finns i avsnittet [Om teckentranslitterering](#about-character-transliteration).
   >
   >När det finns anpassningsfält eller fält för villkorligt innehåll varierar meddelandets storlek från en mottagare till en annan. Meddelandets längd måste utvärderas när personalisering har utförts.
   >
   >När du startar analysen kontrolleras meddelandets längd och en varning visas om det skulle uppstå ett spill.

1. Om du använder NetSize-anslutningen eller en SMPP-anslutning kan du anpassa namnet på leveransavsändaren. Mer information finns i avsnittet [Avancerade parametrar](#advanced-parameters).

## Välja målpopulationen {#selecting-the-target-population}

Den detaljerade processen när målpopulationen för en leverans väljs visas i [det här avsnittet](../../delivery/using/steps-defining-the-target-population.md).

Mer information om användning av anpassningsfält finns i [Om personalisering](../../delivery/using/about-personalization.md).

Mer information om att ta med en startvärdeslista finns i [Om startadresser](../../delivery/using/about-seed-addresses.md).

## Skicka SMS-meddelanden {#sending-sms-messages}

Om du vill godkänna meddelandet och skicka det till mottagarna av den leverans som skapas klickar du på **[!UICONTROL Send]**.

Den detaljerade processen för att validera och skicka en leverans presenteras i avsnitten nedan:

* [Verifierar leveransen](../../delivery/using/steps-validating-the-delivery.md)
* [Skicka leveransen](../../delivery/using/steps-sending-the-delivery.md)

### Avancerade parametrar {#advanced-parameters}

Knappen **[!UICONTROL Properties]** ger åtkomst till den avancerade leveransparametern. Parametrarna som är specifika för SMS-leveranser finns i avsnittet **[!UICONTROL SMS parameters]** på fliken **[!UICONTROL Delivery]**.

Följande alternativ är tillgängliga:

* **Avsändarens adress**: Med kan du anpassa namnet på avsändaren med en alfanumerisk teckensträng som är begränsad till elva tecken. Fältet får inte uteslutande bestå av siffror. Du kan definiera ett villkor som ska visas, t.ex. med olika namn beroende på mottagarens riktnummer:

   ```
   <% if( String(recipient.mobilePhone).indexOf("+1") == 0){ %>NeoShopUS<%} else {%>NeoShopWorld<%}%>
   ```

   >[!IMPORTANT]
   >
   >Läs lagen i ditt land om hur du redigerar avsändarnamn. Du bör också fråga din operatör om de erbjuder den här funktionen.

* **Överföringsläge**: meddelandeöverföring via SMS.
* **Prioritet**: prioritetsnivå som tilldelats ett meddelande. **[!UICONTROL Normal]** som standard är prioritet vald. Fråga tjänsteleverantören om kostnaden för SMS som skickas med **[!UICONTROL High]** prioritet.
* **Typ av program**: välj det program som du vill tilldela din SMS-leverans. Alternativet **[!UICONTROL Direct Marketing]** är valt som standard och är det vanligaste alternativet.

**Parametrar som är specifika för NetSize-kopplingen**

![](assets/s_user_mobile_sms_adv_netsize.png)

* **Använd flera SMS för ett enda meddelande**: Detta gör att du kan skicka ett meddelande som är längre än 160 tecken via flera SMS-meddelanden.

**Parametrar som är specifika för en SMPP-anslutning**

![](assets/s_user_mobile_sms_adv_smpp.png)

* **Högsta antal SMS per meddelande**: Med det här alternativet kan du ange hur många SMS som ska användas för att skicka ett meddelande. Om värdet är 0 kan du skicka meddelandet med ett SMS. Om antalet SMS är inställt på 1 eller 2 och meddelandet överskrider tröskelvärdet skickas det inte.

## Övervaka och spåra SMS-leveranser {#monitoring-and-tracking-sms-deliveries}

När du har skickat meddelanden kan du övervaka och spåra dina leveranser. Mer information om detta hittar du i dessa avsnitt.

* [Övervaka en leverans](../../delivery/using/about-delivery-monitoring.md)
* [Förstå leveransfel](../../delivery/using/understanding-delivery-failures.md)
* [Om att spåra meddelanden](../../delivery/using/about-message-tracking.md)

## Bearbetar inkommande meddelanden {#processing-inbound-messages}

Modulen **nlserver sms** frågar SMS-routern med regelbundna intervall. Detta gör att Adobe Campaign kan följa upp leveransförloppet och hantera statusrapporter och mottagarnas begäran om att ta bort prenumerationen.

* **Statusrapporter**: visa leveransloggar för att kontrollera status för dina meddelanden.

   >[!NOTE]
   >
   >Varje SMS som skickas är länkat till ett externt konto och dess primärnyckel. På det här sättet:
   >
   > * Statusrapporter från ett borttaget externt SMS-konto bearbetas inte korrekt.
   > * Ett SMS-konto kan bara länkas till ett enda externt konto för att säkerställa att statusrapporter tilldelas rätt konto


* **Avbeställ**: Mottagare som inte längre vill ta emot SMS-leveranser kan returnera ett meddelande som innehåller ordet STOP. Om din leverantör tillåter det enligt avtalsvillkoren kan du hämta meddelanden via arbetsflödesaktiviteten **Inkommande SMS** och sedan skapa en fråga för att aktivera alternativet **Kontakta inte längre den här mottagaren** för de berörda mottagarna.

   Se guiden [Arbetsflöden](../../workflow/using/architecture.md).

## InSMS-schema {#insms-schema}

InSMS-schemat innehåller information som är relevant för inkommande SMS. En beskrivning av dessa fält är tillgänglig via attributet desc.

* **meddelande**: det SMS som togs emot.
* **ursprung**: mobilnummer i meddelandets ursprung.
* **providerId**: Identifierare för det meddelande som returneras av SMSC (meddelandecenter).
* **skapad**: datum då inkommande meddelande infogades i Adobe Campaign.
* **TextAccount**: Adobe Campaign externa konto.

   >[!IMPORTANT]
   >
   >Följande fält är specifika för NetSize.
   >
   >Om operatorn som används inte är NetSize, betraktas dessa fält som tomma.

* **alias**: alias för inkommande meddelande.
* **avgränsare**: avgränsare mellan aliaset och meddelandets brödtext.
* **messageDate**: meddelandedatum angivet av operator.
* **receiveDate**: Datummeddelande från operatorn togs emot av SMSC (meddelandecenter).
* **deliveryDate**: Datummeddelande från SMSC (meddelandecenter).
* **largeAccount**: kundkontokod länkad till inkommande SMS.
* **countryCode**: landskod för operator.
* **operatorCode**: operatörens nätverkskod.
* **linkedSmsId**: Adobe Campaign-identifierare (broadlogId) länkad till utgående SMS, där detta SMS är svaret.

## Hantera automatiska svar (amerikansk förordning) {#managing-automatic-replies--american-regulation-}

När prenumeranterna svarar på ett SMS-meddelande som skickats till dem via Adobe Campaign och använder ett nyckelord som STOP, HELP eller YES, är det nödvändigt att konfigurera meddelanden som returneras automatiskt på den amerikanska marknaden.

Om mottagarna skickar nyckelordet STOP får de automatiskt ett bekräftelsemeddelande om att de har avbeställt prenumerationen.

Avsändarnamnet för den här meddelandetypen är en kort kod som vanligtvis används för att skicka leveranser.

>[!IMPORTANT]
>
>Följande detaljerade procedur gäller bara för SMPP-anslutningar, utom för den utökade generiska SMPP-anslutningen. Mer information finns i avsnittet [Skapa ett externt SMPP-konto](#creating-an-smpp-external-account).
>
>Det utgör en del av den certifieringsprocess som utförs av amerikanska aktörer för marknadsföringskampanjer i USA. Dessa svar på SMS-meddelanden som innehåller nyckelordet måste skickas tillbaka till prenumeranten omedelbart efter att ett meddelande har tagits emot.

1. Skapa den här typen av XML-fil:

   ```
   <autoreply>
     <shortcode name="12345">
       <reply keyword="STOP" text="You will not receive SMS anymore" />
       <reply keyword="HELP" text="Powered by Adobe Campaign" />
     </shortcode>
     <shortcode name="43115">
       <reply keyword="STOP" text="Vous ne recevrez plus de SMS" />
       <reply keyword="HELP" text="Service rendu par Adobe Campaign" />
     </shortcode>
     <shortcode name="*">
       <reply keyword="ADOBE" text="This text is replied when you send ADOBE to any short code" />
     </shortcode>
   </autoreply>
   ```

1. För attributet **name** för taggen **`<shortcode>`** anger du den korta kod som ska visas i stället för meddelandets avsändarnamn.

   I varje **`<reply>`**-tagg anger du **nyckelordsattributet** med ett nyckelord och **text**-attributet med meddelandet som du vill skicka för det här nyckelordet.

   >[!NOTE]
   >
   >Varje nyckelord måste skrivas med versaler.

   Om du vill skicka samma meddelande för flera nyckelord duplicerar du motsvarande rad.

   Exempel:

   ```
   <reply keyword="STOP" text="You will not receive SMS anymore" />
   <reply keyword="QUIT" text="You will not receive SMS anymore" />
   ```

1. När du är klar sparar du den här filen under namnet **smsAutoReply.xml**.

   Observera att filens namn är skiftlägeskänsligt i Linux.

1. Kopiera den här filen till katalogen **conf** i Adobe Campaign, på samma plats som webbservern.

>[!IMPORTANT]
>
>Den här typen av automatiska meddelanden sparar ingen historik. Därför visas de inte på [kontrollpanelen](../../delivery/using/delivery-dashboard.md).
>
>Dessa meddelanden anses inte ingå i [reglerna för kommersiellt tryck](../../campaign/using/pressure-rules.md).
