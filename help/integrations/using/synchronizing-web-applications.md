---
product: campaign
title: Synkronisera webbapplikationer
description: Lär dig hur du synkroniserar webbprogram med ACS Connector
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: ACS Connector
hide: true
hidefromtoc: true
exl-id: 975bdc94-5da4-45ae-a3bd-e8674b447098
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '801'
ht-degree: 1%

---

# Synkronisera webbapplikationer{#synchronizing-web-applications}



I det här fallet skickar vi ett meddelande med Campaign Standard som innehåller en länk till ett Campaign v7-webbprogram. När mottagaren klickar på länken i e-postmeddelandet visar webbprogrammet ett formulär som innehåller flera fält som är förinlästa med mottagarens data samt en prenumerationslänk till ett nyhetsbrev. Mottagaren kan uppdatera sina data och prenumerera på tjänsten. Hans profil kommer att uppdateras i Campaign v7 och informationen kommer att återges i Campaign Standard.

Om du har många tjänster och webbprogram i Campaign v7 kan du välja att inte återskapa dem alla i Campaign Standard. Med ACS Connector kan ni använda alla era befintliga webbprogram och tjänster i Campaign v7 och länka dem till en leverans som skickas via Campaign Standard.

## Förhandskrav {#prerequisites}

För att uppnå detta behöver du:

* Mottagare lagrade i Campaign v7-databasen och synkroniserade med Campaign Standard. Se [Synkronisera profiler](../../integrations/using/synchronizing-profiles.md) -avsnitt.
* en tjänst och ett webbprogram som skapats och publicerats i Campaign v7.
* webbprogrammet måste innehålla en **[!UICONTROL Pre-loading]** aktivitet med **[!UICONTROL Adobe Campaign encryption]** identifieringsmetod.

## Skapa webbprogrammet och webbtjänsten {#creating-the-web-application-and-service}

