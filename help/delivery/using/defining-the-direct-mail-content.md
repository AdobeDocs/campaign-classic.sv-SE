---
product: campaign
title: Definiera innehållet i direktmeddelanden
description: Lär dig hur du definierar innehållet i direktreklam
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Direct Mail
role: User
exl-id: 585b2017-9408-4953-8505-2f6d9db8032f
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 10%

---

# Definiera innehållet i direktmeddelanden{#defining-the-direct-mail-content}

## Extraheringsfil {#extraction-file}

Namnet på filen som innehåller extraherade data definieras i **[!UICONTROL File]** fält. Med knappen till höger om fältet kan du använda anpassningsfält för att skapa filnamnet.

Som standard skapas extraheringsfilen och lagras på servern. Du kan spara den på datorn. Om du vill göra det går du till **[!UICONTROL Download the generated file after the analysis of the delivery]**. I det här fallet måste du ange åtkomstsökvägen till den lokala lagringskatalogen samt filnamnet.

![](assets/s_ncs_user_mail_delivery_local_file.png)

För direktutskick definieras innehållet i extraheringen i **[!UICONTROL Edit the extraction file format...]** länk.

![](assets/s_ncs_user_mail_delivery_format_link.png)

Med den här länken kan du komma åt extraheringsguiden och definiera den information (kolumner) som ska exporteras till utdatafilen.

![](assets/s_ncs_user_mail_delivery_format_wz.png)

Det går att infoga en personlig URL i extraheringsfilen. Mer information om detta finns i [det här avsnittet](../../web/using/publishing-a-web-form.md).

>[!NOTE]
>
>Den här guiden innehåller de steg i exportguiden som beskrivs i [Komma igång](../../platform/using/executing-export-jobs.md) -avsnitt.
