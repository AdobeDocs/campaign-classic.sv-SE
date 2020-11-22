---
solution: Campaign Classic
product: campaign
title: Meddelandecenter (köra)
description: Meddelandecenter (köra)
audience: workflow
content-type: reference
topic-tags: technical-workflows
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 6%

---


# Meddelandecenter (köra){#message-center-execution}

De arbetsflöden som beskrivs nedan installeras som standard med **modulen Meddelandecenter - Körning** . For more on this module, refer to this [section](../../message-center/using/about-transactional-messaging.md).

Mer information om hur du konfigurerar tekniska arbetsflöden för modulen Meddelandecenter finns på [den här sidan](../../message-center/using/technical-workflows.md).

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
     <li> <p><strong>Väntande leverans</strong>: Om händelsen finns i en kö har en meddelandemall kopplats till den och bearbetas av leveransen.</p> </li> 
     <li> <p><strong>Skickat</strong>: den här statusen kopieras från leveransloggarna. Det betyder att leveransen har skickats.</p> </li> 
     <li> <p><strong>Ignoreras av leveransen</strong>: den här statusen kopieras från leveransloggarna. Det betyder att leveransen har ignorerats.</p> </li> 
     <li> <p><strong>Leveransfel</strong>: den här statusen kopieras från leveransloggarna. Det innebär att leveransen har misslyckats.</p> </li> 
     <li> <p><strong>Händelsen omfattas</strong>inte: händelsen inte har kopplats till en meddelandemall. Händelsen kommer inte att bearbetas på nytt.</p> </li> 
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

