---
product: campaign
title: Skicka personaliserade aviseringar till operatörer
description: Lär dig hur du skickar personaliserade aviseringar till operatorer
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: 21c97eb3-60cd-4d19-bc0f-5ba9ec17e70a
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 2%

---

# Skicka personaliserade aviseringar till operatörer{#sending-personalized-alerts-to-operators}

I det här exemplet vill vi skicka en varning till en operator som ska innehålla namnet på profiler som öppnade ett nyhetsbrev men som inte klickade på länken som det innehåller.

Profilernas för- och efternamnsfält är länkade till måldimensionen **[!UICONTROL Recipients]**, medan aktiviteten **[!UICONTROL Alert]** är länkad till måldimensionen **[!UICONTROL Operator]**. Därför finns det inget tillgängligt fält mellan de två måldimensionerna för att utföra en avstämning och hämta för- och efternamnsfälten, och visa dem i aviseringsaktiviteten.

Processen är att skapa ett arbetsflöde enligt nedan:

1. Använd en **[!UICONTROL Query]**-aktivitet för måldata.
1. Lägg till en **[!UICONTROL JavaScript code]**-aktivitet i arbetsflödet för att spara ifyllningen från frågan till instansvariabeln.
1. Använd en **[!UICONTROL Test]**-aktivitet för att kontrollera antalet populationer.
1. Använd en **[!UICONTROL Alert]**-aktivitet för att skicka en avisering till en operator, beroende på aktivitetsresultatet för **[!UICONTROL Test]**.

![](assets/uc_operator_1.png)

## Sparar populationen i instansvariabeln {#saving-the-population-to-the-instance-variable}

Lägg till koden nedan i aktiviteten **[!UICONTROL JavaScript code]**.

```
var query = xtk.queryDef.create(  
    <queryDef schema="temp:query" operation="select">  
      <select>  
       <node expr="[target/recipient.@firstName]"/>  
       <node expr="[target/recipient.@lastName]"/>  
      </select>  
     </queryDef>  
  );  
  var items = query.ExecuteQuery();
```

Kontrollera att JavaScript-koden motsvarar arbetsflödesinformationen:

* Taggen **[!UICONTROL queryDef schema]** ska motsvara namnet på måldimensionen som används i frågeaktiviteten.
* Taggen **[!UICONTROL node expr]** ska motsvara namnet på de fält som du vill hämta.

![](assets/uc_operator_3.png)

Följ stegen nedan för att hämta informationen:

1. Högerklicka på den utgående övergången från **[!UICONTROL Query]**-aktiviteten och välj **[!UICONTROL Display the target]**.

   ![](assets/uc_operator_4.png)

1. Högerklicka på listan och välj **[!UICONTROL Configure list]**.

   ![](assets/uc_operator_5.png)

1. Frågemålets dimension och fältnamn visas i listan.

   ![](assets/uc_operator_6.png)

## Testa populationsantalet {#testing-the-population-count}

Lägg till koden nedan i aktiviteten **[!UICONTROL Test]** för att kontrollera om målpopulationen innehåller minst en profil.

```
var.recCount>0
```

![](assets/uc_operator_7.png)

## Konfigurera aviseringen {#setting-up-the-alert}

Nu när populationen har lagts till i instansvariabeln med de önskade fälten kan du lägga till informationen i **[!UICONTROL Alert]**-aktiviteten.

Gör detta genom att lägga till koden nedan på fliken **[!UICONTROL Source]**:

```
<ul>
<%
var items = new XML(instance.vars.items)
for each (var item in items){
%>
<li><%= item.target.@firstName %> <%= item.target.@lastName %></li>
<%
} %></ul>
```

>[!NOTE]
>
>Med kommandot **[!UICONTROL <%= item.target.recipient.@fieldName %>]** kan du lägga till ett av fälten som har sparats i instansvariabeln via aktiviteten **[!UICONTROL JavaScript code]**.\
>Du kan lägga till så många fält som du vill, så länge de har infogats i JavaScript-koden.

![](assets/uc_operator_8.png)
