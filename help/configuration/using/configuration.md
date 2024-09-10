---
product: campaign
title: Konfigurera navigeringsträdet i Campaign Explorer
feature: Application Settings
description: Lär dig konfigurera navigeringsträdet i Campaign Explorer
role: Data Engineer, Developer
exl-id: c7ae7240-0c12-4420-bbb3-4268c9ade3e7
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '1186'
ht-degree: 0%

---

# Konfigurera navigeringsträdet i Campaign Explorer{#configuration}

Som expertanvändare kan du lägga till mappar i utforskarträdet och anpassa det.

Läs mer om Campaign Explorer och navigeringshierarkin [i det här avsnittet](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy).

De typer av mappar som används av navigeringslistan beskrivs i ett XML-dokument som lyder grammatiken i schemat **xtk:navtree**.

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

XML-dokumentet innehåller rotelementet **`<navtree>`** med attributen **name** och **namespace** som anger dokumentnamnet och namnutrymmet. Namnet och namnutrymmet utgör dokumentets ID-nyckel.

Programmets globala kommandon deklareras i dokumentet från elementet **`<commands>`**.

Deklarationen av filtyper är strukturerad i dokumentet med följande element: **`<model>`** och **`<nodemodel>`**.

## Globala kommandon {#global-commands}

Med ett globalt kommando kan du starta ett funktionsmakro. Den här åtgärden kan vara ett indataformulär eller ett SOAP.

Globala kommandon är tillgängliga från huvudmenyn **[!UICONTROL Tools]**.

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

Beskrivningen av ett globalt kommando anges i elementet **`<command>`** med följande egenskaper:

* **name**: kommandots interna namn: namnet måste anges och vara unikt
* **label**: kommandots etikett.
* **desc**: description visible from the status bar of the main screen.
* **form**: formulär som ska startas: det värde som ska anges är identifieringsnyckeln för indataformuläret (t.ex. &quot;cus:mottagare&quot;)
* **rights**: lista med namngivna rättigheter (avgränsade med kommatecken) som tillåter åtkomst till det här kommandot. Listan över tillgängliga rättigheter är tillgänglig från mappen **[!UICONTROL Administration > Access management > Named rights]**.
* **promptLabel**: visar en bekräftelseruta innan kommandot körs.

Ett **`<command>`**-element kan innehålla **`<command>`** underelement. I det här fallet kan du med det överordnade elementet visa en undermeny som består av dessa underordnade element.

Kommandona visas i samma ordning som de deklareras i XML-dokumentet.

Med en kommandoavgränsare kan du visa ett avgränsningstecken mellan kommandona. Den identifieras av värdet **-** som finns i kommandoetiketten.

Den valfria förekomsten av taggen **`<soapcall>`** med dess indataparametrar definierar anropet av en SOAP metod som ska köras. Mer information om SOAP API finns i [Kampanjens JSAPI-dokumentation](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=sv).

Formulärkontexten kan uppdateras vid initiering från taggen **`<enter>`**. Mer information om den här taggen finns i dokumentationen om indataformulär.

**Exempel**:

* Deklaration för ett globalt kommando som startar formuläret &quot;xtk:import&quot;:

  ```
  <command desc="Start the data import assistant" form="xtk:import" label="&amp;Data import..." name="import" rights="import,recipientImport"/>
  ```

  Ett kortkommando deklareras för I-tecknet av närvaron av **&amp;** i kommandoetiketten.

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

* Körning av en SOAP:

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

Mapptypsdeklarationen måste anges under ett **`<model>`**-element. Med det här elementet kan du definiera en hierarkisk organisation som visas på menyn **[!UICONTROL Add new folder]**. Ett **`<model>`**-element måste innehålla **`<nodemodel>`**-element och andra **`<model>`**-element.

Attributen **name** och **label** fyller i elementets interna namn och etiketten som visas på menyn **[!UICONTROL Add new folder]**.

Elementet **`<nodemodel>`** innehåller en beskrivning av mapptypen med följande egenskaper:

* **namn**: internt namn
* **label**: label used in the **[!UICONTROL Add new folder]** menu and as a default label when insering a folder.
* **img**: standardbild vid mappinfogning.
* **hiddenCommands**: lista med kommandon (avgränsade med kommatecken) som ska maskeras. Möjliga värden: &quot;adbnew&quot;, &quot;adbsave&quot;, &quot;adbcancel&quot; och &quot;adbdup&quot;.
* **newFolderShortCuts**: lista med genvägar på modeller (**`<nodemodel>`** avgränsade med kommatecken) när mappar skapas.
* **insertRight**, **editRight**, **deleteRight**: rättigheter för att infoga, redigera och ta bort mappar.

