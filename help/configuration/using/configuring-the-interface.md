---
product: campaign
title: Konfigurera gränssnittet
description: Lär dig hur du konfigurerar Campaign-gränssnittet
feature: Application Settings
role: Data Engineer, Developer
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
exl-id: 9f50f258-845e-4895-b1ef-b73744dea326
source-git-commit: d56038fc8baf766667d89bb73747c20ec041124c
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# Konfigurera gränssnittet{#configuring-the-interface}

Om du vill visa och öppna en dialogruta med den nya mottagartabellen i Adobe Campaign-gränssnittet gör du så här:

* Skapa ett nytt formulär för att redigera innehållet i den nya mottagartabellen.
* Ange en ny typ i mappen för utforskarträdet.
* Skapa ett nytt webbprogram för att komma åt den anpassade tabellen via Adobe Campaign hemsida.

Adobe Campaign använder en global variabel av typen Nms_DefaultRcpSchema för att öppna en dialogruta med standardmottagardatabasen (nms:recipient). Denna variabel måste därför ändras.

1. Gå till noden **[!UICONTROL Administration>Platform>Options]** i Utforskaren.
1. Ändra värdet för variabeln **Nms_DefaultRcpSchema** med namnet på schemat som matchar den externa mottagartabellen (i det här fallet: cus:individual).
1. Spara ändringar.

## Skapa ett nytt formulär {#creating-a-new-form-}

Om du skapar ett nytt formulär kan du visa och redigera data i den externa mottagartabellen.

>[!IMPORTANT]
>
>Formulärets namn måste vara identiskt med namnet på schemat som det gäller.

1. Gå till noden **Administration > Konfiguration > Inmatningsformulär** i Utforskaren.
1. Skapa en ny **xtk:form** type **form** -fil.
1. Beskriv alla övervaknings- och fält som du behöver beroende på tabellmallen.

   >[!NOTE]
   >
   >Mer information om **formulär**-typfiler finns på [den här sidan](../../configuration/using/identifying-a-form.md).

   I vårt aktuella exempel måste filen **form** baseras på schemat **cus:individual** och därför ha följande layout:

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

1. Gå till noden **[!UICONTROL Administration>Configuration>Navigation hierarchies]**.
1. Skapa ett nytt **xtk:navtree** type **navtree** -dokument.
1. Beskriv alla övervaknings- och fält som du behöver beroende på tabellmallen.

   I det aktuella exemplet måste filen **navtree** baseras på schemat **cus:individual** och därför ha följande format:

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
