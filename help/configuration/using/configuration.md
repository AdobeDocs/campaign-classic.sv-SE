---
product: campaign
title: Konfiguration
description: Konfiguration
exl-id: c7ae7240-0c12-4420-bbb3-4268c9ade3e7
source-git-commit: 8fa50d17a9ff36ccc310860ac93771590cfd76fd
workflow-type: tm+mt
source-wordcount: '1185'
ht-degree: 1%

---

# Konfigurera navigeringsträdet i Campaign Explorer{#configuration}

![](../../assets/v7-only.svg)

Som expertanvändare kan du lägga till mappar i utforskarträdet och anpassa det.

Läs mer om Campaign Explorer och navigeringshierarki [i det här avsnittet](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy).

De typer av mappar som används i navigeringslistan beskrivs i ett XML-dokument som lyder grammatiken i **xtk:navtree** schema.

XML-dokumentet är strukturerat på följande sätt:

```
<navtree name="name" namespace="name_space">
  <!-- Global commands -->
  <commands>
      ...
  </commands>
  
  <!-- Structured space for adding a folder -->
  <model name="<name>" label="<Label>">
    <!-- Folder type -->
    <nodeModel>
      ...
    </nodeModel>
<model name="<name>" label="<Sub model>">
      ...
    </model>
  </model> 
</navtree>
```

XML-dokumentet innehåller **`<navtree>`** rotelementet med **name** och **namespace** attribut för att ange dokumentnamnet och namnutrymmet. Namnet och namnutrymmet utgör dokumentets ID-nyckel.

Programmets globala kommandon deklareras i dokumentet från **`<commands>`** -element.

Deklarationen av filtyper är strukturerad i dokumentet med följande element: **`<model>`** och **`<nodemodel>`**.

## Globala kommandon {#global-commands}

Med ett globalt kommando kan du starta ett funktionsmakro. Den här åtgärden kan vara ett indataformulär eller ett SOAP-anrop.

Globala kommandon är tillgängliga från huvudsidan **[!UICONTROL Tools]** -menyn.

Kommandokonfigurationsstrukturen är följande:

```
<commands>
  <!-- Description of a command -->
  <command name="<name>" label="<label>" desc="<Description>" form="<form>" rights="<rights>">
    <soapCall name="<name>" service="<schema>">
      <param type="<type>" exprIn="<xpath>"/>  
        ...
    </soapCall>
    <enter>
      ...
    </enter>
  </command>
  <!-- Separator -->
  <command label="-" name="<name>"/>
  <!-- Command structure -->
  <command name="<name>" label="<Label>">
    <command...
  </command>
</commands>
```

Beskrivningen av ett globalt kommando anges i **`<command>`** element med följande egenskaper:

* **name**: kommandots interna namn: namnet måste anges och vara unikt
* **label**: kommandots etikett.
* **desc**: beskrivning som visas från huvudskärmens statusfält.
* **formulär**: formulär som ska startas: det värde som ska anges är inmatningsformulärets identifieringsnyckel (t.ex. &quot;cus:mottagare&quot;)
* **rättigheter**: lista med namngivna rättigheter (avgränsade med kommatecken) som tillåter åtkomst till det här kommandot. Listan över tillgängliga rättigheter finns på **[!UICONTROL Administration > Access management > Named rights]** mapp.
* **promptLabel**: visar en bekräftelseruta innan kommandot körs.

A **`<command>`** element kan innehålla **`<command>`** delelement. I det här fallet kan du med det överordnade elementet visa en undermeny som består av dessa underordnade element.

Kommandona visas i samma ordning som de deklareras i XML-dokumentet.

Med en kommandoavgränsare kan du visa ett avgränsningstecken mellan kommandona. Den identifieras av **&#39;-&#39;** i kommandoetiketten.

Den valfria närvaron av **`<soapcall>`** -taggen med indataparametrarna definierar anropet till en SOAP-metod som ska köras. Mer information om SOAP API finns i [Kampanj-JSAPI-dokumentation](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=sv).

Formulärkontexten kan uppdateras vid initiering från **`<enter>`** -tagg. Mer information om den här taggen finns i dokumentationen om indataformulär.

**Exempel**:

* Deklaration för ett globalt kommando som startar formuläret &quot;xtk:import&quot;:

   ```
   <command desc="Start the data import wizard" form="xtk:import" label="&amp;Data import..." name="import" rights="import,recipientImport"/>
   ```

   Ett kortkommando deklareras för&quot;I&quot;-tecknet om det finns **&amp;** i kommandoetiketten.

