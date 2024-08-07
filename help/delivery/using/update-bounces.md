---
product: campaign
title: Uppdatera studskvalificering efter ett avbrott hos en internetleverantör
description: Lär dig hur du uppdaterar studskvalifikation efter ett avbrott i en Internet-leverantör
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Deliverability
hide: true
hidefromtoc: true
exl-id: 7a9afe0a-0219-40f1-9fe2-6374db8d555c
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 3%

---

# Uppdatera felaktiga hårda studsar efter ett ISP-avbrott {#update-bounces}



## Kontext{#update-bounce-context}

Om en Internet-leverantör skulle råka ut kan e-postmeddelanden som skickas via Campaign inte levereras till mottagaren: dessa e-postmeddelanden markeras felaktigt som studsar.

Globala problem på Apple eller Gmail kan till exempel leda till att vissa e-postmeddelanden som skickas till giltiga Apple- eller Gmail-e-postadresser inte studsas korrekt som ogiltiga e-postadresser av ISP-servrarna med följande svar:

* &quot;550 5.1.1 &quot;e-postadress&quot;: användarsökningen lyckades, men ingen användarpost hittades.&quot;

* &quot;550 mottagare avvisade &#39;e-postadress&#39;&quot;

Observera att om uppskjutande studsar med meddelandet&quot;452 requested action aborted: try again later&quot; (452 begärd åtgärd avbröts: try again later) observeras dessa automatiskt och inga åtgärder behövs. De bör förbättras i takt med att Internet-leverantören återvinner sin fulla kapacitet.

>[!NOTE]
>
>Du kan kontrollera Apple System Status Dashboard på [den här sidan](https://www.apple.com/support/systemstatus/){_blank}.
>
>Du kan kontrollera Google Workspace Status Dashboard på [den här sidan](https://www.google.com/appsstatus#hl=en&amp;v=status){_blank}.
>

## Effekt{#update-bounce-impact}

Om en Internet-leverantör skulle råka ut kan e-postmeddelanden som skickas via Campaign inte levereras till mottagaren: dessa e-postmeddelanden markeras felaktigt som studsar.

Med hjälp av standardlogik för studshantering har Adobe Campaign automatiskt lagt till de här mottagarna i karantänlistan med **[!UICONTROL Status]**-inställningen **[!UICONTROL Quarantine]**. För att korrigera detta måste du uppdatera karantäntabellen i Campaign genom att hitta och ta bort de här mottagarna, eller ändra deras **[!UICONTROL Status]** till **[!UICONTROL Valid]** så att de tas bort i nattrensningsarbetsflödet.

Om du vill hitta de mottagare som påverkades av problemet kan du läsa instruktionerna nedan.

## Process som ska uppdateras{#update-bounce-update}

Du måste köra en fråga i karantäntabellen för att filtrera bort alla mottagare som påverkas, till exempel Apple, adresserna som omfattar @icloud.com, @me.com, @mac.com - som eventuellt påverkades av driftsavbrottet så att de kan tas bort från karantänlistan och inkluderas i framtida e-postleveranser för Campaign.

Baserat på tidsramen för incidenten och Internet-leverantören nedan är de rekommenderade riktlinjerna för frågan.

* För Campaign-miljöer med regelinformation för inkommande e-post i fältet **[!UICONTROL Error text]** i karantänlistan:

   * **Feltext (karantäntext)** innehåller &quot;Momen_Code10_InvalidRecipient&quot;
   * **E-postdomänen (@domain)** är lika med domain1.com ELLER **E-postdomänen (@domain)** är lika med domain2.com ELLER **E-postdomän (@domain)** är lika med domain3.com
   * **Uppdatera status (@lastModified)** på eller efter `MM/DD/YYYY HH:MM:SS AM`
   * **Uppdatera status (@lastModified)** på eller före `MM/DD/YYYY HH:MM:SS PM`

* För Campaign-miljöer med SMTP-studssvarsinformation i fältet **[!UICONTROL Error text]** i karantänlistan:

   * **Feltext (karantäntext)** innehåller &quot;550-5.1.1&quot; OCH **Feltexten (karantäntext)** innehåller &quot;support.ISP.com&quot;

     där &quot;support.ISP.com&quot; kan vara: &quot;support.apple.com&quot; eller &quot;support.google.com&quot;, till exempel

   * **Uppdatera status (@lastModified)** på eller efter `MM/DD/YYYY HH:MM:SS AM`
   * **Uppdatera status (@lastModified)** på eller före `MM/DD/YYYY HH:MM:SS PM`


När du har en lista över berörda mottagare kan du antingen ange statusen **[!UICONTROL Valid]** så att de tas bort från karantänlistan av arbetsflödet i **[!UICONTROL Database cleanup]** eller bara ta bort dem från tabellen.

**Relaterade ämnen:**
* [Förstå leveransfel](understanding-delivery-failures.md)
* [E-poststudsar](understanding-delivery-failures.md#bounce-mail-qualification)
