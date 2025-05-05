---
product: campaign
title: Distribuera en instans
description: Läs mer om guiden för Campaign-driftsättning
feature: Installation, Instance Settings, Deployment
badge-v7-prem: label="Endast lokal/hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 8b07447c-9a86-4b56-8d29-e0b01357a6ec
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '3389'
ht-degree: 1%

---

# Distribuera en instans{#deploying-an-instance}

>[!NOTE]
>
>Konfigurationer på serversidan kan bara utföras av Adobe för distributioner som hanteras av Adobe. Mer information om de olika distributionerna finns i avsnittet [Värdmodeller](../../installation/using/hosting-models.md) eller i [den här sidan](../../installation/using/capability-matrix.md).

## distributionsguide {#deployment-assistant}

Adobe Campaign tillhandahåller en grafisk assistent, som finns i Adobe Campaign klientkonsol, för att definiera parametrarna för den instans som du ska ansluta till.

Om du vill starta distributionsguiden väljer du **Verktyg > Avancerat > distributionsguiden**.

![](assets/s_ncs_install_deployment_wiz_01.png)

Konfigurationsstegen är följande:

1. [Allmänna parametrar](#general-parameters)
1. [E-postkanalsparametrar](#email-channel-parameters)
1. [Hantera studsade mejl](#managing-bounced-emails)
1. [Spårningskonfiguration](#tracking-configuration)
1. [Mobila kanalparametrar](#mobile-channel-parameters)
1. [Regionala inställningar](#regional-settings)
1. [Åtkomst från Internet](#access-from-the-internet)
1. [Hantera offentliga resurser](#managing-public-resources)
1. [Rensar data](#purging-data)

## Allmänna parametrar {#general-parameters}

I det första steget i distributionsguiden kan du ange allmän information om instansen.

![](assets/s_ncs_install_deployment_wiz_02.png)

### Allmän information {#general-information}

I fönstrets nedre del kan du välja vilka alternativ som ska aktiveras.

* **[!UICONTROL Customer identifier used in billing]** : detta kan vara namnet på instansen och versionsnumret.
* **[!UICONTROL Common name of the customer]** : Ange en teckensträng med ditt företags namn. Den här informationen kan användas i avprenumerationslänkarna.
* **[!UICONTROL Namespace]** : Ange en kort identifierare i gemener. Målet är att skilja mellan din specifika konfiguration och fabrikskonfigurationen om du uppgraderar. Standardnamnutrymmet är **cus** - för kunden.

### Tekniska alternativ {#technical-options}

I fönstrets nedre del kan du välja vilka alternativ som ska aktiveras.

Följande alternativ är tillgängliga:

* **[!UICONTROL Email channel]** : för att aktivera e-postleverans. Se [E-postkanalsparametrar](#email-channel-parameters).
* **[!UICONTROL Tracking]** : Om du vill aktivera spårning av målpopulationen (öppnar och klickar). Se [Spårningskonfiguration](#tracking-configuration).
* **[!UICONTROL Managing bounced emails]** : För att definiera POP-kontot som används för att hämta inkommande e-post. Se [Hantera studsade e-postmeddelanden](#managing-bounced-emails).
* **[!UICONTROL LDAP integration]** : Så här konfigurerar du användarautentisering via en LDAP-katalog. Se [Ansluter via LDAP](../../installation/using/connecting-through-ldap.md).

## E-postkanalsparametrar {#email-channel-parameters}

I följande steg definierar du vilken information som ska visas i meddelanderubriker.

Dessa parametrar kan överlagras i leveransmallar, och individuellt för varje leverans (om användarna har de rättigheter som krävs).

### Parametrar för levererade e-postmeddelanden {#parameters-for-delivered-emails}

![](assets/s_ncs_install_deployment_wiz_04.png)

Ange följande parametrar:

* **[!UICONTROL Sender name]** : Ange avsändarens namn.
* **[!UICONTROL Sender address]** : Ange avsändarens e-postadress. När du skickar e-post från Adobe Campaign övervakas inte postlådan **Avsändaradress** och marknadsföringsanvändare kan inte komma åt den här postlådan. Adobe Campaign erbjuder inte heller möjlighet att svara automatiskt eller vidarebefordra e-postmeddelanden som tas emot i den här postlådan. Läs mer om god praxis [för slutprodukter i den här dokumentationen](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/campaign/ac-starting-new-platform.html){_blank}.

* **[!UICONTROL Reply address text]** : Ange det namn som ska användas när mottagaren klickar på knappen **[!UICONTROL Reply]**.
* **[!UICONTROL Reply address]** : Ange den e-postadress som ska användas när mottagaren klickar på knappen **[!UICONTROL Reply]** i sin e-postklientprogramvara. Syftet med fältet **Svarsadress** är att du vill att mottagaren ska svara på en annan adress än **avsändaradressen**.  Den här adressen måste vara en giltig e-postadress, länkad till en övervakad postlåda och värd av kunden.  Det kan vara en supportpostlåda, till exempel `customer-care@customer.com`, där e-postmeddelanden läses och besvaras.

* **[!UICONTROL Error address]** : Ange e-postadressen för meddelanden med fel. Detta är den tekniska adress som används för att hantera studsmeddelanden, inklusive e-post som tas emot av Adobe Campaign-servern på grund av att måladresserna inte finns. Den här adressen måste vara en giltig e-postadress, länkad till en övervakad postlåda och värd av kunden. Det kan vara en studspostlåda, till exempel `errors@customer.com`. Den här adressen kan ändras för en leverans eller i leveransmallarna på fliken **SMTP** i leveransmallens egenskaper. [Läs mer](../../delivery/using/email-parameters.md#managing-bounce-emails-managing-bounce-emails).


Utöver detta kan du ange **masker** som är behöriga för avsändaradressen och feladressen. Om det behövs kan dessa masker separeras med kommatecken. Den här konfigurationen är valfri. När fält anges kontrollerar Adobe Campaign vid leveranstillfället (under analysen om adressen inte innehåller några variabler) att adresserna är giltiga. Det här operativläget ser till att inga adresser används som kan utlösa leveransproblem. Leveransadresserna måste konfigureras på leveransservern.

>[!NOTE]
>
>* De här inställningarna sparas i Campaign-plattformen. [Läs mer](../../installation/using/configuring-campaign-options.md).
> 
>* För konfigurationer med flera varumärken kan du anpassa feladressen och åsidosätta den här konfigurationen från det externa kontot för e-postroutning. [Läs mer](../../installation/using/external-accounts.md#email-routing-external-account).
>


### Tecken som är godkända i adresser {#characters-authorized-in-addresses}

<!--This window enables you to define, for all email campaigns, the delivery and address-quality management options.-->

I Adobe Campaign-databasen måste alla e-postadresser skapas enligt följande: `x@y.z`. Tecknen **x**, **y** och **z** får inte vara tomma och får inte innehålla otillåtna tecken.

Här definierar du vilka tecken som är tillåtna (&#39;datapolicy&#39;) i databasens e-postfält. Tecken som inte finns med i listan kommer att förbjudas och nekas därför när information matas in i databasen via gränssnittet, via ett webbformulär eller när data importeras.

Två listor är tillgängliga: **Endast europeiska** eller **endast USA**. Andra tecken kan läggas till om det behövs.

### Leveransparametrar {#delivery-parameters}

Länken **Avancerade parametrar..** gör att du kan komma åt leveransalternativ, parametrar som är länkade till återförsök och karantän.

![](assets/s_ncs_install_deployment_wiz_05.png)

I det här fönstret kan ni definiera alternativ för hantering av leverans och adresskvalitet för alla e-postkampanjer.

Följande alternativ är tillgängliga:

* **[!UICONTROL Delivery duration of messages]** : Efter den här tiden stoppas leveransen (som standard 5 dagar).
* **[!UICONTROL Online resources validity duration]** : Tid som information från mottagarprofilen sparas för att generera spegelsidor.
* **[!UICONTROL Exclude recipients who no longer wish to be contacted]** : När det här alternativet är markerat kommer mottagare i blockeringslista inte att kontaktas.
* **[!UICONTROL Automatically ignore doubles]** : När det här alternativet är markerat kommer leveransen inte att ske till dubblettadresser.

>[!NOTE]
>
>Om du har uppgraderat till [Förbättrat MTA](../../delivery/using/sending-with-enhanced-mta.md) för värdbaserade eller hybridbaserade installationer, kommer **[!UICONTROL Delivery duration of the messages]** endast att användas om den är inställd på **3,5 dagar eller mindre**. Om du anger ett värde som är högre än 3,5 dagar kommer det inte att beaktas.

### Försök igen med parametrar {#retry-parameters}

Information om återställningar finns i fälten **Återställningsperioder** och **Antal återställningar**: När en mottagare inte kan nås, till exempel om inkorgen är full, försöker programmet som standard kontakta mottagaren fem gånger med ett timmars intervall mellan varje försök (under den maximala leveranstiden). Dessa värden kan ändras efter behov.

>[!NOTE]
>
>Om du har uppgraderat till [Förbättrat MTA](../../delivery/using/sending-with-enhanced-mta.md) för värdbaserade eller hybridinstallerade installationer används inte längre kampanjens parametrar för nya försök. Mjuka avhoppsförsök och hur lång tid det tar mellan dem bestäms av den förbättrade MTA-metoden baserat på typ och allvarlighetsgrad för de avhoppssvar som kommer tillbaka från meddelandets e-postdomän.

### Karantänparametrar {#quarantine-parameters}

Konfigurationsalternativen för karantän är följande:

* **[!UICONTROL Duration between two significant errors]** : Ange ett värde (&quot;1d&quot; som standard: 1 dag) för att definiera den tid som programmet väntar innan felräknaren ökas om fel uppstår,
* **[!UICONTROL Maximum number of errors before quarantine]** : När det här värdet har uppnåtts sätts e-postadressen i karantän (som standard &quot;5&quot;: adressen sätts i karantän på det sjätte felet). Detta innebär att kontakten automatiskt utesluts från efterföljande leveranser.

## Hantera studsade mejl {#managing-bounced-emails}

För att kvalificera leveransfel är det mycket viktigt med studentpost. Felen kategoriseras i mappen NP@I när reglerna har fastställt orsaken.

Det här steget är bara tillgängligt om hanteringsalternativen **E-postkanal** och **Avsluta e-post** har valts i det första steget i distributionsguiden. Se [Allmänna parametrar](#general-parameters).

I det här steget kan du definiera inställningar för hantering av studsmeddelanden.

![](assets/s_ncs_install_deployment_wiz_06.png)

### POP-konto som används för att hämta inkommande e-post {#pop-account-used-to-retrieve-incoming-mails}

Ange de parametrar som ska anslutas till kontot för att hämta inkommande e-post.

* **[!UICONTROL Label]** : Namn som innehåller alla parametrar nedan,
* **[!UICONTROL Server]** : Servern används för att hämta studentpost (inkommande e-post),
* **[!UICONTROL Security]** : Om det behövs väljer du **[!UICONTROL SSL]** i listrutan,
* **[!UICONTROL Port]** : serverport (vanligtvis 110),
* **[!UICONTROL Account]** : Namn på kontot som används för studsmeddelanden,
* **[!UICONTROL Password]** : Lösenord som är kopplat till kontot.

När POP-inställningarna har angetts klickar du på **Test** för att kontrollera att de är korrekta.

### Obearbetade studsmeddelanden {#unprocessed-bounce-mails}

Satser hanteras automatiskt av Adobe Campaign och de regler som anges i noden **Administration > Campaign Management > Hantering av ej slutprodukter > Leveransloggens kvalificering** tillämpas. Mer information finns i [Avsluta e-posthantering](../../delivery/using/understanding-delivery-failures.md#bounce-mail-management).

Obearbetade studsar visas inte i Adobe Campaign-gränssnittet. De tas automatiskt bort om de inte överförs till en tredje parts postlåda med följande fält:

* **[!UICONTROL Forwarding address]** : Fyll i det här fältet om du vill överföra alla felmeddelanden (bearbetade eller obearbetade) som samlas in av Adobe Campaign-plattformen till en tredje part.
* **[!UICONTROL Address for errors]** : Fyll i det här fältet om du vill överföra felmeddelanden till en tredje partsadress är bara felmeddelanden som InMail-processen inte kunde kvalificera.
* **[!UICONTROL SMTP server]** : Servern använde för att skicka obearbetade studsmeddelanden.

>[!IMPORTANT]
>
>Om du vill vidarebefordra obearbetade studsmeddelanden rekommenderar Adobe att du bara fyller i fältet **[!UICONTROL Address for errors]**. Kontrollera dock att adressen som används kontrolleras regelbundet eftersom det kan medföra en stor belastning på e-postservern. Kontakta er kontoansvarige om du vill ha mer information.

## Spårningskonfiguration {#tracking-configuration}

I nästa steg kan du konfigurera spårning för instansen. Instansen måste deklareras och registreras hos spårningsservern(arna).

Det här steget erbjuds endast när alternativen **E-postkanal** och **Spårning** har valts på den första sidan i distributionsguiden. Se [Allmänna parametrar](#general-parameters).

Mer detaljerad information om webbspårning (spårningsläge, skapa och infoga taggar...) finns i [det här dokumentet](../../configuration/using/about-web-tracking.md).

### Verksamhetsprincip {#operating-principle}

När du aktiverar spårning för en instans ändras URL:erna i leveranserna under sändningen för att aktivera spårning.

* Informationen om externa URL:er (oavsett om de är säkra eller inte) som anges på den här sidan i distributionsguiden används för att skapa den nya URL:en. Förutom den här informationen innehåller den ändrade länken identifierare för leveransen, mottagaren och URL:en.

  Spårningsinformation samlas in av Adobe Campaign på spårningsservrar för att berika mottagarprofiler och data som är länkade till leveransen ( **[!UICONTROL Tracking]** flikar).

  Information om interna URL:er används endast av Adobe Campaign-programservern för att kontakta spårningsservern/-servrarna.

  Mer information finns i [Spårningsserver](#tracking-server).

* När URL-adresserna har konfigurerats måste du aktivera spårning. För att göra detta måste instansen registreras på spårningsservern(arna).

  Mer information finns i [Sparar spårning](#saving-tracking).

### Spårningsserver {#tracking-server}

![](assets/s_ncs_install_deployment_wiz_08.png)

För att säkerställa effektiviteten i spårningen för den här instansen måste följande information visas:
<!--With Mid-sourcing architecture, you can externalize tracking management. To do this:-->

* **[!UICONTROL External URL]** och/eller **[!UICONTROL Secure external URL]** : Ange den omdirigerings-URL som ska användas i det e-postmeddelande som ska skickas.
* **[!UICONTROL Internal URL(s)]** : URL:er som bara används av Adobe Campaign-servern för att kontakta spårningsservern/spårningsservrarna för att samla in loggar och överföra URL:erna. Du behöver inte associera den med instansen.

  Om du inte anger någon URL används spårnings-URL som standard.

Med en arkitektur som bygger på flera källor kan ni externalisera spårningshanteringen. Så här gör du:

1. Välj alternativet **[!UICONTROL Externalize tracking management]**: Det gör att du kan använda en server för mellanlagring som spårningsserver.
1. Fyll i fälten **[!UICONTROL External account]** och **[!UICONTROL Instance name]** för att kunna ansluta till servern med mellankällor.

   Mer information finns på [Mid-sourcing-servern](../../installation/using/mid-sourcing-server.md).

1. Klicka på knappen **[!UICONTROL Enable the tracking instance]** för att godkänna anslutningen till servern.

   ![](assets/s_ncs_install_deployment_wiz_18.png)

### Spårning sparas {#saving-tracking}

När URL-adresserna har fyllts i måste du registrera spårningsservern.

Klicka på länken **Registrering på spårningsservrarna** och välj sedan ett av de tillgängliga alternativen.

![](assets/s_ncs_install_deployment_wiz_09.png)

Det finns tre möjliga typer av arkitektur för implementering av spårning:

1. **Lägg till stöd för spårning i en befintlig instans**

   Det här alternativet gäller om instansen redan har skapats för andra behov (MTA-server osv.) på servrar som ska användas som spårningsservrar.

   ![](assets/s_ncs_install_deployment_wiz_11.png)

   Ange lösenordet för kontot **internal** på omdirigeringsservern(arna) för att konfigurera spårningsinstansen.

   >[!NOTE]
   >
   >Om flera spårningsservrar används måste alla ha samma namn och lösenord.

   Ange namnet på instansen och lösenordet.

1. **Skapa en ny instans som är dedikerad till spårning**

   Det här alternativet är användbart när du spårar instanser som är reserverade för spårning och inte har några andra programmoduler.

   ![](assets/s_ncs_install_deployment_wiz_10.png)

   Ange lösenordet för kontot **internal** på omdirigeringsservern(arna) för att konfigurera spårningsinstansen.

   >[!NOTE]
   >
   >Om flera spårningsservrar har konfigurerats måste alla använda samma lösenord.

   Ange namnet på instansen, lösenordet och eventuella associerade DNS-masker, till exempel **[!UICONTROL Campaign*]**.

1. **Verifiera en spårningsinstans som redan är förkonfigurerad för dig**

   Det här alternativet används när du inte har lösenordet för kontot **internal**. I det här fallet är ett spårningskonto förkonfigurerat för dig på spårningsservern(arna). Ange lösenordet för spårningskontot för omdirigeringsservrarna för att validera spårningsinstansen.

   ![](assets/s_ncs_install_deployment_wiz_17.png)

   Ange namnet på den instans som ska valideras.

Klicka på **Godkänn** för att starta inspelningsprocessen med spårningsservern.

I föregående fönster bekräftar ett meddelande registreringen på spårningsservernivå:

![](assets/s_ncs_install_deployment_wiz_tracking_ok.png)

Parametrarna som är länkade till URL-sökningar **får inte ändras** för en standardinstallation. Kontakta Adobe för alla andra parametrar.

## Mobila kanalparametrar {#mobile-channel-parameters}

I nästa steg kan du definiera standardinställningar för leveranser till mobiler (SMS och WAP Push).

>[!NOTE]
>
>Mobilkanalen är valfri: den här fasen visas bara om den har köpts. Kontrollera licensavtalet.

![](assets/s_ncs_install_deployment_wiz_12.png)

### Standardkonto för SMS-leverans {#default-account-for-sms-delivery}

Ange följande information:

* **[!UICONTROL Label]** : Ange ett namn för det här SMS/Wap-push-kontot. Du kanske vill använda namnet på routern.
* För fälten **[!UICONTROL Server]**, **[!UICONTROL Port]**, **[!UICONTROL Account]**, **[!UICONTROL Password]**, **[!UICONTROL Connector]**, **[!UICONTROL Send Endpoint]**, **[!UICONTROL Reception Endpoint]**, **[!UICONTROL Notification Endpoint]**: Kontakta tjänsteleverantören för att få de inställningar som krävs.

### Parametrar för SMS har skickats {#parameters-of-sms-sent}

I listrutan **Prioritet**: Välj Normal, Hög eller Brådskande för att använda den på de meddelanden som ska skickas.

### Avancerade parametrar {#advanced-parameters}

Länken **Avancerade parametrar..** gör att du kan komma åt alternativen för återförsök och karantän.

![](assets/s_ncs_install_deployment_wiz_13.png)

Information om återförsök finns i fälten **Period med återförsök** och **Antal återförsök**: När det inte går att nå en mobil försöker programmet igen fem gånger med intervall på minst 15 minuter (för den maximala leveransperioden). Dessa värden kan anpassas efter dina behov.

Konfigurationsalternativen för karantän är följande:

* **[!UICONTROL Time between two significant errors]** : Ange ett standardvärde (som standard &quot;1d&quot;: dag) för att definiera den tid som programmet väntar innan felräknaren ökas för ett fel.
* **[!UICONTROL Maximum number of errors before quarantine]** : När det här värdet har nåtts sätts mobilnumret i karantän (som standard &quot;5&quot;: talet sätts i karantän vid det sjätte felet). Det innebär att kontakten automatiskt utesluts från framtida leveranser.

## Regionala inställningar {#regional-settings}

I det här steget kan du ange inställningar för dataprofiler.

![](assets/s_ncs_install_deployment_wiz_14.png)

* **[!UICONTROL Consider all phone numbers as international ones]** : När det här alternativet är markerat används det internationella formatet på telefonnummer (landsprefixet är då obligatoriskt eftersom antalet siffror inte kontrolleras innan formateringen används). Om du inte väljer det här alternativet måste du själv ange &quot;+&quot; eller &quot;00&quot; som prefix för det internationella telefonnumret.
* **[!UICONTROL Store all phone numbers using the international format]** : Det här alternativet gäller endast **inhemska** telefonnummer som importeras eller redigeras. Ange om du vill använda ett internt format (till exempel 425 555 0150) eller det internationella formatet (till exempel +1 425 555 0150)

## Åtkomst från Internet {#access-from-the-internet}

>[!IMPORTANT]
>
>Av sekretesskäl rekommenderar vi att du använder HTTPS för alla externa resurser.

I det här steget kan du definiera åtkomst-URL:er för Adobe Campaign-sidor som visas på Internet.

Här måste du även ange vilka publiceringsalternativ som är länkade till webbformulär.

![](assets/s_ncs_install_deployment_wiz_15.png)

### Servrar som exponeras på webben {#servers-exposed-on-the-web}

Använd den här sidan om du vill fylla i server-URL:er till:

1. Åtkomst till programservern som finns på Internet: prenumerations-/avprenumerationsformulär, extranät osv.
1. Använd programservern för resurser som inte visas på webben: formulär, intranät, bekräftelsesidor.
1. Få åtkomst till leveranssidornas spegelsidor.

   En spegelsida är en dynamisk sida som visar innehållet i e-postmeddelandet. Den öppnas via en länk som infogas i meddelandet som skickas till mottagaren och kan innehålla anpassade element. Spegelsidan ger mottagaren möjlighet att läsa meddelandet i en webbläsare i stället för i e-postprogrammet, oavsett leveransformat (text eller HTML). Spegelsidor genereras dock bara för en viss leverans om det obligatoriska HTML-innehållet har definierats.

Med Adobe Campaign kan du differentiera dessa tre URL-adresser för att sprida belastningen över flera plattformar.


>[!NOTE]
>
>* De här inställningarna sparas i Campaign-plattformen. [Läs mer](../../installation/using/configuring-campaign-options.md).
>* För konfigurationer med flera varumärken kan du anpassa URL:en för speglingssidan och åsidosätta den här konfigurationen från det externa e-postroutningskontot. [Läs mer](../../installation/using/configuring-campaign-options.md).


## Hantera offentliga resurser {#managing-public-resources}

>[!IMPORTANT]
>
>Av sekretesskäl rekommenderar vi att du använder HTTPS för alla externa resurser.

För att kunna ses utifrån måste de bilder som används i e-postmeddelanden och offentliga resurser som är kopplade till kampanjer finnas på en externt tillgänglig server. De kan sedan vara tillgängliga för externa mottagare eller operatorer.

![](assets/s_ncs_install_deployment_wiz_img_uploading.png)

I det här steget måste du ange:

1. Den nya URL:en för offentlig resurs. Mer information finns i avsnittet [URL för offentliga resurser](#public-resources-url).
1. Bildidentifieringsläget i en leverans. Mer information finns i avsnittet [Avläsning av leveransbild](#delivery-image-detection).
1. Publiceringsalternativ. Mer information finns i avsnittet [Publiceringslägen](#publication-modes).

Offentliga resurser är tillgängliga via noden **Administration > Resurser > Online > Offentliga resurser** i Adobe Campaign-trädet. De samlas in i ett bibliotek och kan inkluderas i e-postmeddelanden men också användas i kampanjer eller uppgifter, samt i innehållshantering.

![](assets/install_pub_resources_view.png)

### URL för offentliga resurser {#public-resources-url}

I det första fältet kan du ange början på den URL som används för resurserna när de har överförts. När resurserna överförs är de tillgängliga via den nya URL:en.

I en leverans kan du använda bilder som lagras i resursbiblioteket eller någon annan lokal bild eller bild som lagras på en server.

* För e-postbilder finns URL:en **https://** server **/res/img** .

  Det här värdet kan åsidosättas för varje leverans.

* För offentliga resurser anges URL:en **https://** server **/res/** instance **&#x200B;**&#x200B;där **instance**&#x200B;är namnet på spårningsinstansen.

### Avbildningsidentifiering {#delivery-image-detection}

I en leverans kan du använda bilder som lagras i resursbiblioteket eller någon annan lokal bild eller bild som lagras på en server.

I fältet **URL-masker** kan du ange listan med URL-masker som ska hoppas över när bilder överförs automatiskt. Om du till exempel använder bilder som lagras på en plats som är tillgänglig från utsidan, särskilt på en webbplats, kan du ange webbplatsens URL i det här fältet.

![](assets/s_ncs_install_deployment_wiz_img_mask.png)

Du kan ange flera URL-masker genom att använda kommatecken för att skilja på dem.

* Mer information om hur du använder och hanterar bilder i e-postmeddelanden finns i [det här avsnittet](../../delivery/using/defining-the-email-content.md#adding-images).
* I leveransassistenten kommer bilderna som anropas från dessa URL:er att ha statusen&quot;Ignorerad&quot;.

### Publiceringslägen {#publication-modes}

I det nedre avsnittet av assistenten kan du välja publiceringsalternativ för offentliga resurser och bilder.

Följande publiceringslägen är tillgängliga:

* Spårningsservrar

  Resurserna kopieras automatiskt till olika spårningsservrar. De är konfigurerade i steg [Spårningskonfiguration](#tracking-configuration).

* Andra Adobe Campaign-servrar

  Du kan använda ytterligare en Adobe Campaign-server där resurserna kopieras.

  På serversidan måste du skapa en ny instans med följande kommando för att kunna använda en dedikerad Adobe Campaign-server:

  ```
  nlserver config -addtrackinginstance:<trackingA>/<trackingA*>
  ```

  Ange sedan lösenordet.

  Parametrarna för de dedikerade servrarna anges i fälten **[!UICONTROL Media URL(s)]**, **[!UICONTROL Password]** och **[!UICONTROL Instance name]**.

  ![](assets/s_ncs_install_images_upload_b.png)

* Manuellt publiceringsskript (endast för offentliga medel)

  ![](assets/s_ncs_install_images_upload_c.png)

  Du kan publicera bilderna med hjälp av ett skript:

   * Du måste skapa det här skriptet: dess innehåll beror på din konfiguration.
   * Skriptet anropas av följande kommando:

     ```
     [INSTALL]/copyToFrontal.vbs "$(XTK_INSTALL_DIR)\var\<instance>\upload\" "img1,img2,img3"
     ```

     där `[INSTALL]` är åtkomstsökvägen till Adobe Campaign installationsmapp.

   * Kontrollera att skriptet är körbart i Unix.

För bilder måste de kopieras från mappen &quot;images&quot; som anges via alternativet **NmsDelivery_ImageSubDirectory** till en eller flera frontservrar. Dessa servrar lagrar bilderna så att de blir tillgängliga via den nya konfigurerade URL:en.

Om en leverans publiceras på en Adobe Campaign-server utan ett manuellt skript, lagras bilderna som standard i `$(XTK_INSTALL_DIR)/var/res/img/ directory`. Motsvarande URL är följande: **`https://server/res/img`**.

`XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)`. Motsvarande URL är följande: **`https://server/res/instance`** där instansen är namnet på spårningsinstansen.

>[!NOTE]
>
>Det går att ändra lagringskatalogen för offentliga resurser. Mer information finns i [Hantera offentliga resurser](#managing-public-resources).

### Synkroniserar offentliga resurser {#synchronizing-public-resources}

Med den här funktionen kan du **synkronisera offentliga resurser** på flera reservservrar.

Om det inte finns någon offentlig resurs på spårningsservern eller om resursen returnerar ett 404-fel, kommer spårningsservern att försöka hitta resursen på någon av de extra servrarna.

Deklaration och konfigurering av reservservrar måste göras i marknadsföringsserverns **serverConf.xml** -fil. Alla parametrar som är tillgängliga i **serverConf.xml** listas i det här [avsnittet](../../installation/using/the-server-configuration-file.md).

**Deklaration**

```
<redirection>
<spareServer enabledIf="" id="" url=""/>
</redirection>
```

**Konfiguration**

För varje offentlig resurs som måste synkroniseras måste du lägga till ett statusattribut i elementet `<url>` i delen `<relay>`:

Statusattributet kan vara ett av tre värden:

* reserv: Den offentliga resursen är synkroniserad

* normal: Befintligt beteende (utan synkronisering)

* svartlista: URL:en läggs till i blockeringslista om den returnerar ett 404-fel. Varaktigheten (i sekunder) för den URL som finns i blockeringslista definieras av ett **timeout** -attribut vars standardvärde är 60s.

Synkroniseringens färdiga konfiguration är:

```
(extracted from the serverConf.xml file)

<redirection P3PCompactPolicy="CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV"
databaseId="" defLogCount="30" expirationURL="" maxJobsInCache="100"
startRedirection="true" startRedirectionInModule="true" trackWebVisitors="false" trackingPassword="">
<spareServer enabledIf="" id="1" url=""/>
</redirection>

....


<relay debugRelay="false" forbiddenCharsInAuthority="?#.@/:" forbiddenCharsInPath="?#/"
           modDir="index.html" startRelay="false" startRelayInModule="true" timeout="60">
   <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="normal" targetUrl="https://localhost:8080" timeout="" urlPath="/view/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="*.jsp"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="*.jssp"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="/webApp/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="/report/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="/jssp/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="normal" targetUrl="https://localhost:8080" timeout="" urlPath="/strings/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="normal" targetUrl="https://localhost:8080" timeout="" urlPath="/interaction/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="normal" targetUrl="https://localhost:8080" timeout="" urlPath="/barcode/*"/>

      <url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" status="spare" targetUrl="" timeout="" urlPath="/favicon.*"/>
      <url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" status="spare" targetUrl="" timeout="" urlPath="/*.html"/>
      <url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" status="spare" targetUrl="" timeout="" urlPath="/*.png"/>
      <url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" status="spare" targetUrl="" timeout="" urlPath="/*.jpg"/>

 </relay>
```

## Rensar data {#purging-data}

I det sista steget i distributionsguiden kan du konfigurera automatisk rensning av föråldrade data. Värdena uttrycks i dagar.

![](assets/s_ncs_install_deployment_wiz_16.png)

Data tas automatiskt bort via arbetsflödet för databasrensning. Mer information om hur du konfigurerar och hanterar det här arbetsflödet och information om borttagna objekt finns i det här [dokumentet](../../production/using/database-cleanup-workflow.md).
