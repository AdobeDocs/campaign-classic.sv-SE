---
product: campaign
title: Konfigurera URL-behörigheter
description: Lär dig hur du konfigurerar URL-behörigheter
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 6fe8da3b-57b9-4a69-8602-a03993630b27
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 29%

---

# Konfigurera URL-behörigheter (lokalt){#url-permissions}



Standardlistan med URL:er som kan anropas av JavaScript-koder (arbetsflöden osv.) från dina instanser i Campaign Classic är begränsad. Dessa är URL:er som gör det möjligt för dina instanser att fungerar korrekt.

Som standard tillåts instanser endast att ansluta till interna URL:er. Det är dock möjligt att lägga till vissa externa URL:er i listan över auktoriserade URL:er, så att instansen kan ansluta till dem. Detta gör det möjligt för dig att ansluta instanserna i Campaign till externa system såsom SFTP-servrar eller webbplatser för att möjliggöra fil- och/eller dataöverföring.

>[!NOTE]
>
>Den här proceduren är begränsad till **lokal** distributioner.
>
>Som **värdbaserad** -kund, om du har åtkomst [Kontrollpanelen för kampanj](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=sv)kan du använda självbetjäningsgränssnittet för URL-behörigheter. [Läs mer](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/url-permissions.html?lang=sv)
>
>Övriga **hybrid/värd** Kunder måste kontakta Adobe supportteam för att lägga till IP i tillåtelselista.

För **Hybrid** och **Lokalt** distributioner måste administratören referera till en ny **urlPermission** i **serverConf.xml** -fil.


Tre lägen för anslutningsskydd är tillgängliga:

* **Blockera**: Alla URL:er som inte tillhör tillåtelselista blockeras, med ett felmeddelande. Det här är standardläget efter en efteruppgradering.
* **Tillstånd**: Alla URL:er som inte tillhör tillåtelselista tillåts.
* **Varning**: Alla URL:er som inte tillhör tillåtelselista tillåts, men JS-tolken skickar en varning så att administratören kan samla in dem. I det här läget läggs JST-310027-varningsmeddelanden till.

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

>[!IMPORTANT]
>
>Som standard används **Blockera** läge.
>
>Som befintlig kund som kommer från en migrering kan du tillfälligt använda **Varning** läge. Analysera utgående trafik innan URL-adresserna tillåts. När listan över tillåtna URL:er har definierats kan du lägga till URL:er till tillåtelselista och aktivera **Blockera** läge.

Mer information finns i följande avsnitt:

* [Dokumentation för kontrollpanelen](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=sv)
* [Värdbaserade modeller](hosting-models.md)
* [Konfiguration av Campaign-server](configuring-campaign-server.md)
* [Konfigurationsfilsparametrar för kampanjserver](the-server-configuration-file.md)
* [Checklista för säkerhet och integritet](get-started-security-privacy.md)
