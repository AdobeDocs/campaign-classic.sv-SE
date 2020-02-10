---
title: Message Center (Control)
seo-title: Message Center (Control)
description: Message Center (Control)
seo-description: null
page-status-flag: never-activated
uuid: bdb3610b-a893-4e60-a9f7-f21d90b66919
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: 69e3e99f-d392-4316-926c-3c3c675415ad
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Message Center (Control){#message-center-control}

Arbetsflödet som anges nedan är schemalagt att köras varje timme. Den installeras som standard med **Message Center - Control** -modulen. Mer information om den här modulen finns i det här [avsnittet](../../message-center/using/about-transactional-messaging.md).

Mer information om hur du konfigurerar tekniska arbetsflöden för modulen Meddelandecenter finns på [den här sidan](../../message-center/using/technical-workflows.md).

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

