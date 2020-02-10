---
title: Operatörsprofiler
seo-title: Operatörsprofiler
description: Operatörsprofiler
seo-description: null
page-status-flag: never-activated
uuid: cd718d20-79cb-40ed-b2ae-23186387e2db
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: managing-environments
discoiquuid: 9a3f1dc9-71ef-4039-94b4-a217996f6a80
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Operatörsprofiler{#operator-profiles}

Det finns två typer av operatorer som använder Interaction: erbjuder chefer och leveransansvariga. De har specifika rättigheter som bara ger dem tillgång till vissa delar av trädet och plattformen.

* **[!UICONTROL Offer manager]** : skapar och underhåller erbjudanden
* **[!UICONTROL Delivery manager]** : godkänner och använder erbjudanden

Stegen för att skapa operatorer som är specifika för Interaction är identiska med de som används för att skapa alla andra operatorer på plattformen. Mer information finns i [det här avsnittet](../../platform/using/access-management.md#creating-an-operator). Rättigheterna konfigureras när operatorn skapas.

## Erbjudandehanterare {#offer-manager}

1. Skapa en ny operator.
1. Gå till **[!UICONTROL Groups and named rights]** fönstret, klicka **[!UICONTROL Add]** och markera **[!UICONTROL Offer manager]** gruppen.

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
   >Erbjudandehanteraren kan bara godkänna ett erbjudande i två specifika fall. Det första är om ingen har specificerats som granskare och det andra är om den som ansvarar för att skapa mallar (med behörighet att tilldela granskare) har angett honom/henne som granskare i erbjudandemallen som erbjudandet baserades på.

## Delivery manager {#delivery-manager}

1. Skapa en ny operator.
1. Gå till **[!UICONTROL Groups and named rights]** fönstret, klicka **[!UICONTROL Add]** och markera **[!UICONTROL Delivery manager]** gruppen.

   ![](assets/offer_operators_create_002.png)

Rättigheterna som tilldelats leveransansvarig är/gör det möjligt för dem att utföra följande uppgifter:

* Visa **[!UICONTROL Live]** miljöer.
* Visa och ändra erbjudandekategorier.
* Godkänn erbjudanden om han/hon har angetts som en av dess granskare.

   >[!NOTE]
   >
   >Leveranshanteraren kan bara godkänna ett erbjudande om han har definierats som granskare under konfigurationen av erbjudandet.

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

