---
product: campaign
title: Godkänna och aktivera ett erbjudande
description: Godkänna och aktivera ett erbjudande
feature: Interaction, Offers
badge-v7: label="v7" type="Informative" tooltip="Gäller Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gäller även Campaign v8"
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
exl-id: cf7649fe-f62a-4dfa-a19e-9c1ca545e3e3
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '634'
ht-degree: 2%

---

# Godkänna och aktivera ett erbjudande{#approving-and-activating-an-offer}



När innehållet i erbjudandet är klart måste du godkänna det för att det ska kunna dupliceras i den aktiva miljön och levereras. Godkännandet avser erbjudandeinnehållet och dess behörighet.

Banderollen på instrumentpanelen för erbjudanden anger om erbjudandet behöver gå igenom godkännandecykeln eller inte.

![](assets/offer_validate_001.png)

## Godkänna erbjudandeinnehåll {#approving-offer-content}

Att godkänna erbjudandeinnehåll innebär att välja den eller de representationer som du vill göra tillgängliga i den aktiva miljön.

Innehållet i ett erbjudande har en representation per space. Eftersom varje erbjudande har en egen struktur och sina egna återgivningsfunktioner kan erbjudanderepresentationen variera.

Du kan godkänna erbjudandeinnehållet på vissa tillgängliga platser och avvisa det på andra.

>[!IMPORTANT]
>
>När innehållet i och behörigheten för ett erbjudande har godkänts körs arbetsflödet för publicering (meddelande om erbjudande) automatiskt och erbjudandet görs tillgängligt på alla aktiverade platser.

Så här godkänner du erbjudandeinnehållet:

1. Klicka på **[!UICONTROL Approval]** knapp och markera **[!UICONTROL Approve content]** i popup.

   ![](assets/offer_validate_002.png)

1. Använd listrutan för att välja de representationer du vill fortsätta redigera eller de som du vill publicera i den aktiva miljön och klicka sedan på **[!UICONTROL Content approval]**.

   ![](assets/offer_validate_003.png)

   När innehållet i erbjudandet har godkänts uppdateras informationen i tabellen för instrumentpanel för erbjudanden.

   ![](assets/offer_validate_004.png)

   >[!NOTE]
   >
   >The **[!UICONTROL Content approved]** omnämnandet innebär inte att alla erbjudanderepresentationer har aktiverats och godkänts. Det visar att processen för godkännande av innehåll har uppnåtts, oavsett om alla erbjudanden har aktiverats/godkänts eller inte.

## Godkänna anbudsberättigande {#approving-offer-eligibility}

Godkännande av berättigande för erbjudanden innebär att acceptera eller avvisa erbjudandevikter och att reglerna för behörighet också har konfigurerats i erbjudandet eller ärvts från reglerna som skapats i den överordnade kategorin.

>[!IMPORTANT]
>
>När innehållet i och behörigheten för ett erbjudande har godkänts körs arbetsflödet för publicering (meddelande om erbjudande) automatiskt och erbjudandet görs tillgängligt på alla aktiverade platser.

* Du kan visa den fullständiga listan med regler genom att klicka **[!UICONTROL Schedule and eligibility rules]**.

  ![](assets/offer_validate_005.png)

* Om du vill ändra reglerna för behörighet klickar du på **[!UICONTROL Reject]** och sedan klicka **[!UICONTROL Eligibility approval]**.

  ![](assets/offer_validate_007.png)

  De olika statusvärdena uppdateras på instrumentpanelen för erbjudanden.

  ![](assets/offer_validate_006.png)

* Om du vill acceptera erbjudandet klickar du **[!UICONTROL Approve eligibility]**.

  ![](assets/offer_validate_008.png)

  Godkänn behörighet, lägg till en kommentar om det behövs och klicka sedan på **[!UICONTROL Eligibility approval]**.

  ![](assets/offer_validate_009.png)

  De olika statusvärdena uppdateras på instrumentpanelen för erbjudanden.

  ![](assets/offer_validate_010.png)

## Godkännandespårning {#approval-tracking}

Spårning av godkännande finns på kontrollpanelen för erbjudanden. Klicka **[!UICONTROL Hide/display logs]** för att komma åt den.

![](assets/offer_validate_012.png)

>[!NOTE]
>
>Spårning finns även i **[!UICONTROL Audit]** fliken med erbjudandet, med information om granskarnas kommentarer.

## Starta om godkännandet {#restart-the-approval}

När godkännandet har startats kan det startas om. Gör så här:

1. Klicka **[!UICONTROL Content approved]** på instrumentpanelen för erbjudandet.
1. I **[!UICONTROL Edit]** väljer du det godkännande som ska startas om och klickar sedan på **[!UICONTROL Re-initialize approval to submit it again]**.
1. Bekräfta genom att klicka **[!UICONTROL Ok]**.

![](assets/offer_validate_013.png)

## Publicera erbjudandet {#publishing-the-offer}

När innehållet i och behörigheten för ett erbjudande har godkänts publiceras erbjudandet i ett arbetsflöde som automatiskt körs för varje erbjudande vars godkännandecykel har slutförts. The **[!UICONTROL Offer notification]** arbetsflödet körs också varje timme för att synkronisera (om det behövs) de utrymmen och kategorier som finns i erbjudandekatalogen från designmiljön till den aktiva miljön.

Kontrollpanelen för det erbjudande som finns i designmiljön innehåller information om publicering, inklusive namnet på matchande erbjudande i livemiljön.

![](assets/offer_golive_001.png)

Om du vill visa erbjudandet som finns tillgängligt i den aktiva miljön klickar du på erbjudandeetiketten: erbjudandet har en instrumentpanel som innehåller all relevant information.

![](assets/offer_golive_002.png)

## Inaktivera ett erbjudande {#disabling-an-offer}

När erbjudandet har godkänts kan du inaktivera det.

Det gör du genom att gå till instrumentpanelen för ett erbjudande online eller ett erbjudande som väntar på att bli online. Klicka sedan på **[!UICONTROL Disable offer]**.

Du kan även inaktivera en kategori direkt genom att gå till **[!UICONTROL Eligibility]** och kontrollera **[!UICONTROL Enabled]** box.

>[!NOTE]
>
>När ett erbjudande tas bort i en designmiljö inaktiveras det automatiskt i den länkade online-miljön. Efter en kvarhållningsperiod tas de inaktiverade erbjudandena bort från onlinemiljön.

![](assets/offer_preview_deactivate.png)
