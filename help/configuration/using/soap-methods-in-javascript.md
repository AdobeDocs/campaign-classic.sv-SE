---
title: SOAP-metoder i JavaScript
seo-title: SOAP-metoder i JavaScript
description: SOAP-metoder i JavaScript
seo-description: null
page-status-flag: never-activated
uuid: 8fd1aabc-e51a-433d-835f-6b5a717c7aeb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: api
discoiquuid: 815d3eb9-ac45-441f-9a5f-0cd505fcf88a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

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

