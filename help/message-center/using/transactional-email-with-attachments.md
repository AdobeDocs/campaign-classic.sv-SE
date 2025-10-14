---
product: campaign
title: Skicka transaktionsmeddelanden med bilagor via e-post
description: Lär dig hur du skickar transaktionsmejl med personliga och/eller personliga bilagor med Adobe Campaign
feature: Transactional Messaging, Message Center
exl-id: 755d2364-f6c4-4943-97e8-3ed52a0f2665
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '667'
ht-degree: 1%

---

# Användningsfall: Skicka transaktionsmejl med bilagor {#transactional-email-with-attachments}



Syftet med det här användningsexemplet är att lägga till e-postbilagor direkt till utgående utskick.

## Viktiga steg {#key-steps}

I det här scenariot får du lära dig hur du skickar transaktionsmeddelanden med personliga och/eller personliga bilagor. De bifogade filerna kommer inte att överföras i förväg till Transactional Messaging-servern. I stället genereras de i farten.

När du hämtar in kundinteraktioner eller kundinformation kan du behöva skicka tillbaka den här informationen till kunden i slutet av processen, till exempel i en PDF-fil som bifogas ett e-postmeddelande.

Nedan beskrivs huvudstegen i det här scenariot:

1. Kunden kommer till webbplatsen och hittar en produkt som han/hon vill köpa.
1. Kunden väljer produkten och anpassar några alternativ.
1. Kunden slutför transaktionen.
1. Ett e-postmeddelande skickas till kunden som bekräftar transaktionen. Eftersom det inte rekommenderas att skicka ut PII-filer (personligt identifierbar information) i e-postmeddelandet genereras en säker PDF som bifogas i e-postmeddelandet.
1. Kunden får det mejl och den bilaga som innehåller relevanta data.

I det här scenariot är de bifogade filerna inte färdiga, utan läggs till direkt i de utgående e-postmeddelandena, vilket ger följande fördelar:

* På så sätt kan du anpassa innehållet i den bifogade filen.
* Om den bifogade filen är kopplad till en transaktion (som i det exempel som beskrivs ovan) kan den innehålla dynamiska data som genereras under kundprocessen.
* Genom att bifoga PDF-filer optimeras säkerheten eftersom du kan kryptera dem och skicka dem via HTTPS.

## Rekommendationer och skyddsförslag {#important-notes}

För att undvika prestandaproblem får bilderna i e-postmeddelanden inte överstiga 100 kB. Den här gränsen, som är inställd som standard, kan ändras från alternativet `NmsDelivery_MaxDownloadedImageSize`. Adobe rekommenderar dock att du undviker stora bilder i e-postutskick.

Adobe rekommenderar också att du begränsar storleken och antalet bifogade filer. Som standard kan du bara lägga till en fil som en bifogad fil i ett e-postmeddelande. Det här tröskelvärdet kan konfigureras från alternativet `NmsDelivery_MaxRecommendedAttachments`.

Läs mer i [listan med Campaign Classic-alternativ](../../installation/using/configuring-campaign-options.md#delivery).

Läs riktlinjerna nedan innan du implementerar detta scenario:

* Transactional Messaging-instanserna ska inte användas för att lagra, exportera eller överföra filer eller data. De kan bara användas för händelsedata och relaterad information. De bör inte betraktas som ett fillagringssystem.
* Eftersom det inte finns någon direkt åtkomst till Transactional Messaging-instanser eller -servrar utanför Adobe finns det inget standardsätt att skicka sådana filer till dessa servrar (ingen FTP-åtkomst).
* Det är inte korrekt enligt avtalet att använda diskutrymmet på Transactional Messaging-instanserna för att lagra filer av någon typ, inte ens för bilagor.
* Du måste använda ett annat onlinesystem för att ha dessa filer. Du behöver FTP-åtkomst till det här systemet och du måste kunna skriva och ta bort filer.

>[!NOTE]
>
>För att undvika prestandaproblem rekommenderar vi att du inte inkluderar mer än en bifogad fil per e-post. Det rekommenderade tröskelvärdet kan konfigureras från [listan med Campaign Classic-alternativ](../../installation/using/configuring-campaign-options.md#delivery).

## Implementering {#implementation}

Diagrammet nedan visar de olika stegen för implementering av det här scenariot:

![](assets/message-center-uc1.png)

Om du vill lägga till en e-postbilaga i ett transaktionsmeddelande följer du stegen nedan:

1. Börja med att utforma den bifogade filen. Mer information finns i [dokumentationen för Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/attaching-files.html#attach-a-personalized-file){target="_blank"}.

   Detta gör att du kan bifoga filerna till ett e-postmeddelande, även om de inte finns på körningsinstansen.

1. Du kan skicka e-postmeddelanden via en meddelandeutlösare från SOAP. I SOAP-anropet finns en URL-parameter (attachmentURL).

   Mer information om SOAP-begäranden finns i [Händelsebeskrivning](../../message-center/using/event-description.md).

1. När du utformar din e-post klickar du på **[!UICONTROL Attachment]**.

1. Ange parametern för bifogade SOAP-filer på skärmen **[!UICONTROL Attachment definition]**:

   ```
   <%= rtEvent.ctx.attachmentUrl %>
   ```

1. När meddelandet bearbetas hämtar systemet filen från fjärrplatsen (tredjepartsserver) och bifogar den till det enskilda meddelandet.

   Eftersom den här parametern kan vara en variabel bör den acceptera den fullständiga URL-variabeln för filen som skickas via SOAP-anropet.

   ![](assets/message-center-uc2.png)
