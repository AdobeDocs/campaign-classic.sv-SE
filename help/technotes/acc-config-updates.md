---
solution: Campaign Classic
product: campaign
title: Technote
description: Technote
hide: true
hidefromtoc: true
exl-id: 7db02123-2e2a-40d9-8385-728ff69985e4
translation-type: tm+mt
source-git-commit: 2c47a3e42260a0f04d2c9a665f28c532212997f8
workflow-type: tm+mt
source-wordcount: '1114'
ht-degree: 8%

---

# Konfigurationsuppdateringar för Adobe Campaign - mars 2021 {#acc-config-updates}

Infrastruktur och inställningar bör uppdateras regelbundet med de senaste byggnaderna och produktkorrigeringarna. Dessa korrigeringar är nödvändiga för att säkerställa kontinuitet i service och säkerhet. Dessutom måste man uppgradera för att anpassa sig till ändringar från tredje part.

Som **värd- eller Managed Services-kund** informerar Adobe dig om att du bygger uppgraderingar med regelbundna intervall. Du måste uppgradera i enlighet med rekommendationerna för att säkerställa regelefterlevnaden.

Som **lokal- eller hybridkund** bör du uppgradera implementeringen med regelbundna intervall i enlighet med de senaste versionerna.

Av säkerhetsskäl måste du nu uppgradera till en av versionerna nedan. Förutom de vanliga uppgraderingsstegen måste du utföra några manuella uppgifter för att säkerställa att din miljö är säker och redo för kommande ändringar från Adobe eller tredjepartssystem.

