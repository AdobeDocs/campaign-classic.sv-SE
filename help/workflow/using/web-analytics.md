---
product: campaign
title: Webbanalys
description: Läs mer om Web Analytics-paketet
feature: Workflows, Analytics Integration
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 3%

---


# Webbanalys{#web-analytics}

![](../../assets/v7-only.svg)

Arbetsflödena nedan installeras tillsammans med **Web Analytics-anslutningar** som standard. Mer information om den här modulen finns i [section](../../platform/using/adobe-analytics-connector.md).

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
   <td> Med det här arbetsflödet kan ni skicka kampanjindikatorer från Adobe Campaign till Adobe Experience Cloud Suite via Adobe® Analytics-kontakten. De berörda indikatorerna är följande: <strong>Skickat</strong> (Skickat), <strong>Totalt antal öppningar</strong> (iTotalRecipientOpen), <strong>Totalt antal mottagare som klickat</strong> (iTotalRecipientClick), <strong>Fel</strong> (iError), <strong>Avanmäl dig</strong> (avanmäl dig) (avanmäl dig).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Identifiering av konverterade kontakter</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsFindConverted</span> <br /> </td> 
   <td> Det här arbetsflödet indexerar besökare som har slutfört sitt köp efter en ny marknadsföringskampanj. Data som återställs av det här arbetsflödet kan nås via <span class="uicontrol">Rapport om effektivitet vid återmarknadsföring</span> (Se denna <a href="../../platform/using/adobe-analytics-connector.md#creating-a-re-marketing-campaign"> page</a>). <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Rensa händelse</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsPurgeWebEvents</span> <br /> </td> 
   <td> Med det här arbetsflödet kan du ta bort alla händelser från databasfältet enligt den period som har konfigurerats i <span class="uicontrol">Lifespan</span> fält. <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Återställning av webbhändelser</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsGetWebEvents</span> <br /> </td> 
   <td> Varje timme laddar det här arbetsflödet ned segment för internetanvändare på en viss webbplats, placerar dem i Adobe Campaign-databasen och startar arbetsflödet för ommarknadsföring. <br /> </td> 
  </tr> 
 </tbody> 
</table>

