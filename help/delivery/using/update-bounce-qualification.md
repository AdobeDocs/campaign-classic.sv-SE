---
solution: Campaign Classic
product: campaign
title: Uppdatera studskompetens efter ett avbrott i en Internet-leverantör
description: Lär dig hur du uppdaterar studskompetens efter ett avbrott i en Internet-leverantör.
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
hidefromtoc: true
translation-type: tm+mt
source-git-commit: 0c93193ff30737870803f9fb25019f3162dcc96d
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 1%

---


# Uppdatera studskompetens efter ett internetleverantörsavbrott {#update-bounce-qualification.md}

## Kontext

Om en Internet-leverantör skulle råka ut kan e-post som skickas via Campaign inte levereras till mottagaren: dessa e-postmeddelanden markeras felaktigt som studsar.

I december 2020 resulterade ett globalt problem på Gmail i att vissa e-postmeddelanden som skickades till giltiga Gmail-e-postadresser felaktigt studsade som ogiltiga e-postadresser av Gmail-servrar med följande studssvar: *&quot;550-5.1.1 E-postkontot som du försökte nå finns inte.&quot;*

Google har uppgett att de Gmail-avbrott och -avbrott som orsakade problemet började 14 december kl. 6:55 och slutade kl. 18:09 EST den 15 december. Vår dataanalys visade också en mycket kort topp i Gmail-studsar kl. 02:06 EST den 16 december, där majoriteten inträffar den 15 december mellan kl. 2:00 EST och kl. 18.30 EST.

>[!NOTE]
>
>Du kan kontrollera Google Workspace Status Dashboard på [den här sidan](https://www.google.com/appsstatus#hl=en&amp;v=status).


Med hjälp av standardlogik för studshantering har Adobe Campaign automatiskt lagt till de här mottagarna i karantänlistan med **[!UICONTROL Status]**-inställningen **[!UICONTROL Quarantine]**. För att korrigera detta måste du uppdatera karantäntabellen i Campaign genom att hitta och ta bort de här mottagarna, eller ändra deras **[!UICONTROL Status]** till **[!UICONTROL Valid]** så att de tas bort i nattrensningsarbetsflödet.

Om du vill hitta de mottagare som påverkades av Gmail-problemet, eller om det skulle inträffa igen med någon annan Internet-leverantör, läser du instruktionerna nedan.

## Process som ska uppdateras

Du måste köra en fråga i karantäntabellen för att filtrera bort alla Gmail-mottagare (eller andra ISP-mottagare) som eventuellt påverkades av driftsavfallet så att de kan tas bort från karantänlistan och inkluderas i framtida e-postleveranser för kampanjer.

Baserat på tidsramen för incidenten rekommenderas följande riktlinjer för frågan.

>[!IMPORTANT]
>
>Dessa datum/tider baseras på EST (Eastern Standard Time Zone). Justera efter instansens tidszon.

* För Campaign-instanser med SMTP-studssvarsinformation i fältet **[!UICONTROL Error text]** i karantänlistan:

   * **Feltexten (karantänstext)** innehåller&quot;550-5.1.1 E-postkontot som du försökte nå finns inte&quot; OCH  **feltexten (karantänstext)** innehåller&quot;support.google.com&quot; **
   * **Uppdateringsstatus (@lastModified)** 2020-12-14 6:55:00
   * **Uppdateringsstatus (@lastModified)** den 16 december 2020 kl. 6:00:00

* För Campaign-instanser med regelinformation för inkommande e-post i fältet **[!UICONTROL Error text]** i karantänlistan:

   * **Feltext (karantäntext)** innehåller &quot;Momen_Code10_InvalidRecipient&quot;
   * **E-postdomän (@domain)** lika med &quot;gmail.com&quot; ELLER e-postdomän (@domain) lika med &quot;googlemail.com&quot;
   * **Uppdateringsstatus (@lastModified)** 2020-12-14 6:55:00
   * **Uppdateringsstatus (@lastModified)** den 16 december 2020 kl. 6:00:00

När du har en lista över berörda mottagare kan du antingen ange statusen **[!UICONTROL Valid]** så att de tas bort från karantänlistan av arbetsflödet **[!UICONTROL Database cleanup]** eller bara ta bort dem från tabellen.

**Relaterade ämnen:**
* [Förstå leveransfel](../../delivery/using/understanding-delivery-failures.md)
* [Kvalifikation av studsmeddelanden](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification)

