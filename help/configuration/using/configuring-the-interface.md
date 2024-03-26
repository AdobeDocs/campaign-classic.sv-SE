---
product: campaign
title: Konfigurera gränssnittet
description: Lär dig hur du konfigurerar Campaign-gränssnittet
feature: Application Settings
role: Data Engineer, Developer
badge-v7: label="v7" type="Informative" tooltip="Gäller Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gäller även Campaign v8"
exl-id: 9f50f258-845e-4895-b1ef-b73744dea326
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---

# Konfigurera gränssnittet{#configuring-the-interface}

Om du vill visa och öppna en dialogruta med den nya mottagartabellen i Adobe Campaign-gränssnittet gör du så här:

* Skapa ett nytt formulär för att redigera innehållet i den nya mottagartabellen.
* Ange en ny typ i mappen för utforskarträdet.
* Skapa ett nytt webbprogram för att komma åt den anpassade tabellen via Adobe Campaign hemsida.

Adobe Campaign använder den globala variabeln &quot;Nms_DefaultRcpSchema&quot; för att öppna en dialogruta med standardmottagardatabasen (nms:receive). Denna variabel måste därför ändras.

1. Gå till **[!UICONTROL Administration>Platform>Options]** Utforskarens nod.
1. Ändra värdet för **Nms_DefaultRcpSchema** variabeln med namnet på schemat som matchar den externa mottagartabellen (i det här fallet: cus:individual).
1. Spara ändringar.

## Skapa ett nytt formulär {#creating-a-new-form-}

Om du skapar ett nytt formulär kan du visa och redigera data i den externa mottagartabellen.

>[!IMPORTANT]
>
>Formulärets namn måste vara identiskt med namnet på schemat som det gäller.

1. Gå till **Administration > Konfiguration > Inmatningsformulär** Utforskarens nod.
1. Skapa ett nytt **xtk:formulär** type **formulär** -fil.
1. Beskriv alla övervaknings- och fält som du behöver beroende på tabellmallen.

   >[!NOTE]
   >
   >Om du vill veta mer om **formulär** typfiler, se [den här sidan](../../configuration/using/identifying-a-form.md).

   I vårt nuvarande exempel **formulär** filen måste baseras på **cus:individuell** och därför ha följande layout:

   ```
   <container colspan="2">
       <input xpath="@id"/>
       <static type="separator"/>
   </container>
   <container colcount="2">
       <input xpath="@lastName"/>
       <input xpath="@firstName"/>
       <input xpath="@email"/>
       <input xpath="@mobile"/>
   </container> 
   ```

1. Spara skapelsen.

## Skapa en ny typ av mapp i navigeringshierarkin {#creating-a-new-type-of-folder-in-the-navigation-hierarchy}

1. Gå till **[!UICONTROL Administration>Configuration>Navigation hierarchies]** nod.
1. Skapa ett nytt **xtk:navtree** type **navtree** -dokument.
1. Beskriv alla övervaknings- och fält som du behöver beroende på tabellmallen.

   >[!NOTE]
   >
   >Om du vill ha mer **navtree** typfiler, se [den här sidan](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy).

   I det aktuella exemplet **navtree** filen måste baseras på **cus:individuell** schemat och därför ha följande format:

   ```
    <model name="root">
       <nodeModel img="nms:usergrp.png" label="My recipient table" name="cusindividual">
         <view name="listdet" schema="cus:individual" type="listdet">
           <columns>
             <node xpath="@id"/>
             <node xpath="@lastName"/>
             <node xpath="@firstName"/>
             <node xpath="@email"/>
             <node xpath="@mobile"/>
           </columns>
         </view>
       </nodeModel>
   </model>
   ```

1. Spara skapelsen.
