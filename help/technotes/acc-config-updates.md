---
solution: Campaign Classic
product: campaign
title: Technote
description: Technote
hide: true
hidefromtoc: true
translation-type: tm+mt
source-git-commit: 93dc5a16ce4880c132f4f91c72794892b00e7259
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 5%

---


# Konfigurationsuppdateringar för Adobe Campaign - mars 2021 {#acc-config-updates}

Du måste hålla din infrastruktur och dina inställningar uppdaterade med de senaste byggen och produktkorrigeringarna. Dessa korrigeringar är obligatoriska för att säkerställa tjänstens kontinuitet och säkerhet.

Kampanjanvändare måste uppgradera till en av de senaste versionerna nedan:

* Gold Standard 11. [Läs mer](../rn/using/gold-standard.md)
* Campaign 21.1.1-utgåvan. [Läs mer](../rn/using/latest-release.md)
* Campaign 20.3.3-utgåvan. [Läs mer](../rn/using/release--20-3.md)
* Campaign 20.2.4-utgåvan. [Läs mer](../rn/using/release--20-2.md)
* Campaign 20.1.4-utgåvan. [Läs mer](../rn/using/release--20-1.md)
* Campaign 19.2.4-utgåvan. [Läs mer](../rn/using/release--19-2.md)
* Campaign 19.1.8-utgåvan. [Läs mer](../rn/using/release--19-1.md)

Dessa byggen säkerställer kontinuiteten för vissa kampanjtjänster: Integrering av Experience Cloud-utlösare, APN-autentisering och det nya anslutningsprotokollet som påverkar autentiseringsmekanismen för Adobe Identity Management Service (IMS).

Som värdkund behövs ingen åtgärd: Adobe äger uppgraderings- och konfigurationsuppdateringarna åt dig.

Som lokal kund/hybridkund måste du uppgradera till någon av versionerna ovan. Dessutom behöver du utföra några manuella åtgärder för att säkerställa att din miljö är säker och redo för kommande ändringar från Adobe eller tredjepartssystem.

## Säkerhetsuppdateringar

De senaste Campaign-versionerna har en säkerhetskorrigering som stärker skyddet mot problem med SSRF (Server Side Request Forgery). Läs mer [på den här sidan](https://helpx.adobe.com/security/products/campaign/apsb21-04.html).

### Påverkas du?

Om miljön är på en lägre nivå än Campaign 21.1 påverkas du.

## Hur uppdaterar jag?

Du måste uppgradera till en av de nyare byggen som listas ovan.

* Som hybridkund kommer Adobe att uppgradera mellanleverantörsinstansen till den nya versionen och du rekommenderas att uppgradera deras marknadsinstans också.
Den nya versionen är kompatibel med minst Campaign Classic 17.9, men för att undvika säkerhetsbrister rekommenderar Adobe starkt att du uppgraderar alla instanser till en ny version. 

* Som en lokal kund ombeds ni uppgradera alla instanser av marknadsföring och mellanprodukter till en ny version.

>[!CAUTION]
>
>Om du inte kan uppgradera för tillfället **måste du kontakta kundtjänstteamet på Adobe för att manuellt tillämpa en säkerhetskorrigering på dina instanser**.


## Uppdatering av Campaign Client Console

Den senaste versionen av Gold Standard 11 åtgärdar en regression som förhindrade användningen av vissa komponenter i konsolen, som datumväljaren och bildhantering i leveranser. Konsoluppgradering är obligatoriskt.

[Läs mer](../rn/using/gold-standard.md).

## Anslut till Campaign via IMS

Adobe Identity Service (IMS) kommer inte längre att ha stöd för äldre Internet Explorer-versioner från och med den 31 mars 2021. [Läs mer](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html). Campaign Console har uppdaterats för att säkerställa kompatibilitet med IMS.

### Påverkas du?

Om du ansluter till Campaign [via en Adobe ID](../integrations/using/about-adobe-id.md), via Adobe Identity Service (IMS), måste du uppgradera till en av de nya versionerna som listas ovan för att både Campaign-servern och klientkonsolen ska kunna ansluta till Campaign efter den 31 mars 2021 **.**

### Hur uppdaterar jag?

Som värdkund behövs ingen åtgärd: Adobe har redan uppgraderat dina instanser till en senare version.

Som lokal/hybridkund måste du uppgradera till en av de nyare versionerna för att kunna utnyttja den nya klientkonsolen och säkerställa en smidig övergång **före 31 mars 2021**.

## Integrering med utlösare från Experience Cloud

Den gamla autentiseringstjänsten för autentisering har nått slutet av livscykeln och kommer att upphöra den 30 april 2021. [Läs mer](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411).

### Påverkas du?

Om du använder en äldre version av utlösare-integrering via autentisering, **måste du gå till Adobe I/O**.

### Hur uppdaterar jag?

[Lär dig hur du migrerar till Adobe I/O](../integrations/using/configuring-adobe-io.md).

## HTTP/2-baserat API för APNs-provider

APN:er (Apple Push Notification service) stöder inte längre det äldre binära protokollet från och med den 31 mars 2021. [Läs mer](https://developer.apple.com/news/?id=c88acm2b).

### Påverkas du?

Om dina instanser körs på en äldre version än Campaign 21.1 och skickar push-meddelanden med det äldre binära Apple-protokollet, måste du uppdatera till HTTP/2-baserade API:er för APN-providern.

### Hur uppdaterar jag?

Som värdkund behövs ingen åtgärd: Adobe har redan uppdaterat dina instanser till det HTTP/2-baserade API:t.

Som en lokal/värdbaserad kund måste du uppdatera din konfiguration. [Lär dig hur du migrerar till HTTP/2](https://helpx.adobe.com/se/campaign/kb/migrate-to-apns-http2.html)

## Uppdateringar av APN:s rotcertifikat

Den 29 mars 2021 kommer en infrastrukturuppdatering för Apple Push Notification service (APNs) att påverka Adobe Campaign Classic iOS-kanal. En ändring av operativsystemets konfiguration är **obligatorisk** för att undvika avbrott i push-kanalen i iOS.

Läs mer om ändringar av APN:er [på den här sidan](https://developer.apple.com/news/?id=7gx0a2lp).

### Påverkas du?

Om du använder Campaign för att skicka push-meddelanden på iOS-enheter påverkas du.

### Hur uppdaterar jag?

Som värdkund behövs ingen åtgärd: Adobe har redan införlivat det nya rotcertifikatet i din miljö.

Som lokal/hybridkund måste du uppdatera konfigurationen för att säkerställa en sömlös övergång **före den 29 mars 2021**.

[Lär dig hur du infogar det nya certifikatet](ios-certificate-update.md)
