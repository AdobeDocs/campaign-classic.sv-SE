---
product: campaign
title: Marknadsföringskampanjdokument och leveransdispositioner
description: Läs mer om kampanjdokument och leveransdispositioner för marknadsföring
audience: campaign
content-type: reference
topic-tags: orchestrate-campaigns
exl-id: 891252b0-4700-4a2a-a632-63aad5ce75d7
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 1%

---

# Hantera associerade dokument {#managing-associated-documents}

Du kan koppla olika dokument till en kampanj: rapporter, foton, webbsidor, diagram osv. Dessa dokument kan vara i vilket format som helst (Microsoft Word, PowerPoint, PNG, JPG, Acrobat PDF osv.).

>[!IMPORTANT]
>
>Den här funktionen är reserverad för små resurser och dokument.

I en kampanj kan du även hänvisa till andra saker, som kampanjkuponger, specialerbjudanden som gäller ett visst varumärke eller en viss butik, osv. När dessa element ingår i en disposition kan de kopplas till en direktutskick. Se [Associera och strukturresurser länkade via en leveransdisposition](#associating-and-structuring-resources-linked-via-a-delivery-outline).

>[!NOTE]
>
>Om du använder modulen för hantering av marknadsföringsresurser för Campaign kan du även hantera ett bibliotek med marknadsföringsresurser som är tillgängliga för flera användare för samarbete. [Läs mer](../../campaign/using/managing-marketing-resources.md).

## Lägg till dokument {#adding-documents}

Dokument kan kopplas på kampanjnivå (sammanhangsberoende dokument) eller på programnivå (allmänna dokument).

Fliken **[!UICONTROL Documents]** innehåller:

* Listan över alla dokument som krävs för innehållet (mall, bilder osv.) som kan laddas ned lokalt av Adobe Campaign-operatörer med lämpliga rättigheter,
* Dokument som innehåller information för routern, om sådan finns.

Dokumenten länkas till programmet eller kampanjen via fliken **[!UICONTROL Edit > Documents]**.

![](assets/s_ncs_user_op_add_document.png)

Du kan också lägga till ett dokument i en kampanj via länken på kontrollpanelen.

![](assets/add_a_document_in_op.png)

Klicka på ikonen **[!UICONTROL Details]** för att visa innehållet i en fil och lägga till information:

![](assets/s_ncs_user_op_add_document_details.png)

På kontrollpanelen grupperas dokument som är kopplade till kampanjen i avsnittet **[!UICONTROL Document(s)]**, som i följande exempel:

![](assets/s_ncs_user_op_edit_document.png)

De kan också redigeras och ändras i den här vyn.

## Associera och strukturera resurser som är länkade via en leveransdisposition {#associating-and-structuring-resources-linked-via-a-delivery-outline}

>[!NOTE]
>
>Leveranskonturer används endast i samband med direktreklamkampanjer.

En leveransöversikt betecknar en strukturerad uppsättning element (dokument, butiker, kampanjkuponger osv.) som skapats av företaget och för en viss kampanj.

Dessa element grupperas i leveransdispositioner och varje leveransdisposition kopplas till en leverans. den kommer att refereras i extraheringsfilen som skickas till **tjänstleverantören** för att kopplas till leveransen. Du kan till exempel skapa en leveransdisposition som refererar till en gren och de marknadsföringsbroschyrer som används i den.

För en kampanj kan du strukturera externa element som ska kopplas till leveransen enligt vissa kriterier: närliggande filial, kampanjerbjudande, inbjudan till ett lokalt evenemang osv.

### Skapa en disposition {#creating-an-outline}

Om du vill skapa en disposition klickar du på underfliken **[!UICONTROL Delivery outlines]** på fliken **[!UICONTROL Edit > Documents]** för den aktuella kampanjen.

>[!NOTE]
>
>Om den här fliken inte finns är den här funktionen inte tillgänglig för kampanjen. Se kampanjmallskonfigurationen.
>   
>Mer information om mallar finns i [det här avsnittet](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

![](assets/s_ncs_user_op_composition_link.png)

Klicka sedan på **[!UICONTROL Add a delivery outline]** och skapa en hierarki med konturer för kampanjen:

1. Högerklicka på trädets rot och välj **[!UICONTROL New > Delivery outlines]**.
1. Högerklicka på konturen som du just har skapat och välj **[!UICONTROL New > Item]** eller **[!UICONTROL New > Personalization fields]**.

![](assets/s_ncs_user_op_add_composition.png)

En disposition kan innehålla objekt och personaliseringsfält, resurser och erbjudanden:

* Objekten kan till exempel vara fysiska dokument som refereras och beskrivs här och bifogas till leveransen.
* Med personaliseringsfält kan du skapa personaliseringselement för leveranser i stället för mottagare. Det är därför möjligt att skapa värden som ska användas i leveranser för ett specifikt mål (välkomsterbjudande, rabatt osv.) De skapas i Adobe Campaign och importeras till dispositionen via länken **[!UICONTROL Import personalization fields...]**.

   ![](assets/s_ncs_user_op_add_composition_field.png)

   De kan också skapas direkt i dispositionen genom att klicka på ikonen **[!UICONTROL Add]** till höger om listzonen.

   ![](assets/s_ncs_user_op_add_composition_field_button.png)

* Resurserna är marknadsföringsresurser som genereras i kontrollpanelen för marknadsföringsresurser som du kommer åt via länken **[!UICONTROL Resources]** på fliken **[!UICONTROL Campaigns]**.

   ![](assets/s_ncs_user_mkg_resource_ovv.png)

   >[!NOTE]
   >
   >Mer information om marknadsföringsresurser finns i [det här avsnittet](../../campaign/using/managing-marketing-resources.md).

### Markera en kontur {#selecting-an-outline}

För varje leverans kan du välja den disposition som ska kopplas från det avsnitt som är reserverat för dispositionen, som i följande exempel:

![](assets/s_ncs_user_op_select_composition.png)

Den markerade dispositionen visas sedan i fönstrets nedre del. Den kan redigeras med ikonen till höger om fältet eller ändras med hjälp av listrutan:

![](assets/s_ncs_user_op_select_composition_b.png)

På fliken **[!UICONTROL Summary]** för leveransen visas även den här informationen:

![](assets/s_ncs_user_op_select_composition_c.png)

### Extraheringsresultat {#extraction-result}

I den fil som extraheras och skickas till tjänsteleverantören, namnet på konturen och, i förekommande fall, dess egenskaper (kostnad, beskrivning osv.) läggs till i innehållet enligt informationen i exportmallen som är kopplad till tjänsteleverantören.

I följande exempel läggs etiketten, den uppskattade kostnaden och beskrivningen av dispositionen som är kopplad till leveransen till i extraheringsfilen.

![](assets/s_ncs_user_op_composition_in_export_template.png)

Exportmodellen måste vara kopplad till den tjänsteleverantör som valts för den aktuella leveransen. Se [det här avsnittet](../../campaign/using/providers--stocks-and-budgets.md#creating-service-providers-and-their-cost-structures).

>[!NOTE]
>
>Mer information om export finns i [det här avsnittet](../../platform/using/get-started-data-import-export.md)-avsnittet.
