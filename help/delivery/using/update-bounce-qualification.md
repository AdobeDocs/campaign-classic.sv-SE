---
product: campaign
title: Uppdatera studskvalificering efter ett avbrott hos en internetleverantör
description: Lär dig hur du uppdaterar studskompetens efter ett avbrott i en Internet-leverantör.
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
hidefromtoc: true
exl-id: 34be23f7-17fa-475e-9663-2e353d76b172
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 3%

---

# Uppdatera felaktiga hårddiskstudsar efter Apple-avbrott {#update-bounce-qualification.md}

## Kontext

Den 26 april 2021 resulterade ett globalt problem hos Apple i att vissa e-postmeddelanden som skickades till giltiga Apple-e-postadresser felaktigt studsade som ogiltiga e-postadresser av Apple-servrar med följande studssvar:  &quot;550 5.1.1 &#39;e-postadress&#39;: användarsökningen lyckades, men ingen användarpost hittades.&quot;

Problemet inträffade den 26/4 och varade 07:00-17:00 EST.

>[!NOTE]
>
>Du kan kontrollera Apple System Status Dashboard på [den här sidan](https://www.apple.com/support/systemstatus/).

Om en Internet-leverantör skulle råka ut kan e-post som skickas via Campaign inte levereras till mottagaren: dessa e-postmeddelanden markeras felaktigt som studsar.

Med hjälp av standardlogik för studshantering har Adobe Campaign automatiskt lagt till de här mottagarna i karantänlistan med **[!UICONTROL Status]**-inställningen **[!UICONTROL Quarantine]**. För att korrigera detta måste du uppdatera karantäntabellen i Campaign genom att hitta och ta bort de här mottagarna, eller ändra deras **[!UICONTROL Status]** till **[!UICONTROL Valid]** så att de tas bort i nattrensningsarbetsflödet.

Om du vill hitta de mottagare som påverkades av det här problemet, eller om det händer igen med någon annan Internet-leverantör, kan du läsa instruktionerna nedan.

## Process som ska uppdateras

Du måste köra en fråga i din karantäntabell för att filtrera bort alla Apple-mottagare - inklusive @icloud.com, @me.com, @mac.com - som eventuellt påverkades av driftsavbrottet så att de kan tas bort från karantänlistan och inkluderas i framtida e-postleveranser för Campaign.

Baserat på tidsramen för incidenten rekommenderas följande riktlinjer för frågan.

>[!IMPORTANT]
>
>Dessa datum/tider baseras på EST (Eastern Standard Time Zone). Justera efter instansens tidszon.

* För Campaign-instanser med SMTP-studssvarsinformation i fältet **[!UICONTROL Error text]** i karantänlistan:

   * **Feltexten (karantänstext)** innehåller &quot;användarsökning lyckades men ingen användarpost hittades&quot; OCH  **feltexten (karantänstext)** innehåller &quot;support.apple.com&quot;
   * **Uppdateringsstatus (@lastModified)** 2021 07:00:00-04-26
   * **Uppdateringsstatus (@lastModified)** den 26/4021 01 :00:00 PM eller tidigare

* För Campaign-instanser med regelinformation för inkommande e-post i fältet **[!UICONTROL Error text]** i karantänlistan:

   * **Feltext (karantäntext)** innehåller &quot;Momen_Code10_InvalidRecipient&quot;
   * **E-postdomänen (@domain)** är lika med icloud.com ELLER  **e-postdomänen (@domain)** lika med me.com ELLER  **e-postdomänen (@domain)** lika med mac.com
   * **Uppdateringsstatus (@lastModified)** 2021 07:00:00-04-26
   * **Uppdateringsstatus (@lastModified)** den 26/4021 01 :00:00 PM eller tidigare

När du har en lista över berörda mottagare kan du antingen ange statusen **[!UICONTROL Valid]** så att de tas bort från karantänlistan av arbetsflödet **[!UICONTROL Database cleanup]** eller bara ta bort dem från tabellen.

**Relaterade ämnen:**
* [Förstå leveransfel](understanding-delivery-failures.md)
* [Kvalifikation av studsmeddelanden](understanding-delivery-failures.md#bounce-mail-qualification)
