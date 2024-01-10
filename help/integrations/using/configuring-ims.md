---
product: campaign
title: Konfigurera IMS
description: Lär dig ansluta via en Adobe ID
feature: Configuration
badge-v7: label="v7" type="Informative" tooltip="Gäller Campaign Classic v7"
badge-v7-prem: label="lokal och hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: b70ca220-1c81-4b23-b07a-a2cd694877fe
source-git-commit: 49271e291953483ee14709b26ec053217a336718
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 2%

---

# Konfigurera IMS{#configuring-ims}

>[!IMPORTANT]
>
>Som en Campaign-värd eller hanterad tjänstanvändare ägs IMS-implementeringen av Adobe. De steg som beskrivs nedan gäller endast lokala kunder och hybridkunder.
> Implementeringen av Adobe IMS får endast utföras av Adobe tekniska administratörer. Kontakta Adobe för att starta implementeringsprocessen.

## Förhandskrav {#prerequisites}

* Du måste ha ett namn och ett ID för Adobe Experience Cloud-organisationen. Om du vill hitta ditt organisations-ID går du till [den här sidan](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=sv){_blank}.
* Du måste lägga till användare i Experience Cloud. Mer information finns i [den här sidan](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html){_blank}.

>[!NOTE]
>
>Se till att dina användare är länkade till de Adobe Experience Cloud-grupper som ska synkroniseras med Adobe Campaign. [Läs mer](#configuring-the-external-account).

## Konsolen uppdateras {#updating-the-console}

Om du vill använda den här funktionen måste du installera den senaste versionen av klientkonsolen.

## Installera paketet {#installing-the-package}

Du måste installera det inbyggda **[!UICONTROL Integration with the Adobe Experience Cloud]** paket. Att installera ett integrationspaket är detsamma som att installera ett standardpaket, vilket beskrivs i [den här sidan](../../installation/using/installing-campaign-standard-packages.md).

![](assets/ims_6.png)

## Konfigurera det externa kontot {#configuring-the-external-account}

Konfigurera **Adobe Experience Cloud** externt konto i **[!UICONTROL Administration > Platform > External accounts]**.

![](assets/ims_5.png)

Ange följande information:

* Anslutningsinformation för den IMS-server som används (ID och hemlighet). Denna information tillhandahålls av Adobe kundtjänstteam. Mer information finns i [Frågor och svar för Adobe Experience Cloud-administratörer](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/faq.html).

  The **[!UICONTROL Callback server]** adressen måste anges i **https**. Det här fältet motsvarar åtkomst-URL:en för din Adobe Campaign-instans.

* Organisations-ID: om du vill hitta ditt organisations-ID, se [den här sidan](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=sv){_blank}.

* Associationsmask: I det här fältet kan du definiera syntaxen som gör att konfigurationsnamnen i Enterprise Dashboard kan synkroniseras med grupperna i Adobe Campaign. Om du använder syntaxen&quot;Campaign - tenant_id - (.&#42;)&quot; länkas säkerhetsgruppen som skapas i Adobe Campaign till konfigurationsnamnet Campaign - tenant_id - internal_name i Enterprise Dashboard.

* Adobe Experience Cloud-anslutningsinformation, som är namnet på Adobe Experience Cloud-klienten.
