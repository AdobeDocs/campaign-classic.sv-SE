---
product: campaign
title: Spåra en kampanj
description: Lär dig spåra en kampanj med Campaign Distributed Marketing
feature: Distributed Marketing
hide: true
hidefromtoc: true
exl-id: 87d1909c-d2eb-47ce-a860-0e78a64d2914
source-git-commit: 36fe54cf6d4d762d96205bd637311a426c741427
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 1%

---

# Spåra en kampanj{#tracking-a-campaign}



Operatorer för central enhet kan spåra kampanjorder i listan över kampanjpaket.

Detta gör att de kan:

* [Filterpaket](#filter-packages),
* [Redigera paket](#edit-packages),
* [Avbryt ett paket](#cancel-a-package),
* [Initiera om ett paket](#reinitializing-a-package).

## Filterpaket {#filter-packages}

På fliken **[!UICONTROL Campaigns]** kan du visa listan med **[!UICONTROL Campaign packages]** som grupperar alla befintliga distribuerade marknadsföringskampanjer. Du kan filtrera den här listan så att den endast visar kampanjer som antingen är publicerade, sena, väntar på godkännande osv. Det gör du genom att klicka på länkarna i den övre delen av den här vyn eller genom att använda länken **[!UICONTROL Filter list]** och välja den kampanjpaketstatus som ska visas.

![](assets/mkg_dist_catalog_filter.png)

## Redigera paket {#edit-packages}

På sidan **[!UICONTROL Campaign packages]** kan du visa sammanfattningen för varje paket.

Sammanfattningen visar följande information: etikett, kampanjtyp, namnet på kampanjen som den skapades från samt mappen.

Klicka på paketnamnet för att redigera det. Du kan också visa order efter deras lokala enheter och deras status.

Den här informationen finns också i vyn **[!UICONTROL Campaign orders]** där alla order visas.

![](assets/mkg_dist_catalog_op_command_details.png)

Den centrala operatorn kan redigera ordern. Det finns två sätt att göra detta:

1. Operatorn kan klicka på ordernamnet för att redigera det: här visas orderinformationen.

   ![](assets/mkg_dist_catalog_op_command_edit1.png)

   På fliken **[!UICONTROL Edit > General]** kan du visa information som angetts av den lokala enheten när kampanjen beställdes.

   ![](assets/mkg_dist_catalog_op_command_edit1a.png)

1. Operatören kan klicka på kampanjpaketets etikett för att redigera den och ändra vissa inställningar.

   ![](assets/mkg_dist_catalog_op_command_edit2.png)

## Avbryt ett paket {#cancel-a-package}

Den centrala enheten kan när som helst avbryta ett kampanjpaket.

Klicka på **[!UICONTROL Cancel]** i kampanjpaketet **[!UICONTROL Dashboard]**.

![](assets/mkg_dist_cancel_op_from_dashboard.png)

I fältet **[!UICONTROL Comment]** kan du justera annulleringen.

Om du avbryter ett paket för **lokala kampanjer** tas det bort från listan över tillgängliga marknadsföringskampanjer.

Om du avbryter ett paket för **samarbetskampanjer** utlöses flera åtgärder:

1. Alla beställningar som rör detta paket annulleras,

   ![](assets/mkg_dist_mutual_op_cancelled.png)

1. Referenskampanjen avbryts och alla aktiva processer (arbetsflöden, leveranser) stoppas.

   ![](assets/mkg_dist_mutual_op_cancelled1.png)

1. En anmälan skickas till alla berörda lokala enheter.

   ![](assets/mkg_dist_mutual_op_cancelled2.png)

Avbrutna paket kan fortfarande nås och återinitieras av den centrala enheten (se nedan) om det behövs. De kommer endast att erbjudas lokala enheter igen när de har godkänts och startats. Paketets ominitieringsprocess visas nedan.

## Initiera om ett paket {#reinitializing-a-package}

Kampanjpaket som redan har publicerats kan initieras om, ändras och göras tillgängliga för lokala enheter.

1. Välj det paket det gäller.
1. Klicka på länken **[!UICONTROL Reinitialize the package to reuse it]** och klicka på **[!UICONTROL OK]**.

   ![](assets/mkg_dist_mutual_op_reinit.png)

1. Klicka på knappen **[!UICONTROL Save]** för att godkänna ominitiering av paket.

   ![](assets/mkg_dist_mutual_op_reinit2.png)

1. Paketets status ändras till **[!UICONTROL Being edited]**. Ändra, godkänn och publicera den igen för att återställa den till listan över kampanjpaket.

>[!NOTE]
>
>Du kan även initiera om avbrutna kampanjpaket.
