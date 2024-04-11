---
product: campaign
title: Campaign - Microsoft Dynamics CRM Connector
description: Lär dig ansluta Campaign och Microsoft Dynamics
feature: Microsoft CRM Integration
exl-id: 26737940-b3ce-425c-9604-f4cefd19afaa
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1104'
ht-degree: 1%

---

# Connect Campaign och Microsoft Dynamics 365{#connect-to-msdyn}



På den här sidan får du lära dig att ansluta Campaign Classic till **Microsoft Dynamics CRM 365**.

Möjlig distribution sker via **Webb-API** (rekommenderas). Se [avsnittet nedan](#microsoft-dynamics-implementation-step) om du vill lära dig steg för att konfigurera anslutningen till Microsoft Dynamics.

Datasynkronisering utförs via en dedikerad arbetsflödesaktivitet. [Läs mer](../../platform/using/crm-data-sync.md).

## Implementeringssteg{#microsoft-dynamics-implementation-steps}

Koppla Microsoft Dynamics 365 till Adobe Campaign via **Webb-API** måste du utföra följande steg:

I Microsoft Dynamics CRM:
1. Hämta klient-ID för Microsoft Dynamics
1. Generera nyckelidentifierare och nyckel-ID för Microsoft Dynamics-certifikat
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
> När du ansluter Adobe Campaign med Microsoft Dynamics kan du inte:
> * Installera plugin-program som kan ändra CRM-funktionens beteende och leda till kompatibilitetsproblem med Adobe Campaign
> * Markera flera uppräkningar

## Konfigurera Microsoft Dynamics CRM {#config-crm-microsoft}

Om du vill generera åtkomsttoken och nycklar för att konfigurera kontot måste du logga in på [Microsoft Azure Directory](https://portal.azure.com) med **Global administratör** autentiseringsuppgifter. Följ sedan instruktionerna nedan.

### Hämta klient-ID för Microsoft Dynamics {#get-client-id-microsoft}

Om du vill hämta klient-ID:t måste du registrera en app i Azure Active Directory. Klient-ID är samma som program-ID.

1. Navigera till **Azure Active Directory > App Registrations** och klicka  **Ny ansökningsregistrering**.
1. Ge ett unikt namn som kan hjälpa till att identifiera en instans, till exempel **adobecampaign`<instance identifier>`**.
1. Välj **Programtyp** as **Webbprogram/API**.
1. Använd `http://localhost` for **Inloggnings-URL**.

När du sparar får du en **Program-ID** som är klient-ID för Campaign.

Läs mer på [den här sidan](https://docs.microsoft.com/powerapps/developer/common-data-service/walkthrough-register-app-azure-active-directory).

### Generera nyckelidentifierare och nyckel-ID för Microsoft Dynamics-certifikat {#config-certificate-key-id}

För att få **Identifierare för certifikatnyckel (customKeyIdentifier)** och **Nyckel-ID (keyId)** följer du stegen nedan:

1. Navigera till **Azure Active Directory > App Registrations** och välj det program som skapades tidigare.
1. Klicka på **Certifikat och hemlighet**.
1. Klicka på **Överför certifikat** och sedan bläddra och ladda upp det offentliga certifikat som genererats.
1. Om du vill generera certifikatet kan du använda openssl.

   Exempel:

   ```
   - openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout '<'private key name'>' -out '<'public certificate name'>
   ```

   >[!NOTE]
   >
   >Du kan ändra antalet dagar här `-days 365`, i kodexemplet för en längre certifikatgiltighetsperiod.

1. Sedan måste du koda den i base64. Du kan göra det med hjälp av en Base64-kodare eller via kommandoraden `base64 -w0 private.key` för Linux.

1. Klicka på **Manifest** länk för att hämta **Identifierare för certifikatnyckel (customKeyIdentifier)** och **Nyckel-ID (keyId)**.

The **Identifierare för certifikatnyckel (customKeyIdentifier)** och **Nyckel-ID (keyId)** behövs senare för att konfigurera ditt externa Microsoft Dynamics CRM-konto med hjälp av certifikatet **[!UICONTROL CRM O-Auth type]**.

### Konfigurera behörigheter {#config-permissions-microsoft}

**Steg 1**: Konfigurera **Nödvändiga behörigheter** för programmet som skapades.

1. Navigera till **Azure Active Directory > App Registrations** och välj det program som skapades tidigare.
1. Klicka **Inställningar** överst till vänster.
1. På **Nödvändiga behörigheter**, klicka **Lägg till** och **Välj ett API > Dynamics CRM Online**.
1. Klicka **Välj**, aktivera **Använd Dynamics 365 som organisationsanvändare** kryssruta och klicka **Välj**.
1. Välj sedan **Manifest** under **Hantera** -menyn.

1. Från **Manifest** redigeraren, ange `allowPublicClient` egenskap från `null` till `true` och klicka **Spara**.

**Steg 2**: Medgivande från bidragsadministratör

1. Navigera till **Azure Active Directory > Enterprise-program**.

1. Välj det program som du vill ge innehavaromfattande administratörsgodkännande för.

1. Välj **Behörigheter** under **Säkerhet**.

1. Klicka **Medgivande från bidragsadministratör**.

Mer information finns i [Azure-dokumentation](https://docs.microsoft.com/azure/active-directory/manage-apps/grant-admin-consent#grant-admin-consent-from-the-azure-portal).

### Skapa en appanvändare {#create-app-user-microsoft}

>[!NOTE]
>
> Det här steget är valfritt med **[!UICONTROL Password credentials]** autentisering.

Appanvändaren är den användare som programmet som registrerats ovan kommer att använda. Alla ändringar som görs i Microsoft Dynamics med den app som registrerats ovan görs via den här användaren.

**Steg 1**: Skapa en icke-interaktiv användare i azure Active Directory

1. Klicka **Azure Active Directory > Användare** och klicka **Ny användare**.
1. Ange ett egennamn som du vill använda och användarnamnet ska vara ett e-postformat.
1. Välj **Dynamics 365-administratör** i **Katalogroll**.

**Steg 2**: Tilldela den skapade användaren en korrekt licens

1. Från [Microsoft Azure](https://portal.azure.com), klicka på **Administratörsapp**.
1. Gå till **Användare > Aktiva användare** och klicka på den nyskapade användaren.
1. Klicka på **Redigera produktlicenser** och väljer **Dynamics 365 Customer Engagement Plan**.
1. Klicka **Stäng**.

**Steg 3**: Skapa en programanvändare i Dynamics CRM

1. Från [Microsoft Azure](https://portal.azure.com), navigera till **Inställningar > Dokumentskydd > Användare**.
1. Klicka på listrutan och välj **Programanvändare** och klicka **Nytt**.
1. Använd samma användarnamn som användaren skapade i den aktiva katalogen ovan

   >[!NOTE]
   >
   >Om du använder samma namn genereras ett dubblettnyckelfel, så använd ett annat användarnamn och fortsätt tills vi får en bekräftelse på om det här steget behövs.
   >

1. Tilldela **Program-ID** for [det program du skapade tidigare](#get-client-id-microsoft).
1. Klicka på **Hantera roller** och väljer **Systemadministratör** roll för användaren.

## Konfigurera kampanj {#configure-acc-for-microsoft}

>[!NOTE]
>
> Lägg upp avvecklingen av [RDS från Microsoft](https://docs.microsoft.com/previous-versions/dynamicscrm-2016/developers-guide/dn281891%28v=crm.8%29#microsoft-dynamics-crm-2011-endpoint)är de lokala och Office 365-typerna av CRM-distributioner inte längre kompatibla med Campaign. Adobe Campaign har nu endast stöd för Web API-distribution för CRM-versionen **Dynamisk CRM 365**. [Läs mer](../../rn/using/deprecated-features.md#crm-connectors).

Om du vill ansluta Microsoft Dynamics 365 och Campaign måste du skapa och konfigurera en dedikerad **[!UICONTROL External Account]** i Campaign.

1. Navigera till **[!UICONTROL Administration > Platform > External accounts]**.

1. Välj **[!UICONTROL Microsoft Dynamics CRM]** externt konto. Markera alternativet **[!UICONTROL Enabled]**.

1. Fyll i den information som krävs för att ansluta Microsoft Dynamics 365 och Campaign.

   >[!NOTE]
   >
   >Konfiguration av externt Microsoft Dynamics CRM-konto med varje **[!UICONTROL CRM O-Auth type]** är detaljerad [i det här avsnittet](../../installation/using/external-accounts.md#microsoft-dynamics-crm-external-account).

   ![](assets/crm-ms-dynamics-ext-account.png)

1. Klicka på **[!UICONTROL Microsoft CRM configuration wizard...]** länk. Adobe Campaign identifierar automatiskt tabellerna från datamallen i Microsoft Dynamics.

   ![](assets/crm_connectors_msdynamics_02.png)

1. Markera de tabeller som ska återställas.

   ![](assets/crm_connectors_msdynamics_03.png)

1. Klicka **[!UICONTROL Next]** för att börja skapa motsvarande schema.

   ![](assets/crm_connectors_msdynamics_04.png)

   >[!NOTE]
   >
   >Om du vill godkänna konfigurationen måste du koppla från/återansluta till Adobe Campaign-konsolen.

   Du kan kontrollera att det matchande dataschemat blir tillgängligt i Adobe Campaign.

   ![](assets/crm_connectors_msdynamics_05.png)

1. Klicka på **[!UICONTROL Synchronizing enumerations...]** för att starta synkroniseringen av uppräkningar mellan Adobe Campaign och Microsoft Dynamics.

   ![](assets/crm_connectors_msdynamics_06.png)

Campaign och Microsoft Dynamics är nu anslutna. Du kan konfigurera datasynkronisering mellan de två systemen. Läs mer i [Datasynkronisering](../../platform/using/crm-data-sync.md) -avsnitt.

>[!NOTE]
>
> Du måste se till att lägga till två URL:er i tillåtelselista: serverns URL och `login.microsoftonline.com` i serverkonfigurationen. Mer information om hur du konfigurerar URL-behörigheter finns i [page](../../installation/using/url-permissions.md).

## Datatyper för fält som stöds {#ms-dyn-supported-types}

För Microsoft Dynamics 365 finns följande attributtyper som stöds/inte stöds:


| Attributtyp | Stöds |
| --------------------------------------------------------------------------------- | --------- |
| Grundläggande typer: boolesk, datetime, decimal, float, double, integer, bigint , string | Ja |
| Pengar (som dubbla) | Ja |
| memo, entityname , primarykey, uniqueidentifier (som strängar) | Ja |
| Status, picklist (vi lagrar möjliga värden i uppräkningar), state (sträng) | Ja |
| ägare (som sträng) | Ja |
| Uppslag (endast referenssökningar för en entitet) | Ja |
| kund | Nej |
| Angående | Nej |
| PartyList | Nej |
| ManagedProperty | Nej |
| Alternativuppsättning för MultiSelect | Nej |
