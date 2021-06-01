---
product: campaign
title: Konfigurera IMS
description: Lär dig ansluta via en Adobe ID
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: b70ca220-1c81-4b23-b07a-a2cd694877fe
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 2%

---

# Konfigurerar IMS{#configuring-ims}

>[!IMPORTANT]
>
>Implementeringen av Adobe IMS är strikt förbehållen de tekniska administratörerna i Adobe. Kontakta din Adobe-chef för att starta implementeringsprocessen.

## Förhandskrav {#prerequisites}

Så här använder du integreringen med IMS:

* Du måste ha en Adobe Experience Cloud-organisation och IMS-id (tillhandahålls när du ansluter till Adobe Experience Cloud första gången).
* Du måste lägga till användare i Experience Cloud. Se denna [sida](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/admin-getting-started.html) för mer information om detta.

>[!NOTE]
>
>Se till att dina användare är länkade till de Adobe Experience Cloud-grupper som ska synkroniseras med Adobe Campaign. Se [Konfigurera det externa kontot](#configuring-the-external-account).

## Konsolen {#updating-the-console} uppdateras

Om du vill använda den här funktionen måste du installera den senaste versionen av konsolen.

## Installera paketet {#installing-the-package}

Du måste installera **[!UICONTROL Integration with the Adobe Experience Cloud]**-paketet. Att installera ett integrationspaket är detsamma som att installera ett standardpaket, vilket beskrivs i [den här sidan](../../installation/using/installing-campaign-standard-packages.md).

![](assets/ims_6.png)

## Konfigurerar det externa kontot {#configuring-the-external-account}

Konfigurera det externa kontot **Adobe Experience Cloud** i **[!UICONTROL Administration > Platform > External accounts]**.

>[!CAUTION]
>
>Den här konfigurationen är reserverad för den tekniska administratören.

![](assets/ims_5.png)

Ange följande information:

* Anslutningsinformation för den IMS-server som används (ID och hemlighet). Denna information tillhandahålls av Adobe support. Mer information finns i [Vanliga frågor och svar för Adobe Experience Cloud-administratörer](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/faq.html).

   Adressen **[!UICONTROL Callback server]** måste anges i **https**. Det här fältet motsvarar åtkomst-URL:en för din Adobe Campaign-instans.

* IMS-organisations-ID: den här informationen är tillgänglig på Experience Cloud (i **[!UICONTROL Administration > Experience Cloud Details]**) och tillhandahålls när du ansluter till Adobe Experience Cloud första gången.
* Associationsmask: I det här fältet kan du definiera syntaxen som gör att konfigurationsnamnen i Enterprise Dashboard kan synkroniseras med grupperna i Adobe Campaign. Om du använder syntaxen&quot;Campaign - tenant_id - (.*)&quot; länkas säkerhetsgruppen som skapas i Adobe Campaign till konfigurationsnamnet Campaign - tenant_id - internal_name i Enterprise Dashboard.

   >[!CAUTION]
   >
   >Kopplingsmasken är nödvändig för att anslutningen via Adobe ID ska fungera korrekt.

* Adobe Experience Cloud anslutningsinformation, särskilt namnet på Adobe Experience Cloud-klienten.
