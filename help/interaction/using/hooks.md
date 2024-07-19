---
product: campaign
title: Hookar
description: Hookar
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: e1d7d7c2-61e7-40d6-a8ce-69bc976f8c73
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 1%

---

# Ändra standardmotorns beteende{#hooks}



Med kopplingar i interaktion kan du ändra **standardmotorbeteendet**.

Hokarna **[!UICONTROL Target loading]** och **[!UICONTROL Proposition post-processing]** är konfigurerade i Adobe Campaign i erbjudandeutrymmet:

![](assets/interaction_hooks_1.png)

Haken **[!UICONTROL Dynamic offer]** har konfigurerats med erbjudandevikten i Adobe Campaign:

![](assets/interaction_hooks_2.png)

## Inläsning av mål {#target-loading}

Med den här kroken kan du utöka kontaktens profil (som lästes in av en fråga som inte är installerad) med ytterligare data från ett externt system.

Data som samlas in måste infogas i anropsdatanoden (interaktionsnod). Integratorn måste ha utökat anropsdataramodellen i förväg för att definiera strukturen för insamlade data. Användaren kan komma åt dessa data på samma sätt som för vanliga samtalsdata (enligt reglerna för behörighet och personaliseringsnivå).

**Indataparametrar:**

* xmlInteraction (xml-typ): Interaktionsnod
* aTargetId (tabelltyp): målidentifierare
* sUuid230 (strängtyp): värde för den permanenta cookien uid230
* sNlid (strängtyp): värdet för den nlid-sessionscookien

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

## Föreslå efterbehandling {#proposition-post-processing-}

Med den här funktionen kan du kontrollera konsekvens och kompatibilitet för giltiga förslag i en viss interaktion. Här kan du också definiera en ny funktion för beräkning av poäng eller sannolikhet.

Exempel på användning av konsistensregler:

* Begränsa antalet offerter i samma samtal, länkat till samma produkt eller samma kategori.
* Presentera endast erbjudanden relaterade till en produkt i samma interaktion.

Efterbearbetningen utförs efter typologiregeltillämpningen och den stödberättigande förslagssorteringen, och före prioriteringssteget.

**Indataparametrar:**

* Förslag: tabell över giltiga förslag. Här är ett exempel på strukturen för ett element i den här tabellen

  ```
  { offer_id:1234,
    weight:2}
  ```

* dicOffer (xml-typ): ordlista med alla attribut för giltiga erbjudanden (erbjudandekod, kategori-ID, kategorins fullständiga namn, startdatum, slutdatum, etikett, internt namn, erbjudande-ID, ytterligare erbjudandefält). Till exempel

  ```
  { "1242": <offer category-id="61242" categoryFullName="/FULL/PATH/TO/CATEGORY/" code="CODE" endDate="" id="62473" label="LABEL" name="OFR38_OE4" product-id="43" startDate=""/>,
    "1243": ...}
  ```

* xmlTarget (xml-typ): profildatanod
* xmlInteraction (xml-typ): anropsdatanod
* iPropNumber (heltalstyp): antal förväntade erbjudanden

**Returparametrar:**

* lista över ändrade förslag (krokens första parameter)
* modifierad interaktionsnod

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

I förväg ska integratören utöka förslagsschemat **PropositionRcp** med ytterligare information om produkten. Om du vill ange var dessa data ska lagras finns en **[!UICONTROL Proposition being processed]**-länk på fliken **[!UICONTROL Storage]** i utrymmet

![](assets/interaction_hooks_3.png)

**Indataparametrar:**

* xmlOffer (xml-typ): offer (erbjudandekod, kategori-ID, kategorins fullständiga namn, startdatum, slutdatum, etikett, internt namn, erbjudandeID, ytterligare erbjudandefält)
* Vikt: sammanhangsberoende vikt (dubbeltyp)
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
