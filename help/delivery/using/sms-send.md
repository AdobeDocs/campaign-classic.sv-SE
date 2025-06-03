---
product: campaign
title: Skicka, övervaka och spåra SMS
description: Lär dig hur du skickar, övervakar och spårar SMS i Campaign
feature: SMS
role: User
exl-id: 442672ee-5037-49b7-a06f-3a99920ce2b6
source-git-commit: 42cec0e9bede94a2995a5ad442822512bda14f2b
workflow-type: tm+mt
source-wordcount: '887'
ht-degree: 0%

---

# Ytterligare konfiguration{#sms-properties}

<!--
## Send SMS messages {#sending-sms-messages}

To approve your message and send it to the recipients of the delivery being created, click **[!UICONTROL Send]**.

The detailed process when validating and sending a delivery is presented in the sections below:

* [Validate the delivery](steps-validating-the-delivery.md)
* [Send the delivery](steps-sending-the-delivery.md)
-->

## Avancerade parametrar {#advanced-parameters}

Knappen **[!UICONTROL Properties]** ger åtkomst till den avancerade parametern för leverans. Parametrarna som är specifika för SMS-leveranser finns i avsnittet **[!UICONTROL SMS parameters]** på fliken **[!UICONTROL Delivery]**.

Följande alternativ är tillgängliga:

* **Avsändarens adress**: gör att du kan anpassa namnet på leveransavsändaren med hjälp av en alfanumerisk teckensträng som är begränsad till elva tecken. Fältet får inte uteslutande bestå av siffror. Du kan definiera ett villkor som ska visas, t.ex. med olika namn beroende på mottagarens riktnummer:

  ```
  <% if( String(recipient.mobilePhone).indexOf("+1") == 0){ %>NeoShopUS<%} else {%>NeoShopWorld<%}%>
  ```

  >[!IMPORTANT]
  >
  >Läs lagen i ditt land om hur du redigerar avsändarnamn. Du bör också fråga din operatör om de erbjuder den här funktionen.

* **Överföringsläge**: meddelandeöverföring via SMS.
* **Prioritet**: prioritetsnivå som tilldelats ett meddelande. **[!UICONTROL Normal]**-prioritet är vald som standard. Fråga tjänsteleverantören om kostnaden för SMS som skickas med prioritet **[!UICONTROL High]**.
* **Typ av program**: välj det program som du vill tilldela SMS-leveransen. Alternativet **[!UICONTROL Direct Marketing]** är markerat som standard och är det vanligaste alternativet som används.

**Parametrar som är specifika för NetSize-kopplingen**

![](assets/s_user_mobile_sms_adv_netsize.png)

* **Använd flera SMS för ett enda meddelande**: Det gör att du kan skicka ett meddelande som är längre än 160 tecken via flera SMS-meddelanden.

**Parametrar som är specifika för en SMPP-anslutning**

![](assets/s_user_mobile_sms_adv_smpp.png)

* **Maximalt antal SMS per meddelande**: Med det här alternativet kan du ange hur många SMS som ska användas för att skicka ett meddelande. Om värdet är 0 kan du skicka meddelandet med ett SMS. Om antalet SMS är inställt på 1 eller 2 och meddelandet överskrider tröskelvärdet skickas det inte.

<!--
## Monitor and track SMS {#monitoring-and-tracking-sms-deliveries}

After sending messages, you can monitor and track your deliveries. For more on this, refer to these sections:

* [Monitor a delivery](about-delivery-monitoring.md)
* [Understand delivery failures](understanding-delivery-failures.md)
* [About message tracking](about-message-tracking.md)
-->

## Bearbeta inkommande meddelanden {#processing-inbound-messages}

Modulen **nlserver sms** frågar SMS-routern med regelbundna intervall. Detta gör att Adobe Campaign kan följa upp leveransförloppet och hantera statusrapporter och mottagarnas begäran om att ta bort prenumerationen.

* **Statusrapporter**: visa leveransloggar för att kontrollera status för dina meddelanden.

  >[!NOTE]
  >
  >Varje SMS som skickas är länkat till ett externt konto och dess primärnyckel. Så här:
  >
  > * Statusrapporter från ett borttaget externt SMS-konto bearbetas inte korrekt.
  > * Ett SMS-konto kan bara länkas till ett enda externt konto för att säkerställa att statusrapporter tilldelas rätt konto

* **Unsubscription**: Mottagare som inte längre vill ta emot SMS-leveranser kan returnera ett meddelande som innehåller ordet STOP. Om din leverantör tillåter det enligt villkoren i kontraktet kan du hämta meddelanden via arbetsflödesaktiviteten **Inkommande SMS** och sedan skapa en fråga som aktiverar alternativet **Kontakta inte längre den här mottagaren** för de berörda mottagarna.

  Se guiden [Arbetsflöden](../../workflow/using/architecture.md).

## InSMS-schema {#insms-schema}

InSMS-schemat innehåller information som är relevant för inkommande SMS. En beskrivning av dessa fält är tillgänglig via attributet desc.

* **message**: SMS-innehållet togs emot.
* **ursprung**: mobilnummer i meddelandets ursprung.
* **providerId**: identifieraren för meddelandet som returnerades av SMSC (meddelandecenter).
* **skapad**: datum för inkommande meddelande infogades i Adobe Campaign.
* **extAccount**: Adobe Campaign externt konto.

  >[!IMPORTANT]
  >
  >Följande fält är specifika för NetSize.
  >
  >Om operatorn som används inte är NetSize, betraktas dessa fält som tomma.

* **alias**: alias för inkommande meddelande.
* **separator**: avgränsare mellan aliaset och meddelandetexten.
* **messageDate**: meddelandedatum anges av operatorn.
* **receiveDate**: datummeddelande från operator togs emot av SMSC (meddelandecenter).
* **deliveryDate**: datummeddelande skickat av SMSC (meddelandecenter).
* **largeAccount**: Kundkontokod länkad till inkommande SMS.
* **countryCode**: operatörens landskod.
* **operatorCode**: operatörens nätverkskod.
* **linkedSmsId**: Adobe Campaign-identifierare (broadlogId) länkad till utgående SMS, där detta SMS är svaret.

## Hantera automatiska svar (amerikansk förordning) {#managing-automatic-replies--american-regulation-}

När prenumeranterna svarar på ett SMS-meddelande som skickats till dem via Adobe Campaign och använder ett nyckelord som STOP, HELP eller YES, är det nödvändigt att konfigurera meddelanden som returneras automatiskt på den amerikanska marknaden.

Om mottagarna skickar nyckelordet STOP får de automatiskt ett bekräftelsemeddelande om att de har avbeställt prenumerationen.

Avsändarnamnet för den här meddelandetypen är en kort kod som vanligtvis används för att skicka leveranser.

>[!IMPORTANT]
>
>Följande detaljerade procedur gäller bara för SMPP-anslutningar, utom för den utökade generiska SMPP-anslutningen. Mer information finns i avsnittet [Skapa ett externt SMPP-konto](sms-set-up.md#creating-an-smpp-external-account).
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

   I varje **`<reply>`**-tagg anger du attributet **keyword** med ett nyckelord och attributet **text** med det meddelande som du vill skicka för det här nyckelordet.

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
>Den här typen av automatiska meddelanden sparar ingen historik. Därför visas de inte på kontrollpanelen för leveranser. [Läs mer](delivery-dashboard.md).
>
>Dessa meddelanden tas inte med i de kommersiella tryckreglerna. [Läs mer](../../campaign-opt/using/pressure-rules.md).