* Exempel på en undermeny med en avgränsare:

   ![](assets/d_ncs_integration_navigation_exemple1.png)

   ```
   <command label="Administration" name="admin">
     <command name="cmd1" label="Example 1" form="cus:example1"/>
     <command name="sep" label="-"/>
     <command name="cmd1" label="Example 2" form="cus:example2">
       <enter>
         <set xpath="@type" expr="1"/>
       </enter>
     </command>
   </command>
   ```

* Körning av en SOAP-metod:

   ```
   <command name="cmd3" label="Example 3" promptLabel="Do you really want to execute the command?">
     <soapCall name="Execute" service="xtk:sql"/>
   </command>
   ```

## Mapptyp {#folder-type}

Med en mapptyp kan du ge åtkomst till data i ett schema. Vyn som är associerad med mappen består av en lista och ett inmatningsformulär.

Konfigurationsstrukturen för mapptypen är följande:

```
<!-- Structured location to add the folder -->
<model name="name" label="Labelled">
  <!-- Type of folder -->
  <nodeModel name="<name>" label="<Labelled>" img="<image>">
    <view name="<name>" schema="<schema>" type="<listdet|list|form|editForm>">
      <columns>
        <node xpath="<field1>"/>
        ...
    </columns>
    </view> 
  </nodeModel>
  <model name="<name>" label="<Sous modèle>">
    ...
  </model>
</model>
```

Mapptypsdeklarationen måste anges under en **`<model>`** -element. Med det här elementet kan du definiera en hierarkisk organisation som visas från **[!UICONTROL Add new folder]** -menyn. A **`<model>`** elementet måste innehålla **`<nodemodel>`** element och andra **`<model>`** -element.

The **name** och **label** attribut fyller i elementets interna namn och etiketten som visas i **[!UICONTROL Add new folder]** -menyn.

The **`<nodemodel>`** -elementet innehåller en beskrivning av mapptypen med följande egenskaper:

* **name**: internt namn
* **label**: etikett som används i **[!UICONTROL Add new folder]** och som standardetikett när du infogar en mapp.
* **img**: standardbild vid mappinfogning.
* **hiddenCommands**: lista med kommandon (avgränsade med kommatecken) som ska maskeras. Möjliga värden: &quot;adbnew&quot;, &quot;adbsave&quot;, &quot;adbcancel&quot; och &quot;adbdup&quot;.
* **newFolderShortCuts**: lista med kortkommandon på modeller (**`<nodemodel>`** avgränsade med kommatecken) när du skapar mappar.
* **insertRight**, **editRight**, **deleteRight**: behörighet att infoga, redigera och ta bort mappar.

The **`<view>`** -element under **`<nodemodel>`** -elementet innehåller konfigurationen för listan som är associerad med vyn. Schemat för listan anges i **schema** attributet för **`<view>`** -element.

Om du vill redigera posterna i listan används indataformuläret med samma namn som listschemat implicit. The **type** på **`<view>`** -elementet påverkar hur formuläret visas. Möjliga värden är:

* **listdet**: visar formuläret längst ned i listan.
* **list**: visar listan ensam. Formuläret öppnas genom att man dubbelklickar eller via&quot;Öppna&quot; i menyn när man väljer listan.
* **formulär**: visar ett skrivskyddat formulär.
* **editForm**: visar ett formulär i redigeringsläge.

>[!NOTE]
>
>Namnet på indataformuläret kan överladdas genom att du anger **formulär** i **`<view>`** -element.

Standardkonfigurationen för listkolumnerna anges via **`<columns>`** -element. En kolumn deklareras på en **`<node>`** elementet som innehåller **xpath** attribut med fältet som ska refereras i schemat som dess värde.

**Exempel**: en mapptypdeklaration i schemat &quot;nms:receive&quot;.

```
<model label="Profiles and targets" name="nmsProfiles">
  <nodeModel deleteRight="folderDelete" editRight="folderEdit" folderLink="folder"
             img="nms:folder.png" insertRight="folderInsert" label="Recipients"
             name="nmsFolder">
    <view name="listdet" schema="nms:recipient" type="listdet">
      <columns>
        <node xpath="@firstName"/>
        <node xpath="@lastName"/>
        <node xpath="@email"/>
        <node xpath="@account"/>
      </columns>
    </view>
  </nodeModel>
  <nodeModel name="nmsGroup" label="Groups"...
</model>
```

Motsvarande inmatningsmeny för mappar:

![](assets/d_ncs_integration_navigation_exemple2.png)

Filtrering och sortering kan användas när listan läses in:

