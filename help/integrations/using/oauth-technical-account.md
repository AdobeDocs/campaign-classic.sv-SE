---
product: campaign
title: Skapa och konfigurera ditt Adobe-tekniska konto för API:er
description: Läs mer om hur du skapar ett Adobe API-konto
role: User, Admin
level: Beginner
source-git-commit: efd09fd71069878a5096bfa3592e6ebbaa9dd4e4
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 1%

---

# Skapa ett Adobe-konto {#create-service-account}

Autentiseringsuppgifter för server-till-server gör att programmets server kan generera åtkomsttokens och göra API-anrop för ditt program. [Läs mer](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/)

## Migrera befintliga integreringar {#migrate-jwt}

JWT-autentiseringsuppgifterna (Service Account) har tagits bort av Adobe. Kampanjintegreringar med lösningar och appar från Adobe måste nu förlita sig på autentiseringsuppgifter för OAuth Server-till-Server.

Om du har implementerat inkommande eller utgående integreringar med Campaign före juni 2024 måste du uppgradera din Campaign-miljö till v7.4.1 och migrera ditt tekniska konto till Auth så detaljerat som möjligt [i den här dokumentationen](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration){target="_blank"}. Befintliga JWT-referenser (Service Account) fortsätter att fungera tills **27 januari 2025**.

När migreringen är klar måste du koppla dina nya autentiseringsuppgifter till Campaign enligt anvisningarna i [det här avsnittet](#add-credentials).

## Skapa nytt tekniskt OAuth-konto för nya integreringar {#oauth-service}

Följ de här stegen för att skapa ett tekniskt OAuth-konto för nya integreringar:

1. Öppna Adobe Developer-konsolen och logga in som **Systemadministratör** i er organisation.

   Mer information om administratörsroller finns i [page](https://helpx.adobe.com/enterprise/using/admin-roles.html).

1. Klicka på **[!UICONTROL Create a new project]**.

   ![](assets/api-account-1.png)

1. Klicka **[!UICONTROL Add to Project]** och markera **[!UICONTROL API]**.

   ![](assets/api-account-2.png)

1. Välj den produkt du vill integrera med Campaign och klicka på **[!UICONTROL Next]**.

1. Välj **[!UICONTROL OAuth Server-to-Server]** som autentiseringstyp och klicka **[!UICONTROL Next]**.

   ![](assets/api-account-3.png)

1. Välj **[!UICONTROL Product profile]** länka till ditt projekt.

   Du kan skapa en ny vid behov. [Läs mer](https://helpx.adobe.com/enterprise/using/manage-product-profiles.html)

1. Klicka sedan på **[!UICONTROL Save Configured API]**.

   ![](assets/api-account-4.png)

1. Välj under Autentiseringsuppgifter i ditt projekt [!DNL OAuth Server-to-Server] och kopiera följande information:

   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

## Lägg till OAuth-projektautentiseringsuppgifter i Adobe Campaign {#add-credentials}

Följ stegen nedan för att lägga till dina OAuth-projektautentiseringsuppgifter i Adobe Campaign:

1. Logga in via SSH i alla behållare där Adobe Campaign-instansen är installerad.

1. Lägg till dina OAuth-projektautentiseringsuppgifter i Adobe Campaign genom att köra följande kommando som `neolane` användare. Det här infogar **[!UICONTROL Technical Account]** autentiseringsuppgifter i instanskonfigurationsfilen.

   ```
   nlserver config -instance:<instance_name> -setimsoauth:ims-org-id/client-id/technical-account-id/client-secret
   ```
