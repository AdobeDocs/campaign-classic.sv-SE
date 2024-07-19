---
product: campaign
title: "Användningsfall: välj dirigerade adresser på villkor"
description: "Användningsfall: välj dirigerade adresser på villkor"
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Seed Address
exl-id: 091648b8-bf2d-4595-8be3-287f1ac48edd
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '851'
ht-degree: 2%

---

# Användningsfall: välj dirigerade adresser enligt villkor{#use-case-selecting-seed-addresses-on-criteria}


I samband med en leverans eller en kampanj kan du med länken **[!UICONTROL Edit the dynamic condition...]** välja dirigerade adresser baserat på specifika urvalskriterier.

I det här fallet vill webbplatsen **Mitt onlinebibliotek** anpassa sina nyhetsbrev efter kundernas litterära smak.

Tillsammans med inköpsavdelningen har användaren som ansvarar för leveranser skapat ett nyhetsbrev för prenumeranter som har köpt polisnoveler.

För att kunna dela slutresultatet av samarbetet med dem bestämmer sig leveranschefen för att lägga till sina kollegor från inköpsavdelningen till leveransen som dirigeringsadresser. Om du använder ett dynamiskt villkor kan du spara tid när du konfigurerar och uppdaterar adresser.

Om du vill använda det dynamiska villkoret måste du ha:

* en leverans som är klar att skickas,
* dirigerade adresser som har ett gemensamt värde. Värdet kan vara ett fält som redan finns i Adobe Campaign. I det här exemplet delar dirigeringsadresserna värdet&quot;Inköp&quot; i fältet&quot;Avdelning&quot;, som inte finns i programmet som standard.

## Steg 1 - Skapa en leverans {#step-1---creating-a-delivery}

Stegen för att skapa en leverans beskrivs i avsnittet [Skapa en e-postleverans](creating-an-email-delivery.md).

I det här exemplet har leveranshanteraren skapat nyhetsbrevet och valt mottagare.

![](assets/dlv_seeds_usecase_01.png)

## Steg 2 - Skapa ett gemensamt värde {#step-2---creating-a-common-value}

Om du vill skapa ett gemensamt värde som det i vårt exempel (Inköpsavdelning) måste du först utöka **dataschemat** för dina dirigerade adresser och redigera det associerade indataformuläret.

### Utöka dataschemat {#extending-the-data-schema}

Mer information om schematillägg finns i [det här avsnittet](../../configuration/using/data-schemas.md).

1. Klicka på ikonen **[!UICONTROL New]** i noden **[!UICONTROL Administration > Configuration > Data schemas]**.
1. I fönstret **[!UICONTROL Creation of a data schema]** väljer du alternativet **[!UICONTROL Extension of a schema]** och klickar på **[!UICONTROL Next]**.

   ![](assets/dlv_seeds_usecase_09.png)

1. Välj **[!UICONTROL Seed addresses]**-källschemat, ange **doc** som **[!UICONTROL Namespace]** och klicka på **[!UICONTROL Ok]**.

   ![](assets/dlv_seeds_usecase_10.png)

1. Klicka på **[!UICONTROL Save]**.
1. I schemaredigeringsfönstret kopierar du raderna nedan och klistrar in dem i det område som visas på skärmbilden.

   ```
     <element name="common">
       <element label="Recipient" name="custom_nms_recipient">
         <attribute label="Department" length="80" name="workField" template="nms:recipient:recipient/@company"
                    type="string" userEnum="workField"/>
       </element>
     </element>
   ```

   ![](assets/dlv_seeds_usecase_20.png)

   Kopiera sedan följande rader och klistra in dem under elementet **[!UICONTROL Seed to insert in the export files]**.

   ```
       <element aggregate="doc:seedMember:common">
     </element>
   ```

   ![](assets/dlv_seeds_usecase_29.png)

   I det här fallet anger du att en ny uppräkning med namnet **[!UICONTROL Department]** har skapats i dirigerad adresstabellen, och den är baserad på standarduppräkningsmallen för **[!UICONTROL @company]** (med namnet **Företag** i startadressformuläret).

1. Klicka på **[!UICONTROL Save]**.
1. Välj alternativet **[!UICONTROL Update database structure]** på menyn **[!UICONTROL Tools > Advanced]**.

   ![](assets/dlv_seeds_usecase_12.png)

1. När uppdateringsguiden visas klickar du på knappen **[!UICONTROL Next]** för att öppna fönstret Redigera tabeller: ändringar som görs i schemat för dirigerade adressdata kräver en strukturuppdatering.

   ![](assets/dlv_seeds_usecase_13.png)

1. Följ guiden tills du kommer till sidan för att köra uppdateringen. Klicka på knappen **[!UICONTROL Start]**.

   ![](assets/dlv_seeds_usecase_14.png)

   När uppdateringen är klar kan du stänga guiden.

