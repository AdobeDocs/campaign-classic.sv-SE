---
product: campaign
title: Kontrollregler
description: Lär dig arbeta med kontrollregler i Adobe Campaign
role: User, Data Engineer
feature: Typology Rules, Campaigns
hide: true
hidefromtoc: true
exl-id: 5a5f26f6-38da-4488-aadb-81fcb5359331
source-git-commit: 4f809011a8b4cb3803c4e8151e358e5fd73634e4
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 1%

---

# Kontrollregler{#control-rules}

## Kontrollregler för analys och skiljeförfarande {#analysis-and-arbitration-control-rules}

Med kontrollregler kan du garantera giltigheten och kvaliteten på meddelanden före leverans: teckenvisning, SMS-storlek, adressformat osv.

Med en uppsättning färdiga regler kan du utföra vanliga kontroller. Dessa kontroller (visas i fet stil i gränssnittet) är:

* **[!UICONTROL Object approval]** (e-post): kontrollerar att avsändarobjektet och adressen inte innehåller specialtecken som kan orsaka problem för vissa e-postagenter.
* **[!UICONTROL URL label approval]** (e-post): kontrollerar att varje spårnings-URL har en etikett.
* **[!UICONTROL URL approval]** (e-post): kontrollerar spårnings-URL:er (närvaron av tecknet &quot;&amp;&quot;).
* **[!UICONTROL Message size approval]** (mobil): kontrollerar storleken på SMS-meddelanden.
* **[!UICONTROL Validity period check]** (e-post): kontrollerar att giltighetsperioden för leveransen är tillräckligt lång för att skicka alla meddelanden.
* **[!UICONTROL Proof size check]** (alla kanaler): genererar ett felmeddelande om målpopulationen för korrektur överstiger 100 mottagare.
* **[!UICONTROL Wave scheduling check]** (e-post): Kontrollerar att den senaste leveransvågen är schemalagd att påbörjas före giltighetsperiodens slut, om leveransen bryts ned i flera påfyllnader.
* **[!UICONTROL Unsubscription link approval]** (e-post): kontrollerar om det finns minst en avanmälnings-URL i varje innehåll (HTML och Text).

## Skapa en kontrollregel {#creating-a-control-rule}

Det går att skapa nya kontrollregler som passar dina behov. Om du vill göra det skapar du en **[!UICONTROL Control]**-typologiregel och anger kontrollformeln i SQL på fliken **[!UICONTROL Code]**.

**Exempel:**

I följande exempel ska vi skapa en regel som förhindrar att ett SMS-erbjudande skickas till fler än 100 mottagare. Denna regel kommer att kopplas till en kampanjtypologi och sedan till de SMS-leveranser som det aktuella erbjudandet är tillgängligt för.

Använd följande steg:

1. Skapa en typologiregel för **[!UICONTROL Control]**. Välj en **[!UICONTROL Warning]**-varningsnivå.

   ![](assets/campaign_opt_create_control_01.png)

1. På fliken **[!UICONTROL Code]** anger du det skript som ska tillämpa det önskade tröskelvärdet, som visas nedan:

   ![](assets/campaign_opt_create_control_02.png)

   Skriptet utlöser en varning om leveransmålet överstiger 100 kontakter:

   ```
   if( delivery.FCP == false && delivery.properties.toDeliver > 100 ) { logWarning("Significant number of SMS to deliver (" + delivery.properties.toDeliver + "). Please make sure the target is correct.") return false; } return true
   ```

1. Länka den här regeln till en kampanjtypologi och referera till typologin i den aktuella SMS-leveransen.

   ![](assets/campaign_opt_create_control_03.png)

1. Vid leveransanalys tillämpas regeln och en varning skapas om tillämpligt.

   ![](assets/campaign_opt_create_control_04.png)

   Leveransen är dock fortfarande klar att skickas.

   Om du ökar aviseringsnivån förhindrar detta att leveransen startar.

   ![](assets/campaign_opt_create_control_05.png)

   När analysen är klar är knappen **[!UICONTROL Confirm delivery]** inte tillgänglig.

   ![](assets/campaign_opt_create_control_06.png)
