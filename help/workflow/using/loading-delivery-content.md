---
product: campaign
title: Läsa in leveransinnehåll
description: Läsa in leveransinnehåll
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: a52baffd-402b-4b33-ab72-ac954e4dee85
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 3%

---

# Läsa in leveransinnehåll{#loading-delivery-content}

![](../../assets/common.svg)

Om ditt leveransinnehåll är tillgängligt i en HTML-fil som finns på Amazon S3-, FTP- eller SFTP-servrar kan du enkelt läsa in innehållet i Adobe Campaign-leveranser.

Så här gör du:

1. Om du inte redan har definierat en anslutning mellan Adobe Campaign och den (S)FTP-server som är värd för innehållsfilerna skapar du ett nytt externt S3-, FTP- eller SFTP-konto i **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External Accounts]**. I det här externa kontot anger du den adress och de autentiseringsuppgifter som används för att upprätta anslutningen till S3- eller (S)FTP-servern.

   Här är ett exempel på ett externt S3-konto:

   ![](assets/delivery_loadcontent_filetransfertexamples3.png)

1. Skapa ett nytt arbetsflöde, till exempel från **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Jobs]** > **[!UICONTROL Targeting workflows]**.
1. Lägg till en **[!UICONTROL File transfer]**-aktivitet i arbetsflödet och konfigurera den genom att ange

   * Det externa konto som ska användas för att ansluta till S3- eller (S)FTP-servern.
   * Sökvägen till filen på S3- eller (S)FTP-servern.

   ![](assets/delivery_loadcontent_filetransfertexample.png)

1. Lägg till en **[!UICONTROL Delivery]**-aktivitet och koppla den till den utgående övergången för **[!UICONTROL File transfer]**-aktiviteten. Konfigurera den enligt följande:

   * Leverans: Beroende på dina behov kan det vara en specifik leverans som redan har skapats i systemet eller en ny leverans som baseras på en befintlig mall.
   * Mottagare: I det här exemplet anses målet vara angivet i själva leveransen.
   * Innehåll: Även om innehållet importeras i den tidigare aktiviteten väljer du **[!UICONTROL Specified in the delivery]**. Eftersom innehållet importeras direkt från en fil som finns på en fjärrserver, har det ingen identifierare när det bearbetas av arbetsflödet och kan inte identifieras som om det kommer från den inkommande händelsen.
   * Åtgärd som ska utföras: Välj **[!UICONTROL Save]** om du vill spara leveransen och kunna komma åt den från **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]** när arbetsflödet har körts.

   ![](assets/delivery_loadcontent_activityexample.png)

1. På fliken **[!UICONTROL Script]** i aktiviteten **[!UICONTROL Delivery]** lägger du till följande kommando för att läsa in innehållet i den importerade filen i leveransen:

   ```
   delivery.content.md.source=loadFile(vars.filename)
   ```

   ![](assets/delivery_loadcontent_script.png)

1. Spara och kör arbetsflödet. En ny leverans med det inlästa innehållet skapas under **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

>[!NOTE]
>
>Bästa praxis och felsökning för SFTP-serveranvändning finns i [på den här sidan](../../platform/using/sftp-server-usage.md).