Elementet **`<view>`** under elementet **`<nodemodel>`** innehåller konfigurationen för listan som är associerad med vyn. Schemat för listan anges i attributet **schema** för elementet **`<view>`**.

Om du vill redigera posterna i listan används indataformuläret med samma namn som listschemat implicit. Attributet **type** i elementet **`<view>`** påverkar visningen av formuläret. Möjliga värden är:

* **list**: visar formuläret längst ned i listan.
* **list**: visar enbart listan. Formuläret öppnas genom att man dubbelklickar eller via&quot;Öppna&quot; i menyn när man väljer listan.
* **formulär**: visar ett skrivskyddat formulär.
* **editForm**: visar ett formulär i redigeringsläge.

>[!NOTE]
>
>Namnet på indataformuläret kan överläsas genom att attributet **form** anges i elementet **`<view>`**.

Listkolumnernas standardkonfiguration anges via elementet **`<columns>`**. En kolumn deklareras i ett **`<node>`**-element som innehåller attributet **Path** med fältet som ska refereras i schemat som dess värde.

**Exempel**: deklaration av en mapptyp i schemat nms:mottagare.

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

Med ett kortkommando kan du starta en åtgärd när du markerar listan. Åtgärden kan vara ett indataformulär eller ett SOAP.

Kommandon är tillgängliga på menyn **[!UICONTROL Action]** i listan eller på den associerade menyknappen.

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

Beskrivningen av ett kommando anges för elementet **`<command>`** med följande egenskaper:

* **namn**: Kommandots interna namn: namnet måste anges och vara unikt.
* **label**: kommandots etikett.
* **desc**: description visible from the status bar of the main screen.
* **form**: formulär som ska startas: det värde som ska anges är identifieringsnyckeln för indataformuläret (t.ex. &quot;cus:mottagare&quot;).
* **rights**: lista med namngivna rättigheter (avgränsade med kommatecken) som tillåter åtkomst till det här kommandot. Listan över tillgängliga rättigheter är tillgänglig från mappen **[!UICONTROL Administration > Access management > Named rights]**.
* **promptLabel**: visar en bekräftelseruta innan kommandot körs
* **monoSelection**: tvingar enmarkering (flera markeringar som standard).
* **refreshView**: Tvingar fram ominläsning av listan efter att kommandot har körts.
* **enabledIf**: aktiverar kommandot beroende på vilket uttryck som anges.
* **img**: anger en bild som ger åtkomst till kommandot från listverktygsfältet.

Ett **`<command>`**-element kan innehålla **`<command>`** underelement. I det här fallet kan du med det överordnade elementet visa en undermeny som består av dessa underordnade element.

Kommandona visas i samma ordning som de deklareras i XML-dokumentet.

Med en kommandoavgränsare kan du visa ett avgränsningstecken mellan kommandona. Den identifieras av värdet **-** som finns i kommandoetiketten.

Den valfria förekomsten av taggen **`<soapcall>`** med dess indataparametrar definierar anropet av en SOAP metod som ska köras. Mer information om SOAP API:er finns i [Kampanjens JSAPI-dokumentation](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=sv).

Formulärkontexten kan uppdateras vid initieringen via taggen **`<enter>`**. Mer information om den här taggen finns i dokumentationen till indataformuläret.

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

1. Mappen är en vy: i listan visas alla poster som är associerade med schemat, med möjlighet till systemfiltrering som anges i mappegenskaperna.
1. Mappen är länkad: posterna i listan filtreras implicit på mapplänken.

För en länkad mapp måste attributet **folderLink** för elementet **`<nodemodel>`** fyllas i. Det här attributet innehåller namnet på länken i mappen som är konfigurerad i dataschemat.

Exempel på deklaration av en länkad mapp i dataschemat:

```
<element default="DefaultFolder('nmsFolder', [@_folder-id])" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="define" revLabel="Recipients" target="xtk:folder" type="link"/>
```

Konfigurationen för **`<nodemodel>`** på länken för mappen med namnet &quot;folder&quot; är följande:

```
<nodeModel deleteRight="folderDelete" editRight="folderEdit" folderLink="folder"
  img="nms:folder.png" insertRight="folderInsert" label="Recipients" name="nmsFolder">
...
</nodeModel>
```
