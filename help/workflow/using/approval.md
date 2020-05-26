---
title: Godkännande
seo-title: Godkännande
description: Godkännande
seo-description: null
page-status-flag: never-activated
uuid: 49285790-5aa7-4e15-a657-42e4f78be518
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: a0090c78-5873-446d-8d5f-b0f94ff5d373
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b369a17fabc55607fc6751e7909e1a1cb3cd4201
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 0%

---


# Godkännande{#approval}

En **godkännandeuppgift** kräver att en operatör deltar. Operatorn tilldelas en uppgift och kan svara via e-post, via den webbsida som är länkad i e-postmeddelandet eller via konsolen.

## Uppgiftstilldelning {#task-assignment}

Som standard tilldelas godkännande till en grupp operatorer. Den här gruppen representerar en roll, t.ex. &#39;Innehållsgrupp för nyhetsbrev&#39; eller &#39;Målgrupp för nyhetsbrev&#39;. Varje operator i gruppen kan svara, men endast det första svaret beaktas (utom vid flera godkännanden).

Om det behövs kan du tilldela godkännandeuppgiften till en enda operator eller en uppsättning operatorer som definieras av ett filter.

* Om du vill välja en enskild operator markerar du **[!UICONTROL Operator]** värdet i **[!UICONTROL Assignment type]** fältet och väljer den relevanta operatorn i listrutan i **[!UICONTROL Assignee]** fältet.

   ![](assets/s_advuser_validation_box_assign.png)

   >[!CAUTION]
   >
   >Endast den valda operatorn kommer att få behörighet att godkänna uppgiften.

* Du kan definiera en fråga för filtrering av godkännandeoperatorer. Det gör du genom att markera **[!UICONTROL Filter]** värdet i **[!UICONTROL Assignment type]** fältet och klicka på **[!UICONTROL Advanced parameters...]** länken för att definiera filtreringsvillkoren, vilket visas i följande exempel:

   ![](assets/s_advuser_validation_box_filter.png)

Vid ett enda godkännande aktiveras övergången som motsvarar valet av operator och uppgiften är slutförd: övriga operatorer inte kan svara.

Vid flera godkännanden aktiveras övergångar som motsvarar valet av operatorer. Uppgiften är slutförd när alla operatorer i gruppen har svarat eller när uppgiften har upphört att gälla.

Den här aktiviteten blockerar inte bearbetning och arbetsflödet kan utföra andra åtgärder medan det väntar på ett svar.

En operator kan godkänna uppgifterna som tilldelats den operatorn från konsolen. En operator med administratörsbehörighet kan visa och ta bort uppgifter som tilldelats en operator, men kan inte svara på dem.

Om du ändrar aktivitetens titel eller meddelandetext påverkas inte de aktuella uppgifterna, men om du å andra sidan ändrar de möjliga alternativen påverkas de aktuella uppgifterna direkt, vilket automatiskt ärver den nya listan med alternativ.

**Typgodkännandeåtgärder** är tillgängliga från **[!UICONTROL Administration > Production > Objects created automatically > Approvals pending]** noden: -operatorer kan komma åt godkännandeformuläret direkt via den här vyn.

![](assets/s_advuser_validation_from_console.png)

## Egenskaper {#properties}

Anpassningsvariabler kan användas i meddelanden som skickas till granskarna. De kan infogas i meddelandets rubrik eller brödtext.

![](assets/edit_validation.png)

Det här **[!UICONTROL Title]** fältet innehåller meddelandets titel: Det här är ämnet för det skickade e-postmeddelandet. Titeln och meddelandetexten är JavaScript-mallar och kan därför innehålla värden som beräknas utifrån arbetsflödets sammanhang.

I den nedre delen av redigeraren kan du definiera en lista med möjliga svar. Det finns en övergång som motsvarar varje svar. Namnet är den interna identifieraren och etiketten är den text som visas i listan med alternativ.

Klicka på **[!UICONTROL Advanced parameters...]** länken för att välja den leveransmall som ska användas för att meddela operatorer. Standardmallen (det interna namnet notifyAssigner) tar titeln och meddelandet och lägger till en länk till den webbsida som används för att svara.

Den här mallen kan ändras för att anpassa meddelandelayouten, men du bör skapa en kopia. Målinriktningsmekanismen (extern fil, målmappning) får inte ändras eftersom den krävs för att meddelanden ska fungera korrekt.

Ett exempel på godkännande visas i [Definiera godkännanden](../../workflow/using/defining-approvals.md).

## Utdataparametrar {#output-parameters}

* **[!UICONTROL response]**

   Kommentar relaterade till svaret

* **[!UICONTROL responseOperator]**

   Identifierare för den operator som svarade. Det här fältet är ett numeriskt värde, men ett **[!UICONTROL String]** fält.

