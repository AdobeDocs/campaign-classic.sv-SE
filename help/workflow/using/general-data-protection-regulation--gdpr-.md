---
title: Arbetsflöden för dataskyddsförordningen
description: Läs mer om arbetsflödena i förordningen om skydd av personuppgifter
page-status-flag: never-activated
uuid: cb5f5d79-52ac-4ce4-abc7-a3a1f0a001cf
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: 050c804e-87b7-4d68-b787-c396fec329d2
translation-type: tm+mt
source-git-commit: 6be6c353c3464839a74ba857d8d93d0f68bc8865
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 10%

---


# Sekretessdataskyddsförordningen{#general-data-protection-regulation-gdpr}

De arbetsflöden som beskrivs nedan installeras som standard tillsammans med modulen **Sekretessdataskyddsförordningen** . For more on this module, refer to this [article](https://helpx.adobe.com/se/campaign/kb/acc-privacy.html).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etikett</strong><br /> </td> 
   <td> <strong>Internt namn</strong><br /> </td> 
   <td> <strong>Beskrivning</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Samla in sekretessförfrågningar</span> <br /> </td> 
   <td> <span class="uicontrol">collectPrivacyRequests</span> <br /> </td> 
   <td> Det här arbetsflödet genererar mottagarens data som lagras i Adobe Campaign och gör dem tillgängliga för hämtning på skärmen för sekretesspolicy.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Ta bort data för sekretessförfrågningar</span> <br /> </td> 
   <td> <span class="uicontrol">deletePrivacyRequestsData</span> <br /> </td> 
   <td> Det här arbetsflödet tar bort mottagarens data som lagras i Adobe Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Rensa sekretessbegäran</span> <br /> </td> 
   <td> <span class="uicontrol">cleanupPrivacyRequests</span> <br /> </td> 
   <td> Det här arbetsflödet raderar filer för åtkomstbegäran som är äldre än 90 dagar.<br /> </td> 
  </tr> 
 </tbody> 
</table>

