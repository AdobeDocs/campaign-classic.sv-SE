---
product: campaign
title: Arbetsflöden för dataskyddsförordningen
description: Läs mer om arbetsflödena i förordningen om skydd av personuppgifter
audience: workflow
content-type: reference
topic-tags: technical-workflows
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 10%

---


# Sekretessdataskyddsförordningen{#general-data-protection-regulation-gdpr}

![](../../assets/common.svg)

Arbetsflödena som beskrivs nedan installeras som standard med modulen **Sekretessdataskydd**. Mer information om den här modulen finns i den här [artikeln](https://helpx.adobe.com/se/campaign/kb/acc-privacy.html).

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

