---
title: IMS-felsökning
seo-title: IMS-felsökning
description: IMS-felsökning
seo-description: null
page-status-flag: never-activated
uuid: 5db95afc-8cbf-4ec3-b58f-504486fe4a40
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
discoiquuid: e31db11a-ad8e-4fd0-bab7-0df1079231c9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 54cb4143fc534aa436c4b8b28e031e87a2a02e40
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---


# IMS-felsökning{#ims-troubleshooting}

Följande felsökningstips hjälper **lokala** kunder att lösa de vanligaste problemen som uppstår när IMS-integreringen används. Kontakta Adobe om du har **värdtjänster** .

**Externt konto**

Det ska bara finnas **ett** externt konto med följande inställningar:

* **Internt namn**: Adobe_Marketing_Cloud
* **Typ**: Adobe Marketing Cloud

Ta bort alla dubbletter av externa konton som har samma inställningar.

**Produktsammanhang**

Om det externa kontot har ett **produktkontextfält** kontrollerar du att dess värde är inställt på: **dma_campaign_classic**

Se till att produktsammanhanget är detsamma för Campaign och Experience Cloud.

Om till exempel **produktkontexten** inte visas ska standardproduktkontexten vara **dma_campaign** både i Campaign och Experience Cloud. Om **produktkontextfältet** visas ska standardproduktsammanhanget vara **dma_campaign_classic** både i Campaign och Experience Cloud.

**[!UICONTROL IMS Server URL]**

I det externa Campaign **Adobe Marketing Cloud** -kontot kontrollerar du att **[!UICONTROL IMS Server URL]** är antingen [adobeid-na1.services.adobe.com](https://adobeid-na1.services.adobe.com/) eller [ims-na1.adobelogin.com](http://ims-na1.adobelogin.com/). Se till att både fas- och produktionsinstanser pekar på samma IMS-produktionsslutpunkt.

**Associationsmask**

* Kontrollera att användaren som försöker logga in är en del av en operatörsgrupp på Enterprise Dashboard.
* Kontrollera att **[!UICONTROL Association Mask]** det är ett prefix till användarens användargruppnamn i Enterprise Dashboard.
* Se till att det inte finns några blanksteg eller stavfel.
* Kontrollera att namnen på operatörsgrupperna i Campaign inte har ändrats och att följande syntax följs:

```
<Association Mask> + <Operator Group Name in Campaign> = Complete name of the operator group in Enterprise Dashboard
```

**Omfång**

Omfattningar som definieras i det externa Campaign-kontot måste vara en delmängd av de som tillhandahålls av IMS.

**Återanrops-URL**

URL:en **för** återanrop ska läggas till i listan Tillåt och börja med https://. Kontrollera att **återanrops-URL** är länkad till motsvarande instans. Produktionsinstansen bör till exempel omdirigeras till produktions-URL:en.

**Klient-ID och hemlighet**

Klient-ID:t matchar mellan det externa Campaign-kontot och det som tillhandahålls av IMS.

Kontrollera att den angivna klienthemligheten är korrekt.

**Starta om servern**

Starta om servern om några ändringar görs i inställningarna ovan i det externa Campaign-kontot

**Vanliga typer av fel och möjliga lösningar**

* Användaren omdirigeras till adobe.com-sidan:

   Det är ett problem med **[!UICONTROL Callback URL]**. Kontrollera konfigurationen genom att gå till föregående steg **[!UICONTROL Callback URL]** .

* Meddelandet&quot;Inloggningen har ingen rättighet som matchar uttrycket&quot;:

   Läs föregående steg för att kontrollera konfigurationen av **[!UICONTROL Association Mask]** operatorgrupperna och operatorgrupperna.

* Användaren kan inte komma åt Adobe IDS inloggningssida:

   Kontrollera scopekonfigurationen i föregående steg.

