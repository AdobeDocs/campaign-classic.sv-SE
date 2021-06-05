---
product: campaign
title: Webbanalys
description: Läs mer om Web Analytics-paketet
audience: workflow
content-type: reference
topic-tags: technical-workflows
source-git-commit: 4a41aea9edfe5e6ca0454049cbb2892449eec153
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 3%

---


# Webbanalys{#web-analytics}

Arbetsflödena som beskrivs nedan installeras som standard med **Web Analytics-anslutningarna**-modulen. Mer information om den här modulen finns i [avsnittet](../../platform/using/adobe-analytics-connector.md).

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
   <td> Med det här arbetsflödet kan ni skicka kampanjindikatorer från Adobe Campaign till Adobe Experience Cloud Suite via Adobe® Analytics-kontakten. De berörda indikatorerna är följande: <strong>Skickat</strong> (Skickat), <strong>Totalt antal öppningar</strong> (iTotalRecipientOpen), <strong>Totalt antal mottagare som klickat på</strong> (iTotalRecipientClick), <strong>Fel</strong> (iError), <strong>OO pt-Out</strong> (opt-out) (OptionOut).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Identifiering av konverterade kontakter</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsFindConverted</span> <br /> </td> 
   <td> Det här arbetsflödet indexerar besökare som har slutfört sitt köp efter en ny marknadsföringskampanj. Data som återställs av det här arbetsflödet finns i <span class="uicontrol">rapporten om effektivitet vid återmarknadsföring</span> (se den här <a href="../../platform/using/adobe-analytics-connector.md#creating-a-re-marketing-campaign">-sidan</a>). <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Rensa händelse</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsPurgeWebEvents</span> <br /> </td> 
   <td> Med det här arbetsflödet kan du ta bort alla händelser från databasfältet enligt den period som konfigurerats i fältet <span class="uicontrol">Lifespan</span>. <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Återställning av webbhändelser</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsGetWebEvents</span> <br /> </td> 
   <td> Varje timme laddar det här arbetsflödet ned segment för internetanvändare på en viss webbplats, placerar dem i Adobe Campaign-databasen och startar arbetsflödet för ommarknadsföring. <br /> </td> 
  </tr> 
 </tbody> 
</table>

