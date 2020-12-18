---
solution: Campaign Classic
product: campaign
title: Extern signal
description: Läs mer om arbetsflödesaktiviteten för externa signaturer
audience: workflow
content-type: reference
topic-tags: flow-control-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 2%

---


# Extern signal{#external-signal}

Med aktiviteten **Extern signal** kan du utlösa körning av en uppsättning uppgifter i ett arbetsflöde enligt ett schema.

När en aktivitet av typen &quot;Extern signal&quot; aktiveras pausas den oavbrutet eller tills den angivna tidsperioden är slut. Övergången aktiveras av SOAP-anropet **PostEvent(sessionToken, workflowId, activity, transition, parameters, complete).** Med  **[!UICONTROL complete]** parametern kan aktiviteten slutföras, så den kommer inte att reagera på efterföljande anrop.

Mer information om funktionen PostEvent finns i onlinedokumentationen för SOAP-anrop.

Du kan konfigurera den här aktiviteten för att definiera händelser om ingen signal tas emot. Om du vill göra det redigerar du aktiviteten och klickar på fliken **[!UICONTROL Expiration]**. Klicka på knappen **[!UICONTROL Insert]** för att skapa och konfigurera en händelse.

![](assets/edit_signal.png)

Konfigurationen av förfallodatum anges i [Förfallodatum](../../workflow/using/defining-approvals.md).

I fältet **Fördröjning** kan du ange en förfallofördröjning i valfria enheter. Se [Vänta](../../workflow/using/wait.md).

Varje rad motsvarar en typ av förfallodatum och sammanfaller med en övergång.

![](assets/external_sign_diag.png)

