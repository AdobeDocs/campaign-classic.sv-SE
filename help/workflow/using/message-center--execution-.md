---
product: campaign
title: Meddelandecenter (körning)
description: Meddelandecenter (körning)
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
feature: Workflows
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 5%

---


# Meddelandecenter (körning){#message-center-execution}



Arbetsflödena nedan installeras tillsammans med **Meddelandecenter - körning** tillägg som standard.

Beroende på vilken Campaign-version du har finns mer information i följande avsnitt:

![](assets/do-not-localize/v7.jpeg)[Dokumentation för Campaign v7](../../message-center/using/about-transactional-messaging.md)

![](assets/do-not-localize/v8.png)[Kampanjdokumentation v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/transactional.html)

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etikett</strong><br /> </td> 
   <td> <strong>Internt namn</strong><br /> </td> 
   <td> <strong>Beskrivning</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Uppdatera händelsestatus</span> <br /> </td> 
   <td> <span class="uicontrol">updateEventsStatus</span> <br /> </td> 
   <td> Med det här arbetsflödet kan du tilldela en status till en händelse. Händelsestatus är följande:<br /> 
    <ul> 
     <li> <p><strong>Väntande</strong>: händelsen finns i en kö. Ingen meddelandemall har ännu kopplats till den.</p> </li> 
     <li> <p><strong>Väntande leverans</strong>: händelsen finns i en kö, en meddelandemall har kopplats till den och bearbetas för närvarande av leveransen.</p> </li> 
     <li> <p><strong>Skickat</strong>: den här statusen kopieras från leveransloggarna. Det betyder att leveransen har skickats.</p> </li> 
     <li> <p><strong>Ignoreras av leveransen</strong>: den här statusen kopieras från leveransloggarna. Det betyder att leveransen har ignorerats.</p> </li> 
     <li> <p><strong>Leveransfel</strong>: den här statusen kopieras från leveransloggarna. Det innebär att leveransen har misslyckats.</p> </li> 
     <li> <p><strong>Händelsen täcks inte</strong>: händelsen kunde inte kopplas till en meddelandemall. Händelsen kommer inte att bearbetas på nytt.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Bearbetar grupphändelser</span> <br /> </td> 
   <td> <span class="uicontrol">batchEventsProcessing</span> <br /> </td> 
   <td> Med det här arbetsflödet kan du placera grupphändelser i en kö innan du associerar dem med en meddelandemall. <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Bearbeta realtidshändelser</span> <br /> </td> 
   <td> <span class="uicontrol">rtEventsProcessing</span> <br /> </td> 
   <td> Med det här arbetsflödet kan du placera realtidshändelser i en kö innan du associerar dem med en meddelandemall. <br /> </td> 
  </tr> 
 </tbody> 
</table>

