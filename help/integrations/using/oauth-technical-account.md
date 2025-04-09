---
product: campaign
title: Skapa och konfigurera ditt Adobe-konto för API:er
description: Läs mer om hur du skapar ett Adobe API-konto
role: User, Admin
level: Intermediate, Experienced
exl-id: 5d830ea0-a0a3-4b35-8dc4-e955380431fb
source-git-commit: 2bfcec5eaa1145cfb88adfa9c8b2f72ee3cd9469
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 2%

---

# Skapa ett tekniskt Adobe-konto {#create-service-account}

Autentiseringsuppgifter för server-till-server gör att programmets server kan generera åtkomsttokens och göra API-anrop för ditt program. [Läs mer](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/)

## Migrera befintliga integreringar {#migrate-jwt}

JWT-autentiseringsuppgifterna (Service Account) har tagits bort av Adobe. Kampanjintegreringar med Adobe lösningar och appar måste nu förlita sig på autentiseringsuppgifter för OAuth Server-till-Server.

Om du har implementerat inkommande eller utgående integreringar med Campaign före juni 2024 måste du uppgradera din Campaign-miljö till v7.4.1 och migrera ditt tekniska konto till Autentisering enligt informationen [i den här dokumentationen](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration){target="_blank"}. Befintliga JWT-autentiseringsuppgifter (Service Account) fortsätter att fungera till den **27 januari 2025**.

När migreringen är klar måste du koppla dina nya autentiseringsuppgifter till Campaign enligt beskrivningen i [det här avsnittet](#add-credentials).

## Skapa nytt tekniskt OAuth-konto för nya integreringar {#oauth-service}

Följ de här stegen för att skapa ett tekniskt OAuth-konto för nya integreringar:

1. Gå till Adobe Developer-konsolen och logga in som **systemadministratör** för din organisation.

   Mer information om administratörsroller finns på [sidan](https://helpx.adobe.com/enterprise/using/admin-roles.html).

1. Klicka på **[!UICONTROL Create a new project]**.

   ![](assets/api-account-1.png)

1. Klicka på **[!UICONTROL Add to Project]** och välj **[!UICONTROL API]**.

   ![](assets/api-account-2.png)

1. Välj den produkt som du vill integrera med Campaign och klicka på **[!UICONTROL Next]**.

1. Välj **[!UICONTROL OAuth Server-to-Server]** som autentiseringstyp och klicka på **[!UICONTROL Next]**.

   ![](assets/api-account-3.png)

1. Välj länken **[!UICONTROL Product profile]** till ditt projekt.

   Du kan skapa en ny vid behov. [Läs mer](https://helpx.adobe.com/enterprise/using/manage-product-profiles.html)

1. Klicka sedan på **[!UICONTROL Save Configured API]**.

   ![](assets/api-account-4.png)

1. Välj [!DNL OAuth Server-to-Server] under Autentiseringsuppgifter i ditt projekt och kopiera följande information:

   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

## Lägg till OAuth-projektautentiseringsuppgifter i Campaign {#add-credentials}

När du har utfört stegen ovan lägger du till dina OAuth-projektautentiseringsuppgifter i Adobe Campaign.

>[!NOTE]
>
>Detta är inte nödvändigt som värdkund eller hanterad molntjänstkund: Adobe har redan lagt till dina OAuth-projektbehörigheter i din miljö.
>

Följ de här stegen om du är lokal kund eller hybridkund:

1. Logga in via SSH i alla behållare där Adobe Campaign-instansen är installerad.

1. Lägg till dina OAuth-projektautentiseringsuppgifter i Adobe Campaign genom att köra följande kommando som `neolane`-användare. Detta infogar inloggningsuppgifterna **[!UICONTROL Technical Account]** i instanskonfigurationsfilen.

   ```
   nlserver config -instance:<instance_name> -setimsoauth:ims-org-id/client-id/technical-account-id/client-secret
   ```

   >[!NOTE]
   >
   > Använd `setimsauth` eller `setimsjwtauth` i stället för `setimsoauth` för versioner som är äldre än 7.4.1.


