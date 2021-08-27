---
product: campaign
title: IMS-felsökning
description: IMS-felsökning
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: 1ce89c3a-1fe6-4ed6-9547-2eb9713a0ec3
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 1%

---

# IMS-felsökning{#ims-troubleshooting}

![](../../assets/common.svg)

Följande felsökningstips hjälper **lokala**-kunder att lösa de vanligaste problemen som uppstår när IMS-integreringen används. Kontakta Adobe för **värdbaserade**-kunder.

**Externt konto**

Det får bara finnas ett **externt**-konto med följande inställningar:

* **Internt namn**: Adobe_Marketing_Cloud
* **Typ**: Adobe Marketing Cloud

Ta bort alla dubbletter av externa konton som har samma inställningar.

**Produktsammanhang**

Om det externa kontot har ett **produktkontextfält**-fält kontrollerar du att dess värde är inställt på: **dma_campaign_classic**

Se till att produktsammanhanget är detsamma för Campaign och Experience Cloud.

Om till exempel **produktkontexten** inte visas, ska standardproduktkontexten vara **dma_campaign** i både Campaign och Experience Cloud. Om fältet **Product Context** visas ska standardproduktsammanhanget vara **dma_campaign_classic** i både Campaign och Experience Cloud.

**[!UICONTROL IMS Server URL]**

I det externa kontot för Campaign **Adobe Marketing Cloud** kontrollerar du att **[!UICONTROL IMS Server URL]** antingen är [adobeid-na1.services.adobe.com](https://adobeid-na1.services.adobe.com/) eller [ims-na1.adobelogin.com](http://ims-na1.adobelogin.com/). Se till att både fas- och produktionsinstanser pekar på samma IMS-produktionsslutpunkt.

**Associationsmask**

* Kontrollera att användaren som försöker logga in är en del av en operatörsgrupp på Enterprise Dashboard.
* Kontrollera att **[!UICONTROL Association Mask]** är ett prefix till användarens användargruppnamn i Enterprise Dashboard.
* Se till att det inte finns några blanksteg eller stavfel.
* Kontrollera att namnen på operatörsgrupperna i Campaign inte har ändrats och att följande syntax följs:

```
<Association Mask> + <Operator Group Name in Campaign> = Complete name of the operator group in Enterprise Dashboard
```

**Omfång**

Omfattningar som definieras i det externa Campaign-kontot måste vara en delmängd av de som tillhandahålls av IMS.

**Återanrops-URL**

**Återanrops-URL** ska läggas till tillåtelselista och börja med &quot;https://&quot;. Kontrollera att **Återanrops-URL** är länkad till motsvarande instans. Produktionsinstansen bör till exempel omdirigeras till produktions-URL:en.

**Klient-ID och hemlighet**

Klient-ID:t matchar mellan det externa Campaign-kontot och det som tillhandahålls av IMS.

Kontrollera att den angivna klienthemligheten är korrekt.

**Starta om servern**

Starta om servern om några ändringar görs i inställningarna ovan i det externa Campaign-kontot

**Vanliga typer av fel och möjliga lösningar**

* Användaren omdirigeras till adobe.com-sidan:

   Det har uppstått ett problem med **[!UICONTROL Callback URL]**. Kontrollera **[!UICONTROL Callback URL]**-konfigurationen genom att gå till föregående steg.

* Meddelandet&quot;Inloggningen har ingen rättighet som matchar uttrycket&quot;:

   Se föregående steg för att kontrollera konfigurationen för **[!UICONTROL Association Mask]**- och operatorgrupperna.

* Användaren har inte åtkomst till Adobe ID inloggningssida:

   Kontrollera scopekonfigurationen i föregående steg.
