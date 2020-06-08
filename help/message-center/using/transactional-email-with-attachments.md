---
title: Lägga till bilagor i transaktionsmeddelanden med Adobe Campaign Classic
description: Lär dig hur du skickar transaktionsmeddelanden med personliga och/eller personliga bilagor med Adobe Campaign Classic
page-status-flag: never-activated
uuid: 4452d839-318a-49d8-8abb-4ba04c803e9f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: use-case
discoiquuid: 7b8ab9d6-e47e-46d8-99df-da793486654c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 22d0e70f77eb3759632e05ab1cb0d8ee53adfac9
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 0%

---


# Användningsfall: Skicka transaktionsmejl med bilagor{#transactional-email-with-attachments}

Syftet med det här användningsexemplet är att lägga till e-postbilagor direkt till utgående utskick.

## Viktiga steg {#key-steps}

I det här scenariot får du lära dig hur du skickar transaktionsmeddelanden med personliga och/eller personliga bilagor. Bifogade filer överförs inte i förväg till Transactional Messaging-servern: i stället genereras de direkt.

När du hämtar kundinteraktioner eller kundinformation kan du behöva skicka tillbaka informationen till kunden i slutet av processen, till exempel i en PDF-fil som bifogas till ett e-postmeddelande.

Nedan beskrivs huvudstegen i det här scenariot:

1. Kunden kommer till webbplatsen och hittar en produkt som han/hon vill köpa.
1. Kunden väljer produkten och anpassar några alternativ.
1. Kunden slutför transaktionen.
1. Ett e-postmeddelande skickas till kunden som bekräftar transaktionen. Eftersom det inte rekommenderas att skicka ut PII (personligt identifierbar information) i e-postmeddelandet genereras en säker PDF-fil som bifogas till e-postmeddelandet.
1. Kunden får det mejl och den bilaga som innehåller relevanta data.

I det här scenariot är de bifogade filerna inte färdiga, utan läggs till direkt i de utgående e-postmeddelandena, vilket ger följande fördelar:

* På så sätt kan du anpassa innehållet i den bifogade filen.
* Om den bifogade filen är kopplad till en transaktion (som i det exempel som beskrivs ovan) kan den innehålla dynamiska data som genereras under kundprocessen.
* Genom att bifoga PDF-filer optimeras säkerheten eftersom du kan kryptera dem och skicka dem via HTTPS.

>[!NOTE]
>
>För att undvika prestandaproblem bör varje bildstorlek som standard inte överstiga 100 000 byte om du tar med bilder som laddas ned direkt från en anpassad URL som bilaga. Det rekommenderade tröskelvärdet kan konfigureras från [listan med Campaign Classic-alternativ](../../installation/using/configuring-campaign-options.md#delivery).

## Rekommendationer {#important-notes}

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

1. Börja med att utforma den bifogade filen. Mer information finns i [det här avsnittet](../../delivery/using/attaching-files.md#attach-a-personalized-file).

   Detta gör att du kan bifoga filerna till ett e-postmeddelande, även om de inte finns på körningsinstansen.

1. Du kan skicka e-postmeddelanden via en SOAP-utlösare. I SOAP-anropet finns det en URL-parameter (attachmentURL).

   Mer information om SOAP-begäranden finns i [Händelsebeskrivning](../../message-center/using/event-description.md).

1. När du utformar e-postmeddelandet klickar du på **[!UICONTROL Attachment]**.

1. Ange parametern SOAP attachment på **[!UICONTROL Attachment definition]** skärmen:

   ```
   <%= rtEvent.ctx.attachementUrl %>
   ```

1. När meddelandet bearbetas hämtar systemet filen från fjärrplatsen (tredjepartsserver) och bifogar den till det enskilda meddelandet.

   Eftersom den här parametern kan vara en variabel bör den acceptera den fullständiga URL-variabeln för filen, som skickas via SOAP-anropet.

   ![](assets/message-center-uc2.png)