I Campaign v7 kan du skapa webbprogram där mottagarna kan prenumerera på en tjänst. Webbprogrammet och webbtjänsten är utformade och lagrade i Campaign v7 och du kan uppdatera tjänsten via en Campaign Standard. Mer information om webbprogram i Campaign v7 finns i [det här avsnittet](../../web/using/adding-fields-to-a-web-form.md#subscription-checkboxes).

I Campaign v7 har följande objekt skapats:

* en nyhetsbrevstjänst
* ett webbprogram som innehåller **[!UICONTROL Pre-loading]**, a **[!UICONTROL Page]** och **[!UICONTROL Storage]** aktivitet.

1. Gå till **[!UICONTROL Resources > Online > Web applications]** och välja ett befintligt webbprogram.

   ![](assets/acs_connect_lp_2.png)

1. Redigera **[!UICONTROL Preloading]** aktivitet. The **[!UICONTROL Auto-load data referenced in the form]** kryssrutan är markerad och **[!UICONTROL Adobe Campaign encryption]** identifieringsmetod har valts. Detta gör att webbprogrammet kan förhandsladda formulärfälten med data lagrade i Adobe Campaign-databasen. Se [det här dokumentet](../../web/using/publishing-a-web-form.md#pre-loading-the-form-data).

   ![](assets/acs_connect_lp_4.png)

1. Redigera **[!UICONTROL Page]**. Tre fält (Namn, E-post och Telefon) har inkluderats, samt en kryssruta där mottagaren kan prenumerera på ett nyhetsbrev (**[!UICONTROL Newsletter]** service).

   ![](assets/acs_connect_lp_3.png)

1. Gå till **[!UICONTROL Profiles and Target > Services and subscriptions]** och öppna **[!UICONTROL Newsletter]** service. Det här är den tjänst som kommer att uppdateras från Campaign Standarden. Du kan se att ingen mottagare har prenumererat på den här tjänsten ännu.

   ![](assets/acs_connect_lp_5.png)

1. Gå till **[!UICONTROL Profiles and Targets > Recipient]** och välj en mottagare. Du kan se att den här profilen inte har prenumererat på tjänsten än.

   ![](assets/acs_connect_lp_6.png)

## Replikera data {#replicating-the-data}

För att replikera nödvändiga data mellan Campaign v7 och Campaign Standard finns flera arbetsflödesmallar för replikering tillgängliga. The **[!UICONTROL Profiles replication]** arbetsflödet replikerar automatiskt alla Campaign v7-mottagare till Campaign Standarden. Se [Tekniska arbetsflöden och arbetsflöden för replikering](../../integrations/using/acs-connector-principles-and-data-cycle.md#technical-and-replication-workflows). The **[!UICONTROL Landing pages replication]** arbetsflödet möjliggör replikering av de webbprogram som vi vill använda i Campaign Standard.

![](assets/acs_connect_lp_1.png)

Följ de här stegen i Campaign Standarden för att kontrollera att data har replikerats korrekt:

1. Klicka på **[!UICONTROL Customer profiles]**.

   ![](assets/acs_connect_lp_7.png)

1. Sök efter Campaign v7-mottagaren och kontrollera att mottagaren visas i Campaign Standarden.

   ![](assets/acs_connect_lp_8.png)

1. Klicka på **[!UICONTROL Marketing activities]** och söka efter webbprogrammet Campaign v7. Den visas som en landningssida i Campaign Standard.

   ![](assets/acs_connect_lp_9.png)

1. Klicka på **[!UICONTROL Adobe Campaign]** logotyp, i det övre vänstra hörnet, och välj **Profiler och målgrupper > Tjänster** och kontrollera att nyhetsbrevet också finns där.

   ![](assets/acs_connect_lp_10.png)

## Designa och skicka e-post {#designing-and-sending-the-email}

I den här delen får vi se hur vi kan inkludera en länk, i ett e-postmeddelande med Campaign Standard, till landningssidan som replikeras från en Campaign v7-webbapplikation.

Stegen för att skapa, utforma och skicka e-postmeddelanden är desamma som för klassiska e-postmeddelanden. Se [Adobe Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard/using/campaign-standard-home.html?lang=sv) dokumentation.

1. Skapa ett nytt e-postmeddelande och välj en eller flera replikerade profiler som målgrupp.
1. Redigera innehållet och infoga en **[!UICONTROL Link to a landing page]**.

   ![](assets/acs_connect_lp_12.png)

1. Välj landningssidan som replikerades från webbprogrammet Campaign v7.

   ![](assets/acs_connect_lp_13.png)

1. Förbered din e-post, skicka korrektur och skicka det slutliga e-postmeddelandet.
1. En av mottagarna öppnar e-postmeddelandet och klickar på länken till nyhetsbrevet.

   ![](assets/acs_connect_lp_14.png)

1. Mottagaren lägger till ett telefonnummer och markerar prenumerationsrutan för nyhetsbrevet.

   ![](assets/acs_connect_lp_15.png)

## Hämtar uppdaterad information {#retrieving-the-updated-information}

När mottagaren uppdaterar sina data via webbprogrammet hämtar Adobe Campaign v7 synkront den uppdaterade informationen. Den replikeras sedan från Campaign v7 till Campaign Standard.

1. I Campaign v7 går du till **[!UICONTROL Profiles and Target > Services and subscriptions]** och öppna **[!UICONTROL Newsletter]** service. Du ser att mottagaren nu visas i prenumerationslistan.

   ![](assets/acs_connect_lp_16.png)

1. Gå till **[!UICONTROL Profiles and Targets > Recipient]** och välj mottagare. Du ser att telefonnumret nu lagras.

   ![](assets/acs_connect_lp_17.png)

1. I **[!UICONTROL Subscriptions]** kan vi även se att den här mottagaren har prenumererat på nyhetsbrevet.

   ![](assets/acs_connect_lp_18.png)

1. Vänta några minuter tills arbetsflödet för profilreplikering körs.
1. I Campaign Standard kan du komma åt din mottagarprofil för att kontrollera att uppdaterade data har replikerats korrekt från Campaign v7.

   ![](assets/acs_connect_lp_19.png)

1. Redigera profilen. Telefonnumret har uppdaterats.

   ![](assets/acs_connect_lp_20.png)

1. Klicka på **[!UICONTROL Subscriptions]** -fliken. Nyhetsbrevet visas nu.

   ![](assets/acs_connect_lp_21.png)