1. Koppla från och återanslut sedan till Adobe Campaign. Ändringarna i schemat för startadressdata gäller nu. För att de ska kunna visas från startadressskärmen måste du uppdatera den associerade **[!UICONTROL Input form]**. Se avsnittet [Uppdatera indataformuläret](#updating-the-input-form).

#### Utöka dataschemat från en länkad tabell {#extending-the-data-schema-from-a-linked-table}

Startadressernas dataschema kan använda värden från en tabell som är länkad till mottagardataschemat - mottagare (nms).

Användaren vill till exempel integrera **[!UICONTROL Internet Extension]** som finns i tabellen **[!UICONTROL Country]** som är länkad till mottagarschemat.

![](assets/dlv_seeds_usecase_06.png)

De måste därför utöka dataschemat för dirigerade adresser så som beskrivs i avsnittet. Däremot är kodraderna som ska integreras vid **steg 4** följande:

```
<element name="country">
      <attribute label="Internet Extension" length="2" name="iana" type="string"/>
      <attribute label="Country ISO" length="2" name="countryIsoA2" type="string"/>
    </element>
```

![](assets/dlv_seeds_usecase_11.png)

De anger

* som användaren vill skapa ett nytt element med namnet **[!UICONTROL Internet Extension]**,
* att elementet kommer från tabellen **[!UICONTROL Country]**.

>[!CAUTION]
>
>I den länkade tabellens namn måste du ange **xpath-dst** för den länkade tabellen.
>
>Detta finns i elementet **[!UICONTROL Country]** i mottagartabellen.

![](assets/dlv_seeds_usecase_07.png)

Användaren kan sedan följa från **steg 5** i avsnittet och uppdatera **[!UICONTROL Input form]** för startadresserna.

Se avsnittet [Uppdatera indataformuläret](#updating-the-input-form).

#### Uppdatera indataformuläret {#updating-the-input-form}

1. I noden **[!UICONTROL Administration > Configuration > Input forms]** hittar du indataformuläret för dirigerade adresser.

   ![](assets/dlv_seeds_usecase_19.png)

1. Redigera formuläret och infoga följande rad i behållaren **[!UICONTROL Recipient]**.

   ```
   <input xpath="@workField"/>
   ```

   ![](assets/dlv_seeds_usecase_21.png)

1. Spara ändringarna.
1. Öppna en startadress. Fältet **[!UICONTROL Department]** visas i tabellen **[!UICONTROL Recipient]**.

   ![](assets/dlv_seeds_usecase_22.png)

1. Redigera de dirigerade adresser som du vill använda för leveransen och ange **Inköp** som värde i fältet **[!UICONTROL Department]**.

## Steg 3 - Definiera villkoret {#step-3---defining-the-condition}

Nu kan du ange det dynamiska villkoret för startadresserna för leveransen. Så här gör du:

1. Öppna en leverans.

   ![](assets/dlv_seeds_usecase_01.png)

1. Klicka på länken **[!UICONTROL To]** och sedan på fliken **[!UICONTROL Seed addresses]** för att komma åt länken **[!UICONTROL Edit the dynamic condition...]**.

   ![](assets/dlv_seeds_usecase_02.png)

1. Välj det uttryck som gör att du kan välja vilka dirigerade adresser du vill använda. Här väljer användaren uttrycket **[!UICONTROL Department (@workField)]**.

   ![](assets/dlv_seeds_usecase_03.png)

1. Välj det värde du vill ha. I det här exemplet väljer användaren avdelningen **Inköp** i den nedrullningsbara listan med värden.

   ![](assets/dlv_seeds_usecase_17.png)

   >[!NOTE]
   >
   >Schematillägget som skapades tidigare kommer från schemat **mottagare**. Värdena som visas på skärmen ovan kommer från en uppräkning av schemat **mottagare**.

1. Klicka på **[!UICONTROL Ok]**.

   Frågan visas i fönstret **[!UICONTROL Select target]**.

   ![](assets/dlv_seeds_usecase_04.png)

1. Klicka på **[!UICONTROL Ok]** för att godkänna frågan.
1. Analysera leveransen och klicka sedan på fliken **[!UICONTROL Delivery]** för att komma åt leveransloggarna.

   Startadresserna för inköpsavdelningen visas som väntande leveranser, precis som för mottagarna eller andra startadresser.

   ![](assets/dlv_seeds_usecase_05.png)

1. Klicka på knappen **[!UICONTROL Send]** för att starta leveransen.

   Medlemmarna på inköpsavdelningen utgör en del av dina dirigerade adresser som får leveransen i sin inkorg.

   ![](assets/dlv_seeds_usecase_18.png)
