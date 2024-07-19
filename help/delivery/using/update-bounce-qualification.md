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

# Uppdatera felaktiga hårddiskgränser efter Apple-avbrott {#update-bounce-qualification.md}

## Kontext

Den 26 april 2021 resulterade ett globalt problem på Apple i att vissa e-postmeddelanden som skickades till giltiga Apple-e-postadresser felaktigt studsade som ogiltiga e-postadresser av Apple-servrar med följande studs:&quot;550 5.1.1 &quot;email address&quot;: user lookup success but no user record.&quot;

Problemet inträffade den 26/4 och varade 07:00-17:00 EST.

>[!NOTE]
>
>Du kan kontrollera Apple System Status Dashboard på [den här sidan](https://www.apple.com/support/systemstatus/).

Om en Internet-leverantör skulle råka ut kan e-postmeddelanden som skickas via Campaign inte levereras till mottagaren: dessa e-postmeddelanden markeras felaktigt som studsar.

Med hjälp av standardlogik för studshantering har Adobe Campaign automatiskt lagt till de här mottagarna i karantänlistan med **[!UICONTROL Status]**-inställningen **[!UICONTROL Quarantine]**. För att korrigera detta måste du uppdatera karantäntabellen i Campaign genom att hitta och ta bort de här mottagarna, eller ändra deras **[!UICONTROL Status]** till **[!UICONTROL Valid]** så att de tas bort i nattrensningsarbetsflödet.

Om du vill hitta de mottagare som påverkades av det här problemet, eller om det händer igen med någon annan Internet-leverantör, kan du läsa instruktionerna nedan.

## Process som ska uppdateras

Du måste köra en fråga i din karantäntabell för att filtrera bort alla Apple-mottagare - som innehåller @icloud.com, @me.com, @mac.com - som eventuellt påverkades av driftsavbrottet så att de kan tas bort från karantänlistan och inkluderas i framtida e-postleveranser för Campaign.

Baserat på tidsramen för incidenten är nedanstående de rekommenderade riktlinjerna för frågan.

>[!IMPORTANT]
>
>Dessa datum/tider baseras på EST (Eastern Standard Time Zone). Justera efter instansens tidszon.

* För Campaign-instanser med SMTP-studssvarsinformation i fältet **[!UICONTROL Error text]** i karantänlistan:

   * **Feltext (karantänstext)** innehåller &quot;användarsökning lyckades men ingen användarpost hittades&quot; OCH **Feltexten (karantänstext)** innehåller &quot;support.apple.com&quot;
   * **Uppdatera status (@lastModified)** den 26/2021 07:00:00
   * **Uppdateringsstatus (@lastModified)** senast 2021-01-04-26:00:00

* För Campaign-instanser med regelinformation för inkommande e-post i fältet **[!UICONTROL Error text]** i karantänlistan:

   * **Feltext (karantäntext)** innehåller &quot;Momen_Code10_InvalidRecipient&quot;
   * **E-postdomänen (@domain)** är lika med icloud.com ELLER **E-postdomänen (@domain)** är lika med me.com ELLER **E-postdomän (@domain)** är lika med mac.com
   * **Uppdatera status (@lastModified)** den 26/2021 07:00:00
   * **Uppdateringsstatus (@lastModified)** senast 2021-01-04-26:00:00

När du har en lista över berörda mottagare kan du antingen ange statusen **[!UICONTROL Valid]** så att de tas bort från karantänlistan av arbetsflödet i **[!UICONTROL Database cleanup]** eller bara ta bort dem från tabellen.

**Relaterade ämnen:**
* [Förstå leveransfel](understanding-delivery-failures.md)
* [E-poststudsar](understanding-delivery-failures.md#bounce-mail-qualification)
