---
product: campaign
title: Skicka, övervaka och spåra SMS
description: Lär dig hur du skickar, övervakar och spårar SMS i Campaign
badge-v7: label="v7" type="Informative" tooltip="Gäller Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: SMS
role: User
exl-id: 442672ee-5037-49b7-a06f-3a99920ce2b6
source-git-commit: d2f5f2a662c022e258fb3cc56c8502c4f4cb2849
workflow-type: tm+mt
source-wordcount: '970'
ht-degree: 3%

---

# Skicka, övervaka och spåra SMS-leveranser{#sms-properties}

## Skicka SMS-meddelanden {#sending-sms-messages}

Om du vill godkänna meddelandet och skicka det till mottagarna av det som skapas klickar du på **[!UICONTROL Send]**.

Den detaljerade processen för att validera och skicka en leverans presenteras i avsnitten nedan:

* [Validera leveransen](steps-validating-the-delivery.md)
* [Skicka leveransen](steps-sending-the-delivery.md)

## Avancerade parametrar {#advanced-parameters}

The **[!UICONTROL Properties]** ger åtkomst till den avancerade parametern för leverans. Parametrarna som är specifika för SMS-leveranser finns i **[!UICONTROL SMS parameters]** i **[!UICONTROL Delivery]** -fliken.

Följande alternativ är tillgängliga:

* **Avsändarens adress**: gör att du kan anpassa namnet på avsändaren med en alfanumerisk teckensträng som är begränsad till elva tecken. Fältet får inte uteslutande bestå av siffror. Du kan definiera ett villkor som ska visas, t.ex. med olika namn beroende på mottagarens riktnummer:

  ```
  <% if( String(recipient.mobilePhone).indexOf("+1") == 0){ %>NeoShopUS<%} else {%>NeoShopWorld<%}%>
  ```

  >[!IMPORTANT]
  >
  >Läs lagen i ditt land om hur du redigerar avsändarnamn. Du bör också fråga din operatör om de erbjuder den här funktionen.

* **Överföringsläge**: meddelandeöverföring via SMS.
* **Prioritet**: prioritetsnivå för ett meddelande. **[!UICONTROL Normal]** som standard är prioriteten vald. Fråga tjänsteleverantören om kostnaden för SMS som skickas med **[!UICONTROL High]** prioritet.
* **Typ av tillämpning**: välj det program som du vill tilldela SMS-leveransen. The **[!UICONTROL Direct Marketing]** är markerat som standard och är det vanligaste alternativet.

**Parametrar som är specifika för NetSize-kopplingen**

![](assets/s_user_mobile_sms_adv_netsize.png)

* **Använd flera SMS för ett enda meddelande**: du kan då skicka ett meddelande med mer än 160 tecken via flera SMS-meddelanden.

**Parametrar som är specifika för en SMPP-anslutning**

![](assets/s_user_mobile_sms_adv_smpp.png)

* **Högsta antal SMS per meddelande**: Med det här alternativet kan du ange hur många SMS som ska användas för att skicka ett meddelande. Om värdet är 0 kan du skicka meddelandet med ett SMS. Om antalet SMS är inställt på 1 eller 2 och meddelandet överskrider tröskelvärdet skickas det inte.

## Övervaka och spåra SMS {#monitoring-and-tracking-sms-deliveries}

När du har skickat meddelanden kan du övervaka och spåra dina leveranser. Mer information om detta hittar du i dessa avsnitt.

* [Övervaka en leverans](about-delivery-monitoring.md)
* [Förstå leveransfel](understanding-delivery-failures.md)
* [Om att spåra meddelanden](about-message-tracking.md)

## Bearbeta inkommande meddelanden {#processing-inbound-messages}

The **nlserver sms** Modulen frågar SMS-routern med regelbundna intervall. Detta gör att Adobe Campaign kan följa upp leveransförloppet och hantera statusrapporter och mottagarnas begäran om att ta bort prenumerationen.

