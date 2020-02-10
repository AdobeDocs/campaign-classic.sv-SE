---
title: Implementering
seo-title: Implementering
description: Implementering
seo-description: null
page-status-flag: never-activated
uuid: 12b5fbbf-fe0d-4598-8845-f7b8ee7672c3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: use-case
discoiquuid: ac1c0a00-41ef-4cc2-bb51-2808ef400bb1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Implementering{#implementation}

Här följer ett diagram med de olika stegen som ingår i det här scenariot.

![](assets/message-center-uc1.png)

Börja med att utforma den bifogade filen. Se den här [artikeln](../../delivery/using/attaching-files.md#attach-a-personalized-file). Detta gör att du kan bifoga filerna till ett e-postmeddelande, även om de inte finns på körningsinstansen.

Du kan skicka e-postmeddelanden via en SOAP-utlösare. Mer information om SOAP-begäranden finns i [Händelsebeskrivning](../../message-center/using/event-description.md). I SOAP-anropet finns det en URL-parameter (attachmentURL).

När du utformar e-postmeddelandet klickar du på **[!UICONTROL Attachment]** . Ange parametern SOAP attachment på **[!UICONTROL Attachment definition]** skärmen:

```
<%= rtEvent.ctx.attachementUrl %>
```

När meddelandet bearbetas/distribueras hämtar systemet filen från fjärrplatsen (tredjepartsserver) och bifogar den till det enskilda meddelandet.

Eftersom den här parametern kan vara en variabel bör den acceptera den fullständiga URL-variabeln för filen, som skickas via SOAP-anropet.

![](assets/message-center-uc2.png)

