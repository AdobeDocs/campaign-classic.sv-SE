---
solution: Campaign Classic
product: campaign
title: Kontrollregler
description: Kontrollregler
audience: campaign
content-type: reference
topic-tags: campaign-optimization
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 1%

---


# Kontrollregler{#control-rules}

## Kontrollregler för analys och skiljeförfarande {#analysis-and-arbitration-control-rules}

Med kontrollregler kan du garantera giltigheten och kvaliteten på meddelanden före leverans: teckenvisning, SMS-storlek, adressformat osv.

Med en uppsättning färdiga regler kan du utföra vanliga kontroller. Dessa kontroller (visas i fet stil i gränssnittet) är:

* **[!UICONTROL Object approval]** (e-post): kontrollerar att avsändarobjektet och avsändaradressen inte innehåller specialtecken som kan orsaka problem för vissa e-postagenter.
* **[!UICONTROL URL label approval]** (e-post): kontrollerar att varje spårnings-URL har en etikett.
* **[!UICONTROL URL approval]** (e-post): kontrollerar spårnings-URL:er (om tecknet &quot;&amp;&quot; finns).
* **[!UICONTROL Message size approval]** (mobil): kontrollerar storleken på SMS-meddelanden.
* **[!UICONTROL Validity period check]** (e-post): kontrollerar att giltighetsperioden för leveransen är tillräckligt lång för att skicka alla meddelanden.
* **[!UICONTROL Proof size check]** (alla kanaler): genererar ett felmeddelande om målgruppen för korrektur överstiger 100 mottagare.
* **[!UICONTROL Wave scheduling check]** (e-post): kontrollerar att den sista leveranshastigheten är planerad att påbörjas före utgången av giltighetsperioden, om leveransen delas upp i flera vågor.
* **[!UICONTROL Unsubscription link approval]** (e-post): kontrollerar om det finns minst en avanmälan (avanmälan)-URL i varje innehåll (HTML och Text).

## Creating a control rule {#creating-a-control-rule}

Det går att skapa nya kontrollregler som passar dina behov. Det gör du genom att skapa en **[!UICONTROL Control]** typologiregel och ange kontrollformeln i SQL på **[!UICONTROL Code]** fliken.

**Exempel:**

I följande exempel ska vi skapa en regel som förhindrar att ett SMS-erbjudande skickas till fler än 100 mottagare. Denna regel kommer att kopplas till en kampanjtypologi och sedan till de SMS-leveranser som det aktuella erbjudandet är tillgängligt för.

Använd följande steg:

1. Skapa en **[!UICONTROL Control]** typologiregel. Välj en **[!UICONTROL Warning]** varningsnivå.

   ![](assets/campaign_opt_create_control_01.png)

1. På **[!UICONTROL Code]** fliken anger du det skript som ska använda det önskade tröskelvärdet, som visas nedan:

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

   När analysen är klar är knappen inte tillgänglig **[!UICONTROL Confirm delivery]** .

   ![](assets/campaign_opt_create_control_06.png)

