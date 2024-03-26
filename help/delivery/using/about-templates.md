---
product: campaign
title: Om mallar
description: Kom igång med leveransmallar
badge-v7: label="v7" type="Informative" tooltip="Gäller Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Delivery Templates
role: User
exl-id: d943898c-06fe-451d-aa28-8a95665f4112
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 1%

---

# Om mallar{#about-templates}

En leveranskonfiguration kan sparas i en leveransmall för återanvändning. Mallen kan innehålla en fullständig eller partiell konfiguration av leveransen.

Leveransmallen kan köras manuellt, enligt beskrivningen i detta kapitel, eller enligt en händelse (som startas vid en viss tidpunkt, när en fil anländer till en server, osv.). Leveransmallar kan konfigureras via **[!UICONTROL Resources > Templates > Delivery templates]** i trädet.

![](assets/s_user_template_list.png)

Det finns två typer av mallar:

1. Adobe Campaign inbyggda leveransmallar

   Inbyggda mallar FÅR INTE tas bort från systemet. De innehåller en minimikonfiguration för varje leveranskanal. Administratören kan dock begränsa vissa funktioner eller erbjuda standardvärden till användare (spårningsaktivering, e-postadresser till avsändaren osv.). Inbyggda scenarier visas i fet stil i listan med mallar. De måste dupliceras för att kunna ändras.

1. Fördefinierade leveransmallar

   Adobe Campaign-administratören kan skapa nya leveransmallar. De kan återanvändas av operatorer (de med lämpliga åtkomsträttigheter) eller automatiskt av serverprocesser. Du kan till exempel konfigurera en e-postleveransmall, och när användare skapar en leverans med den här mallen behöver de bara ange texten eller HTML-innehållet och sedan leverera det. De andra alternativen har redan definierats av administratören.

>[!NOTE]
>
>Vilka mallar som är tillgängliga beror på din åtkomstbehörighet, instanskonfigurationen och kontexten. När du t.ex. skapar en informationstjänst kan du länka en leveransmall för bekräftelsemeddelanden: du kan då bara komma åt mallar vars målmappning är prenumerationsmappningen. Mer information finns i [Välj en målmappning](selecting-a-target-mapping.md) och [Tjänster och prenumerationer](about-services-and-subscriptions.md).
