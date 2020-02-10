---
title: Skapa erbjudandemellanslag
seo-title: Skapa erbjudandemellanslag
description: Skapa erbjudandemellanslag
seo-description: null
page-status-flag: never-activated
uuid: 2ad38697-db14-4dc0-abb8-9b71d57e0e35
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: managing-environments
discoiquuid: 0fae2149-0980-466d-ac9e-8afec2e278be
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 215e4d1ca78938b38b53cae0357612deebf7727b

---


# Skapa erbjudandemellanslag{#creating-offer-spaces}

Det går endast att skapa utrymme för erbjudandet av en **teknisk administratör** med tillgång till undermappen för erbjudandeutrymmet. Utrymmen kan bara skapas i designmiljön och dupliceras automatiskt till den aktiva miljön när erbjudandet godkänns.

Innehållet i katalogerbjudandena konfigureras i erbjudandeutrymmena. Som standard kan innehållet innehålla följande fält: **[!UICONTROL Title]**, **[!UICONTROL Destination URL]**, **[!UICONTROL Image URL]**, **[!UICONTROL HTML content]** och **[!UICONTROL Text content]**. Fältsekvensen är konfigurerad i erbjudandeutrymmet.

Med avancerade parametrar kan du ange en kontaktidentifieringsnyckel (som kan bestå av olika element, till exempel namn- och e-postfältet, samtidigt). Mer information finns i avsnittet [Presentera ett identifierat erbjudande](../../interaction/using/integration-via-javascript--client-side-.md#presenting-an-identified-offer) .

HTML- eller XML-återgivningen skapas via en återgivningsfunktion. Sekvensen för fälten som definieras i återgivningsfunktionen måste vara identisk med sekvensen som konfigurerats i innehållet.

![](assets/offer_space_create_009.png)

Gör så här för att skapa ett nytt erbjudande:

1. Gå till listan med erbjudanden och klicka på **[!UICONTROL New]**.

   ![](assets/offer_space_create_001.png)

1. Markera den kanal som du vill använda och ändra etiketten för erbjudandeutrymmet.

   ![](assets/offer_space_create_002.png)

1. Markera **[!UICONTROL Enable unitary mode]** rutan om något av följande gäller dig:

   * Du använder Interaktion med Message Center
   * Du använder Unikt läge för interaktion (inkommande interaktioner)

1. Gå till **[!UICONTROL Content field]** fönstret och klicka **[!UICONTROL Add]**.

   ![](assets/offer_space_create_003.png)

1. Gå till **[!UICONTROL Content]** noden och markera fälten i följande ordning: **[!UICONTROL Title]**, då **[!UICONTROL Image URL]**, då **[!UICONTROL HTML content]**, **[!UICONTROL Destination URL]**.

   ![](assets/offer_space_create_004.png)

1. Markera **[!UICONTROL Required]** rutan för att göra varje fält obligatoriskt.

   >[!NOTE]
   >
   >Den här konfigurationen används vid förhandsgranskningen och gör att erbjudanden blir ogiltiga vid publicering om något av de obligatoriska elementen saknas i det aktuella erbjudandet. Om ett erbjudande redan finns på en plats där erbjudandet ska erbjudas beaktas dock inte dessa kriterier.

   ![](assets/offer_space_create_005.png)

1. Klicka **[!UICONTROL Edit functions]** för att skapa en återgivningsfunktion.

   Dessa funktioner används för att generera offertrepresentationer på ett visst utrymme. Det finns flera möjliga format: HTML eller text för utgående interaktioner och XML för inkommande interaktioner.

   ![](assets/offer_space_create_006.png)

1. Gå till **[!UICONTROL HTML rendering]** fliken och välj **[!UICONTROL Overload the HTML rendering function]**.
1. Infoga återgivningsfunktionen.

   ![](assets/offer_space_create_007.png)

Om det behövs kan du överlagra XML-återgivningsfunktionerna för inkommande interaktioner. Du kan också överlagra återgivningsfunktioner för HTML och text för utgående interaktioner. Mer information finns i [Om inkommande kanaler](../../interaction/using/about-inbound-channels.md).

## Erbjud förslagsstatus {#offer-proposition-statuses}

Ett erbjudande kan ha olika status beroende på interaktionen med målpopulationen. Interaktionen innehåller en uppsättning värden som kan tillämpas på erbjudandet under hela dess livscykel. Du måste dock konfigurera plattformen så att statusen ändras när erbjudandeförslaget skapas och godkänns.

>[!NOTE]
>
>Status för erbjudandeförslaget uppdateras inte omedelbart. Den utförs av spårningsarbetsflödet som aktiveras varje timme.

### Statuslista {#status-list}

Interaktionen innehåller följande värden som kan användas för att kvalificera status för ett erbjudande:

* **[!UICONTROL Accepted]**.
* **[!UICONTROL Scheduled]**.
* **[!UICONTROL Generated]**.
* **[!UICONTROL Interested]**.
* **[!UICONTROL Presented]**.
* **[!UICONTROL Rejected]**.

De här värdena används inte som standard: måste konfigureras.

>[!NOTE]
>
>Status för ett erbjudande ändras automatiskt till Presenterat om erbjudandet är kopplat till en leverans med statusen Skickat.

### Konfigurera status när förslaget skapas {#configuring-the-status-when-the-proposition-is-created}

När ett erbjudande skapas av interaktionsmotorn ändras dess status, oavsett om det är en inkommande eller en utgående interaktion. Valet mellan dessa två värden beror på hur de tillgängliga utrymmena konfigurerades i **[!UICONTROL Design]** miljön

För varje space kan du konfigurera den status som du vill använda när ett förslag skapas, beroende på vilken information som ska visas i erbjudanderapporten.

Gör så här:

1. Gå till fliken **[!UICONTROL Storage]** för det önskade utrymmet.
1. Välj den status som du vill tillämpa på utkastet när det skapas.

   ![](assets/offer_update_status_001.png)

### Konfigurera status när förslaget godkänns {#configuring-the-status-when-the-proposition-is-accepted}

När ett offertförslag har godkänts kan du använda ett av de värden som anges som standard för att konfigurera förslagets nya status. Uppdateringen gäller när en mottagare klickar på en länk i erbjudandet som anropar interaktionsmotorn.

Gör så här:

1. Gå till fliken **[!UICONTROL Storage]** för det önskade utrymmet.
1. Välj den status som du vill tillämpa på förslaget när det godkänns.

   ![](assets/offer_update_status_002.png)

**Inkommande interaktion**

På fliken **[!UICONTROL Storage]** kan du bara definiera status för **föreslagna** och **godkända** erbjudandeförslag. För inkommande interaktion ska status för erbjudandeförslag anges direkt i URL:en för anrop av erbjudandemotorn, i stället för via gränssnittet. På så sätt kan du ange vilken status som ska gälla i andra fall, t.ex. om ett erbjudande avvisas.

```
<BASE_URL>?a=UpdateStatus&p=<PRIMARY_KEY_OF_THE_PROPOSITION>&st=<NEW_STATUS_OF_THE_PROPOSITION>&r=<REDIRECT_URL>
```

Det förslag (ID **40004**) som matchar **hemförsäkringserbjudandet** som visas på **Neobank** -webbplatsen innehåller följande URL:

```
<BASE_URL>?a=UpdateStatus&p=<40004>&st=<3>&r=<"http://www.neobank.com/insurance/subscribe.html">
```

Så snart en besökare klickar på erbjudandet, och därmed URL:en, tillämpas **[!UICONTROL Accepted]** statusen (värde **3**) på erbjudandet och besökaren omdirigeras till en ny sida på **Neobank** -webbplatsen för att teckna försäkringsavtalet.

>[!NOTE]
>
>Om du vill ange en annan status på URL:en (till exempel om ett erbjudande avvisas) använder du värdet som motsvarar önskad status. Exempel: **[!UICONTROL Rejected]** = &quot;5&quot;, **[!UICONTROL Presented]** = &quot;1&quot; och så vidare.
>
>Status och deras värden kan hämtas i **[!UICONTROL Offer propositions (nms)]** dataschemat. Mer information finns på [den här sidan](../../configuration/using/data-schemas.md).

**Utgående interaktion**

Om det gäller en utgående interaktion kan du automatiskt tillämpa **[!UICONTROL Interested]** status på ett erbjudande när leveransen innehåller en länk. Lägg bara till **_urlType=&quot;11&quot;** -värdet till länken:

```
<a _urlType="11" href="<DEST_URL>">Link inserted into the delivery</a>
```

## Förhandsgranska per utrymme {#offer-preview-per-space}

På den här fliken kan du visa de erbjudanden som mottagaren är berättigad till via en vald metod. I exemplet nedan är mottagaren berättigad till tre offerter via post.

![](assets/offer_space_overview_002.png)

Om en mottagare inte är berättigad till något erbjudande visas detta i förhandsgranskningen.

![](assets/offer_space_overview_001.png)

Förhandsvisningen kan ignorera kontexter när de är begränsade till ett mellanslag. Detta är fallet när interaktionsschemat har utökats för att lägga till fält som refereras i ett utrymme med en inkommande kanal (mer information finns i [Extension-exemplet](../../interaction/using/extension-example.md)).
