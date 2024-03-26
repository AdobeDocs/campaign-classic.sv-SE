---
product: campaign
title: Hantera förfrågningar om användarens information
description: Läs mer om förfrågningar om användarens information
feature: Privacy, Privacy Tools
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: c7688c2a-f0a7-4c51-a4cf-bf96fe8bf9b6
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 100%

---

# Om förfrågningar om användarens information {#privacy-requests}



Se [det här avsnittet](privacy-management.md) för en allmän presentation om sekretesshantering.

Denna information gäller för GDPR, CCPA, PDPA och LGPD. Se [det här avsnittet](privacy-management.md#privacy-management-regulations) för mer information om dessa regelverk.

>[!NOTE]
>
>[Det här avsnittet](#sale-of-personal-information-ccpa) förklarar avanmälan till försäljning av personuppgifter vilken är specifik för CCPA.

<!--Installation procedures described in this document are applicable starting Campaign Classic 18.4 (build 8931+). If you are running on a previous version, refer to this [technote](https://helpx.adobe.com/campaign/kb/how-to-install-gdpr-package-on-legacy-versions.html).-->

För att underlätta beredskapen gällande din integritet kan du hantera förfrågningar om åtkomst och borttagning med Adobe Campaign. **Det här avsnittet** beskriver **åtkomsträttigheter** och [rätten att glömmas](privacy-management.md#right-access-forgotten) (borttagningsbegäran).

Adobe Campaign erbjuder personuppgiftsansvariga två möjligheter att utföra förfrågningar om åtkomst till eller radering av användarens information:

* Via **Adobe Campaign-gränssnittet**: För varje förfrågan om användarens information skapar den personuppgiftsansvariga en ny förfrågan om användaren information i Adobe Campaign. Se [det här avsnittet](privacy-requests-ui.md).
* Via **API:et**: Adobe Campaign tillhandahåller ett API som tillåter automatisk behandling av förfrågningar om användarens information med SOAP. Se [det här avsnittet](privacy-requests-api.md).

>[!NOTE]
>
>Mer information om personuppgifter och de olika enheter som hanterar data (personuppgiftsansvarig, personuppgiftsbiträde och registrerad) finns i [Personuppgifter och personer](privacy-and-recommendations.md#personal-data).

## Förhandskrav {#prerequesites}

Adobe Campaign erbjuder verktyg för personuppgiftsansvarig som låter dig skapa och bearbeta förfrågningar om användarens information gällande data som lagras i Adobe Campaign. Det är dock den personuppgiftsansvariges ansvar att hantera relationen med den registrerade (e-post, kundtjänst eller en webbportal).

Det är därför ditt ansvar som personuppgiftsansvarig att bekräfta identiteten på den registrerade som gör förfrågan och bekräfta att de uppgifter som skickas tillbaka till den som utförde förfrågan avser den registrerade.

## Installera sekretesspaketet {#install-privacy-package}

Om du vill använda den här funktionen måste du installera **[!UICONTROL Privacy Data Protection Regulation]**-paketet via menyn **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** > **[!UICONTROL Adobe Campaign Package]**. Mer information om hur du installerar paket finns i den [detaljerade dokumentationen](../../installation/using/installing-campaign-standard-packages.md).

Två nya mappar, som är specifika för sekretess, skapas under **[!UICONTROL Administration]** > **[!UICONTROL Platform]**:

* **[!UICONTROL Privacy Requests]**: Här skapar du dina förfrågningar om användarens information och följer deras utveckling.
* **[!UICONTROL Namespaces]**: Här definierar du fältet som används för att identifiera den registrerade i databasen i Adobe Campaign.

![](assets/privacy-folders.png)

I **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]** körs tre tekniska arbetsflöden varje dag för att behandla förfrågningar om användarens information.

![](assets/privacy-workflows.png)

* **[!UICONTROL Collect privacy requests]**: Det här arbetsflödet genererar mottagarens data som lagras i Adobe Campaign och gör dem tillgängliga att hämta på skärmen om förfrågan om användarens information.
* **[!UICONTROL Delete privacy requests data]**: Det här arbetsflödet tar bort mottagarens data som lagras i Adobe Campaign.
* **[!UICONTROL Privacy request cleanup]**: Det här arbetsflödet raderar de filer för åtkomstförfrågan som är äldre än 90 dagar.

Den namngivna rättigheten **[!UICONTROL Privacy Data Right]** har lagts till i **[!UICONTROL Administration]** > **[!UICONTROL Access Management]** > **[!UICONTROL Named rights]**. Den här namngivna rättigheten krävs för att personuppgiftsansvariga ska kunna använda sekretessverktyg. På så sätt kan de skapa nya förfrågningar, spåra deras utveckling, använda API:et, osv.

![](assets/privacy-right.png)

## Namnrymder {#namesspaces}

Innan du skapar förfrågningar om användarens information måste du definiera det namnutrymme som ska användas. Det här är nyckeln som används för att identifiera den registrerade i databasen i Adobe Campaign.

Tre namnutrymmen är tillgängliga direkt: e-post, telefon och mobiltelefon. Om du behöver ett annat namnutrymme (till exempel ett anpassat mottagarfält) kan du skapa ett nytt från **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Namespaces]**.

>[!NOTE]
>
>För att få bästa möjliga prestanda bör du använda färdiga namnutrymmen.
