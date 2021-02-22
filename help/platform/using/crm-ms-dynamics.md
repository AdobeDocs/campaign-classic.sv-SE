---
solution: Campaign Classic
product: campaign
title: Microsoft Dynamics CRM Connector
description: Connect Campaign och Microsoft Dynamics
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 521bc3bf9b2507947007d7f458679275d407f910
workflow-type: tm+mt
source-wordcount: '958'
ht-degree: 0%

---


# Connect Campaign och Microsoft Dynamics 365{#connect-to-msdyn}

På den här sidan får du lära dig att ansluta Campaign Classic till **Microsoft Dynamics CRM 365**.

Möjliga distributioner är:

* via **webb-API** (rekommenderas). Läs [avsnittet nedan](#microsoft-dynamics-implementation-step) om du vill veta mer om hur du konfigurerar anslutningen till Microsoft Dynamics.
* med **Office 365**. Se [den här videon](#microsoft-dynamics-office-365) om du vill veta hur du konfigurerar integreringen.
* för en **lokal**-distribution använder du nyckelstegen för Office 365.

Datasynkronisering utförs via en dedikerad arbetsflödesaktivitet. [Läs mer](../../platform/using/crm-data-sync.md).


>[!NOTE]
>
> CRM-systemversioner som är kompatibla med Campaign visas i [kompatibilitetsmatrisen](../../rn/using/compatibility-matrix.md#CRMconnectors).


## Implementeringssteg{#microsoft-dynamics-implementation-steps}

Om du vill ansluta Microsoft Dynamics 365 till Adobe Campaign via **webb-API** måste du utföra följande steg:

I Microsoft Dynamics CRM:
1. Hämta klient-ID för Microsoft Dynamics
1. Generera Microsoft Dynamics-klienthemlighet
1. Konfigurera behörigheter
1. Skapa en appanvändare
1. Koda den privata nyckeln

[Läs mer i det här avsnittet](#config-crm-microsoft)

I Campaign Classic:
1. Skapa ett nytt externt konto
1. Konfigurera det externa kontot med inställningarna för Microsoft Dynamics
1. Använd konfigurationsguiden för att mappa tabeller och synkronisera uppräkningar
1. Skapa synkroniseringsarbetsflödet

[Läs mer i det här avsnittet](#configure-acc-for-microsoft)


>[!CAUTION]
>
> När du ansluter Adobe Campaign med Microsoft Dynamics kan du inte:
> * Installera plugin-program som kan ändra CRM-funktionens beteende och leda till kompatibilitetsproblem med Adobe Campaign
> * Markera flera uppräkningar
>



## Konfigurera Microsoft Dynamics CRM {#config-crm-microsoft}

Om du vill generera åtkomsttoken och nycklar för att konfigurera kontot måste du logga in på [Microsoft Azure Directory](https://portal.azure.com) med en **global administratör**-inloggningsinformation. Följ sedan instruktionerna nedan.

### Hämta Microsoft Dynamics klient-ID {#get-client-id-microsoft}

Om du vill hämta klient-ID:t måste du registrera en app i Azure Active Directory. Klient-ID är samma som program-ID.

1. Navigera till **Azure Active Directory > App Registrations** och klicka på **Ny programregistrering**.
1. Ge ett unikt namn som kan hjälpa till att identifiera en instans, till exempel **adobecampaign`<instance identifier>`**.
1. Välj **Programtyp** som **Webbprogram/API**.
1. Använd `http://localhost` för **inloggnings-URL**.

När du har sparat får du ett **program-ID** som är Klient-ID för Campaign.

Läs mer i [den här sidan](https://docs.microsoft.com/en-us/powerapps/developer/common-data-service/walkthrough-register-app-azure-active-directory).

### Generera Microsoft Dynamics-klienthemlighet {#config-client-secret-microsoft}

Klienthemligheten är nyckeln som är unik för klient-ID:t. Följ stegen nedan för att hämta identifieraren för certifikatnyckeln:

1. Navigera till **Azure Active Directory > App Registrations** och välj det program som skapades tidigare.
1. Klicka på **Certifikat och hemlighet**.
1. Klicka på **Överför certifikat** och bläddra sedan och överför det offentliga certifikat som genererats.
1. Om du vill generera certifikatet kan du använda openssl.

   Exempel:

   ```
   - openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout '<'private key name'>' -out '<'public certificate name'>
   ```

1. Klicka på länken **manifest** för att hämta **certifikatnyckelidentifieraren** och **nyckel-ID**.

### Konfigurera behörigheter {#config-permissions-microsoft}

Du måste konfigurera **Nödvändiga behörigheter** för det program som skapades.

1. Navigera till **Azure Active Directory > App Registrations** och välj det program som skapades tidigare.
1. Klicka på **Inställningar** överst till vänster.
1. På **Nödvändiga behörigheter** klickar du på **Lägg till** och **Välj ett API > Dynamics CRM Online**.
1. Klicka sedan på **Markera**, aktivera **Använd Dynamics 365 som organisationsanvändare** och klicka på **Välj**.

### Skapa en appanvändare {#create-app-user-microsoft}

Appanvändaren är den användare som programmet som registrerats ovan kommer att använda. Alla ändringar som görs i Microsoft Dynamics med den app som registrerats ovan görs via den här användaren.

**Steg 1**: Skapa en icke-interaktiv användare i azure Active Directory

1. Klicka på **Azure Active Directory > Användare** och klicka på **Ny användare**.
1. Ange ett egennamn som du vill använda och användarnamnet ska vara ett e-postformat.
1. Välj **Dynamics 365 Administrator** i **katalogrollen**.

**Steg 2**: Tilldela den skapade användaren en korrekt licens

1. Från [Microsoft Azure](https://portal.azure.com), klicka på **Admin-appen**.
1. Gå till **Användare > Aktiva användare** och klicka på den nyskapade användaren.
1. Klicka på **Redigera produktlicenser** och välj **Dynamics 365 Customer Engagement Plan**.
1. Klicka på **Stäng**.

**Steg 3**: Skapa en programanvändare i Dynamics CRM

1. Navigera från [Microsoft Azure](https://portal.azure.com) till **Inställningar > Säkerhet > Användare**.
1. Klicka på listrutan, välj **Programanvändare** och klicka på **Nytt**.
1. Använd samma användarnamn som användaren skapade i den aktiva katalogen ovan

   >[!NOTE]
   >
   >Om du använder samma namn genereras ett dubblettnyckelfel, så använd ett annat användarnamn och fortsätt tills vi får en bekräftelse på om det här steget behövs.

1. Tilldela **program-ID** för [det program du skapade tidigare](#get-client-id-microsoft).
1. Klicka på **Hantera roller** och välj rollen **Systemadministratör** för användaren.

## Konfigurera kampanj {#configure-acc-for-microsoft}

Om du vill ansluta till Microsoft Dynamics 365 och Campaign måste du skapa och konfigurera ett dedikerat externt konto i Campaign.

1. Navigera till **[!UICONTROL Administration > Platform > External accounts]**.

1. Skapa ett nytt externt konto, välj typen **[!UICONTROL Microsoft Dynamics CRM]** och alternativet **[!UICONTROL Enable]**.

1. Välj distributionstypen **[!UICONTROL Web API]**:

   Adobe Campaign Classic stöder Dynamics 365 REST-gränssnittet med OAuth-protokollet för autentisering med en **[!UICONTROL Certificate]** eller **[!UICONTROL Password Credentials]**.

   Använd inställningarna [som tidigare definierats](#get-client-id-microsoft) i Azure Directory för att konfigurera det externa kontot.

   ![](assets/crm-ms-dynamics-ext-account.png)

   >[!NOTE]
   >
   >Konfigurationen av det externa Microsoft Dynamics CRM-kontot är detaljerad [i det här avsnittet](../../installation/using/external-accounts.md#microsoft-dynamics-crm-external-account).

1. Klicka på länken **[!UICONTROL Microsoft CRM configuration wizard...]**: Adobe Campaign identifierar automatiskt tabellerna från datamallen i Microsoft Dynamics.

   ![](assets/crm_connectors_msdynamics_02.png)

1. Markera de tabeller som ska återställas.

   ![](assets/crm_connectors_msdynamics_03.png)

1. Klicka på **[!UICONTROL Next]** för att börja skapa motsvarande schema.

   ![](assets/crm_connectors_msdynamics_04.png)

   >[!NOTE]
   >
   >Om du vill godkänna konfigurationen måste du koppla från/återansluta till Adobe Campaign-konsolen.

   Du kan kontrollera att det matchande dataschemat blir tillgängligt i Adobe Campaign.

   ![](assets/crm_connectors_msdynamics_05.png)

1. Klicka på länken **[!UICONTROL Synchronizing enumerations...]** för att starta synkroniseringen av uppräkningar mellan Adobe Campaign och Microsoft Dynamics.

   ![](assets/crm_connectors_msdynamics_06.png)

Campaign och Microsoft Dynamics är nu anslutna. Du kan konfigurera datasynkronisering mellan de två systemen. Läs mer i avsnittet [Datasynkronisering](../../platform/using/crm-data-sync.md).

## Konfigurera Microsoft Dynamics CRM Office 365-integrering{#microsoft-dynamics-office-365}

I den här videon får du lära dig hur du integrerar Dynamics 365 med Adobe Campaign Classic i samband med en Office 365-distribution.

>[!VIDEO](https://video.tv.adobe.com/v/23837?quality=12)


## Fältdatatyper som stöds {#ms-dyn-supported-types}

För attributtyper som stöds/inte stöds i Microsoft Dynamics 365 anges nedan:


| Attributtyp | Stöds |
| --------------------------------------------------------------------------------- | --------- |
| Grundläggande typer: boolean, datetime, decimal, float, double, integer, bigint , string | Ja |
| Pengar (som dubbla) | Ja |
| memo, entityname , primarykey, uniqueidentifier (som strängar) | Ja |
| Status, picklist (vi lagrar möjliga värden i uppräkningar), state (sträng) | Ja |
| ägare (som sträng) | Ja |
| Uppslag (endast referenssökningar för en enhet) | Ja |
| kund | Nej |
| Angående | Nej |
| PartyList | Nej |
| ManagedProperty | Nej |
