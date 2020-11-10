---
title: Webbanalys
description: Läs mer om Web Analytics-paketet
page-status-flag: never-activated
uuid: 63742453-16d9-48c2-9a3d-d96f5b131fb3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: cc2d4741-2b26-4933-a28d-5dd7b5f436be
translation-type: tm+mt
source-git-commit: 6be6c353c3464839a74ba857d8d93d0f68bc8865
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 3%

---


# Webbanalys{#web-analytics}

Arbetsflödena som beskrivs nedan installeras som standard med **anslutningsmodulen** för Web Analytics. For more on this module, refer to this [section](../../platform/using/adobe-analytics-data-connector.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etikett</strong><br /> </td> 
   <td> <strong>Internt namn</strong><br /> </td> 
   <td> <strong>Beskrivning</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Skicka indikatorer och kampanjattribut</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsSendMetrics</span> <br /> </td> 
   <td> Med det här arbetsflödet kan du skicka indikatorer för e-postkampanjer från Adobe Campaign till Adobe Experience Cloud Suite via Adobe® Genesis Connector. De berörda indikatorerna är följande: <strong>Skickat</strong> (Skickat), <strong>totalt antal öppningar</strong> (iTotalRecipientOpen), <strong>totalt antal mottagare som klickade</strong> (iTotalRecipientClick), <strong>Fel</strong> (iError), <strong>Avanmäl</strong> (avanmäl) (iOptOut).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Identifiering av konverterade kontakter</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsFindConverted</span> <br /> </td> 
   <td> Det här arbetsflödet indexerar besökare som har slutfört sitt köp efter en ny marknadsföringskampanj. Data som återställs av det här arbetsflödet finns i rapporten <span class="uicontrol"></span> Effektiv ommarknadsföring (se den här <a href="../../platform/using/adobe-analytics-data-connector.md#creating-a-re-marketing-campaign"> sidan</a>). <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Rensa händelse</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsPurgeWebEvents</span> <br /> </td> 
   <td> Med det här arbetsflödet kan du ta bort alla händelser från databasfältet enligt den period som har konfigurerats i fältet <span class="uicontrol">Lifespan</span> . <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Återställning av webbhändelser</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsGetWebEvents</span> <br /> </td> 
   <td> Varje timme laddar det här arbetsflödet ned segment för internetanvändare på en viss webbplats, placerar dem i Adobe Campaign-databasen och startar arbetsflödet för ommarknadsföring. <br /> </td> 
  </tr> 
 </tbody> 
</table>

