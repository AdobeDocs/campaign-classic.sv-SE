---
product: campaign
title: Definiera innehållet i direktutskick
description: Definiera innehållet i direktutskick
audience: delivery
content-type: reference
topic-tags: sending-direct-mail
exl-id: 585b2017-9408-4953-8505-2f6d9db8032f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 14%

---

# Definiera innehållet i direktutskick{#defining-the-direct-mail-content}

![](../../assets/common.svg)

## Extraheringsfil {#extraction-file}

Namnet på filen som innehåller extraherade data definieras i fältet **[!UICONTROL File]**. Med knappen till höger om fältet kan du använda anpassningsfält för att skapa filnamnet.

Som standard skapas extraheringsfilen och lagras på servern. Du kan spara den på datorn. Det gör du genom att kontrollera **[!UICONTROL Download the generated file after the analysis of the delivery]**. I det här fallet måste du ange åtkomstsökvägen till den lokala lagringskatalogen samt filnamnet.

![](assets/s_ncs_user_mail_delivery_local_file.png)

För direktutskick definieras innehållet i extraheringen i länken **[!UICONTROL Edit the extraction file format...]**.

![](assets/s_ncs_user_mail_delivery_format_link.png)

Med den här länken kan du komma åt extraheringsguiden och definiera den information (kolumner) som ska exporteras till utdatafilen.

![](assets/s_ncs_user_mail_delivery_format_wz.png)

Det går att infoga en personlig URL i extraheringsfilen. Mer information om detta finns i [det här avsnittet](../../web/using/publishing-a-web-form.md).

>[!NOTE]
>
>Den här guiden innehåller stegen i exportguiden som beskrivs i avsnittet [Komma igång](../../platform/using/executing-export-jobs.md).
