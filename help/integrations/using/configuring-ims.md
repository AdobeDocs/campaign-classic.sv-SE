---
title: Konfigurera IMS
description: Lär dig ansluta via en Adobe ID
page-status-flag: never-activated
uuid: b659d29f-2a27-4a7b-b5ca-f44c3271dd4e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
discoiquuid: 279d0548-c876-4d5f-a195-48618bd5e9d1
translation-type: tm+mt
source-git-commit: 48acf8cbc52a54a2dd08f0b8f29be57d4e5e006f
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 2%

---


# Configuring IMS{#configuring-ims}

## Förutsättningar {#prerequisites}

Så här använder du integreringen med IMS:

* Du måste ha en Adobe Experience Cloud-organisation och IMS-id (tillhandahålls när du ansluter till Adobe Experience Cloud första gången).
* Du måste lägga till användare i Experience Cloud. Se denna [sida](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/admin-getting-started.html) för mer information om detta.

>[!NOTE]
>
>Se till att dina användare är länkade till de Adobe Experience Cloud-grupper som ska synkroniseras med Adobe Campaign. Se [Konfigurera det externa kontot](#configuring-the-external-account).

## Konsolen uppdateras {#updating-the-console}

Om du vill använda den här funktionen måste du installera den senaste versionen av konsolen.

## Installera paketet {#installing-the-package}

Du måste installera **[!UICONTROL Integration with the Adobe Experience Cloud]** paketet. Att installera ett integrationspaket är detsamma som att installera ett standardpaket, som beskrivs på [den här sidan](../../installation/using/installing-campaign-standard-packages.md).

![](assets/ims_6.png)

## Konfigurera det externa kontot {#configuring-the-external-account}

Konfigurera **Adobe Experience Cloud** externa konto i **[!UICONTROL Administration > Platform > External accounts]**.

>[!CAUTION]
>
>Den här konfigurationen är reserverad för den tekniska administratören.

![](assets/ims_5.png)

Ange följande information:

* Anslutningsinformation för den IMS-server som används (ID och hemlighet). Denna information tillhandahålls av Adobe support. Mer information finns i [Frågor och svar för Adobe Experience Cloud-administratörer](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/faq.html).

   Adressen **[!UICONTROL Callback server]** måste anges i **https**. Det här fältet motsvarar åtkomst-URL:en för din Adobe Campaign-instans.

* IMS-organisations-ID: denna information finns tillgänglig på Experience Cloud (i **[!UICONTROL Administration > Experience Cloud Details]** ) och tillhandahålls när du ansluter till Adobe Experience Cloud första gången.
* Associationsmask: I det här fältet kan du definiera syntaxen som gör att konfigurationsnamnen i Enterprise Dashboard kan synkroniseras med grupperna i Adobe Campaign. Om du använder syntaxen&quot;Campaign - tenant_id - (.*)&quot; länkas säkerhetsgruppen som skapas i Adobe Campaign till konfigurationsnamnet Campaign - tenant_id - internal_name i Enterprise Dashboard.

   >[!CAUTION]
   >
   >Kopplingsmasken är nödvändig för att anslutningen via Adobe ID ska fungera korrekt.

* Adobe Experience Cloud anslutningsinformation, särskilt namnet på Adobe Experience Cloud-klienten.

