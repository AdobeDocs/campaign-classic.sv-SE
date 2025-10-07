---
product: campaign
title: Kom igång med mobilappskanalen
description: Kom igång med mobilappskanalen i Adobe Campaign
feature: Push
role: User
exl-id: c3b0406f-f652-42f4-ad0d-23fb719cd1b6
source-git-commit: a1e9fec0e9c85bf25b79e24a7432dfb45bd1a0cb
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 2%

---

# Kom igång med mobilappskanalen{#about-mobile-app-channel}

Med Adobe Campaign kan du skapa push-meddelandeleveranser för att skicka personaliserade meddelanden till mobilappsanvändarna.

Med push-meddelanden kan du engagera användare på iOS och Android i realtid. Oavsett om ni skickar uppdateringar, meddelanden eller kampanjer kan ni styra innehåll, timing och målinriktning. Lär dig hur du konfigurerar och använder push-kanalen, hanterar prenumerationer, integrerar med APN och FCM samt anpassar meddelanden i [Adobe Campaign v8-dokumentationen](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/emails/email){target=_blank}.

Som en del av kampanjsatsningen v8 har Campaign Classic-dokumentationen omstrukturerats. Gemensamma funktioner är nu bara tillgängliga i Campaign v8-dokumentationsuppsättningen.

>[!BEGINTABS]

>[!TAB Tryckkanalsdokumentation]

Mer information om push-meddelandekanalen finns i [dokumentationen för Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html){target=_blank}.

[![bild](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html){target=_blank}


>[!TAB Skapa push-leverans]

Lär dig de viktigaste stegen för att skapa push-leveranser i dokumentationen för Campaign v8:

* [Skapa ett push-meddelande](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html#push-create){target="_blank"}: Lär dig mer om de olika stegen som krävs för att skapa en push-leverans.
* [Skicka och övervaka push-meddelandet](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html#push-test){target="_blank"}: Lär dig hur du validerar, skickar och spårar leveranser.
* [Designa en omfattande push-leverans från Android](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/rich-push/rich-push-android.html){target="_blank"}: Lär dig hur du skapar och konfigurerar omfattande push-meddelanden för Android-enheter.
* [Designa en omfattande push-leverans från iOS](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/rich-push/rich-push-ios.html){target="_blank"}: Lär dig hur du utformar och konfigurerar omfattande push-meddelanden för iOS-enheter i Adobe Campaign v8.


>[!TAB Push-parametrar]

Läs dessa sidor för att lära dig mer om push-parametrar i dokumentationen för Campaign v8:

* [Konfigurationskrav](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html#before-starting){target="_blank"}: Lär dig hur du konfigurerar behörigheter och konfigurerar din app.
* [Konfigurera startegenskapen](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html#launch-property){target="_blank"}: Lär dig hur du ställer in en mobil taggegenskap i Adobe Experience Platform Data Collection för att aktivera push-meddelanden.
* [Konfigurera push-tjänster för mobiltjänster](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html#push-service){target="_blank"}: Konfigurera push-tjänster för iOS och Android i Adobe för att aktivera riktade push-meddelanden för mobilappsanvändare.
* [Konfigurera tillägget i din mobila egenskap](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html#configure-extension){target="_blank"}: Integrera Campaign-tillägget i din mobila egenskap för att aktivera push-meddelanden och hantera användarinteraktioner effektivt.

>[!ENDTABS]


Följande information gäller endast Campaign Classic.

+++ **Paketinstallation**

![](assets/do-not-localize/how-to-video.png) [Lär dig hur du installerar mobilappspaketet i video](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/sending-messages/push-channel/installing-the-mobile-app-channel.html#sending-messages)

Kontakta [Adobe Customer Care](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) -teamet om du vill få åtkomst till en push-meddelandekanal i Campaign som hybridkund/värdkund.

Som lokal kund måste du installera ett inbyggt paket.

>[!CAUTION]
>
>Läs mer om Campaigns inbyggda paket, metodtips och rekommendationer i [den här sidan](../../installation/using/installing-campaign-standard-packages.md).

Installationsstegen är:

1. Få åtkomst till paketimportassistenten från **[!UICONTROL Tools > Advanced > Import package]** i Adobe Campaign klientkonsol.

   ![](assets/package_ios.png)

1. Välj **[!UICONTROL Install a standard package]**.

1. Markera **[!UICONTROL Mobile App Channel]** i listan som visas.

   ![](assets/package_ios_2.png)

1. Klicka på **[!UICONTROL Next]** och sedan på **[!UICONTROL Start]** för att starta paketinstallationen.

   När paketen har installerats visas **100%** i förloppsindikatorn och följande meddelande visas i installationsloggarna: **[!UICONTROL Installation of packages successful]**.

   ![](assets/package_ios_3.png)

1. **[!UICONTROL Close]** installationsfönstret.

När det här steget är klart kan du konfigurera dina Android- och iOS-appar. Se Campaign v8 [dokumentation](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html){target="_blank"}.

+++

+++ **Felsökning**

Om din mobila enhet är ansluten till ett trådlöst nätverk och du inte får några meddelanden kontrollerar du att FCM-/APN-portarna inte blockeras av din brandvägg.

**Android**: Den mobila enheten ansluter till FCM-servrarna på portarna 5228 till 5230. Därför måste du konfigurera brandväggen så att den tillåter anslutning till FCM. Portarna som ska öppnas är: 5228 (den vanligaste), 5229 och 5230.

**iOS**:

HTTP/2-anslutning: Du måste tillåta kommunikation till och från följande servrar:

* api.push.apple.com: port 443
* api.development.push.apple.com: port 443

>[!NOTE]
>
>Mer information om de två anslutningarna finns i [dokumentationen för Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html){target="_blank"}.

+++
