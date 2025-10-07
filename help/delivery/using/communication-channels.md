---
product: campaign
title: Kommunikationskanaler
description: Skapa leveranser för att skicka personanpassade meddelanden i olika kanaler
feature: Cross Channel Orchestration, Email, SMS, In App, Direct Mail, Push
role: User
exl-id: 92b5e013-b619-4f0b-b0b1-1fc2e653ceac
source-git-commit: 89e350c727fb9379d28916f79d9749f22fd4974f
workflow-type: tm+mt
source-wordcount: '943'
ht-degree: 2%

---

# Kommunikationskanaler{#communication-channels}

Med Adobe Campaign kan ni skicka flerkanalskampanjer, inklusive e-post, SMS, push-meddelanden och direktreklam, och mäta hur effektiva de är med hjälp av olika dedikerade rapporter. Dessa meddelanden är utformade och skickas genom leveranser och kan anpassas för varje mottagare.

De viktigaste funktionerna är målinriktning, definition och personalisering av meddelanden, genomförande av kommunikation och tillhörande verksamhetsrapporter.

Som en del av kampanjsatsningen v8 har Campaign Classic-dokumentationen omstrukturerats. Gemensamma funktioner är nu bara tillgängliga i Campaign v8-dokumentationsuppsättningen.



>[!BEGINTABS]

>[!TAB Dokumentation för kommunikationskanaler]

Mer information om kommunikationskanaler finns i [dokumentationen för Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/gs-message.html){target=_blank}.


