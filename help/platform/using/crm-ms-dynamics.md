---
product: campaign
title: Campaign - Microsoft Dynamics CRM Connector
description: Lär dig hur du ansluter Campaign och Microsoft Dynamics
feature: Microsoft CRM Integration
exl-id: 26737940-b3ce-425c-9604-f4cefd19afaa
hide: true
hidefromtoc: true
source-git-commit: 42cec0e9bede94a2995a5ad442822512bda14f2b
workflow-type: tm+mt
source-wordcount: '1104'
ht-degree: 1%

---

# Connect Campaign och Microsoft Dynamics 365{#connect-to-msdyn}



På den här sidan får du lära dig hur du ansluter Campaign Classic till **Microsoft Dynamics CRM 365**.

Möjlig distribution sker via **webb-API** (rekommenderas). Mer information om hur du konfigurerar anslutningen till Microsoft Dynamics finns i [avsnittet nedan](#microsoft-dynamics-implementation-step).

Datasynkronisering utförs via en dedikerad arbetsflödesaktivitet. [Läs mer](../../platform/using/crm-data-sync.md).

## Implementeringssteg{#microsoft-dynamics-implementation-steps}

Om du vill ansluta Microsoft Dynamics 365 till Adobe Campaign via **webb-API** måste du utföra följande steg:

I Microsoft Dynamics CRM:
1. Hämta Microsoft Dynamics klient-ID
1. Generera nyckelidentifierare och nyckel-ID för Microsoft Dynamics-certifikat
1. Konfigurera behörigheter
1. Skapa en appanvändare
1. Koda den privata nyckeln

[Läs mer i det här avsnittet](#config-crm-microsoft)

I Campaign Classic:
1. Skapa ett nytt externt konto
1. Konfigurera det externa kontot med Microsoft Dynamics-inställningar
1. Använd konfigurationsassistenten för att mappa tabeller och synkronisera uppräkningar
1. Skapa synkroniseringsarbetsflödet

[Läs mer i det här avsnittet](#configure-acc-for-microsoft)


>[!CAUTION]
> När du ansluter Adobe Campaign till Microsoft Dynamics kan du inte:
> * Installera plugin-program som kan ändra CRM-funktionens beteende och leda till kompatibilitetsproblem med Adobe Campaign
> * Markera flera uppräkningar

## Konfigurera Microsoft Dynamics CRM {#config-crm-microsoft}

Om du vill generera åtkomsttoken och nycklar för att konfigurera kontot måste du logga in på [Microsoft Azure Directory](https://portal.azure.com) med hjälp av autentiseringsuppgifter för **Global administratör**. Följ sedan instruktionerna nedan.

### Hämta Microsoft Dynamics klient-ID {#get-client-id-microsoft}

Om du vill hämta klient-ID:t måste du registrera en app i Azure Active Directory. Klient-ID är samma som program-ID.

1. Navigera till **Azure Active Directory > Appregistreringar** och klicka på **Ny programregistrering**.
1. Ge ett unikt namn som kan hjälpa till att identifiera en instans, till exempel **adobecampaign`<instance identifier>`**.
1. Välj **Programtyp** som **webbprogram/API**.
1. Använd `http://localhost` som **inloggnings-URL**.

När du har sparat får du ett **program-ID** som är klient-ID för Campaign.

Läs mer på [den här sidan](https://docs.microsoft.com/powerapps/developer/common-data-service/walkthrough-register-app-azure-active-directory).

### Generera nyckelidentifierare och nyckel-ID för Microsoft Dynamics-certifikat {#config-certificate-key-id}

Följ stegen nedan för att hämta **certifikatnyckelidentifieraren (customKeyIdentifier)** och **nyckel-ID (keyId)**:

1. Navigera till **Azure Active Directory > App Registrations** och välj det program som skapades tidigare.
1. Klicka på **Certifikat och hemlighet**.
1. Klicka på **Överför certifikat** och bläddra sedan och överför det offentliga certifikat som genererats.
1. Om du vill generera certifikatet kan du använda openssl.

   Exempel:

   ```
   - openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout '<'private key name'>' -out '<'public certificate name'>
   ```

   >[!NOTE]
   >
   >Du kan ändra antalet dagar, här `-days 365`, i kodexemplet för en längre certifikatgiltighetsperiod.

1. Sedan måste du koda den i base64. Det gör du genom att använda en Base64-kodare eller kommandoraden `base64 -w0 private.key` för Linux.

1. Klicka på länken **Manifest** för att hämta **identifieraren för certifikatnyckeln (customKeyIdentifier)** och **nyckel-ID:t (keyId)**.

Identifieraren **för certifikatnyckeln (customKeyIdentifier)** och **nyckel-ID (keyId)** kommer att behövas senare för att konfigurera ditt externa Microsoft Dynamics CRM-konto med certifikatet **[!UICONTROL CRM O-Auth type]**.

### Konfigurera behörigheter {#config-permissions-microsoft}

**Steg 1**: Konfigurera **nödvändiga behörigheter** för det program som skapades.

1. Navigera till **Azure Active Directory > App Registrations** och välj det program som skapades tidigare.
1. Klicka på **Inställningar** överst till vänster.
1. På **Nödvändiga behörigheter** klickar du på **Lägg till** och **Välj ett API > Dynamics CRM Online**.
1. Klicka på kryssrutan **Välj**, aktivera kryssrutan **Använd Dynamics 365 som organisationsanvändare** och klicka på **Välj**.
1. Välj sedan **Manifest** på menyn **Hantera** i din app.

1. Ange egenskapen `allowPublicClient` från `null` till `true` i redigeraren **Manifest** och klicka på **Spara**.

**Steg 2**: Medgivande från bidragsadministratör

1. Navigera till **Azure Active Directory > Enterprise-program**.

1. Välj det program som du vill ge innehavaromfattande administratörsgodkännande för.

1. Välj **Behörigheter** under **Dokumentskydd** på den vänstra panelmenyn.

1. Klicka på **Bevilja administratörens samtycke**.

Mer information finns i [Azure-dokumentationen](https://docs.microsoft.com/azure/active-directory/manage-apps/grant-admin-consent#grant-admin-consent-from-the-azure-portal).

### Skapa en appanvändare {#create-app-user-microsoft}

>[!NOTE]
>
> Det här steget är valfritt med **[!UICONTROL Password credentials]**-autentisering.

Appanvändaren är den användare som programmet som registrerats ovan kommer att använda. Alla ändringar som görs i Microsoft Dynamics med appen som registrerats ovan görs via den här användaren.

**Steg 1**: Skapa en icke-interaktiv användare i Azure Active Directory

1. Klicka på **Azure Active Directory > Användare** och sedan på **Ny användare**.
1. Ange ett egennamn som du vill använda och användarnamnet ska vara ett e-postformat.
1. Välj **Dynamics 365 Administrator** i **katalogrollen**.

**Steg 2**: Tilldela rätt licens till den skapade användaren

1. Klicka på **Admin-appen** från [Microsoft Azure](https://portal.azure.com).
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
   >

1. Tilldela **program-ID** för [det program du skapade tidigare](#get-client-id-microsoft).
1. Klicka på **Hantera roller** och välj rollen **Systemadministratör** för användaren.

## Konfigurera kampanj {#configure-acc-for-microsoft}

>[!NOTE]
>
> När [RDS har tagits bort från Microsoft](https://docs.microsoft.com/previous-versions/dynamicscrm-2016/developers-guide/dn281891%28v=crm.8%29#microsoft-dynamics-crm-2011-endpoint) är de lokala och Office 365-typerna av CRM-distributioner inte längre kompatibla med Campaign. Adobe Campaign har nu endast stöd för Web API-distribution för CRM-versionen **Dynamic CRM 365**. [Läs mer](../../rn/using/deprecated-features.md#crm-connectors).

Om du vill ansluta Microsoft Dynamics 365 och Campaign måste du skapa och konfigurera en dedikerad **[!UICONTROL External Account]** i Campaign.

1. Navigera till **[!UICONTROL Administration > Platform > External accounts]**.

1. Välj det **[!UICONTROL Microsoft Dynamics CRM]** externa kontot. Markera alternativet **[!UICONTROL Enabled]**.

1. Fyll i de uppgifter som krävs för att ansluta Microsoft Dynamics 365 och Campaign.

   >[!NOTE]
   >
   >Konfiguration av det externa Microsoft Dynamics CRM-kontot med varje **[!UICONTROL CRM O-Auth type]** beskrivs [ i det här avsnittet ](../../installation/using/external-accounts.md#microsoft-dynamics-crm-external-account).

   ![](assets/crm-ms-dynamics-ext-account.png)

1. Klicka på länken **[!UICONTROL Microsoft CRM configuration assistant...]**. Adobe Campaign identifierar automatiskt tabellerna från Microsoft Dynamics datamall.

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

Campaign och Microsoft Dynamics är nu uppkopplade. Du kan konfigurera datasynkronisering mellan de två systemen. Läs mer i avsnittet [Datasynkronisering](../../platform/using/crm-data-sync.md).

>[!NOTE]
>
> Du måste se till att lägga till två URL:er i tillåtelselista: server-URL:en och `login.microsoftonline.com` i serverkonfigurationen. Mer information om hur du konfigurerar URL-behörigheter finns på [sidan](../../installation/using/url-permissions.md).

## Datatyper för fält som stöds {#ms-dyn-supported-types}

För Microsoft Dynamics 365-attributtyper som stöds/inte stöds finns följande:


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
