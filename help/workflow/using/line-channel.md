---
solution: Campaign Classic
product: campaign
title: LINE-kanal
description: LINE-kanal
audience: workflow
content-type: reference
topic-tags: technical-workflows
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 11%

---


# LINE-kanal{#line-channel}

Arbetsflödena som beskrivs nedan installeras som standard med modulen **LINE-kanal**. Mer information om den här modulen finns i [avsnittet](../../delivery/using/line-channel.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etikett</strong><br /> </td> 
   <td> <strong>Internt namn</strong><br /> </td> 
   <td> <strong>Beskrivning</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Uppdatering av åtkomsttoken för LINE V2</span> <br /> </td> 
   <td> <span class="uicontrol">updateLineV2AccessToken</span> <br /> </td> 
   <td> Det här arbetsflödet uppdaterar åtkomsttoken till LINE V2.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Ta bort blockerade LINE-användare</span> <br /> </td> 
   <td> <span class="uicontrol">deleteBlockedLineUsersV2</span> <br /> </td> 
   <td> Det här arbetsflödet säkerställer att LINE V2-användarnas data tas bort efter att de har blockerat LINE-kontot i 180 dagar.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MID till LineUserID-migrering</span> <br /> </td> 
   <td> <span class="uicontrol">MIDToUserIDMigration</span> <br /> </td> 
   <td> Det här arbetsflödet genererar användar-ID:t för LINE V2 för migrering från LINE V1 till LINE V2.<br /> </td> 
  </tr> 
 </tbody> 
</table>

