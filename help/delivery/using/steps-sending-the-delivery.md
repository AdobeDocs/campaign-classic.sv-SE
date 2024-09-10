---
product: campaign
title: Konfigurera och skicka leveransen
description: Lär dig konfigurera och skicka leveransen
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Channel Configuration
role: User
exl-id: 0411686e-4f13-401e-9333-e14b05ebe9cd
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '1526'
ht-degree: 3%

---

# Konfigurera och skicka leveransen {#configuring-and-sending-the-delivery}

## Behörigheter{#delivery-permissions}

Endast leveransägaren kan påbörja en leverans. För att andra operatorer (eller operatorgrupper) ska kunna starta en leverans lägger du till dem som granskare i fältet **[!UICONTROL Delivery start:]**. [Läs mer](../../campaign/using/marketing-campaign-approval.md#selecting-reviewers).

## Ytterligare leveransparametrar {#delivery-additiona-parameters}

Innan du skickar leveransen kan du definiera sändningsparametrarna i leveransegenskaperna via fliken **[!UICONTROL Delivery]**.

![](assets/s_ncs_user_wizard_delivery.png)

* **[!UICONTROL Delivery priority]**: Använd det här alternativet om du vill ändra avsändarordningen för dina leveranser genom att ange deras prioritetsnivå: normal, hög eller låg.

* **[!UICONTROL Message batch quantity]**: använd det här alternativet för att definiera antalet meddelanden som grupperas i samma XML-leveranspaket. Om parametern är inställd på 0 grupperas meddelandena automatiskt. Paketstorleken definieras av beräkningen `<delivery size>/1024`, med minst 8 och högst 256 meddelanden per paket.

  >[!IMPORTANT]
  >
  >När leveransen skapas genom duplicering av en befintlig, återställs den här parametern.

* **[!UICONTROL Send using multiple waves]**: använd det här alternativet om du vill skicka meddelanden gruppvis i stället för till hela målgruppen samtidigt. [Läs mer](#sending-using-multiple-waves).

* **[!UICONTROL Test SMTP delivery]**: använd det här alternativet om du vill testa att skicka via SMTP. Leveransen behandlas upp till anslutning till SMTP-servern men skickas inte: För varje mottagare av leveransen ansluter Campaign till SMTP-providerservern, kör SMTP RCPT TO-kommandot och stänger anslutningen före SMTP DATA-kommandot.

  >[!NOTE]
  >
  >* Det här alternativet får inte ställas in i mitten av källkoden.
  >
  >* Läs mer om SMTP-serverkonfigurationen i [det här avsnittet](../../installation/using/configure-delivery-settings.md).

* **[!UICONTROL Email BCC]**: Använd det här alternativet om du vill lagra e-post på ett externt system via BCC genom att lägga till en e-postadress för hemlig kopia till meddelandemålet. [Läs mer](sending-messages.md#archiving-emails).

## Bekräfta leverans {#confirming-delivery}

Kör leveransanalysen när leveransen är konfigurerad och klar att skickas.

Om du vill göra det klickar du på **[!UICONTROL Send]**, väljer önskad åtgärd och klickar på **[!UICONTROL Analyze]**. [Läs mer](steps-validating-the-delivery.md#analyzing-the-delivery).

![](assets/s_ncs_user_email_del_send.png)

När du är klar klickar du på **[!UICONTROL Confirm delivery]** för att starta meddelandeleveransen.

Du kan sedan stänga leveransassistenten och spåra leveransen från fliken **[!UICONTROL Delivery]**, som du kommer åt via leveransinformationen eller genom leveranslistan.

När du har skickat meddelanden kan du övervaka och spåra dina leveranser. Mer information om detta hittar du i dessa avsnitt.

* [Övervaka en leverans](about-delivery-monitoring.md)
* [Förstå leveransfel](understanding-delivery-failures.md)
* [Om att spåra meddelanden](about-message-tracking.md)

## Schemalägg leverans som skickas {#scheduling-the-delivery-sending}

Du kan skjuta upp sändningen genom att schemalägga leveransen.

1. Klicka på knappen **[!UICONTROL Send]** och välj alternativet **[!UICONTROL Postpone delivery]**.

1. Ange ett startdatum i fältet **[!UICONTROL Contact date]**.

![](assets/dlv_email_del_plan.png)

1. Du kan sedan starta leveransanalysen och bekräfta leveransen. Leveranssändningen kommer dock inte att börja förrän det datum som anges i fältet **[!UICONTROL Contact date]**.

>[!IMPORTANT]
>
>När du har startat analysen är det kontaktdatum som du har definierat fixerat. Om du ändrar det här datumet måste du starta om analysen så att dina ändringar beaktas.

![](assets/s_ncs_user_email_del_start_delayed.png)

I leveranslistan visas leveransen med statusen **[!UICONTROL Pending]**.

![](assets/s_ncs_user_email_del_waiting.png)

Schemaläggningen kan också konfigureras uppströms via leveransknappen **[!UICONTROL Scheduling]**.

![](assets/s_ncs_user_email_del_save_in_calendar_ico.png)

Du kan skjuta upp leveransen till ett senare datum eller spara leveransen i den preliminära kalendern.

* Med alternativet **[!UICONTROL Schedule delivery (no automatic execution)]** kan du schemalägga en preliminär analys av leveransen.

  När den här konfigurationen sparas ändras leveransstatusen till **[!UICONTROL Targeting pending]**. Analysen startas på det angivna datumet.

* Med alternativet **[!UICONTROL Schedule delivery (automatic execution on planned date)]** kan du ange leveransdatum.

  Klicka på **[!UICONTROL Send]** och välj **[!UICONTROL Postpone delivery]**, starta analysen och bekräfta leveransen. När analysen är klar är leveransmålet klart och meddelanden skickas automatiskt det angivna datumet.

Datum och tider anges i tidszonen för den aktuella operatorn. Med den nedrullningsbara listan **[!UICONTROL Time zone]** som finns under kontaktdatumsinmatningsfältet kan du automatiskt konvertera det angivna datumet och den angivna tiden till den valda tidszonen.

Om du till exempel schemalägger att en leverans ska köras automatiskt vid klockan 8 London, konverteras tiden automatiskt till den valda tidszonen:

![](assets/s_ncs_user_email_del_plan_calendar_timezone.png)

## Skicka med flera vågor {#sending-using-multiple-waves}

För att balansera lasten kan du dela upp leveranser i flera satser. Konfigurera antalet batchar och deras proportioner i förhållande till hela leveransen.

>[!NOTE]
>
>Du kan bara definiera storleken och fördröjningen mellan två på varandra följande påfyllnader. Det går inte att konfigurera urvalskriterierna för mottagare för varje påfyllnad.

1. Öppna fönstret för leveransegenskaper och klicka på fliken **[!UICONTROL Delivery]**.
1. Välj alternativet **[!UICONTROL Send using multiple waves]** och klicka på länken **[!UICONTROL Define waves...]**.

   ![](assets/s_ncs_user_wizard_waves.png)

1. Så här konfigurerar du påfyllnader:

   * Definiera storleken för varje våg. Om du till exempel anger **[!UICONTROL 30%]** i motsvarande fält representerar varje påfyllnad 30 % av meddelandena som ingår i leveransen, förutom det sista, som representerar 10 % av meddelandena.

     I fältet **[!UICONTROL Period]** anger du fördröjningen mellan början av två på varandra följande påfyllnader. Om du till exempel anger **[!UICONTROL 2d]** startar den första vågen omedelbart, den andra om två dagar, den tredje vågen om fyra dagar och så vidare.

     ![](assets/s_ncs_user_wizard_waves_create_size.png)

   * Definiera en kalender för att skicka varje påfyllnad.

     I kolumnen **[!UICONTROL Start]** anger du fördröjningen mellan början av två på varandra följande påfyllnader. Ange ett fast tal eller en procentsats i kolumnen **[!UICONTROL Size]**.

     I exemplet nedan representerar den första vågen 25 % av det totala antalet meddelanden som ingår i leveransen och börjar omedelbart. Nästa två vågor slutför leveransen och är inställda på att börja med 6 timmars intervall.

     ![](assets/s_ncs_user_wizard_waves_create.png)

   En specifik typologiregel, **[!UICONTROL Wave scheduling check]**, säkerställer att den sista påfyllnaden planeras före leveransens giltighetsgräns. Kampanjtypologier och deras regler, som har konfigurerats på fliken **[!UICONTROL Typology]** i leveransegenskaperna, presenteras i [valideringsprocessen med typologier](steps-validating-the-delivery.md#validation-process-with-typologies).

   >[!IMPORTANT]
   >
   >Kontrollera att de sista påfyllnaderna inte överskrider leveransdeadline, som definieras på fliken **[!UICONTROL Validity]**. Annars kanske vissa meddelanden inte skickas.
   >
   >Du måste också ge tillräckligt med tid för att försöka igen när du konfigurerar de sista vågorna. Se [det här avsnittet](steps-sending-the-delivery.md#configuring-retries).

1. Gå till leveransloggarna för att övervaka dina utskick. Läs [den här sidan](delivery-dashboard.md#delivery-logs-and-history).

   Du kan se leveranser som redan har skickats i de bearbetade påfyllnaderna (**[!UICONTROL Sent]** status) och leveranser som ska skickas i återstående påfyllnader (**[!UICONTROL Pending]** status).

De två exemplen nedan är de vanligaste användningsområdena när du använder flera vågor.

* **Under avstämningsprocessen**

  När e-postmeddelanden skickas via en ny plattform, är Internetleverantörer (ISP) misstänkta för IP-adresser som inte känns igen. Om stora mängder e-postmeddelanden plötsligt skickas markerar internetleverantörerna dem ofta som skräppost.

  För att undvika att markeras som skräppost kan du stegvis öka volymen som skickas med vågor. Detta bör säkerställa en smidig utveckling av startfasen och göra det möjligt att minska den totala frekvensen av ogiltiga adresser.

  Använd alternativet **[!UICONTROL Schedule waves according to a calendar]** om du vill göra det. Du kan till exempel ställa in den första vågen på 10 %, den andra på 15 % och så vidare.

  ![](assets/s_ncs_user_wizard_waves_ramp-up.png)

* **Kampanjer som berör ett callcenter**

  När ni hanterar en lojalitetskampanj per telefon har organisationen begränsad kapacitet att behandla antalet samtal till kontaktprenumeranter.

  Med hjälp av vågor kan du begränsa antalet meddelanden till 20 per dag, till exempel med tanke på den dagliga bearbetningskapaciteten hos ett callcenter.

  Välj alternativet **[!UICONTROL Schedule multiple waves of the same size]** om du vill göra det. Ange **[!UICONTROL 20]** som vågstorlek och **[!UICONTROL 1d]** i fältet **[!UICONTROL Period]**.

  ![](assets/s_ncs_user_wizard_waves_call_center.png)

## Konfigurera återförsök {#configuring-retries}

Tillfälligt olevererade meddelanden på grund av ett fel av typen **Mjuk** eller **Ignorerad** kan återförsökas automatiskt. Leveransfeltyperna och anledningarna visas i det här [avsnittet](understanding-delivery-failures.md#delivery-failure-types-and-reasons).

>[!IMPORTANT]
>
>Om du har uppgraderat till [Förbättrat MTA](sending-with-enhanced-mta.md) för värdbaserade eller hybridinstallerade installationer används inte längre inställningarna för nya försök i leveransen av Campaign. Mjuka avhoppsförsök och hur lång tid det tar mellan dem bestäms av den förbättrade MTA-metoden baserat på typ och allvarlighetsgrad för de avhoppssvar som kommer tillbaka från meddelandets e-postdomän.

För lokala installationer och värdbaserade/hybridinstallationer som använder det äldre kampanjavtalet MTA, visar det centrala avsnittet på fliken **[!UICONTROL Delivery]** för leveransparametrar hur många försök som ska utföras dagen efter leveransen och den minsta fördröjningen mellan återförsök.

![](assets/s_ncs_user_wizard_retry_param.png)

Som standard schemaläggs fem återförsök till den första dagen i leveransen med ett minsta intervall på en timme som sprids ut över dygnets 24 timmar. Ett nytt försök per dag är programmerat efter detta och fram till leveransdatumet, som definieras på fliken **[!UICONTROL Validity]**. Se [Definiera giltighetsperioden](#defining-validity-period).

## Definiera giltighetsperioden {#defining-validity-period}

När leveransen har startats kan meddelandena (och eventuella försök) skickas till leveransdatumet. Detta anges i leveransegenskaperna via fliken **[!UICONTROL Validity]**.

![](assets/s_ncs_user_email_del_valid_period.png)

* I fältet **[!UICONTROL Delivery duration]** kan du ange gränsen för globala leveransförsök. Detta innebär att Adobe Campaign skickar meddelanden som börjar på startdatumet och sedan, för meddelanden som bara returnerar ett fel, kommer regelbundna, konfigurerbara försök att utföras tills giltighetsgränsen nås.

  Du kan också välja att ange datum. Välj **[!UICONTROL Explicitly set validity dates]** om du vill göra det. I det här fallet kan du även ange datum för leveransdatum och giltighetsgräns. Den aktuella tiden används som standard, men du kan ändra den direkt i indatafältet.

  >[!IMPORTANT]
  >
  >Om du har uppgraderat till [Förbättrat MTA](sending-with-enhanced-mta.md) för värdbaserade eller hybridbaserade installationer, kommer inställningen **[!UICONTROL Delivery duration]** i e-postleveranserna för Campaign endast att användas om den är inställd på **.5 dagar eller mindre**. Om du anger ett värde som är högre än 3,5 dagar kommer det inte att beaktas.

* **Giltighetsgräns för resurser**: Fältet **[!UICONTROL Validity limit]** används för överförda resurser, främst för spegelsidan och bilder. Resurserna på den här sidan är giltiga under en begränsad tid (för att spara diskutrymme).

  Värdena i det här fältet kan uttryckas i de enheter som visas i [det här avsnittet](../../platform/using/adobe-campaign-workspace.md#default-units).
