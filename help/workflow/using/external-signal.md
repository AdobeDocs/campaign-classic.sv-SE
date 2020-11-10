---
title: Extern signal
description: Läs mer om arbetsflödesaktiviteten för externa signaturer
page-status-flag: never-activated
uuid: dbe6624a-70cf-4ac4-adfd-bc72db9bb3f3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 3739593f-056c-4165-87ef-63c812bd3c43
translation-type: tm+mt
source-git-commit: 6be6c353c3464839a74ba857d8d93d0f68bc8865
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 2%

---


# Extern signal{#external-signal}

Med aktiviteten för **extern signal** kan du utlösa körning av en uppsättning uppgifter i ett arbetsflöde enligt ett schema.

När en aktivitet av typen &quot;Extern signal&quot; aktiveras pausas den oavbrutet eller tills den angivna tidsperioden är slut. Övergången aktiveras av SOAP-anropet **PostEvent(sessionToken, workflowId, activity, transition, parameters, complete).** Parametern **[!UICONTROL complete]** tillåter att aktiviteten slutförs, så den kommer inte att reagera på efterföljande anrop.

Mer information om funktionen PostEvent finns i onlinedokumentationen för SOAP-anrop.

Du kan konfigurera den här aktiviteten för att definiera händelser om ingen signal tas emot. Om du vill göra det redigerar du aktiviteten och klickar på **[!UICONTROL Expiration]** fliken. Klicka på **[!UICONTROL Insert]** knappen för att skapa och konfigurera en händelse.

![](assets/edit_signal.png)

Konfigurationen av förfallodatum finns i [Förfallodatum](../../workflow/using/defining-approvals.md).

I fältet **Fördröjning** kan du ange en förfallofördröjning i valfria enheter. Se [Vänta](../../workflow/using/wait.md).

Varje rad motsvarar en typ av förfallodatum och sammanfaller med en övergång.

![](assets/external_sign_diag.png)

