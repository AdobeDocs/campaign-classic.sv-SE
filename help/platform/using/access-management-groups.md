---
product: campaign
title: Skapa och hantera operatorgrupper
description: Lär dig hur du ger åtkomst till operatörsgrupper
badge: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
feature: Access Management, Permissions
role: User, Admin
level: Beginner
exl-id: d5833d3d-e8ef-4f2b-8084-4ba825c79525
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 1%

---

# Skapa och hantera operatorgrupper {#operator-groups}



Operatorgrupper skapas via **[!UICONTROL Administration > Access management > Operator groups]** i trädet.

## Skapa en ny operatorgrupp {#creating-a-new-operator-group}

Så här skapar du en ny operatorgrupp:

1. Klicka på **[!UICONTROL New]** till höger om listan med grupper eller högerklicka på listan och välj **[!UICONTROL New]**.
1. I det nedre avsnittsfönstret, från **[!UICONTROL General]** anger du namnet och en beskrivning för gruppen i motsvarande fält.

   ![](assets/s_ncs_user_create_operator_gp.png)

1. Klicka på **[!UICONTROL Content]** för att definiera auktoriseringar för den här gruppen.
1. Klicka på **[!UICONTROL Add]** för att välja en utsedd rättighet eller en operator att koppla till gruppen.
1. Klicka på listrutan eller på mappen till höger om **[!UICONTROL Folder]** fält för att hitta de utsedda rättigheter eller operatörer som ska associeras med den här gruppen.
1. Välj rättigheter eller operatorer att lägga till och klicka på **[!UICONTROL OK]** för att validera.

   ![](assets/s_ncs_user_create_operator_gp03.png)

   Upprepa den här åtgärden om du vill lägga till andra rättigheter eller operatorer.

1. Klicka på **[!UICONTROL Save]** om du vill lägga till gruppen i listan.

## Standardgrupper {#default-groups}

Standardoperatorgrupperna är:

1. **[!UICONTROL Administrator]**

   Operatorerna i den här gruppen har fullständig åtkomst till instansen. Administratörer är användare som har tillgång till de flesta tekniska delarna av gränssnittet. De håller **[!UICONTROL Administration]** och se till att plattformen är konfigurerad.

   Den här gruppen innehåller följande namngivna rättigheter:

   * **[!UICONTROL ADMINISTRATION]**: rätt att köra/skapa/redigera/ta bort objekt som arbetsflöde, leverans, skript osv.

1. **[!UICONTROL Delivery operators]**

   Operatörerna i den här gruppen ansvarar för att hantera leveranser: de ger åtkomst till de viktigaste resurser som krävs för att skapa och förbereda leveranser (kampanjtyper, leveransmappningar, standardmallar, personaliseringsblock osv.).

   Den här gruppen innehåller följande namngivna rättigheter:

   * **[!UICONTROL PREPARE DELIVERIES]**: rätt att skapa, redigera och starta leveransanalysen,
   * **[!UICONTROL START DELIVERIES]**: rätt att godkänna tidigare analyserade leveranser.

1. **[!UICONTROL Campaign managers]**

   Operatörerna i den här gruppen kan hantera marknadsföringskampanjer: ni får tillgång till objekt som är kopplade till kampanjer (planer, program, arbetsflöden, budgetar osv.) inom ramen för **[!UICONTROL Campaign]** (Adobe Campaign-modul som tillval).

   Den här gruppen innehåller följande namngivna rättigheter:

   * **[!UICONTROL INSERT FOLDERS]**: rätt att lägga in mappar i Adobe Campaign-trädet (förutsatt att du har redigeringsbehörighet för de berörda grenarna),
   * **[!UICONTROL WORKFLOW]**: rätt att använda arbetsflöden.

   >[!NOTE]
   >
   >Den här gruppen tillåter inte att operatorer påbörjar leveranser.

1. **[!UICONTROL Content contributors]**

   Operatorerna i den här gruppen har åtkomst till innehållsmapparna inom ramen för **[!UICONTROL Content management]** (Adobe Campaign-modul som tillval). Den här gruppen ger inte några ytterligare rättigheter.

1. **[!UICONTROL Access to reports]**

   Den här gruppen är reserverad för externa operatorer för att få åtkomst till leveransrapporter via webbåtkomst.

1. **[!UICONTROL Workflow execution]**

   Med den här gruppen kan ni tilldela operatörer rätten att hantera arbetsflöden som inte har med kampanjer att göra.

1. **[!UICONTROL Workflow supervisors]**

   Operatörerna i den här gruppen får ett e-postmeddelande om det uppstår varningar om kampanjarbetsflöden.

1. Lokal/central hantering

   Med de här grupperna kan du använda **[!UICONTROL Distributed marketing]** (Adobe Campaign-modul som tillval).

1. **[!UICONTROL Offer managers]**

   Operatorerna i den här gruppen kan skapa och underhålla erbjudanden. Mer information finns i [page](../../interaction/using/operator-profiles.md).
Den här gruppen innehåller följande namngivna rättigheter:

   * **[!UICONTROL INSERT FOLDERS]**: Rätt att lägga in mappar i Adobe Campaign-trädet (förutsatt att du har redigeringsbehörighet för de berörda grenarna),
   * **[!UICONTROL EDIT FOLDERS]**: Rätt att ändra mappegenskaper som internt namn, etikett, associerad bild, undermappsordning osv.