>[!NOTE]
>
>Om du har frågor om dessa ändringar kan du kontakta [Adobe kundtjänst](https://helpx.adobe.com/sv/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).


## Säkerhetsuppdateringar {#acc-security-updates}

De senaste Campaign-versionerna har en säkerhetskorrigering som förstärker skyddet mot problem med SSRF (Server Side Request Forgery). Läs mer [på den här sidan](https://helpx.adobe.com/security/products/campaign/apsb21-04.html).

**Påverkas du?**

Om miljön är på en lägre nivå än de som anges nedan påverkas du:

* Gold Standard 11. [Läs mer](../rn/using/gold-standard.md)
* Campaign 21.1.1-utgåvan. [Läs mer](../rn/using/latest-release.md)
* Campaign 20.3.3-utgåvan. [Läs mer](../rn/using/release--20-3.md)
* Campaign 20.2.4-utgåvan. [Läs mer](../rn/using/release--20-2.md)
* Campaign 20.1.4-utgåvan. [Läs mer](../rn/using/release--20-1.md)
* Campaign 19.2.4-utgåvan. [Läs mer](../rn/using/release--19-2.md)
* Campaign 19.1.8-utgåvan. [Läs mer](../rn/using/release--19-1.md)

Lär dig hur du kontrollerar din version [i det här avsnittet](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**Hur uppdaterar jag?**

Du måste uppgradera till en av de nyare byggen som listas ovan.

* Som hybridkund informerar Adobe dig om de schemalagda uppgraderingsdatumen för dina mellanleverantörer. Adobe rekommenderar starkt att du uppgraderar din marknadsinstans också.

   Den nya versionen är bakåtkompatibel med version 17.9 av Campaign Classic, men Adobe rekommenderar starkt en uppgradering för alla instanser för att åtgärda säkerhetsluckor

* Som lokal kund ombeds ni att uppgradera alla instanser av marknadsföring och mellanprodukter till den senaste versionen.

>[!CAUTION]
>
>Om du inte kan uppgradera inom den rekommenderade tidsramen, **bör du kontakta Adobe kundtjänstteam för att göra en kortsiktig manuell säkerhetskorrigering för dina instanser**.


## Uppdatering av Campaign Classic Client Console {#acc-cc-updates}

**Nu tillgängliga**-konsolversionerna nedan bör installeras för att lösa en nyligen identifierad regression. Den här regressionen förhindrade användningen av vissa komponenter i klientkonsolen, som datumväljaren och bildhantering i leveranser. **Konsoluppgradering** är obligatoriskt.

* Senaste Gold Standard 11 build 9032@10c2709. [Läs mer](../rn/using/gold-standard.md)
* Campaign 20.1.4-utgåvan. [Läs mer](../rn/using/release--20-1.md)
* Campaign 19.2.4-utgåvan. [Läs mer](../rn/using/release--19-2.md)
* Campaign 19.1.8-utgåvan. [Läs mer](../rn/using/release--19-1.md)

## IMS-uppdatering (Adobe Identity Management System)

Adobe Identity Service (IMS) kommer inte längre att ha stöd för gamla Internet Explorer-versioner från och med den 30 juni 2021 **.** [Läs mer](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html).

Det krävs en uppgradering av Campaign Client Console för att säkerställa kompatibilitet med Adobe IMS.

**Påverkas du?**

Om du ansluter till Campaign [via en Adobe ID](../integrations/using/about-adobe-id.md) via Adobe Identity Management Service (IMS) är en uppgradering till en av de nya versionerna som listas nedan obligatorisk:

* Gold Standard 11. [Läs mer](../rn/using/gold-standard.md)
* Campaign 21.1.1-utgåvan. [Läs mer](../rn/using/latest-release.md)
* Campaign 20.3.3-utgåvan. [Läs mer](../rn/using/release--20-3.md)
* Campaign 20.2.4-utgåvan. [Läs mer](../rn/using/release--20-2.md)
* Campaign 20.1.4-utgåvan. [Läs mer](../rn/using/release--20-1.md)
* Campaign 19.2.4-utgåvan. [Läs mer](../rn/using/release--19-2.md)
* Campaign 19.1.8-utgåvan. [Läs mer](../rn/using/release--19-1.md)

De här versionerna har ett nytt anslutningsprotokoll: måste uppgraderas för att både Campaign-servern och Client Console ska kunna ansluta till Campaign efter den 30 juni 2021 **.**

Lär dig hur du kontrollerar din version [i det här avsnittet](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**Hur uppdaterar jag?**

Som värdkund kommer Adobe att arbeta med dig för att uppgradera dina instanser till den nyare versionen inom kort.

Som lokal/hybridkund måste du uppgradera till en av de nyare versionerna för att kunna utnyttja den nya klientkonsolen och säkerställa en smidig övergång **före 30 juni 2021**.

När alla instanser har uppgraderats måste även klientkonsolen uppgraderas till den här versionen.

* Lär dig hur du får åtkomst till [Adobe Software Distribution](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=en).

* [Lär dig hur du installerar Campaign Client Console](../installation/using/installing-the-client-console.md).

## Integrering med Experience Cloud-utlösare {#acc-triggers-updates}

Den gamla autentiseringstjänsten för autentisering har nått slutet av livscykeln. Autentisering av utlösarintegration, som ursprungligen baserades på AUTH-autentiseringsinställningar för åtkomst till pipeline, har flyttats till Adobe I/O. Den upphör den 30 november 2021 **.** [Läs mer](https://github.com/AdobeDocs/analytics-1.4-apis/blob/master/docs/APIEOL.md?mv=email).

**Påverkas du?**

Om dina instanser körs på en **äldre version än Campaign 19.1.8, 20.2.4, Gold Standard 11** använder du en äldre version av Triggers-integrering via Autentisering: **du måste uppgradera till en nyare version och gå till Adobe I/O**.

Uppgradera till en av de nya versionerna som listas nedan är obligatorisk:

* Gold Standard 11. [Läs mer](../rn/using/gold-standard.md)
* Campaign 21.1.1-utgåvan. [Läs mer](../rn/using/latest-release.md)
* Campaign 20.3.3-utgåvan. [Läs mer](../rn/using/release--20-3.md)
* Campaign 20.2.5-utgåvan. [Läs mer](../rn/using/release--20-2.md)
* Campaign 19.1.8-utgåvan. [Läs mer](../rn/using/release--19-1.md)

Lär dig hur du kontrollerar din version [i det här avsnittet](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**Hur uppdaterar jag?**

När instanserna har uppgraderats till en nyare version måste alla kunder följa [proceduren för att gå över till det nya autentiseringsläget](../integrations/using/configuring-adobe-io.md). Detta kräver att du skapar den nya Adobe I/O-token och använder den i implementeringen.  

För hybridmiljöer måste kunderna dessutom se till att pipeline är konfigurerad på en instans av mellanleverantörer. [Läs mer](../integrations/using/configuring-pipeline.md).

[Lär dig hur du migrerar till Adobe I/O](../integrations/using/configuring-adobe-io.md).

## APNs-uppdateringar {#acc-apns-updates}

### HTTP/2-baserat API för APNs-provider

Apple Push Notification-tjänsten (APN:er) stöder inte längre det äldre binära protokollet den 31 mars 2021 **.** [Läs mer](https://developer.apple.com/news/?id=c88acm2b).

**Påverkas du?**

Om dina instanser körs på en **äldre version än Campaign 21.1,** och du skickar push-meddelanden med det äldre binära Apple-protokollet, måste du uppdatera till det HTTP/2-baserade API:t för APN-providern.

Lär dig hur du kontrollerar din version [i det här avsnittet](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**Hur uppdaterar jag?**

Om du är en värdkund och har uppgraderat till den nya versionen har Adobe redan uppdaterat dina instanser till det HTTP/2-baserade API:t.

Som lokal/hybridkund måste du uppdatera din konfiguration. [Lär dig hur du migrerar till HTTP/2](https://helpx.adobe.com/se/campaign/kb/migrate-to-apns-http2.html)

### Uppdateringar av APN:s rotcertifikat

Den 29 mars 2021 kommer en infrastrukturuppdatering för Apple Push Notification service (APNs) att påverka Adobe Campaign Classic iOS-kanal. En ändring av operativsystemets konfiguration är **obligatorisk** för att undvika avbrott i push-kanalen i iOS.

Läs mer om ändringar av APN:er [på den här sidan](https://developer.apple.com/news/?id=7gx0a2lp).

**Påverkas du?**

Om du använder Campaign för att skicka push-meddelanden på iOS-enheter påverkas du.

**Hur uppdaterar jag?**

Som värdkund behövs ingen åtgärd: Adobe har redan införlivat det nya rotcertifikatet i din miljö.

Som lokal/hybridkund måste du uppdatera konfigurationen för att säkerställa en sömlös övergång **före den 29 mars 2021**.

[Lär dig hur du infogar det nya certifikatet](ios-certificate-update.md).

## Användbara länkar

* [Uppgradera din miljö](../production/using/build-upgrade.md)
* [Vanliga frågor och svar om builduppgradering](../platform/using/faq-build-upgrade.md)
* [Ladda ned Campaign Classic build](https://experience.adobe.com/#/downloads/content/software-distribution/sv/campaign.html)
* [Gör den nya klientkonsolen tillgänglig för användare](../installation/using/client-console-availability-for-windows.md)
