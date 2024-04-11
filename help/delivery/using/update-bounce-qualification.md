---
product: campaign
title: Uppdatera studskompetens efter avbrott i Apple 2021
description: Lär dig hur du uppdaterar studskvalifikation efter ett avbrott i Apple 2021
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Deliverability
exl-id: 34be23f7-17fa-475e-9663-2e353d76b172
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# Uppdatera felaktiga hårddiskmarkeringar efter Apple avbrott {#update-bounce-qualification.md}

## Kontext

Den 26 april 2021 resulterade ett globalt problem på Apple i att vissa e-postmeddelanden som skickades till giltiga Apple-e-postadresser felaktigt studsade som ogiltiga e-postadresser av Apple-servrar med följande studs:&quot;550 5.1.1 &quot;email address&quot;: user lookup success but no user record.&quot;

Problemet inträffade den 26/4 och varade 07:00-17:00 EST.

>[!NOTE]
>
>Du kan kontrollera Apple System Status Dashboard på [den här sidan](https://www.apple.com/support/systemstatus/).

Om en Internet-leverantör skulle råka ut kan e-postmeddelanden som skickas via Campaign inte levereras till mottagaren: dessa e-postmeddelanden markeras felaktigt som studsar.

Enligt standardlogiken för studshantering har Adobe Campaign automatiskt lagt till dessa mottagare i karantänlistan med en **[!UICONTROL Status]** inställning för **[!UICONTROL Quarantine]**. För att korrigera detta måste du uppdatera din karantäntabell i Campaign genom att söka efter och ta bort de här mottagarna eller ändra deras **[!UICONTROL Status]** till **[!UICONTROL Valid]** så att nattrensningsarbetsflödet tar bort dem.

Om du vill hitta de mottagare som påverkades av det här problemet, eller om det händer igen med någon annan Internet-leverantör, kan du läsa instruktionerna nedan.

## Process som ska uppdateras

Du måste köra en fråga i din karantäntabell för att filtrera bort alla Apple-mottagare - som innehåller @icloud.com, @me.com, @mac.com - som eventuellt påverkades av driftsavbrottet så att de kan tas bort från karantänlistan och inkluderas i framtida e-postleveranser för Campaign.

Baserat på tidsramen för incidenten är nedanstående de rekommenderade riktlinjerna för frågan.

>[!IMPORTANT]
>
>Dessa datum/tider baseras på EST (Eastern Standard Time Zone). Justera efter instansens tidszon.

* För Campaign-instanser med SMTP-studssvarsinformation i **[!UICONTROL Error text]** karantänlistans fält:

   * **Feltext (karantäntext)** innehåller &quot;användarsökning lyckades men ingen användarpost hittades&quot; OCH **Feltext (karantäntext)** innehåller &quot;support.apple.com&quot;
   * **Uppdateringsstatus (@lastModified)** 4/26/2021 07 eller senare:00:00:00
   * **Uppdateringsstatus (@lastModified)** senast 2021-04-26:00:00 PM

* För Campaign-instanser med information om regel för inkommande e-post i **[!UICONTROL Error text]** karantänlistans fält:

   * **Feltext (karantäntext)** innehåller &quot;Momen_Code10_InvalidRecipient&quot;
   * **E-postdomän (@domän)** lika med icloud.com OR **E-postdomän (@domän)** lika med me.com OR **E-postdomän (@domän)** lika med mac.com
   * **Uppdateringsstatus (@lastModified)** 4/26/2021 07 eller senare:00:00:00
   * **Uppdateringsstatus (@lastModified)** senast 2021-04-26:00:00 PM

När du har en lista över mottagare som påverkas kan du antingen ställa in deras status **[!UICONTROL Valid]** så att de tas bort från karantänlistan av **[!UICONTROL Database cleanup]** eller bara ta bort dem från tabellen.

**Relaterade ämnen:**
* [Förstå leveransfel](understanding-delivery-failures.md)
* [E-poststudsar](understanding-delivery-failures.md#bounce-mail-qualification)
