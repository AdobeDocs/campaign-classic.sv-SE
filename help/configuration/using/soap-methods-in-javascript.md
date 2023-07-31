---
product: campaign
title: SOAP-metoder i JavaScript
feature: Configuration, Instance Settings
description: SOAP-metoder i JavaScript
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
exl-id: 62020447-fe59-4363-994d-de4d8032bbd7
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 9%

---

# SOAP-metoder i JavaScript{#soap-methods-in-javascript}

Detta är det JavaScript som körs på Adobe Campaign-servern.

## Statiska metoder {#static-methods}

Statiska SOAP-metoder nås genom att en metod anropas i objektet som representerar schemat. Scheman är egenskaper för namespace-objekt. Dessa namnutrymmen är globala variabler, vilket innebär att variablerna xtk och nms representerar motsvarande namnutrymmen

I följande exempel anropas den statiska PostEvent-metoden för xtk:workflow-schemat:

```
xtk.workflow.PostEvent("WKF1", "signal", "", $recipient-id='123', false) 
```

## Icke-statiska metoder {#non-static-methods}

Om du vill använda icke-statiska SOAP-metoder måste du först hämta en entitet med metoderna&quot;get&quot; eller&quot;create&quot; i motsvarande scheman.

I följande exempel anropas metoden ExecuteQuery för schemat &quot;xtk:queryDef&quot;:

```
var query = xtk.queryDef.create(
  <queryDef schema="xtk:workflow" operation="select">
    <select>
      <node expr="@internalName"/>
    </select>
  </queryDef>
)

var res = query.ExecuteQuery()

for each (var w in res.workflow) 
  logInfo(w.@internalName)
```

## Exempel {#examples}

* Fråga i mottagartabellen med en get-åtgärd:

  ```
  var query = xtk.queryDef.create(  
    <queryDef schema="nms:recipient" operation="get">    
      <select>      
        <node expr="@firstName"/>      
        <node expr="@lastName"/>      
        <node expr="@email"/>    
      </select>    
      <where>      
        <condition expr="@email = 'peter.martinez@adobe.com'"/>    
      </where>  
    </queryDef>)
  
  var recipient = query.ExecuteQuery()
  
  logInfo(recipient.@firstName)
  logInfo(recipient.@lastName)
  ```

* Fråga i mottagartabellen med åtgärden &quot;select&quot;:

  ```
  var query = xtk.queryDef.create(  
    <queryDef schema="nms:recipient" operation="select">    
      <select>      
        <node expr="@email"/>      
        <node expr="@lastName"/>      
        <node expr="@firstName"/>    
      </select>    
      <where>      
        <condition expr="@age > 25"/>    
      </where>    
    </queryDef>)
  
  var res = query.ExecuteQuery()
  
  for each (var recipient in res.recipient) 
  {  
    logInfo(recipient.@email)  
    logInfo(recipient.@firstName)  
    logInfo(recipient.@lastName)
  }
  ```

* Skriver data till mottagartabellen:

  ```
  xtk.session.Write(<recipient _operation="insert" lastName="Martinez" firstName="Peter" xtkschema="nms:recipient"/>);
  ```
