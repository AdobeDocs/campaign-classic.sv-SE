---
product: campaign
title: Extern signal
description: Läs mer om arbetsflödesaktiviteten för externa signaturer
audience: workflow
content-type: reference
topic-tags: flow-control-activities
exl-id: da84d3ff-1e64-45ef-bef0-da4a24d93461
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 2%

---

# Extern signal{#external-signal}

![](../../assets/common.svg)

The **Extern signal** Med -aktivitet kan du utlösa körning av en uppsättning uppgifter i ett arbetsflöde enligt ett schema.

När en aktivitet av typen &quot;Extern signal&quot; aktiveras pausas den oavbrutet eller tills den angivna tidsperioden är slut. Övergången aktiveras av SOAP-anropet **PostEvent(sessionToken, workflowId, activity, transition, parameters, complete).** The **[!UICONTROL complete]** -parametern gör att aktiviteten kan slutföras så att den inte svarar på efterföljande anrop.

Mer information om funktionen PostEvent finns i onlinedokumentationen för SOAP-anrop.

Du kan konfigurera den här aktiviteten för att definiera händelser om ingen signal tas emot. Om du vill göra det redigerar du aktiviteten och klickar på knappen **[!UICONTROL Expiration]** -fliken. Klicka på **[!UICONTROL Insert]** för att skapa och konfigurera en händelse.

![](assets/edit_signal.png)

Konfigurationen av förfallodatum finns i [Förfallodatum](defining-approvals.md).

The **Fördröjning** I kan du ange en förfallotid i valfri enhet. Se [Vänta](wait.md).

Varje rad motsvarar en typ av förfallodatum och sammanfaller med en övergång.

![](assets/external_sign_diag.png)
