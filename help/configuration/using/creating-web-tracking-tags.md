---
product: campaign
title: Skapa webbspårningstaggar
description: Lär dig hur du skapar webbspårningstaggar
feature: Application Settings
role: Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
exl-id: 160df6e1-43e5-4eb9-ad2f-5db444e314ea
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 2%

---

# Skapa webbspårningstaggar{#creating-web-tracking-tags}

Alla sidor på webbplatsen som du vill spåra måste refereras till på din Adobe Campaign-plattform. Den här referensen kan utföras på två sätt:

1. Manuell definition av URL:er som ska spåras.
1. Skapa URL:er som ska spåras direkt.

## Definiera de URL:er som ska spåras i programmet {#defining-the-urls-to-be-tracked-in-the-application}

Med den här metoden kan du manuellt definiera sidorna som ska spåras och sedan generera ett exempel på den associerade webbspårningstaggen. Den här åtgärden definieras i **[!UICONTROL Campaign execution>Resources>Web tracking tags]** klientkonsolens nod.

![](assets/d_ncs_integration_webtracking_screen.png)

Så här genererar du den HTML-kod som ska infogas på sidan:

* Ange taggens etikett: den kommer att visas i spårningsloggarna,
* Ange käll-URL: det här fältet används i informationssyfte och du kan ange den spårade sidan (valfritt),
* Ange vid behov en giltighetsperiod,
* Klicka **[!UICONTROL Generate]** HTML-kod.

Kopiera sedan den genererade koden och klistra in den på sidan som ska spåras.

## Skapa URL:er som ska spåras direkt {#on-the-fly-creation-of-urls-to-be-tracked}

Du kan skapa URL:er för webbspårning direkt genom att lägga till information till värdet för **tagid** parameter:

* Typ av spårad sida: &#39;w&#39; för WEB eller &#39;t&#39; för TRANSACTION.
* Det interna namnet på mappen där URL:en måste skapas.

Dessa två informationsdelar måste sammanfogas med den spårade sidans identifierare genom att tecknet | läggs till:

```
tagid=<identifier>|<type>|<foldername>
```

>[!IMPORTANT]
>
>Kom ihåg att koda värdet för **tagid** när den används som en URL-parameter.

**Exempel**: Skapande av en webbspårnings-URL av transaktionstyp.

**http://myserver.adobe.com/r/a?tagid=home%7Ct%7CMyFolder**
