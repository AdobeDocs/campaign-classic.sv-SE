---
product: campaign
title: Använd din Adobe ID för att ansluta till Adobe Campaign
description: Läs mer om Adobe IMS-implementering i Adobe Campaign
feature: Configuration
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: 8dad8fa9-674c-433c-af30-8c6d0aadf525
source-git-commit: ffab91fc9fa7e60973fdda930239f5836671a341
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 13%

---

# Om Adobe ID {#about-adobe-id}

Adobe Identity Management System (IMS) hjälper administratörer att skapa och hantera användarnas åtkomst till program och tjänster. Mer information om de olika typerna av Adobe-ID finns i [den här sidan](https://helpx.adobe.com/enterprise/using/identity.html).

Kampanjanvändare kan ansluta till Adobe Campaign-konsolen med sin Adobe ID istället för [autentisering av inbyggda användare/lösenord](../../platform/using/access-management-operators.md). Implementeringen har följande fördelar:

* Samma ID kan användas för alla Experience Cloud-lösningar.
* Anslutningen behålls när du använder Adobe Campaign med olika integreringar.
* Skyddar lösenordshanteringsprincip som inte är för inbyggd inloggning/lösenord.
* Använda Federated ID-konton (extern ID-leverantör).

>[!IMPORTANT]
>
> Observera att det inte är tillåtet att ansluta till användare/lösenord (dvs. inbyggd autentisering) i Campaign v8. **Adobe rekommenderar att du utför migreringen från och med Campaign v7.3.5 för att smidigt kunna migrera till Campaign v8.**
>
>Lär dig hur du migrerar till Adobe IMS i [det här avsnittet](../../technotes/using/ac-ims.md).
>


<!--
>[!IMPORTANT]
>
>If you are connecting to Campaign through Adobe Identity Service (IMS), you need to upgrade to the latest build to be able to connect to Campaign after **June 30, 2021**. This upgrade is mandatory for both Campaign server and client console. 
>
>Depending on your current version, you must upgrade to one of the following releases: 
>
> * [Campaign [!DNL Gold Standard] 11](../../rn/using/gold-standard.md)
> * [Campaign 21.1.4](../../rn/using/latest-release.md)
>
>[Learn more about IMS updates](../../technotes/using/ims-updates.md)
-->

## Fler resurser

| Användbara sidor | Ytterligare resurser |
|---|---|
| [Konfigurera IMS](../../integrations/using/configuring-ims.md) | [Vanliga frågor om Experience Cloud](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/faq.html) |
| [Implementera IMS](../../integrations/using/implementing-ims.md) | [Åtkomsthantering](../../platform/using/access-management.md) |
| [IMS-felsökning](../../integrations/using/ims-troubleshooting.md) | [Installera Campaign-paket](../../installation/using/installing-campaign-standard-packages.md) |
