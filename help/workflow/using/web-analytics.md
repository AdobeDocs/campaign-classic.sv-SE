---
title: Webbanalys
seo-title: Webbanalys
description: Webbanalys
seo-description: null
page-status-flag: never-activated
uuid: 63742453-16d9-48c2-9a3d-d96f5b131fb3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: cc2d4741-2b26-4933-a28d-5dd7b5f436be
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Webbanalys{#web-analytics}

Arbetsflödena som beskrivs nedan installeras som standard med **anslutningsmodulen** för Web Analytics. Mer information om den här modulen finns i det här [avsnittet](../../platform/using/adobe-analytics-data-connector.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etikett</strong><br /> </td> 
   <td> <strong>Internt namn</strong><br /> </td> 
   <td> <strong>Beskrivning</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Skicka indikatorer och kampanjattribut</span><br /> </td> 
   <td> <span class="uicontrol">webAnalyticsSendMetrics</span><br /> </td> 
   <td> Med det här arbetsflödet kan ni skicka indikatorer för e-postkampanjer från Adobe Campaign till Adobe Experience Cloud Suite via Adobe® Genesis-kontakten. De berörda indikatorerna är följande: <strong>Skickat</strong> (Skickat), <strong>Totalt antal öppningar</strong> (iTotalRecipientOpen), <strong>Totalt antal mottagare som klickade</strong> (iTotalRecipientClick), <strong>Fel</strong> (iError), <strong>Avanmäl</strong> (avanmäl) (iOptOut).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Identifiering av konverterade kontakter</span><br /> </td> 
   <td> <span class="uicontrol">webAnalyticsFindConverted</span><br /> </td> 
   <td> Det här arbetsflödet indexerar besökare som har slutfört sitt köp efter en ny marknadsföringskampanj. Data som återställs av det här arbetsflödet finns i rapporten <span class="uicontrol"></span> Effektiv ommarknadsföring (se den här <a href="../../platform/using/adobe-analytics-data-connector.md#creating-a-re-marketing-campaign"> sidan</a>). <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Rensa</span> händelse <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsPurgeWebEvents</span><br /> </td> 
   <td> Med det här arbetsflödet kan du ta bort alla händelser från databasfältet enligt den period som har konfigurerats i fältet <span class="uicontrol">Lifespan</span> . <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Återställning av webbhändelser</span><br /> </td> 
   <td> <span class="uicontrol">webAnalyticsGetWebEvents</span><br /> </td> 
   <td> Varje timme laddar det här arbetsflödet ned segment för internetanvändarbeteende på en viss webbplats, placerar dem i Adobe Campaign-databasen och startar arbetsflödet för ommarknadsföring. <br /> </td> 
  </tr> 
 </tbody> 
</table>

