---
title: Konfigurera IMS
seo-title: Konfigurera IMS
description: Konfigurera IMS
seo-description: null
page-status-flag: never-activated
uuid: b659d29f-2a27-4a7b-b5ca-f44c3271dd4e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
discoiquuid: 279d0548-c876-4d5f-a195-48618bd5e9d1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0a4272ae13b469c7c17b8c3afa9748cbfbcf07ff

---


# Konfigurera IMS{#configuring-ims}

## Förutsättningar {#prerequisites}

Så här använder du integreringen med IMS:

* Du måste ha en Adobe Experience Cloud-organisation och IMS-ID (tillhandahålls när du först ansluter till Adobe Experience Cloud).
* Du måste lägga till användare i Experience Cloud. For more on this, refer to [this page](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/admin-getting-started.html).

>[!NOTE]
>
>Se till att användarna är länkade till de Adobe Experience Cloud-grupper som ska synkroniseras med Adobe Campaign. Se [Konfigurera det externa kontot](#configuring-the-external-account).

## Konsolen uppdateras {#updating-the-console}

Om du vill använda den här funktionen måste du installera den senaste versionen av konsolen.

## Installera paketet {#installing-the-package}

Du måste installera **[!UICONTROL Integration with the Adobe Experience Cloud]** paketet. Att installera ett integrationspaket är detsamma som att installera ett standardpaket, som beskrivs på [den här sidan](../../installation/using/installing-campaign-standard-packages.md).

![](assets/ims_6.png)

## Konfigurera det externa kontot {#configuring-the-external-account}

Konfigurera det externa **Adobe Experience Cloud** -kontot i **[!UICONTROL Administration > Platform > External accounts]**.

>[!CAUTION]
>
>Den här konfigurationen är reserverad för den tekniska administratören.

![](assets/ims_5.png)

Ange följande information:

* Anslutningsinformation för den IMS-server som används (ID och hemlighet). Denna information tillhandahålls av Adobes support. Mer information finns i [Vanliga frågor för Adobe Experience Cloud-administratörer](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/faq.html).

   Adressen **[!UICONTROL Callback server]** måste anges i **https**. Det här fältet motsvarar åtkomstwebbadressen för din Adobe Campaign-instans.

* IMS-organisations-ID: den här informationen är tillgänglig på Experience Cloud (i **[!UICONTROL Administration > Experience Cloud Details]** ) och tillhandahålls när du först ansluter till Adobe Experience Cloud.
* Associationsmask: I det här fältet kan du definiera syntaxen som gör att konfigurationsnamnen i Enterprise Dashboard kan synkroniseras med grupperna i Adobe Campaign. Om du använder syntaxen&quot;Campaign - tenant_id - (.*)&quot; länkas den säkerhetsgrupp som skapas i Adobe Campaign till konfigurationsnamnet Campaign - tenant_id - internal_name i Enterprise Dashboard.

   >[!CAUTION]
   >
   >Associationsmasken är nödvändig för att anslutningen via Adobe-ID ska fungera korrekt.

* Adobe Experience Cloud-anslutningsinformation, särskilt namnet på Adobe Experience Cloud-klienten.

