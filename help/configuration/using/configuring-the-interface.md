---
product: campaign
title: Konfigurera gränssnittet
description: Konfigurera gränssnittet
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
exl-id: 9f50f258-845e-4895-b1ef-b73744dea326
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 2%

---

# Konfigurera gränssnittet{#configuring-the-interface}

![](../../assets/v7-only.svg)

Om du vill visa och öppna en dialogruta med den nya mottagartabellen i Adobe Campaign-gränssnittet gör du så här:

* Skapa ett nytt formulär för att redigera innehållet i den nya mottagartabellen.
* Ange en ny typ i mappen för utforskarträdet.
* Skapa ett nytt webbprogram för att komma åt den anpassade tabellen via Adobe Campaign hemsida.

Adobe Campaign använder den globala variabeln &quot;Nms_DefaultRcpSchema&quot; för att öppna en dialogruta med standardmottagardatabasen (nms:receive). Denna variabel måste därför ändras.

1. Gå till noden **[!UICONTROL Administration>Platform>Options]** i Utforskaren.
1. Ändra värdet för variabeln **Nms_DefaultRcpSchema** med namnet på schemat som matchar den externa mottagartabellen (i det här fallet: cus:individual).
1. Spara ändringar.

## Skapa ett nytt formulär {#creating-a-new-form-}

Om du skapar ett nytt formulär kan du visa och redigera data i den externa mottagartabellen.

>[!IMPORTANT]
>
>Formulärets namn måste vara identiskt med namnet på schemat som det gäller.

1. Gå till noden **Administration > Konfiguration > Inmatningsformulär** i Utforskaren.
1. Skapa en ny **xtk:form** typ **form**-fil.
1. Beskriv alla övervakningar och fält som du behöver beroende på tabellmallen.

   >[!NOTE]
   >
   >Mer information om **formulärfiler** finns på [den här sidan](../../configuration/using/identifying-a-form.md).

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
1. Skapa ett nytt **xtk:navtree** typ **navtree**-dokument.
1. Beskriv alla övervakningar och fält som du behöver beroende på tabellmallen.

   >[!NOTE]
   >
   >Mer information om **navtree**-typfiler finns på [den här sidan](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy).

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
