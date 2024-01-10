---
product: campaign
title: IMS-felsökning
description: IMS-felsökning
feature: Configuration
badge-v7: label="v7" type="Informative" tooltip="Gäller Campaign Classic v7"
badge-v7-prem: label="lokal och hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: 1ce89c3a-1fe6-4ed6-9547-2eb9713a0ec3
source-git-commit: 49271e291953483ee14709b26ec053217a336718
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 1%

---

# IMS-felsökning{#ims-troubleshooting}


Följande felsökningstips är till hjälp **lokal** och **hybrid** -kunder löser de vanligaste problemen som uppstår när IMS-integreringen används. För **värdbaserad** kontakta Adobe.

**Externt konto**

Det ska bara finnas **en** externt konto med följande inställningar:

* **Internt namn**: Adobe_Marketing_Cloud
* **Typ**: ADOBE MARKETING CLOUD

Ta bort alla dubbletter av externa konton som har samma inställningar.

**Produktsammanhang**

Om det externa kontot har en **Produktsammanhang** kontrollerar du att värdet är: **dma_campaign_classic**

Se till att produktsammanhanget är detsamma för Campaign och Experience Cloud.

Om **Produktsammanhang** visas inte, standardproduktkontexten ska **dma_campaign** i både Campaign och Experience Cloud. Om **Produktsammanhang** visas ska standardproduktsammanhanget vara **dma_campaign_classic** i både Campaign och Experience Cloud.

**[!UICONTROL IMS Server URL]**

I Campaign **Adobe Marketing Cloud** externt konto, kontrollera att **[!UICONTROL IMS Server URL]** är antingen `adobeid-na1.services.adobe.com` eller `ims-na1.adobelogin.com`. Se till att både fas- och produktionsinstanser pekar på samma IMS-produktionsslutpunkt.

**Associationsmask**

* Kontrollera att användaren som försöker logga in är en del av en operatörsgrupp på Enterprise Dashboard.
* Kontrollera att **[!UICONTROL Association Mask]** är ett prefix för användarens användargruppnamn i Enterprise Dashboard.
* Se till att det inte finns några blanksteg eller stavfel.
* Kontrollera att namnen på operatörsgrupperna i Campaign inte har ändrats och att följande syntax följs:

```
<Association Mask> + <Operator Group Name in Campaign> = Complete name of the operator group in Enterprise Dashboard
```

**Omfång**

Omfattningar som definieras i det externa Campaign-kontot måste vara en delmängd av de som tillhandahålls av IMS.

**Återanrops-URL**

The **Återanrops-URL** ska läggas till tillåtelselista och börja med&quot;https://&quot;. Kontrollera att **Återanrops-URL** är länkad till motsvarande instans. Produktionsinstansen bör till exempel omdirigeras till produktions-URL:en.

**Klient-ID och hemlighet**

Klient-ID:t matchar mellan det externa Campaign-kontot och det som tillhandahålls av IMS.

Kontrollera att den angivna klienthemligheten är korrekt.

**Starta om servern**

Starta om servern om några ändringar görs i inställningarna ovan i det externa Campaign-kontot

**Vanliga typer av fel och möjliga lösningar**

* Användaren omdirigeras till adobe.com:

  Ett problem har uppstått med **[!UICONTROL Callback URL]**. Gå till föregående steg för att kontrollera **[!UICONTROL Callback URL]** konfiguration.

* Meddelandet&quot;Inloggningen har ingen rättighet som matchar uttrycket&quot;:

  Gå till föregående steg för att kontrollera **[!UICONTROL Association Mask]** och operatorgruppskonfiguration.

* Användaren har inte åtkomst till Adobe ID inloggningssida:

  Kontrollera scopekonfigurationen i föregående steg.
