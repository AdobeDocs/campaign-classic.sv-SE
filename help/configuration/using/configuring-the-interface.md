---
title: Konfigurera gränssnittet
seo-title: Konfigurera gränssnittet
description: Konfigurera gränssnittet
seo-description: null
page-status-flag: never-activated
uuid: 101ba02f-da43-4dcc-b9ff-6e5ca848fc5d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: 8fb9ff23-17a7-4425-9195-738d6fd914dc
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Konfigurera gränssnittet{#configuring-the-interface}

Gör så här för att visa och kommunicera med den nya mottagartabellen i Adobe Campaign-gränssnittet:

* Skapa ett nytt formulär för att redigera innehållet i den nya mottagartabellen.
* Ange en ny typ i mappen för utforskarträdet.
* Skapa ett nytt webbprogram för att komma åt den anpassade tabellen via hemsidan för Adobe Campaign.

Adobe Campaign använder en global variabel av typen Nms_DefaultRcpSchema för att öppna en dialogruta med standardmottagardatabasen (nms:receive). Denna variabel måste därför ändras.

1. Gå till **[!UICONTROL Administration>Platform>Options]** noden för Utforskaren.
1. Ändra värdet för variabeln **Nms_DefaultRcpSchema** med namnet på schemat som matchar den externa mottagartabellen (i det här fallet: cus:individual).
1. Spara ändringar.

## Skapa ett nytt formulär {#creating-a-new-form-}

Om du skapar ett nytt formulär kan du visa och redigera data i den externa mottagartabellen.

>[!CAUTION]
>
>Formulärets namn måste vara identiskt med namnet på schemat som det gäller.

1. Gå till noden **Administration > Konfiguration > Inmatningsformulär** i Utforskaren.
1. Skapa en ny **xtk:formulärtyp** **formulärfil** .
1. Beskriv alla övervakningar och fält som du behöver beroende på tabellmallen.

   >[!NOTE]
   >
   >Mer information om **formulärtypsfiler** finns på [den här sidan](../../configuration/using/identifying-a-form.md).

   I vårt aktuella exempel måste **formulärfilen** baseras på **cus:individual** -schemat och därför ha följande layout:

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

1. Gå till **[!UICONTROL Administration>Configuration>Navigation hierarchies]** noden.
1. Skapa ett nytt **xtk:navtree** -typ av **navtree** -dokument.
1. Beskriv alla övervakningar och fält som du behöver beroende på tabellmallen.

   >[!NOTE]
   >
   >Mer information om **navtree** -typfiler finns på [den här sidan](../../configuration/using/about-navigation-hierarchy.md).

   I det aktuella exemplet måste **navtree** -filen baseras på **cus:individual** -schemat och därför ha följande format:

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

