---
product: campaign
title: Konfigurera Developer Console för Adobe Experience Cloud Triggers
description: Så här konfigurerar du Developer Console Adobe Experience Cloud Triggers
feature: Triggers
audience: integrations
content-type: reference
index: y
internal: n
snippet: y
exl-id: ab30f697-3022-4a29-bbdb-14ca12ec9c3e
hide: true
hidefromtoc: true
source-git-commit: 8d15a5666b5768bc0f17a4391061c4fcb9f76811
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 1%

---

# Konfigurera Developer Console för Adobe Experience Cloud Triggers {#configuring-adobe-io}

<!--
>[!CAUTION]
>
>If you are using an older version of Triggers integration through oAuth authentication, **you need to move to Adobe I/O as described below**. 
>Note that during this move to [!DNL Adobe I/O], some incoming triggers may be lost.
>
>Legacy oAuth authentication mode with Campaign has been retired on **October 20, 2021**. Hosted environments benefit from an extension until **May 25, 2022**. As an on-premise or hybrid customer, contact Adobe Customer Care to extend support to **May 2022**. You must [provide the AppID of the OAuth application](../../integrations/using/configuring-pipeline.md#step-optional) to Adobe.
-->

## Förhandskrav {#adobe-io-prerequisites}

<!--
This integration only applies starting **Campaign Classic 20.2.4 and above, 19.1.8 and Gold Standard 11 releases**.
-->

Kontrollera att du har:

* en giltig **organisationsidentifierare**: Organisations-ID är den unika identifieraren inom Adobe Experience Cloud, som används t.ex. för VisitorID-tjänsten och IMS Single-Sign On (SSO). [Läs mer](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=sv)
* en **utvecklaråtkomst** till din organisation. Organisationens systemadministratör måste följa proceduren **Lägg till utvecklare i en enskild produktprofil** som beskrivs [ på den här sidan](https://helpx.adobe.com/se/enterprise/using/manage-developers.html) för att ge utvecklare åtkomst till produktprofilen `Analytics - {tenantID}` för den Adobe Analytics-produkt som är associerad med utlösare.

## Steg 1: Skapa/uppdatera OAuth-projekt {#creating-adobe-io-project}

>[!AVAILABILITY]
>
> JWT-autentiseringsuppgifterna (Service Account) har tagits bort av Adobe, och Campaign-integreringar med Adobe-lösningar och appar måste nu förlita sig på autentiseringsuppgifter för OAuth Server-till-Server. </br>
>
> * Om du har implementerat inkommande integreringar med Campaign måste du migrera ditt tekniska konto enligt beskrivningen i [den här dokumentationen](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#_blank). Befintliga [JWT-autentiseringsuppgifter ](oauth-technical-account.md) fortsätter att fungera till 27 januari 2025.</br>
>
> * Om ni har implementerat utgående integreringar, som integrering med Campaign-Analytics eller integrering med Experience Cloud-utlösare, fortsätter de att fungera fram till 27 januari 2025. Innan detta datum måste ni dock uppgradera er Campaign-miljö till v7.4.1 och migrera ert tekniska konto till Autentisering.

Om du vill fortsätta konfigurera din Adobe Analytics-anslutning öppnar du Adobe Developer-konsolen och skapar ett OAuth Server-till-Server-projekt.

Mer information finns på [den här sidan](oauth-technical-account.md#oauth-service).

## Steg 2: Lägg till projektautentiseringsuppgifterna i Adobe Campaign {#add-credentials-campaign}

Följ stegen som beskrivs på [den här sidan](oauth-technical-account.md#add-credentials) för att lägga till dina OAuth-projektautentiseringsuppgifter i Adobe Campaign.

## Steg 3: Uppdatera tagg för pipeline {#update-pipelined-tag}

Om du vill uppdatera taggen [!DNL pipelined] måste du uppdatera autentiseringstypen till utvecklarkonsolprojektet i konfigurationsfilen **config-&lt; instance-name >.xml** enligt följande:

```
<pipelined ... authType="imsJwtToken"  ... />
```

Kör sedan en `config -reload` och en omstart av [!DNL pipelined] för att ta hänsyn till ändringarna.
