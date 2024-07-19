---
product: campaign
title: Konfigurera URL-behörigheter
description: Lär dig hur du konfigurerar URL-behörigheter
feature: Installation, Instance Settings, Permissions
badge-v7-prem: label="Endast lokal/hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 6fe8da3b-57b9-4a69-8602-a03993630b27
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 24%

---

# Konfigurera URL-behörigheter (lokalt){#url-permissions}



Standardlistan med URL:er som kan anropas av JavaScript-koder (arbetsflöden osv.) från dina instanser i Campaign Classic är begränsad. Dessa är URL:er som gör det möjligt för dina instanser att fungerar korrekt.

Som standard tillåts instanser endast att ansluta till interna URL:er. Det är dock möjligt att lägga till vissa externa URL:er i listan över auktoriserade URL:er, så att instansen kan ansluta till dem. Detta gör det möjligt för dig att ansluta instanserna i Campaign till externa system såsom SFTP-servrar eller webbplatser för att möjliggöra fil- och/eller dataöverföring.

>[!NOTE]
>
>Den här proceduren är begränsad till **lokala**-distributioner.
>
>Om du är en **värdbaserad**-kund och har åtkomst till [Campaign Control Panel](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=sv) kan du använda självbetjäningsgränssnittet för URL-behörigheter. [Läs mer](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/url-permissions.html?lang=sv)
>
>Andra **hybridkunder/värdkunder** måste kontakta Adobe supportteam för att kunna lägga till IP i tillåtelselista.
>

För **hybriddistributioner** och **lokala distributioner** måste administratören referera till en ny **urlPermission** i filen **serverConf.xml**.


Tre lägen för anslutningsskydd är tillgängliga:

* **Blockering**: Alla URL:er som inte tillhör tillåtelselista blockeras, med ett felmeddelande. Det här är standardläget efter en efteruppgradering.
* **Behörighet**: Alla URL:er som inte tillhör tillåtelselista tillåts.
* **Varning**: Alla URL:er som inte tillhör tillåtelselista tillåts, men JS-tolken genererar en varning så att administratören kan samla in dem. I det här läget läggs JST-310027-varningsmeddelanden till.

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

>[!IMPORTANT]
>
>Som standard används läget **Blockera** för nya implementeringar.
>
>Om en befintlig kund kommer från en migrering kan du tillfälligt använda läget **Varning**. Analysera utgående trafik innan URL-adresserna tillåts. När listan över tillåtna URL:er har definierats kan du lägga till URL:er till tillåtelselista och aktivera läget **Blockera**.

Mer information finns i följande avsnitt:

* [Dokumentation för kontrollpanelen](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=sv)
* [Värdmodeller](hosting-models.md)
* [Konfiguration av Campaign-server](configuring-campaign-server.md)
* [Konfigurationsfilsparametrar för kampanjserver](the-server-configuration-file.md)
* [Checklista för säkerhet och integritet](get-started-security-privacy.md)
