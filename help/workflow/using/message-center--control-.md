---
product: campaign
title: Message Center (Control)
description: Message Center (Control)
hide: true
hidefromtoc: true
feature: Workflows
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 1%

---


# Message Center (Control){#message-center-control}



Arbetsflödet som anges nedan är schemalagt att köras varje timme. Den installeras med modulen **Message Center - Control** som standard.


Beroende på vilken Campaign-version du har finns mer information i följande avsnitt:

![](assets/do-not-localize/v7.jpeg) [Kampanjdokumentation v7](../../message-center/using/about-transactional-messaging.md)

![](assets/do-not-localize/v8.png) [Kampanjdokumentation v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/transactional.html)


<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etikett</strong><br /> </td> 
   <td> <strong>Internt namn</strong><br /> </td> 
   <td> <strong>Beskrivning</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Meddelandecenter &lt;external_account_name&gt;<br /> </td> 
   <td> mcSynch_&lt;external_account_name&gt;<br /> </td> 
   <td> Det här arbetsflödet:<br /> 
    <ul> 
     <li> <p>återställer listan över händelser som bearbetats av åtgärderna.</p> </li> 
     <li> <p>synkroniserar med tabellen NmsBroadLogMsg för att återställa leveranskunskaper.</p> </li> 
     <li> <p>återställer händelseloggar så snart synkroniseringen med tabellen NmsBroadLogMsg har slutförts.</p> </li> 
     <li> <p>synkroniserar med NmsTrackingUrl-tabellen för att återställa spårningen för leverans-URL:er.</p> </li> 
     <li> <p>återställer URL:er för händelsespårning så snart synkroniseringen med tabellen NmsTrackingUrl har slutförts.</p> </li> 
     <li> <p>Med kan du återställa alla e-postadresser som placerats i karantän var tredje timme efter att en leverans har skickats.</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

