---
product: campaign
title: Om Adobe Experience Cloud-utlösare
description: Kom igång med Adobe Experience Cloud Triggers implementering
feature: Triggers
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
audience: integrations
content-type: reference
exl-id: 0e337620-a49f-4e14-8c67-9279d74736f1
source-git-commit: 8de62db2499449fc9966b6464862748e2514a774
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 7%

---

# Arbeta med utlösare för Campaign och Experience Cloud{#about-adobe-experience-triggers}

[!DNL Triggers] är en integrering mellan Adobe Campaign och Adobe Analytics. Pipelinen hämtar användarens åtgärder eller utlösare från din webbplats. En kundvagnsöverläggning är ett exempel på utlösare. Utlösare bearbetas i Adobe Campaign för att skicka e-post i nära realtid.

>[!CAUTION]
>
>Den här funktionen är inte tillgänglig som en del av produkten. För den här implementeringen kan du samarbeta med din Adobe-representant/kundtjänst. Du kan sedan följa de steg som beskrivs här [page](../../integrations/using/configuring-pipeline.md#prerequisites).

[!DNL Triggers] köra marknadsföringsåtgärder inom ett kort tidsintervall efter en användares åtgärd. Den typiska svarstiden är mindre än en timme.

Det ger smidigare integrering eftersom konfigurationen är minimal och en tredje part inte berörs.
Det stöder också stora trafikvolymer utan att påverka marknadsföringsaktiviteternas resultat. Integrationen kan till exempel behandla en miljon utlösare per timme.

![](assets/do-not-localize/book.png) Upptäck hur man [skapa en Experience Cloud-utlösare](https://experienceleague.adobe.com/docs/experience-cloud/triggers/create.html) och identifiera, definiera och övervaka viktiga konsumentbeteenden.

## [!DNL Triggers] arkitektur {#triggers-architecture}

The [!DNL pipelined] körs alltid på Adobe Campaign marknadsföringsserver. Den ansluter till pipeline, hämtar händelserna och bearbetar dem direkt.

![](assets/triggers_2.png)

The [!DNL pipelined] loggar in på Experience Cloud med en autentiseringstjänst och skickar en privat nyckel. Autentiseringstjänsten returnerar en token. Token används för att autentisera vid hämtning av händelser.

## Förhandskrav {#adobe-io-prerequisites}

Kontrollera att du har:

* en giltig **Organisationens identifierare**: Organisations-ID är den unika identifieraren inom Adobe Experience Cloud, som används t.ex. för tjänsten VisitorID och IMS Single-Sign On (SSO). [Läs mer](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=sv)
* a **Åtkomst för utvecklare** till din organisation. Organisationens systemadministratör måste följa **Lägga till utvecklare i en enda produktprofil** detaljerad [på den här sidan](https://helpx.adobe.com/enterprise/using/manage-developers.html) för att ge utvecklare åtkomst till `Analytics - {tenantID}` Produktprofil för den Adobe Analytics-produkt som är kopplad till utlösare.

## Implementeringssteg {#implement}

Följ stegen nedan för att implementera Campaign och Experience Cloud Triggers:

1. Skapa ett OAuth-projekt. [Läs mer](oauth-technical-account.md#oauth-service)

1. Lägg till dina OAuth-projektbehörigheter i Adobe Campaign. [Läs mer](oauth-technical-account.md#add-credentials)

1. Uppdatera autentiseringstypen till utvecklarkonsolprojektet i konfigurationsfilen **config-&lt; instance-name >.xml** enligt följande:

   ```
   <pipelined ... authType="imsJwtToken"  ... />
   ```

   Kör sedan en `config -reload` och en omstart av [!DNL pipelined] för de ändringar som ska beaktas.

