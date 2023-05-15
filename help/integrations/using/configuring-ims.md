---
product: campaign
title: Konfigurera IMS
description: Lär dig ansluta via en Adobe ID
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: b70ca220-1c81-4b23-b07a-a2cd694877fe
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 4%

---

# Konfigurera IMS{#configuring-ims}



>[!IMPORTANT]
>
>Implementeringen av Adobe IMS är strikt förbehållen de tekniska administratörerna på Adobe. Kontakta din Adobe-chef för att starta implementeringsprocessen.

## Förhandskrav {#prerequisites}

Så här använder du integreringen med IMS:

* Du måste ha ett namn och ett ID för Adobe Experience Cloud-organisationen. Om du vill hitta ditt organisations-ID går du till [den här sidan](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=sv){_blank}.
* Du måste lägga till användare i Experience Cloud. Mer information finns i [den här sidan](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html){_blank}.

>[!NOTE]
>
>Se till att dina användare är länkade till de Adobe Experience Cloud-grupper som ska synkroniseras med Adobe Campaign. [Läs mer](#configuring-the-external-account).

## Konsolen uppdateras {#updating-the-console}

Om du vill använda den här funktionen måste du installera den senaste versionen av konsolen.

## Installera paketet {#installing-the-package}

Du måste installera det inbyggda **[!UICONTROL Integration with the Adobe Experience Cloud]** paket. Att installera ett integrationspaket är detsamma som att installera ett standardpaket, vilket beskrivs i [den här sidan](../../installation/using/installing-campaign-standard-packages.md).

![](assets/ims_6.png)

## Konfigurera det externa kontot {#configuring-the-external-account}

Konfigurera **Adobe Experience Cloud** externt konto i **[!UICONTROL Administration > Platform > External accounts]**.

>[!CAUTION]
>
>Den här konfigurationen är reserverad för den tekniska administratören.

![](assets/ims_5.png)

Ange följande information:

* Anslutningsinformation för den IMS-server som används (ID och hemlighet). Denna information tillhandahålls av Adobe support. Mer information finns i [Frågor och svar för Adobe Experience Cloud-administratörer](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/faq.html).

   The **[!UICONTROL Callback server]** adressen måste anges i **https**. Det här fältet motsvarar åtkomst-URL:en för din Adobe Campaign-instans.

* Organisations-ID: för att hitta ditt organisations-ID, se [den här sidan](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=sv){_blank}.
* Associationsmask: I det här fältet kan du definiera syntaxen som gör att konfigurationsnamnen i Enterprise Dashboard kan synkroniseras med grupperna i Adobe Campaign. Om du använder syntaxen&quot;Campaign - tenant_id - (.&#42;)&quot; länkas säkerhetsgruppen som skapas i Adobe Campaign till konfigurationsnamnet Campaign - tenant_id - internal_name i Enterprise Dashboard.

   >[!CAUTION]
   >
   >Kopplingsmasken är nödvändig för att anslutningen via Adobe ID ska fungera korrekt.

* Adobe Experience Cloud anslutningsinformation, särskilt namnet på Adobe Experience Cloud-klienten.
