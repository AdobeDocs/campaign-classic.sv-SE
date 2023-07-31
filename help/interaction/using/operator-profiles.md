---
product: campaign
title: Operatörsprofiler
description: Operatörsprofiler
feature: Interaction, Offers
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
audience: interaction
content-type: reference
topic-tags: managing-environments
exl-id: e11fb28c-d530-45a2-862a-ff1c20975577
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 5%

---

# Operatörsprofiler{#operator-profiles}



Det finns två typer av operatorer som använder Interaction: offer managers och delivery managers. De har specifika rättigheter som bara ger dem tillgång till vissa delar av trädet och plattformen.

* **[!UICONTROL Offer manager]** : skapar och underhåller erbjudanden. Observera att om erbjudanden används i arbetsflödet måste operatorn finnas i **[!UICONTROL Administrator]** eller **[!UICONTROL Offer managers]** operatörsgrupp för att köra arbetsflödet.
* **[!UICONTROL Delivery manager]** : godkänner och använder erbjudanden

Stegen för att skapa operatorer som är specifika för Interaction är identiska med de som används för att skapa alla andra operatorer på plattformen. Mer information om detta finns i [det här avsnittet](../../platform/using/access-management.md). Rättigheterna konfigureras när operatorn skapas.

## Erbjudandehanterare {#offer-manager}

1. Skapa en ny operator.
1. Gå till **[!UICONTROL Groups and named rights]** fönster, klicka **[!UICONTROL Add]** och väljer **[!UICONTROL Offer manager]** grupp.

   ![](assets/offer_operators_create_001.png)

Rättigheterna som tilldelats den som ansvarar för erbjudandet gör att de kan utföra följande uppgifter:

* Ändra **[!UICONTROL Design]** miljöer.
* Visa **[!UICONTROL Live]** miljöer.
* Konfigurera administrationsfunktioner (fördefinierade blanksteg och filter).
* Skapa och ändra kategorier.
* Skapa erbjudanden.
* Konfigurera berättigande för erbjudanden.
* Godkänn erbjudanden.

  >[!NOTE]
  >
  >Erbjudandehanteraren kan bara godkänna ett erbjudande i två specifika fall. Det första är om ingen har specificerats som granskare och det andra är om den som ansvarar för att skapa mallar (med behörighet att tilldela granskare) har angett dem som granskare i erbjudandemallen som erbjudandet baseras på.

## Delivery manager {#delivery-manager}

1. Skapa en ny operator.
1. Gå till **[!UICONTROL Groups and named rights]** fönster, klicka **[!UICONTROL Add]** och väljer **[!UICONTROL Delivery manager]** grupp.

   ![](assets/offer_operators_create_002.png)

De rättigheter som tilldelats till leveransansvariga gör det möjligt för dem att utföra följande uppgifter:

* Visa **[!UICONTROL Live]** miljöer.
* Visa och ändra erbjudandekategorier.
* Godkänn erbjudanden om den här leveranshanteraren har angetts som en av dess granskare.

  >[!NOTE]
  >
  >Leveransansvariga kan bara godkänna ett erbjudande om de har definierats som granskare under konfigurationen av erbjudandet.

## Återvinning av rättigheter enligt operatör {#recap-of-rights-according-to-operator}

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>Erbjudandehanterare (redigering)</strong><br /> </td> 
   <td> <strong>Erbjudandehanterare (live)</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Trädstrukturnivå</strong><br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Erbjudanden som redigeras/Live-erbjudanden<br /> </td> 
   <td> Läs/skriv<br /> </td> 
   <td> Läs<br /> </td> 
  </tr> 
  <tr> 
   <td> Mottagare - miljö<br /> </td> 
   <td> Läs/skriv<br /> </td> 
   <td> Läs<br /> </td> 
  </tr> 
  <tr> 
   <td> Administration<br /> </td> 
   <td> Läs/skriv<br /> </td> 
   <td> Läs<br /> </td> 
  </tr> 
  <tr> 
   <td> Blanksteg<br /> </td> 
   <td> Läs/skriv<br /> </td> 
   <td> Läs<br /> </td> 
  </tr> 
  <tr> 
   <td> Fördefinierade erbjudandefilter<br /> </td> 
   <td> Läs/skriv<br /> </td> 
   <td> Läs<br /> </td> 
  </tr> 
  <tr> 
   <td> Typologi<br /> </td> 
   <td> Läs/skriv<br /> </td> 
   <td> Läs<br /> </td> 
  </tr> 
  <tr> 
   <td> Typologiregler<br /> </td> 
   <td> Läs/skriv<br /> </td> 
   <td> Läs<br /> </td> 
  </tr> 
  <tr> 
   <td> Erbjudandekatalog<br /> </td> 
   <td> Läs/skriv<br /> </td> 
   <td> Läs<br /> </td> 
  </tr> 
  <tr> 
   <td> Erbjudandekategori<br /> </td> 
   <td> Läs/skriv<br /> </td> 
   <td> Läs<br /> </td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>Delivery manager (redigering)</strong><br /> </td> 
   <td> <strong>Delivery manager (live)</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Trädstrukturnivå</strong><br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Erbjudanden som redigeras/Live-erbjudanden<br /> </td> 
   <td> </td> 
   <td> Läs<br /> </td> 
  </tr> 
  <tr> 
   <td> Mottagare - miljö<br /> </td> 
   <td> </td> 
   <td> Läs<br /> </td> 
  </tr> 
  <tr> 
   <td> Administration<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Blanksteg<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Fördefinierade erbjudandefilter<br /> </td> 
   <td> Läs<br /> </td> 
   <td> Läs<br /> </td> 
  </tr> 
  <tr> 
   <td> Typologi<br /> </td> 
   <td> Läs<br /> </td> 
   <td> Läs<br /> </td> 
  </tr> 
  <tr> 
   <td> Typologiregler<br /> </td> 
   <td> </td> 
   <td> Läs<br /> </td> 
  </tr> 
  <tr> 
   <td> Erbjudandekatalog<br /> </td> 
   <td> Läs<br /> </td> 
   <td> Läs<br /> </td> 
  </tr> 
  <tr> 
   <td> Erbjudandekategori<br /> </td> 
   <td> </td> 
   <td> Läs<br /> </td> 
  </tr> 
 </tbody> 
</table>
