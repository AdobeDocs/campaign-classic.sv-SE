---
product: campaign
title: IMS-felsökning
description: IMS-felsökning
feature: Configuration
badge-v7-prem: label="Endast lokal/hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: 1ce89c3a-1fe6-4ed6-9547-2eb9713a0ec3
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 1%

---

# IMS-felsökning{#ims-troubleshooting}


Följande felsökningstips hjälper **lokala** - och **hybridkunder** att lösa de vanligaste problemen som uppstår när IMS-integreringen används. Kontakta Adobe för **värdbaserade** kunder.

**Externt konto**

Det får bara finnas **ett** externt konto med följande inställningar:

* **Internt namn**: Adobe_Marketing_Cloud
* **Typ**: Adobe Marketing Cloud

Ta bort alla dubbletter av externa konton som har samma inställningar.

**Produktkontext**

Om det externa kontot har ett **produktkontextfält** kontrollerar du att värdet är inställt på: **dma_campaign_classic**

Se till att produktsammanhanget är detsamma för Campaign och Experience Cloud.

Om till exempel **produktkontexten** inte visas ska standardproduktkontexten vara **dma_campaign** i både Campaign och Experience Cloud. Om fältet **Produktkontext** visas ska standardproduktkontexten vara **dma_campaign_classic** i både Campaign och Experience Cloud.

**[!UICONTROL IMS Server URL]**

Kontrollera att **[!UICONTROL IMS Server URL]** är antingen `adobeid-na1.services.adobe.com` eller `ims-na1.adobelogin.com` i det externa kontot för Campaign **Adobe Marketing Cloud**. Se till att både fas- och produktionsinstanser pekar på samma IMS-produktionsslutpunkt.

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

**Återanrops-URL:en** ska läggas till i tillåtelselista och börja med https://. Kontrollera att URL:en för **återanrop** är länkad till motsvarande instans. Produktionsinstansen bör till exempel omdirigeras till produktions-URL:en.

**Klient-ID och hemlighet**

Klient-ID:t matchar mellan det externa Campaign-kontot och det som tillhandahålls av IMS.

Kontrollera att den angivna klienthemligheten är korrekt.

**Starta om servern**

Starta om servern om några ändringar görs i inställningarna ovan i det externa Campaign-kontot

**Vanliga typer av fel och möjliga lösningar**

* Användaren omdirigeras till adobe.com:

  Det har uppstått ett problem med **[!UICONTROL Callback URL]**. Kontrollera konfigurationen av **[!UICONTROL Callback URL]** genom att gå till föregående steg.

* Meddelandet&quot;Inloggningen har ingen rättighet som matchar uttrycket&quot;:

  Titta på föregående steg för att kontrollera konfigurationen för **[!UICONTROL Association Mask]**- och operatorgrupperna.

* Användaren har inte åtkomst till Adobe ID inloggningssida:

  Kontrollera scopekonfigurationen i föregående steg.