* **Statusrapporter**: visa leveransloggar för att kontrollera status för dina meddelanden.

  >[!NOTE]
  >
  >Varje SMS som skickas är länkat till ett externt konto och dess primärnyckel. Så här:
  >
  > * Statusrapporter från ett borttaget externt SMS-konto bearbetas inte korrekt.
  > * Ett SMS-konto kan bara länkas till ett enda externt konto för att säkerställa att statusrapporter tilldelas rätt konto

* **Avsluta prenumeration**: Mottagare som inte längre vill ta emot SMS-leveranser kan returnera ett meddelande som innehåller ordet STOP. Om din leverantör tillåter det enligt avtalsvillkoren kan du hämta meddelanden via **Inkommande SMS** arbetsflödesaktivitet och skapa sedan en fråga för att aktivera **Kontakta inte längre den här mottagaren** möjlighet för de berörda mottagarna.

  Se [Arbetsflöden](../../workflow/using/architecture.md) guide.

## InSMS-schema {#insms-schema}

InSMS-schemat innehåller information som är relevant för inkommande SMS. En beskrivning av dessa fält är tillgänglig via attributet desc.

* **message**: innehållet i det SMS som togs emot.
* **ursprung**: mobilnummer i meddelandets ursprung.
* **providerId**: identifierare för det meddelande som returneras av SMSC (meddelandecenter).
* **skapad**: datum för inkommande meddelande infogades i Adobe Campaign.
* **extAccount**: Adobe Campaign externt konto.

  >[!IMPORTANT]
  >
  >Följande fält är specifika för NetSize.
  >
  >Om operatorn som används inte är NetSize, betraktas dessa fält som tomma.

* **alias**: alias för inkommande meddelande.
* **avgränsare**: avgränsare mellan alias och meddelandets brödtext.
* **messageDate**: meddelandedatum angivet av operator.
* **receiveDate**: datummeddelande från operatorn togs emot av SMSC (meddelandecenter).
* **deliveryDate**: datummeddelande skickat av SMSC (meddelandecenter).
* **largeAccount**: kundkontokod länkad till inkommande SMS.
* **countryCode**: operatorns landskod.
* **operatorCode**: operatörens nätverkskod.
* **linkedSmsId**: Adobe Campaign-identifierare (broadlogId) länkad till utgående SMS, där detta SMS är svaret.

## Hantera automatiska svar (amerikansk förordning) {#managing-automatic-replies--american-regulation-}

När prenumeranterna svarar på ett SMS-meddelande som skickats till dem via Adobe Campaign och använder ett nyckelord som STOP, HELP eller YES, är det nödvändigt att konfigurera meddelanden som returneras automatiskt på den amerikanska marknaden.

Om mottagarna skickar nyckelordet STOP får de automatiskt ett bekräftelsemeddelande om att de har avbeställt prenumerationen.

Avsändarnamnet för den här meddelandetypen är en kort kod som vanligtvis används för att skicka leveranser.

>[!IMPORTANT]
>
>Följande detaljerade procedur gäller bara för SMPP-anslutningar, utom för den utökade generiska SMPP-anslutningen. Mer information finns i [Skapa ett externt SMPP-konto](sms-set-up.md#creating-an-smpp-external-account) -avsnitt.
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

1. För **name** attributet för **`<shortcode>`** anger du den korta kod som ska visas i stället för meddelandets avsändarnamn.

   I varje **`<reply>`** -taggen, ange **nyckelord** attribut med ett nyckelord och **text** attribut med meddelandet som du vill skicka för det här nyckelordet.

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

1. Kopiera filen till **conf** i Adobe Campaign, på samma plats som webbservern.

>[!IMPORTANT]
>
>Den här typen av automatiska meddelanden sparar ingen historik. Därför visas de inte på kontrollpanelen för leveranser. [Läs mer](delivery-dashboard.md).
>
>Dessa meddelanden tas inte med i de kommersiella tryckreglerna. [Läs mer](../../campaign-opt/using/pressure-rules.md).
