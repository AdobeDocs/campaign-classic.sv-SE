---
solution: Campaign Classic
product: campaign
title: Technote
description: Technote
hide: true
hidefromtoc: true
translation-type: tm+mt
source-git-commit: f47b0ecfd3e35d15a78779fd9f38cc93c798d5d2
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 6%

---

# Spårade URL:er signaturproblem {#tracked-urls}

Efter de senaste ändringarna kan spårade URL-adresser misslyckas när URL-signaturen är aktiv i Campaign. Vissa postlådor kan påverkas mer än andra eftersom vissa företag har särskilda säkerhetsverktyg som kan påverka länkar och ändra URL-signaturmekanismen.

Därför rekommenderar Adobe att du inaktiverar signaturmekanismen för att spåra länkar. Med den här proceduren korrigeras gamla spårningslänkar förutom de som tagits emot med dubbel escape-konvertering.

Observera att prenumerationslänkar inte kan användas som andra länkar. Frekvensen varierar från värd till värd men är mindre än 1 %.

**Påverkas du?**

För att förbättra säkerheten introducerades signaturfunktionen för att spåra länkar i e-postmeddelanden i [Campaign Gold Standard 8](../rn/using/gold-standard.md#gs8) - april 2020 - och är aktiverad som standard för alla kunder med början Build 19.1.4 (9032@3a9dc9c) och Campaign 20.2.

Om miljön körs i någon av versionerna som listas nedan kan du påverkas:

* Gold Standard 7 - 11. [Läs mer](../rn/using/gold-standard.md)
* Kampanj 21.1.1 - 21.1.2-utgåvor. [Läs mer](../rn/using/latest-release.md)
* Kampanj 20.3.1 - 20.3.3. [Läs mer](../rn/using/release--20-3.md)
* Kampanj 20.2.1 - 20.2.3-utgåvor. [Läs mer](../rn/using/release--20-2.md)
* Kampanj 20.1.1 - 21.1.3-utgåvor. [Läs mer](../rn/using/release--20-1.md)
* Kampanj 19.2.2 - 19.2.3-utgåvor. [Läs mer](../rn/using/release--19-2.md)
* Kampanj 19.1.5 - 19.1.7-utgåvor. [Läs mer](../rn/using/release--19-1.md)

Lär dig hur du kontrollerar din version [i det här avsnittet](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**Hur uppdaterar jag?**

Som **värdkund** arbetar Adobe tillsammans med dig för att uppdatera din konfiguration inom kort.

Som **lokal/hybrid-kund** måste du uppdatera din konfiguration.

Följ stegen nedan:

1. I [serverkonfigurationsfilen](../installation/using/the-server-configuration-file.md) (serverConf.xml) ändrar du **signEmailLinks** till **false**.
1. Starta om tjänsten **nlserver**.
1. Starta om webbservern på spårningsservern (apache2 på Debian, httpd on CentOS/RedHat, IIS on Windows).

   ```
   nlserver restart web
   ```

>[!NOTE]
>
>Filen **config-`<instance>`.xml** åsidosätter inställningarna för **serverConf.xml**. Om **signEmailLinks** finns i **config-`<instance>`.xml** (där **instance** är namnet på din instans) måste den också vara **false**.


**Vilken är effekten?**

Underhåll kräver högst 25 minuters driftstopp och under den här perioden fungerar inte alla leveranser, spårningslänkar och API-anrop.

När uppdateringen är klar fungerar alla länkar som förväntat.

>[!NOTE]
>
>Om du har frågor om dessa ändringar kan du kontakta [Adobe kundtjänst](https://helpx.adobe.com/sv/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

