---
title: Skapa webbspårningstaggar
seo-title: Skapa webbspårningstaggar
description: Skapa webbspårningstaggar
seo-description: null
page-status-flag: never-activated
uuid: c5599bdd-e6b8-4db4-b0ca-aaee2adc1919
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 647ca037-4efb-4524-9642-11056d096aea
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# Skapa webbspårningstaggar{#creating-web-tracking-tags}

Varje sida på webbplatsen som du vill spåra måste refereras till i din Adobe Campaign-plattform. Den här referensen kan utföras på två sätt:

1. Manuell definition av URL:er som ska spåras.
1. Skapa URL:er som ska spåras direkt.

## Definiera de URL:er som ska spåras i programmet {#defining-the-urls-to-be-tracked-in-the-application}

Med den här metoden kan du manuellt definiera sidorna som ska spåras och sedan generera ett exempel på den associerade webbspårningstaggen. Den här åtgärden definieras i klientkonsolens **[!UICONTROL Campaign execution>Resources>Web tracking tags]** nod.

![](assets/d_ncs_integration_webtracking_screen.png)

Så här genererar du den HTML-kod som ska infogas på sidan:

* Ange taggens etikett: den kommer att visas i spårningsloggarna,
* Ange käll-URL: detta fält är avsett som information och gör att du kan ange den spårade sidan (valfritt),
* Ange vid behov en giltighetsperiod,
* Klicka på **[!UICONTROL Generate]** HTML-kod.

Kopiera sedan den genererade koden och klistra in den på sidan som ska spåras.

## Skapa URL:er som ska spåras direkt {#on-the-fly-creation-of-urls-to-be-tracked}

Du kan skapa URL:er för webbspårning direkt genom att lägga till information till värdet för **tagid** -parametern:

* Typ av spårad sida: &#39;w&#39; för WEB eller &#39;t&#39; för TRANSACTION,
* Det interna namnet på mappen där URL:en måste skapas.

Dessa två informationsdelar måste sammanfogas med den spårade sidans identifierare genom att tecknet | läggs till:

```
tagid=<identifier>|<type>|<foldername>
```

>[!IMPORTANT]
>
>Kom ihåg att koda värdet för **tagid** -parametern när den används som en URL-parameter.

**Exempel**: skapa en webbspårnings-URL av transaktionstyp.

**http://myserver.adobe.com/r/a?tagid=home%7Ct%7CMyFolder**
