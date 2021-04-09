---
solution: Campaign Classic
product: campaign
title: Konfigurera URL-behörigheter
description: Lär dig hur du konfigurerar URL-behörigheter
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 67dda58f-97d1-4df5-9648-5f8a1453b814,6fe8da3b-57b9-4a69-8602-a03993630b27
translation-type: tm+mt
source-git-commit: 5d8d9e6ba41f94179bbf5f6d41f86267381b9b93
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 23%

---

# Konfigurera URL-behörigheter (lokalt){#url-permissions}

Standardlistan med URL:er som kan anropas av JavaScript-koder (arbetsflöden osv.) från dina instanser i Campaign Classic är begränsad. Dessa är URL:er som gör det möjligt för dina instanser att fungerar korrekt.

Som standard tillåts instanser endast att ansluta till interna URL:er. Det är dock möjligt att lägga till vissa externa URL:er i listan över auktoriserade URL:er, så att instansen kan ansluta till dem. Detta gör det möjligt för dig att ansluta instanserna i Campaign till externa system såsom SFTP-servrar eller webbplatser för att möjliggöra fil- och/eller dataöverföring.

>[!NOTE]
>
>Den här proceduren är begränsad till **lokala**-distributioner.
>
>Om du är **värd**-kund och har åtkomst till [Campaign Control Panel](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html) kan du använda självbetjäningsgränssnittet för URL-behörigheter. [Läs mer](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/url-permissions.html)
>
>Andra **hybrid-/hosted**-kunder måste kontakta Adobe supportteam för att lägga till IP i tillåtelselista.


För **hybriddistributioner** och **lokala distributioner** måste administratören referera till en ny **urlPermission** i filen **serverConf.xml**.


Tre lägen för anslutningsskydd är tillgängliga:

* **Blockering**: Alla URL:er som inte tillhör tillåtelselista blockeras, med ett felmeddelande. Det här är standardläget efter en efteruppgradering.
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
>Som standard används läget **Blockera** för nya implementeringar.
>
>Om en befintlig kund kommer från en migrering kan du tillfälligt använda läget **Varning**. Analysera utgående trafik innan URL-adresserna tillåts. När listan över tillåtna URL:er har definierats kan du lägga till URL:er till tillåtelselista och aktivera läget **Blockera**.

Mer information finns i följande avsnitt:

* [Dokumentation för kontrollpanelen](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html)
* [Värdbaserade modeller](hosting-models.md)
* [Konfiguration av kampanjservern](configuring-campaign-server.md)
* [Konfigurationsfilsparametrar för kampanjserver](the-server-configuration-file.md)
* [Checklista för säkerhet och integritet](get-started-security-privacy.md)
