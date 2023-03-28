---
product: campaign
title: Skapa dirigerade adresser
description: Lär dig hur du skapar och använder dirigerade adresser
feature: Seed Address
exl-id: f7dc97f0-3423-4b6f-88e2-08180f9adf8a
source-git-commit: 0065a25250d73c71e7569768a38b5836cccab992
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 1%

---

# Skapa dirigerade adresser{#creating-seed-addresses}

![](../../assets/common.svg)

Seed-adresser hanteras inte via standardprofiler och -mål, utan i en dedikerad nod i Adobe Campaign-hierarkin **[!UICONTROL Resources > Campaign management > Seed addresses]**.

Du kan skapa undermappar för att ordna startadresserna. Om du vill göra det högerklickar du på **[!UICONTROL Seed addresses]** nod och markera **[!UICONTROL Create a new 'Seed addresses' folder]**. Namnge undermappen och tryck sedan på **[!UICONTROL Enter]** att validera. Nu kan du skapa eller kopiera dirigerade adresser till den här undermappen. Mer information finns i [Definiera adresser](#defining-addresses).

Med Adobe Campaign kan ni också skapa mallar för dirigerade adresser som importeras till leveranser eller kampanjer och som anpassas utifrån de specifika behoven hos de aktuella leveranserna och kampanjerna. Se [Skapa mallar för dirigerade adresser](#creating-seed-address-templates).

## Definiera adresser {#defining-addresses}

Följ stegen nedan för att skapa dirigerade adresser:

1. Klicka på **[!UICONTROL New]** ovanför listan med dirigerade adresser.
1. Ange data som är länkade till adressen i matchande fält från **[!UICONTROL Recipient]** -fliken. De tillgängliga fälten motsvarar standardfälten i leveransmottagarnas profiler (nms:mottagartabellen): namn, förnamn, e-postadress osv.

   >[!NOTE]
   >
   >Adressetiketten fylls automatiskt i med det efternamn och förnamn som du har definierat.
   >
   >Du behöver inte ange alla fält på varje flik när du skapar en startadress. Personaliseringselement som saknas anges slumpmässigt under leveransanalysen.

   ![](assets/s_ncs_user_seedlist_new_address.png)

1. I **[!UICONTROL Address fields]** anger du de värden som ska infogas i leveransloggarna under analysfasen (i dialogrutan **[!UICONTROL nms:broadLog]** tabell).

1. I **[!UICONTROL Additional data]** Ange de personaliseringsdata som används för leveranser som skapas i arbetsflödena för datahantering och som du vill tilldela ett specifikt värde till.

   >[!NOTE]
   >
   >Kontrollera att ytterligare måldata har definierats med ett alias som börjar med @ i **[!UICONTROL Enrichment]** aktivitet. Annars kan du inte använda dem på rätt sätt med dina dirigerade adresser i leveransaktiviteten.

## Skapa mallar för dirigerade adresser {#creating-seed-address-templates}

Om du vill skapa adressmallar som ska importeras och ändras för varje leverans, är processen densamma som när du definierar en ny dirigeringsadress. Den enda skillnaden är att adresser för startadressmallar måste lagras i en mapp av typen &quot;Mall&quot;.

Så här definierar du en mallmapp:

1. Skapa ett nytt **[!UICONTROL Seed addresses]** typmapp, högerklicka på mappen och välj **[!UICONTROL Properties...]**.

   ![](assets/s_ncs_user_seedlist_template_folder.png)

1. Klicka på **[!UICONTROL Restriction]** och lägga till följande filtervillkor: **@isModel = true**.

   ![](assets/s_ncs_user_seedlist_folder_is_model.png)

   Adresser som lagras i den här mappen kan nu användas som adressmallar. Du kan importera dem till leveranser eller kampanjer och anpassa dem baserat på de specifika behoven för aktuella leveranser och kampanjer (se [Lägg till dirigerade adresser](adding-seed-addresses.md)).
