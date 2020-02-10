---
title: Kontrollregler
seo-title: Kontrollregler
description: Kontrollregler
seo-description: null
page-status-flag: never-activated
uuid: a83e56d0-573a-4592-b2b1-0d3b3e52b03f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: campaign-optimization
discoiquuid: be037a80-3f94-465c-ba7d-ae7d50f70e36
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d30de91002862b664249c5a704b7c0f521dd30f2

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

## Skapa en kontrollregel {#creating-a-control-rule}

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

