---
product: campaign
title: Hookar
description: Hookar
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: e1d7d7c2-61e7-40d6-a8ce-69bc976f8c73
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 1%

---

# Hookar{#hooks}

Med kopplingar i interaktion kan du ändra **standardmotorbeteendet**.

Hakarna **[!UICONTROL Target loading]** och **[!UICONTROL Proposition post-processing]** är konfigurerade i Adobe Campaign i erbjudandeutrymmet:

![](assets/interaction_hooks_1.png)

Haken **[!UICONTROL Dynamic offer]** är konfigurerad med erbjudandevikten i Adobe Campaign:

![](assets/interaction_hooks_2.png)

## Inläsning av mål {#target-loading}

Med den här kroken kan du utöka kontaktens profil (som lästes in av en fråga som inte är installerad) med ytterligare data från ett externt system.

Data som samlas in måste infogas i anropsdatanoden (interaktionsnod). Integratorn måste ha utökat anropsdataramodellen i förväg för att definiera strukturen för insamlade data. Användaren kan komma åt dessa data på samma sätt som för vanliga samtalsdata (enligt reglerna för behörighet och personaliseringsnivå).

**Indataparametrar:**

* xmlInteraction (xml-typ): Interaktionsnod
* aTargetId (registertyp): målidentifierare
* sUuid230 (strängtyp): värdet för den permanenta cookien uid230
* Nlid (strängtyp): värdet på den ogiltiga sessionskakan

**Returparametrar:**

* anrikad interaktionsnod (den första parametern i den här kroken)

>[!NOTE]
>
>Parametern **xmlInteraction** innehåller både anropsdata och profilen för kontakten som lästes in av frågan som inte finns i kartongen.

**Exempel:**

```
// Call an external system to get additional data for the target
  var additionalData  = getUrl("https://EXTERNAL_SYSTEM?target=" + encodeURIComponent(aTargetId.join("|")));
  // Enrich the context with this data
  interaction.@additionalData = additionalData;
```

## Efterbearbetning av offert {#proposition-post-processing-}

Med den här funktionen kan du kontrollera konsekvens och kompatibilitet för giltiga förslag i en viss interaktion. Här kan du också definiera en ny funktion för beräkning av poäng eller sannolikhet.

Exempel på användning av konsistensregler:

* Begränsa antalet offerter i samma samtal, länkat till samma produkt eller samma kategori.
* Presentera endast erbjudanden relaterade till en produkt i samma interaktion.

Efterbearbetningen utförs efter typologiregeltillämpningen och den stödberättigande förslagssorteringen, och före prioriteringssteget.

**Indataparametrar:**

* Föreslå: Tabell över godtagbara förslag. Här är ett exempel på strukturen för ett element i den här tabellen

   ```
   { offer_id:1234,
     weight:2}
   ```

* dicOffer (xml-typ): ordlista över alla attribut för berättigade erbjudanden (erbjudandekod, kategori-ID, kategorins fullständiga namn, startdatum, slutdatum, etikett, internt namn, erbjudandeID, ytterligare erbjudandefält). Exempel

   ```
   { "1242": <offer category-id="61242" categoryFullName="/FULL/PATH/TO/CATEGORY/" code="CODE" endDate="" id="62473" label="LABEL" name="OFR38_OE4" product-id="43" startDate=""/>,
     "1243": ...}
   ```

* xmlTarget (xml-typ): profildatanod
* xmlInteraction (xml-typ): anropsdatanod
* iPropNumber (heltalstyp): antal förväntade erbjudanden

**Returparametrar:**

* lista över ändrade förslag (krokens första parameter)
* Nod för ändrad interaktion

**Exempel:**

```
var aReturnedProps = [];

if( aProposition.length > 0 )
{
  var iReturnedProps = 0;
  for( var iPropIdx = 0; iPropIdx < aProposition.length && iReturnedProps < iPropNumber; iPropIdx ++ )
  {
    // Check a consistency rule for instance
    if( true )
    {
      aReturnedProps.push(aProposition[iPropIdx]);
      iReturnedProps++;
    }
  }
}

return aReturnedProps;
```

## Dynamiskt erbjudande {#dynamic-offer}

Med den här funktionen kan du ringa ett samtal till en extern motor för att välja en lista över produkter som är kopplade till ett erbjudande. Det konfigureras i erbjudandet efter berättiganderegler och före typologiregelprogrammet.

I förväg ska integratören utöka schemat **PropositionRcp** med ytterligare information om produkten. För att ange var dessa data ska lagras finns en **[!UICONTROL Proposition being processed]**-länk på fliken **[!UICONTROL Storage]** i utrymmet

![](assets/interaction_hooks_3.png)

**Indataparametrar:**

* xmlOffer (xml-typ): offer (erbjudandekod, kategori-ID, fullständigt namn för kategori, startdatum, slutdatum, etikett, internt namn, erbjudandeid, extra erbjudandefält)
* Vikt: snabbvikt (dubbel text)
* xmlTarget (xml-typ): profildatanod
* xmlInteraction (xml-typ): anropsdatanod

**Returparametrar:**

En tabell med förslag som ska genereras returneras. Varje element i denna tabell består av följande information:

* erbjudandeidentifierare
* ytterligare produktdata (t.ex. produktkod)
* vikt

>[!NOTE]
>
>Systemet kontrollerar att erbjudandets ID är detsamma för parametrarna input och return.

**Exempel:**

```
var product = getUrl("https://EXTERNAL_SYSTEM?offerCode=" + encodeURIComponent(xmlOffer.@code));
if( product )
  return [{offer_id: parseInt(String(xmlOffer.@id)), weight: dWeight, productId: product}];
```
