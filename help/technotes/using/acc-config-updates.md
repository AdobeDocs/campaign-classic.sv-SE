---
product: campaign
title: Technote - Adobe Campaign-konfigurationsuppdateringar
description: Adobe Campaign konfigurationsuppdateringar
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
hide: true
hidefromtoc: true
exl-id: 7db02123-2e2a-40d9-8385-728ff69985e4
source-git-commit: 403d0b7df74b2c958bea9a2d718a15f597ca0d9c
workflow-type: tm+mt
source-wordcount: '1097'
ht-degree: 10%

---

# Konfigurationsuppdateringar för Adobe Campaign 2021 {#acc-config-updates}



Infrastruktur och inställningar bör uppdateras regelbundet med de senaste byggnaderna och produktkorrigeringarna. Dessa korrigeringar är nödvändiga för att säkerställa kontinuitet i service och säkerhet. Dessutom måste man uppgradera för att anpassa sig till ändringar från tredje part.

Som **Hosted or Managed Services customer** kommer Adobe att informera dig om att bygga uppgraderingar med jämna mellanrum. Du måste uppgradera i enlighet med rekommendationerna för att säkerställa regelefterlevnaden.

Som en **Lokal kund eller hybridkund** bör du uppgradera implementeringen med jämna mellanrum enligt de senaste versionerna.

Av säkerhetsskäl måste du nu uppgradera till en av versionerna nedan. Förutom de vanliga uppgraderingsstegen måste du utföra några manuella uppgifter för att säkerställa att din miljö är säker och redo för kommande ändringar från Adobe eller tredjepartssystem.

>[!NOTE]
>
>Om du har frågor om de här ändringarna kan du kontakta [Adobes kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).
>

## Säkerhetsuppdateringar {#acc-security-updates}

