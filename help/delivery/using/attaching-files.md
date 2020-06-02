---
title: Bifoga filer
seo-title: Bifoga filer
description: Bifoga filer
seo-description: null
page-status-flag: never-activated
uuid: a4dc1908-a6ef-4bc8-a310-605fc80c34ca
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-emails
discoiquuid: f3666c12-5e6f-452e-b1d6-b69a7e9f6f6e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: adb25307146847a1c49d9c548d00557e95562541
workflow-type: tm+mt
source-wordcount: '880'
ht-degree: 0%

---


# Bifoga filer{#attaching-files}

## Om e-postbilagor {#about-email-attachments}

Du kan bifoga en eller flera filer till en e-postleverans. Det finns två möjliga fall:

* Välj en fil och bifoga den till leveransen som den är.
* Anpassa innehållet i bilagan för varje mottagare. I det här fallet måste du skapa en **beräknad bilaga**: namnet på den bifogade filen beräknas vid leveranstillfället för varje meddelande beroende på mottagaren. Innehållet kan också anpassas och konverteras till PDF-format när det levereras, om du har alternativet **Variabel digital utskrift** .

>[!NOTE]
>
>Den här typen av konfiguration utförs vanligtvis i leveransmallarna. Mer information finns i [Om mallar](../../delivery/using/about-templates.md).

## Bifoga en lokal fil {#attaching-a-local-file}

Följ stegen nedan för att bifoga en lokal fil till en leverans.

>[!NOTE]
>
>Du kan bifoga flera filer till en leverans. Bifogade filer kan ha vilket format som helst, inklusive zippat format.

1. Klicka på **[!UICONTROL Attachments]** länken.
1. Klicka på **[!UICONTROL Add]** knappen.
1. Klicka **[!UICONTROL File...]** för att välja den fil som ska bifogas leveransen.

   ![](assets/s_ncs_user_wizard_email_attachement.png)

Du kan också dra och släppa filen direkt i leveransfältet, **[!UICONTROL Attachments]** eller använda **[!UICONTROL Attach]** ikonen från leveransguideverktygsfältet,

![](assets/s_ncs_user_wizard_add_file_ico.png)

När filen är markerad överförs den direkt till servern för att vara tillgänglig vid leveransen. Den visas i **[!UICONTROL Attachments]** fältet.

![](assets/s_ncs_user_wizard_email_attachement_e.png)

## Skapa en beräknad bilaga {#creating-a-calculated-attachment}

När du skapar en beräknad bilaga kan namnet på den bifogade filen beräknas under analys eller leverans av varje meddelande och kan bero på mottagaren. Den kan också personaliseras och konverteras till PDF.

![](assets/s_ncs_user_wizard_attachment.png)

Så här skapar du en personlig bifogad fil:

1. Klicka på **[!UICONTROL Attachments]** länken.
1. Klicka på **[!UICONTROL Add]** knappen och välj sedan **[!UICONTROL Calculated attachment]**.
1. Välj typ av beräkning i den **[!UICONTROL Type]** nedrullningsbara listan:

![](assets/s_ncs_user_wizard_email01_136.png)

Följande alternativ är tillgängliga:

* **Filnamnet anges när leveransmallen skapas**
* **Innehållet i filen anpassas och konverteras till PDF när varje meddelande skickas**
* **Filnamnet beräknas vid leveransanalys (det kan inte bero på mottagarprofilen)**
* **Filnamnet beräknas vid leveranstillfället för varje mottagare (det kan bero på mottagaren)**

### Bifoga en lokal fil {#attach-a-local-file}

Om den bifogade filen är en lokal fil väljer du alternativet: **[!UICONTROL File name is specified when creating the delivery template]**. Filen markeras lokalt och överförs till servern. Följ stegen nedan:

1. Markera filen som ska överföras i **[!UICONTROL Local file]** fältet.
1. Ange etiketten om det behövs. Etiketten ersätter filnamnet när den visas i meddelandesystem. Om inget anges används filnamnet som standard.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_02.png)

1. Om det behövs markerar du **[!UICONTROL Upload file on the server]** och klickar sedan på **[!UICONTROL Update on server]** för att starta överföringen.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_01.png)

   Filen är sedan tillgänglig på servern för att bifogas till de olika leveranser som skapas från den här mallen.