[![bild](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/gs-message.html){target=_blank}


>[!TAB Leverera innehåll och målgrupp]

Lär dig de viktigaste stegen som rör leveransskapande, innehåll och målgrupp i dokumentationen för Campaign v8:

* [Skapa leveransen](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html#create-the-delivery){target="_blank"}: Lär dig hur du skapar en engångsleverans med ett enda foto.
* [Definiera innehållet](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html#content-of-the-delivery){target="_blank"}: Konfigurera leveransinnehållet för varje kanal.
* [Ange målgruppen](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html#target-population){target="_blank"}: Definiera flera typer av mål: huvudmålgrupp, korrekturmål, dirigerade adresser och kontrollgrupper.
* [Arbeta med leveransmallar](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-templates.html){target="_blank"}: Lär dig hur du definierar mallar för att underlätta skapandet av leveransen.





>[!TAB Leveransvalidering och sändning]

På dessa sidor finns information om leveransvalidering, sändning och metodtips i dokumentationen för Campaign v8:

* [Verifiera leveransen](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html#validate-the-delivery){target="_blank"}: Lär dig hur du validerar leveransen innan du skickar den till huvudmålet.
* [Skicka leveransen](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html#configuring-and-sending-the-delivery){target="_blank"}: Konfigurera leveransinställningarna och definiera hur meddelanden ska skickas.
* [Bästa praxis för leverans](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/delivery-best-practices.html){target="_blank"}: Ta del av de bästa metoderna för leveransfunktioner i Campaign.

>[!ENDTABS]

Följande inställningar är specifika för Campaign Classic. Andra leveransinställningar finns i [dokumentationen för Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/gs-message.html){target="_blank"}.

+++ **Leveransanalys**

**Förbättra prestanda för leveransanalys**

Om du vill påskynda leveransförberedelsen kan du kontrollera alternativet **[!UICONTROL Prepare the delivery parts in the database]** innan du startar analysen.

När det här alternativet är aktiverat utförs leveransförberedelsen direkt i databasen, vilket avsevärt kan snabba upp analysen.

För närvarande är det här alternativet endast tillgängligt när följande villkor är uppfyllda:

* Leveransen måste vara ett e-postmeddelande. De andra kanalerna stöds inte för tillfället.
* Du får inte använda medelstor eller extern routning, endast bulkleveransroutningstyp. Du kan kontrollera routningen som används på fliken **[!UICONTROL General]** i **[!UICONTROL Delivery properties]**.
* Du kan inte ange en målgrupp som kommer från en extern fil som mål. Klicka på länken **[!UICONTROL To]** i **[!UICONTROL Email parameters]** för en enskild leverans och kontrollera att alternativet **[!UICONTROL Defined in the database]** är markerat. Kontrollera att mottagarna är **[!UICONTROL Specified by the inbound event(s)]** på fliken **[!UICONTROL Delivery]** för en leverans som används i ett arbetsflöde.
* Du måste använda en PostgreSQL-databas.

**Konfigurera analysprioriteten**

När leveransen är en del av en kampanj finns det ytterligare ett alternativ på fliken **[!UICONTROL Advanced]**. På så sätt kan du ordna bearbetningsordningen för leveranser i samma kampanj.

Innan leveransen skickas analyseras varje leverans. Analysens längd beror på leveransens extraheringsfil. Ju större filstorlek, desto längre tid tar analysen och följande leveranser väntar.

Med alternativen för **[!UICONTROL Message preparation by the scheduler]** kan du prioritera leveransanalysen i ett kampanjarbetsflöde.

![](assets/delivery_analysis_priority.png)

Om en leverans är för stor är det bättre att tilldela den en låg prioritet för att undvika att analysen av andra arbetsflödesleveranser går långsammare.

>[!NOTE]
>
>Om du vill vara säker på att de större leveransanalyserna inte gör arbetsflödena långsammare kan du schemalägga deras körningar genom att trycka på **[!UICONTROL Schedule execution for a time of low activity]**.

+++

+++ **Leveransmeddelande**

**Konfigurera återförsök**

Tillfälligt olevererade meddelanden på grund av ett fel av typen **Mjuk** eller **Ignorerad** kan återförsökas automatiskt. Leveransfeltyperna och anledningarna visas i det här [avsnittet](understanding-delivery-failures.md#delivery-failure-types-and-reasons).

>[!IMPORTANT]
>
>Om du har uppgraderat till [Förbättrat MTA](sending-with-enhanced-mta.md) för värdbaserade eller hybridinstallerade installationer används inte längre inställningarna för nya försök i leveransen av Campaign. Mjuka avhoppsförsök och hur lång tid det tar mellan dem bestäms av den förbättrade MTA-metoden baserat på typ och allvarlighetsgrad för de avhoppssvar som kommer tillbaka från meddelandets e-postdomän.

För lokala installationer och värdbaserade/hybridinstallationer som använder det äldre kampanjavtalet MTA, visar det centrala avsnittet på fliken **[!UICONTROL Delivery]** för leveransparametrar hur många försök som ska utföras dagen efter leveransen och den minsta fördröjningen mellan återförsök.

![](assets/s_ncs_user_wizard_retry_param.png)

Som standard schemaläggs fem återförsök till den första dagen i leveransen med ett minsta intervall på en timme som sprids ut över dygnets 24 timmar. Ett nytt försök per dag är programmerat efter detta och fram till leveransdatumet, som definieras på fliken **[!UICONTROL Validity]**. Se [Definiera giltighetsperioden](#defining-validity-period).

**Definiera giltighetsperioden**

När leveransen har startats kan meddelandena (och eventuella försök) skickas till leveransdatumet. Detta anges i leveransegenskaperna via fliken **[!UICONTROL Validity]**.

![](assets/s_ncs_user_email_del_valid_period.png)

* I fältet **[!UICONTROL Delivery duration]** kan du ange gränsen för globala leveransförsök. Detta innebär att Adobe Campaign skickar meddelanden som börjar på startdatumet och sedan, för meddelanden som bara returnerar ett fel, kommer regelbundna, konfigurerbara försök att utföras tills giltighetsgränsen nås.

  Du kan också välja att ange datum. Välj **[!UICONTROL Explicitly set validity dates]** om du vill göra det. I det här fallet kan du även ange datum för leveransdatum och giltighetsgräns. Den aktuella tiden används som standard, men du kan ändra den direkt i indatafältet.

  >[!IMPORTANT]
  >
  >Om du har uppgraderat till [Förbättrat MTA](sending-with-enhanced-mta.md) för värdbaserade eller hybridbaserade installationer, kommer inställningen **[!UICONTROL Delivery duration]** i e-postleveranserna för Campaign endast att användas om den är inställd på **.5 dagar eller mindre**. Om du anger ett värde som är högre än 3,5 dagar kommer det inte att beaktas.

* **Giltighetsgräns för resurser**: Fältet **[!UICONTROL Validity limit]** används för överförda resurser, främst för spegelsidan och bilder. Resurserna på den här sidan är giltiga under en begränsad tid (för att spara diskutrymme).

  Värdena i det här fältet kan uttryckas i de enheter som visas i [det här avsnittet](../../platform/using/adobe-campaign-workspace.md#default-units).

+++

<!--

   Learn how to create a one-shot single delivery. You can create other types of deliveries to build your use cases. 

For more information about the different types of deliveries and how to create them, refer to the [Campaign v8 documentation](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html){target="_blank"}. 

>[!NOTE]
>
>Adobe Campaign offers a set of tools to monitor your deliverability and optimize email sending. Learn more in [this section](about-deliverability.md).

Delivery sending can be automated by preparing a delivery and/or sending it in the process of a workflow. For more on delivery-type activities in workflows, refer to [this section](../../workflow/using/about-action-activities.md).

Adobe Campaign offers the following delivery channels:

1. **Email channel**: email deliveries let you send personalized emails to the target population. Refer to [About email channel](about-email-channel.md).
1. **Direct mail channel**: direct mail deliveries let you generate an extraction file which contains data on the target population. Refer to [About direct mail channel](about-direct-mail-channel.md).
1. **Mobile channel**: deliveries on mobile channels let you send personalized SMS or LINE messages to the target population. Refer to [SMS channel](sms-channel.md).
1. **Mobile application channel**: mobile app deliveries let you send notifications to iOS and Android systems. Refer to the [Mobile app channel](about-mobile-app-channel.md) chapter.

   Other channels are described on [this section](#other-channels).

   >[!NOTE]
   >
   >The number of available channels depends on your contract. Please check your license agreement.

Deliveries can be carried out **online** (via email, one of the mobile channels and push notifications), and **offline** (direct mail channel).

Depending on the channel, delivery modes can be:

* Direct mass delivery via Adobe Campaign (default mode for email channel).
* External delivery via a specialist operator who is given the output file generated by the delivery assistant (default mode for direct mail channel).

External accounts are configured via the **[!UICONTROL Administration > Platform > External accounts]** node. This configuration should be performed by expert users only.

## Email deliveries {#email-deliveries}

The [Email channel](about-email-channel.md) is one of the core channels in Adobe Campaign, allowing you to schedule and send personalized emails to specific targets.

You can send different types of emails:

* Single-send emails: emails that you can send once to a defined target. They are usually used to promote a specific content that would be prepared and sent only once (newsletter, promotional email, etc.).
* Recurring emails: in a campaign, send the same email regularly and aggregate each send and its reports on a periodic basis. The same email is sent, but usually to a different target, based on the eligible target for the day of the send. A common example is a birthday email. For more on this, refer to [Recurring deliveries](../../workflow/using/recurring-delivery.md).
* Transactional emails: unitary emails that are triggered based on your customers' behavior. Refer to [Transactional messaging](../../message-center/using/about-transactional-messaging.md).

To learn about delivery usage and recommendations, consult Campaign [Delivery best practices](delivery-best-practices.md).

For more on the different types of deliveries, refer to [this section](#types-of-deliveries).

## Mobile deliveries {#mobile-deliveries}

Adobe Campaign allows you to deliver [SMS](sms-channel.md) and [LINE](line-channel.md) messages on mobiles.

For SMS messages, you can create, modify, and personalize messages in text format only. You can also preview your SMS messages before they are sent.

For LINE messages, you can send text or images and links.

To deliver SMS or LINE messages to a mobile phone you need:

* An external account configured on the **[!UICONTROL Mobile (SMS)]** channel or on the **[!UICONTROL LINE]** channel. 
* An SMS or LINE delivery template that is correctly linked to this external account.

## Push notifications {#push-notifications}

Adobe Campaign allows you to send personalized and segmented [push notifications](about-mobile-app-channel.md) on iOS and Android mobile devices, through dedicated apps. Once configuration and integration steps have been performed, iOS and Android deliveries can be created and sent. You can also design rich notifications with images or videos.

## Direct mail {#direct-mail}

[Direct mail](about-direct-mail-channel.md) is an offline channel that allows you to personalize and generate the file required by direct mail providers. It gives you the possibility to mix online and offline channels in your customer journeys.

Online channels allow you to create your messages (email, SMS, mobile app delivery, etc.) and send them to your audience directly from Adobe Campaign. With offline channels, it is different. When you prepare a direct mail delivery, Adobe Campaign generates a file including all the targeted profiles and the chosen contact information (postal address for example). You will then be able to send this file to your direct mail provider who will take care of the actual sending.

## Other channels {#other-channels}

Adobe Campaign offers Telephone delivery template, which is used to create external deliveries. Using this channel implies you set up dedicated methodologies to process output files. Configuration steps are the same as for [Direct mail channel](about-direct-mail-channel.md).

>[!NOTE]
>
>The Telephone channel is not available out-of-the-box. Its implementation requires Adobe Consulting or an Adobe Partner to be engaged. Please reach out to your Adobe representative for more information.

In addition, 'Other' type deliveries use a specific technical template which does not execute a process: this lets them manage marketing actions executed outside of the Adobe Campaign platform.

This channel has no specific mechanism. It is a generic channel that has its own external account routing option, delivery template type and campaign workflow activity, just like any other communication channel available in Adobe Campaign.

This channel is designed for descriptive purposes only, for example to define deliveries for which you want to keep a trace of the target of a campaign performed in a tool other than Adobe Campaign.

## Types of deliveries{#types-of-deliveries}

There are three types of delivery objects in Campaign:

### Single delivery {#single-delivery}

A **delivery** is a standalone delivery object that is executed once. It can be duplicated, prepared again, but as long as it is in its final state (canceled, stopped, finished), it cannot be reused.

Deliveries can be created either from the list of deliveries, or within a workflow via a [Delivery](../../workflow/using/delivery.md) activity.

Workflows also provide specific delivery activities according to the type of channel you want to use. For more on these activities, refer to [this section](../../workflow/using/cross-channel-deliveries.md).

### Recurring delivery {#recurring-delivery}

A **recurring delivery** lets you create a new delivery each time the activity is executed. This avoids you having to create a new delivery for recurring tasks.

As an example, if you run this type of activity once a month, you will end up with 12 deliveries after a year.

Recurring deliveries are created within workflows via the [Recurring delivery activity](../../workflow/using/recurring-delivery.md). An example of this activity being used is presented in this section: [Creating a recurring delivery in a targeting workflow](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow).

### Continuous delivery {#continuous-delivery}

A **continuous delivery** lets you add new recipients to an existing delivery, which avoids having to create a new delivery each time it is executed.

If an information in the delivery changes (content, name, etc.), a new delivery object is created at the delivery execution. If no information was changed, the same delivery object is reused and the delivery and tracking logs are added in the same object.

As an example, if you run this type of activity once a month, you will end up with a single delivery after a year (provided you did not make any change to the delivery).

Continuous deliveries are created within workflows via the [Continuous delivery activity](../../workflow/using/continuous-delivery.md).-->