De senaste Campaign-versionerna har en säkerhetskorrigering som förstärker skyddet mot problem med SSRF (Server Side Request Forgery). Läs mer [på den här sidan](https://helpx.adobe.com/se/security/products/campaign/apsb21-04.html).

**Påverkas du?**

Om miljön är på en lägre nivå än de som anges nedan påverkas du:

* Gold Standard 11. [Läs mer](../../rn/using/gold-standard.md)
* Campaign 21.1.1-utgåvan. [Läs mer](../../rn/using/latest-release.md)
* Campaign 20.2.5-utgåvan.
* Campaign 20.1.4-utgåvan.
* Campaign 19.2.4-utgåvan.
* Campaign 19.1.8-utgåvan.

Lär dig hur du kontrollerar din version [i det här avsnittet](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**Hur uppdaterar jag?**

Du måste uppgradera till en av de nyare byggen som listas ovan.

* Som hybridkund informerar Adobe dig om de schemalagda uppgraderingsdatumen för dina mellanleverantörer. Adobe rekommenderar starkt att du uppgraderar din marknadsinstans också.

  Den nya versionen är bakåtkompatibel med version 17.9 av Campaign Classic, men Adobe rekommenderar starkt en uppgradering för alla instanser för att åtgärda säkerhetsluckor

* Som lokal kund ombeds ni att uppgradera alla instanser av marknadsföring och mellanprodukter till den senaste versionen.

>[!CAUTION]
>
>Om du inte kan uppgradera inom den rekommenderade tidsramen **kontakta kundtjänst på Adobe för att göra en kortsiktig manuell säkerhetskorrigering**.
>

## Campaign Classic Client Console - uppdatering  {#acc-cc-updates}

The **nu tillgänglig** Konsolversioner nedan bör installeras för att lösa en nyligen identifierad regression. Den här regressionen förhindrade användningen av vissa komponenter i klientkonsolen, som datumväljaren och bildhantering i leveranser. **Konsoluppgradering** är obligatoriskt.

* Senaste Gold Standard 11 build 9032@10c2709. [Läs mer](../../rn/using/gold-standard.md)
* Campaign 20.1.4-utgåvan.
* Campaign 19.2.4-utgåvan.
* Campaign 19.1.8-utgåvan.

## IMS-uppdatering (Adobe Identity Management System)

IMS-tjänsten (Adobe Identity Service) har inte längre stöd för äldre Internet Explorer-versioner från **30 juni 2021**. [Läs mer](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html).

Det krävs en uppgradering av Campaign Client Console för att säkerställa kompatibilitet med Adobe IMS.

**Påverkas du?**

Om du ansluter till Campaign [via en Adobe ID](../../integrations/using/about-adobe-id.md)via Adobe Identity Management Service (IMS) är uppgradering till en av de nya versionerna som listas nedan obligatorisk:

* Gold Standard 11. [Läs mer](../../rn/using/gold-standard.md)
* Campaign 21.1.1-utgåvan. [Läs mer](../../rn/using/latest-release.md)
* Campaign 20.2.5-utgåvan.
* Campaign 20.1.4-utgåvan.
* Campaign 19.2.4-utgåvan.
* Campaign 19.1.8-utgåvan.

De här versionerna har ett nytt anslutningsprotokoll: uppgradering är obligatoriskt för både Campaign-servern och Client Console för att kunna ansluta till Campaign efter **30 juni 2021**.

Lär dig hur du kontrollerar din version [i det här avsnittet](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**Hur uppdaterar jag?**

Som värdkund kommer Adobe att arbeta med dig för att uppgradera dina instanser till den nyare versionen inom kort.

Som lokal/hybridkund måste du uppgradera till en av de nyare versionerna för att kunna dra nytta av den nya klientkonsolen och säkerställa en smidig övergång **före 30 juni 2021**.

När alla instanser har uppgraderats måste även klientkonsolen uppgraderas till den här versionen.

* Lär dig hur du får åtkomst [Adobe Software Distribution](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html).

* [Lär dig hur du installerar Campaign Client Console](../../installation/using/installing-the-client-console.md).

## Integrering med utlösare från Experience Cloud {#acc-triggers-updates}

Den gamla autentiseringstjänsten för autentisering har nått slutet av livscykeln. Autentisering av utlösarintegration, som ursprungligen baserades på AUTH-autentiseringsinställningar för åtkomst till pipeline, har flyttats till Adobe I/O. Äldre autentiseringsmodell med Campaign [har tagits ur bruk](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411) på **September 2021**. Värdmiljöer drar nytta av en förlängning till **23 februari 2022**. Kontakta Adobe kundtjänst för support på plats eller som hybridkund till februari 2022. Du måste ange [AppID:et för OAuth-applikationen](../../integrations/using/configuring-pipeline.md#step-optional) till Adobe.

**Påverkas du?**

Om dina instanser körs på en **äldre version än Campaign 19.1.8, 20.2.4, Gold Standard 11** använder du en äldre version av integreringen av utlösare via autentisering: **du behöver uppgradera till en nyare version och gå över till Adobe I/O**.

Uppgradera till en av de nya versionerna som listas nedan är obligatorisk:

* Gold Standard 11. [Läs mer](../../rn/using/gold-standard.md)
* Campaign 21.1.1-utgåvan. [Läs mer](../../rn/using/latest-release.md)
* Campaign 20.2.5-utgåvan.
* Campaign 19.1.8-utgåvan.

Lär dig hur du kontrollerar din version [i det här avsnittet](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**Hur uppdaterar jag?**

När instanserna har uppgraderats till en nyare version måste alla kunder följa [proceduren flyttas till det nya autentiseringsläget](../../integrations/using/configuring-adobe-io.md). Detta kräver att du skapar den nya Adobe I/O-token och använder den i implementeringen.  

För hybridmiljöer måste kunderna dessutom se till att pipeline är konfigurerad på en instans av mellanleverantörer. [Läs mer](../../integrations/using/configuring-pipeline.md).

[Lär dig hur du migrerar till Adobe I/O](../../integrations/using/configuring-adobe-io.md).

## APNs-uppdateringar {#acc-apns-updates}

### HTTP/2-baserat API för APNs-provider

Sedan **31 mars 2021** stöder inte längre Apple Push Notification-tjänsten (APN:er) det äldre binära protokollet. [Läs mer](https://developer.apple.com/news/?id=c88acm2b).

**Påverkas du?**

Om dina instanser körs på en **äldre version än Campaign 21.1,** och du skickar push-meddelanden med det gamla binära Apple-protokollet måste du uppdatera till HTTP/2-baserade API:er för APN:er-providern.

Lär dig hur du kontrollerar din version [i det här avsnittet](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**Hur uppdaterar jag?**

Om du är en värdkund och har uppgraderat till den nya versionen har Adobe redan uppdaterat dina instanser till det HTTP/2-baserade API:t.

Som lokal/hybridkund måste du uppdatera din konfiguration.

### Uppdateringar av APN:s rotcertifikat

Den 29 mars 2021 påverkade en infrastrukturuppdatering för Apple Push Notification service (APNs) Adobe Campaign Classic iOS-kanal. En ändring av operativsystemets konfiguration är **obligatoriskt** för att undvika avbrott i iOS-kanaler.

Läs mer om ändringar i APN:er [på den här sidan](https://developer.apple.com/news/?id=7gx0a2lp).

**Påverkas du?**

Om du använder Campaign för att skicka push-meddelanden på iOS-enheter påverkas du.

**Hur uppdaterar jag?**

Som värdkund behövs ingen åtgärd: Adobe har redan införlivat det nya rotcertifikatet i din miljö.

Som lokal/hybridkund måste du uppdatera din konfiguration för att säkerställa en smidig övergång **före den 29 mars 2021**.

[Lär dig hur du infogar det nya certifikatet](ios-certificate-update.md).

## Användbara länkar

* [Uppgradera din miljö](../../production/using/build-upgrade.md)
* [Vanliga frågor och svar om builduppgradering](../../platform/using/faq-build-upgrade.md)
* [Ladda ned Campaign Classic build](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
* [Gör den nya klientkonsolen tillgänglig för användare](../../installation/using/client-console-availability-for-windows.md)
