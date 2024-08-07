---
product: campaign
title: Signaturproblem med spårade URL:er
description: Signaturproblem med spårade URL:er
feature: Technote
hide: true
hidefromtoc: true
exl-id: e7d4331b-7149-4768-8e46-2e2911319074
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 30%

---

# Signaturproblem med spårade URL:er {#tracked-urls}



Efter de senaste ändringarna kan spårade URL-adresser misslyckas när URL-signaturen är aktiv i Campaign. Vissa postlådor kan påverkas mer än andra eftersom vissa företag har särskilda säkerhetsverktyg som kan påverka länkar och ändra URL-signaturmekanismen.

Därför rekommenderar Adobe att du inaktiverar signaturmekanismen för att spåra länkar. Med den här proceduren korrigeras gamla spårningslänkar förutom de som tagits emot med dubbel escape-konvertering.

Observera att prenumerationslänkar inte kan användas som andra länkar. Frekvensen varierar från värd till värd men är mindre än 1 %.

**Påverkas du?**

För att förbättra säkerheten introducerades signaturfunktionen för att spåra länkar i e-postmeddelanden i [Campaign Gold Standard 8](../../rn/using/gold-standard.md#gs8) - april 2020 - och är aktiverad som standard för alla kunder med början Build 19.1.4 (9032@3a9dc9c) och Campaign 20.2.

Om miljön körs i någon av versionerna som listas nedan kan du påverkas:

* Gold Standard 8 till 11. [Läs mer](../../rn/using/gold-standard.md#gs-8)
* Kampanj 21.1.1 (build 9277) till 21.1.2 (build 9282). [Läs mer](../../rn/using/latest-release.md)
* Kampanj 20.3.1 (build 9228) till 20.3.3 (build 9234).
* Kampanj 20.2.1 (build 9178) till 20.2.4 (build 9187).
* Kampanj 20.1.1 (build 9122) till 21.1.3 (build 9124).
* Kampanj 19.2.2 (build 9080) till 19.2.3 (build 9081).
* Kampanj 19.1.5 (build 9033) till 19.1.7 (build 9036).


Lär dig hur du kontrollerar version [ i det här avsnittet](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**Hur uppdaterar jag?**

Som **värdkund** arbetar Adobe med dig för att uppdatera din konfiguration inom kort.

Som **lokal/hybridkund** måste du uppdatera din konfiguration.

Följ stegen nedan:

1. I [serverkonfigurationsfilen](../../installation/using/the-server-configuration-file.md) (serverConf.xml) ändrar du **signEmailLinks** till **false**.
1. Starta om tjänsten **nlserver**.
1. Starta om webbservern på spårningsservern (apache2 på Debian, httpd on CentOS/RedHat, IIS on Windows).

   ```
   nlserver restart web
   ```

>[!NOTE]
>
>Filen **config-`<instance>`.xml** åsidosätter inställningarna för **serverConf.xml**. Om **signEmailLinks** finns i **config-`<instance>`.xml** (där **instance** är namnet på din instans) måste den också vara **false**.
>

**Vad ändras?**

Underhåll kräver högst 25 minuters driftstopp och under den här perioden fungerar inte alla leveranser, spårningslänkar och API-anrop.

När uppdateringen är klar fungerar alla länkar som förväntat.

>[!NOTE]
>
>Om du har frågor om de här ändringarna kan du kontakta [Adobes kundtjänst](https://helpx.adobe.com/sv/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).
>