### Bifoga ett personligt meddelande {#attach-a-personalized-message}

Med det här alternativet **[!UICONTROL The file content is personalized and converted into PDF format at the time of delivery for each message]** kan du välja en fil med anpassningsfält, till exempel efternamnet och förnamnet för den avsedda mottagaren.

![](assets/s_ncs_user_wizard_email_calc_attachement_06.png)

Använd följande konfigurationssteg för den här typen av bifogad fil:

1. Markera filen som ska överföras.

   >[!NOTE]
   >
   >Källfilen måste skapas i LibraryOffice. Instansen måste konfigureras enligt de krav som anges i [det här avsnittet](../../installation/using/before-starting.md).

1. Ange etiketten om det behövs.
1. Markera **[!UICONTROL Upload file on the server]** och klicka sedan på **[!UICONTROL Update on server]** för att starta överföringen.
1. Du kan visa en förhandsgranskning. Välj en mottagare om du vill göra det.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_07.png)

1. Analysera leveransen och starta den sedan.

   Varje mottagare får en skräddarsydd PDF som bifogas leveransen.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_08.png)

### Bifoga en beräknad fil {#attach-a-calculated-file}

Du kan beräkna namnet på den bifogade filen under färdigställandet av leveransen. Välj alternativet **[!UICONTROL The file name is calculated during delivery analysis (it cannot depend on the recipient)]**.

>[!NOTE]
>
>Det här alternativet används bara när leveransen skickas av en extern process eller ett arbetsflöde.

1. Ange den etikett som du vill använda för den bifogade filen.
1. Ange filens åtkomstsökväg och dess exakta namn i definitionsfönstret.

   >[!CAUTION]
   >
   >Filen måste finnas på servern.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_04.png)

1. Analysera och påbörja sedan leveransen.

   Filnamnsberäkningen visas i analysloggen.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_05.png)

### Bifoga en personlig fil {#attach-a-personalized-file}

När du markerar den bifogade filen kan du välja alternativet **[!UICONTROL The file name is calculated during delivery for each recipient (it can depend on the recipient)]**. Du kan sedan mappa mottagarnas personaliseringsdata med namnet på filen som ska skickas.

>[!NOTE]
>
>Det här alternativet används bara när leveransen skickas av en extern process eller ett arbetsflöde.

1. Ange den etikett som du vill använda för den bifogade filen.
1. Ange filens åtkomstsökväg och dess exakta namn i definitionsfönstret. Om filnamnet är anpassat kan du använda personaliseringsfälten för relevanta värden.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_010.png)

   >[!CAUTION]
   >
   >Filen måste finnas på servern.

1. Analysera och påbörja sedan leveransen.

   I exemplet nedan valdes den bifogade filen utifrån dess namn så som det definierats med hjälp av kopplingsfälten.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_011.png)

### Inställningar för bifogade filer {#attachment-settings}

För de första två alternativen kan du välja **[!UICONTROL Upload file on the server]** genom att välja lämpligt alternativ. Med **[!UICONTROL Update the file on the server]** länken kan du börja överföra.

![](assets/s_ncs_user_wizard_email01_137.png)

Ett meddelande om att filen har överförts till servern:

![](assets/s_ncs_user_wizard_email01_1371.png)

Ett varningsmeddelande visas för en ändring av filen:

![](assets/s_ncs_user_wizard_email01_1372.png)

På fliken **[!UICONTROL Advanced]** kan du definiera avancerade alternativ för bifogade filer:

* Du kan definiera filteralternativ för att undvika att skicka den bifogade filen till alla mottagare. Alternativet **[!UICONTROL Enable filtering of recipients who will receive the attachment]** aktiverar ett inmatningsfält som används för att definiera ett mottagarvalsskript, som måste anges i JavaScript.
* Du kan skripta namnet på filen för att anpassa den.

   Ange texten i fönstret och använd de anpassningsfält som finns i listrutan. I följande exempel anpassas filnamnet så att det innehåller dagens datum och namnet på mottagaren.

   ![](assets/s_ncs_user_wizard_email_calc_attachement_09.png)