```
<view name="listdet" schema="nms:recipient" type="listdet">
  <columns>
    ...
  </columns>

  <orderBy>
    <node expr="@lastName" desc="true"/>
</orderBy>
  <sysFilter>
    <condition expr="@type = 1"/>
  </sysFilter>
</view>  
```

### Kortkommandon {#shortcut-commands}

Med ett kortkommando kan du starta en åtgärd när du väljer listan. Åtgärden kan vara ett indataformulär eller ett SOAP-anrop.

Kommandon är tillgängliga via **[!UICONTROL Action]** menyn för listan eller den tillhörande menyknappen.

Kommandokonfigurationsstrukturen är följande:

```
<nodeModel...
  ...
  <command name="<name>" label="<label>" desc="<Description>" form="<form>" rights="<rights>">
    <soapCall name="<name>" service="<schema>">
      <param type="<type>" exprIn="<xpath>"/>  
        ...
    </soapCall>
    <enter>
      ...
    </enter>
  </command>
</nodeModel>
```

Beskrivningen av ett kommando anges på **`<command>`** element med följande egenskaper:

* **name**: kommandots interna namn: namnet måste anges och vara unikt.
* **label**: kommandots etikett.
* **desc**: beskrivning som visas från huvudskärmens statusfält.
* **formulär**: formulär som ska startas: det värde som ska anges är inmatningsformulärets identifieringsnyckel (t.ex. &quot;cus:mottagare&quot;).
* **rättigheter**: lista med namngivna rättigheter (avgränsade med kommatecken) som tillåter åtkomst till det här kommandot. Listan över tillgängliga rättigheter finns på **[!UICONTROL Administration > Access management > Named rights]** mapp.
* **promptLabel**: visar en bekräftelseruta innan kommandot körs
* **monoSelection**: tvingar enval (flerval som standard).
* **refreshView**: Tvingar att läsa in listan igen efter att kommandot har körts.
* **enabledIf**: aktiverar kommandot beroende på vilket uttryck som anges.
* **img**: anger en bild som ger åtkomst till kommandot från listverktygsfältet.

A **`<command>`** element kan innehålla **`<command>`** delelement. I det här fallet kan du med det överordnade elementet visa en undermeny som består av dessa underordnade element.

Kommandona visas i samma ordning som de deklareras i XML-dokumentet.

Med en kommandoavgränsare kan du visa ett avgränsningstecken mellan kommandona. Den identifieras av **&#39;-&#39;** i kommandoetiketten.

Den valfria närvaron av **`<soapcall>`** -taggen med indataparametrarna definierar anropet till en SOAP-metod som ska köras. Mer information om SOAP API:er finns i [Kampanj-JSAPI-dokumentation](https://experienceleague.adobe.com/developer/campaign-api/api/index.html).

Formulärkontexten kan uppdateras vid initieringen via **`<enter>`** -tagg. Mer information om den här taggen finns i dokumentationen till indataformuläret.

**Exempel**:

```
<command desc="Cancel execution of the job" enabledIf="EV(@status, 'running')"
         img="nms:difstop.bmp" label="Cancel..." name="cancelJob" 
         promptLabel="Do you really want to cancel this job?" refreshView="true">
  <soapCall name="Cancel" service="xtk:jobInterface"/>
</command>
<command label="-" name="sep1"/>
<command desc="Execute selected template" form="cus:form" lmonoSelection="true" name="executeModel"
         rights="import,export,aggregate">
  <enter>
    <set expr="0" xpath="@status"/>
  </enter>
</command>
```

### Länkad mapp {#linked-folder}

Det finns två typer av mapphanteringsåtgärder:

1. Mappen är en vy: I listan visas alla poster som är associerade med schemat, med möjlighet till systemfiltrering som anges i mappegenskaperna.
1. Mappen är länkad: posterna i listan filtreras implicit på mapplänken.

För en länkad mapp visas **folderLink** på **`<nodemodel>`** -elementet måste fyllas i. Det här attributet innehåller namnet på länken i mappen som är konfigurerad i dataschemat.

Exempel på deklaration av en länkad mapp i dataschemat:

```
<element default="DefaultFolder('nmsFolder', [@_folder-id])" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="define" revLabel="Recipients" target="xtk:folder" type="link"/>
```

Konfigurationen av **`<nodemodel>`** på länken till mappen &quot;folder&quot; är följande:

```
<nodeModel deleteRight="folderDelete" editRight="folderEdit" folderLink="folder"
  img="nms:folder.png" insertRight="folderInsert" label="Recipients" name="nmsFolder">
...
</nodeModel>
```
