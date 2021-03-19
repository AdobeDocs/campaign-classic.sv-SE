---
solution: Campaign Classic
product: campaign
title: Technote
description: Technote
hide: true
hidefromtoc: true
translation-type: tm+mt
source-git-commit: cac3e22dd9aa8220f6980bef0d57c11d47c91163
workflow-type: tm+mt
source-wordcount: '1027'
ht-degree: 7%

---


# Konfigurationsuppdateringar för Adobe Campaign - mars 2021 {#acc-config-updates}

Du måste hålla din infrastruktur och dina inställningar uppdaterade med de senaste byggnaderna och produktkorrigeringarna. Dessa korrigeringar är obligatoriska för att säkerställa tjänstens kontinuitet och säkerhet. Dessutom måste ni anpassa implementeringen så att den överensstämmer med ändringar från tredje part.

Som värdkund kommer Adobe att informera dig om nödvändiga bygguppgraderingar med jämna mellanrum. Ni måste uppgradera i enlighet med rekommendationerna för att säkerställa regelefterlevnaden.

Som lokal kund/hybridkund måste du av säkerhetsskäl uppgradera till en av versionerna på den här sidan. Dessutom måste några manuella åtgärder utföras för att säkerställa att din miljö är säker och redo för kommande ändringar från Adobe eller tredjepartssystem.

>[!NOTE]
>
>Kontakta [Adobe kundtjänst](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) om du har frågor om dessa ändringar.


## Säkerhetsuppdateringar

De senaste Campaign-versionerna har en säkerhetskorrigering som stärker skyddet mot problem med SSRF (Server Side Request Forgery). Läs mer [på den här sidan](https://helpx.adobe.com/security/products/campaign/apsb21-04.html).

**Påverkas du?**

Om miljön är på en lägre nivå än de som anges nedan påverkas du:

* Gold Standard 11. [Läs mer](../rn/using/gold-standard.md)
* Campaign 21.1.1-utgåvan. [Läs mer](../rn/using/latest-release.md)
* Campaign 20.3.3-utgåvan. [Läs mer](../rn/using/release--20-3.md)
* Campaign 20.2.4-utgåvan. [Läs mer](../rn/using/release--20-2.md)
* Campaign 20.1.4-utgåvan. [Läs mer](../rn/using/release--20-1.md)
* Campaign 19.2.4-utgåvan. [Läs mer](../rn/using/release--19-2.md)
* Campaign 19.1.8-utgåvan. [Läs mer](../rn/using/release--19-1.md)

**Hur uppdaterar jag?**

Du måste uppgradera till en av de nyare byggen som listas ovan.

* Som hybridkund uppgraderar Adobe marknadsinstansen till den nya versionen och du rekommenderas att uppgradera deras marknadsinstans också.

   Den nya versionen är kompatibel med minst Campaign Classic 17.9, men för att undvika säkerhetsbrister rekommenderar Adobe starkt att du uppgraderar alla instanser till en ny version. 

* Som en lokal kund ombeds ni uppgradera alla instanser av marknadsföring och mellanprodukter till en nyare version.

>[!CAUTION]
>
>Om du inte kan uppgradera just nu **måste du kontakta kundtjänstteamet på Adobe för att manuellt tillämpa en säkerhetskorrigering på dina instanser**.


## Uppdatering av Campaign Client Console

Den senaste versionen av Gold Standard 11 åtgärdar en regression som förhindrade användningen av vissa komponenter i Clien Console, till exempel datumväljaren och bildhantering i leveranser. Konsoluppgradering är obligatoriskt.

[Läs mer](../rn/using/gold-standard.md).

>[!NOTE]
>
>Den nya klientkonsolen för andra versioner är snart tillgänglig.

## IMS-uppdatering (Adobe Identity Management System)

Adobe Identity Service (IMS) kommer inte att ha stöd för äldre Internet Explorer-versioner från och med den 30 juni 2021 **.** [Läs mer](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html).

Campaign Client Console har uppdaterats för att säkerställa kompatibilitet med Adobe IMS.

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

**Hur uppdaterar jag?**

Som värdkund behövs ingen åtgärd: Adobe har redan uppgraderat dina instanser till en senare version.

Som lokal/hybridkund måste du uppgradera till en av de nyare versionerna för att kunna utnyttja den nya klientkonsolen och säkerställa en smidig övergång **före 30 juni 2021**.

När alla instanser har uppgraderats måste även klientkonsolen uppgraderas till den här versionen.

* Lär dig hur du får åtkomst till [Adobe Software Distribution](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=en).

* [Lär dig hur du installerar Campaign Client Console](../installation/using/installing-the-client-console.md).

## Integrering med utlösare från Experience Cloud

Den gamla autentiseringstjänsten för autentisering har nått slutet av livscykeln. Autentisering av utlösarintegration, som ursprungligen baserades på AUTH-autentiseringsinställningar för åtkomst till pipeline, har flyttats till Adobe I/O. Den upphör den 30 november 2021 **.** [Läs mer](https://github.com/AdobeDocs/analytics-1.4-apis/blob/master/docs/APIEOL.md?mv=email).

**Påverkas du?**

Om dina instanser körs på en **äldre version än Campaign 19.1.8, 20.2.4, Gold Standard 11** använder du en äldre version av Triggers-integrering via Autentisering: **du måste uppgradera till en nyare version och gå till Adobe I/O**.

Uppgradera till en av de nya versionerna som listas nedan är obligatorisk:

* Gold Standard 11. [Läs mer](../rn/using/gold-standard.md)
* Campaign 21.1.1-utgåvan. [Läs mer](../rn/using/latest-release.md)
* Campaign 20.3.3-utgåvan. [Läs mer](../rn/using/release--20-3.md)
* Campaign 20.2.4-utgåvan. [Läs mer](../rn/using/release--20-2.md)
* Campaign 19.1.8-utgåvan. [Läs mer](../rn/using/release--19-1.md)

**Hur uppdaterar jag?**

När instanserna har uppgraderats till en nyare version måste alla kunder följa [proceduren för att gå över till det nya autentiseringsläget](../integrations/using/configuring-adobe-io.md). Detta kräver att den nya Adobe I/O-token genereras och används i implementeringen.  

För hybridmiljöer måste kunderna dessutom se till att pipeline är konfigurerad på en instans av mellanleverantörer. [Läs mer](../integrations/using/configuring-pipeline.md).

[Lär dig hur du migrerar till Adobe I/O](../integrations/using/configuring-adobe-io.md).

## APNs-uppdateringar

### HTTP/2-baserat API för APNs-provider

Apple Push Notification-tjänsten (APN:er) stöder inte längre det äldre binära protokollet den 31 mars 2021 **.** [Läs mer](https://developer.apple.com/news/?id=c88acm2b).

**Påverkas du?**

Om dina instanser körs på en **äldre version än Campaign 21.1,** och skickar push-meddelanden med det gamla binära Apple-protokollet, måste du uppdatera till det HTTP/2-baserade API:t för APN-providern.

**Hur uppdaterar jag?**

Som värdkund behövs ingen åtgärd: Adobe har redan uppdaterat dina instanser till det HTTP/2-baserade API:t.

Som en lokal/värdbaserad kund måste du uppdatera din konfiguration. [Lär dig hur du migrerar till HTTP/2](https://helpx.adobe.com/se/campaign/kb/migrate-to-apns-http2.html)

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
* [Vanliga frågor om uppgradering av bygge](../platform/using/faq-build-upgrade.md)
* [Ladda ned Campaign Classic build](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
* [Gör den nya klientkonsolen tillgänglig för användare](../installation/using/client-console-availability-for-windows.md)
