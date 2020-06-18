---
title: Definiera målpopulationen
seo-title: Definiera målpopulationen
description: Definiera målpopulationen
seo-description: null
page-status-flag: never-activated
uuid: 8bf70ea4-5f28-4d85-b5ce-0bd3ed3eea55
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
discoiquuid: df29492f-ed73-4ab8-b075-e76b3b9ebce3
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: fa9e4ddc716809b96e259acd1137a0c24ef68fee
workflow-type: tm+mt
source-wordcount: '1528'
ht-degree: 0%

---


# Definiera målpopulationen {#defining-the-target-population}

## Om målpopulationer {#about-target-populations}

För varje leverans kan du definiera flera typer av målpopulationer. Avsnittet nedan innehåller mer information om hur du väljer:

* **Leveransens** huvudmottagare. [Läs mer](../../delivery/using/steps-defining-the-target-population.md#selecting-the-main-target).
* **Mottagarna av korrekturmeddelanden** för att skapa en valideringscykel. [Läs mer](../../delivery/using/steps-defining-the-target-population.md#defining-a-specific-proof-target).

Dessutom kan du definiera [dirigerade adresser](../../delivery/using/about-seed-addresses.md)och [kontrollgrupper](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group). om leveransen ingår i en marknadsföringskampanj.

## Välja huvudmottagare för leveransen {#selecting-the-main-target}

I de flesta fall extraheras huvudmålet från Campaign-databasen (standardläge).

Mottagarna kan också lagras i en extern fil. Konfigurationen av den här typen av leverans visas i [Välja externa mottagare](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients).

Så här väljer du mottagare av leveransen som skapas:

1. Klicka på **[!UICONTROL To]** länken.
1. Om mottagarna lagras i databasen markerar du det första alternativet.

   ![](assets/s_ncs_user_wizard_email02a.png)

1. Välj målmappning i **[!UICONTROL Target mapping]** listrutan. Standardmålmappningen för Adobe Campaign är **[!UICONTROL Recipients]**.

   Andra målmappningar är tillgängliga, och vissa kan vara relaterade till din specifika konfiguration. Mer information om målmappningar finns i [Välja målmappning](../../delivery/using/selecting-a-target-mapping.md).

1. Klicka på **[!UICONTROL Add]** knappen för att definiera begränsningsfilter.

   Du kan sedan välja vilken typ av filtrering du vill använda:

   ![](assets/s_ncs_user_wizard_email02b.png)

   Du kan välja mottagare med hjälp av de typer av mål som definieras i databasen. Om du vill använda en måltyp markerar du den och klickar på **[!UICONTROL Next]**. För varje mål kan du visa de berörda mottagarna genom att klicka på **[!UICONTROL Preview]** fliken. För vissa typer av mål kan du med **[!UICONTROL Refine target]** knappen kombinera flera målinriktningskriterier.

   Följande måltyper erbjuds som standard:

   * **[!UICONTROL Filtering conditions]** : Med det här alternativet kan du definiera en fråga och visa resultatet. Metoden för att definiera frågor beskrivs i [det här avsnittet](../../platform/using/creating-filters.md#creating-an-advanced-filter).
   * **[!UICONTROL Subscribers of an information service]** : Med det här alternativet kan du välja ett nyhetsbrev som mottagarna måste prenumerera på för att få det mål som gäller för leveransen som skapas.

      ![](assets/s_ncs_user_wizard_email02c.png)

   * **[!UICONTROL Recipients of a delivery]** : Med det här alternativet kan du definiera mottagarna av en befintlig leverans som ett målinriktningskriterium. Du måste sedan välja leveransen i listan:

      ![](assets/s_ncs_user_wizard_email02d.png)

   * **[!UICONTROL Delivery recipients belonging to a folder]** : Med det här alternativet kan du välja en leveransmapp och ange mottagaren för leveranserna i den mappen som mål.

      ![](assets/s_ncs_user_wizard_email02e.png)

      Du kan filtrera mottagarnas beteende genom att välja i listrutan:

      ![](assets/s_ncs_user_wizard_email02f.png)

      >[!NOTE]
      >
      >Med det här **[!UICONTROL Include sub-folders]** alternativet kan du även ange leveranser i mappar i trädstrukturen nedanför den valda noden som mål.

   * **[!UICONTROL Recipients included in a folder]** : Med det här alternativet kan du ange profiler i en viss mapp i trädet som mål.
   * **[!UICONTROL A recipient]** : Med det här alternativet kan du välja en viss mottagare bland profilerna i databasen.
   * **[!UICONTROL A list of recipients]** : Med det här alternativet kan du ange en lista över mottagare som mål. Listor visas i [det här avsnittet](../../platform/using/creating-and-managing-lists.md).
   * **[!UICONTROL User filters]** : Med det här alternativet kan du komma åt de förkonfigurerade filtren och använda dem som filtreringsvillkor för profiler i databasen. Förkonfigurerade filter visas i [det här avsnittet](../../platform/using/creating-filters.md#saving-a-filter).
   * Med det här alternativet **[!UICONTROL Exclude recipients corresponding to this segment]** kan du rikta in dig på mottagare som inte uppfyller de definierade målvillkoren. Om du vill använda det här alternativet markerar du lämplig ruta och tillämpar sedan målinriktning, enligt definitionen ovan, för att utesluta de resulterande profilerna.

      ![](assets/s_ncs_user_wizard_email02g.png)

1. Ange ett namn för den här målsättningen i **[!UICONTROL Label]** fältet. Som standard kommer etiketten att vara etiketten för det första målinriktningskriteriet. För en kombination är det bättre att använda ett explicit namn.
1. Klicka **[!UICONTROL Finish]** för att validera den konfigurerade målsättningen.

   De definierade målinriktningskriterierna sammanfattas i det centrala avsnittet på fliken för huvudmålkonfiguration. Klicka på ett villkor för att visa dess innehåll (konfiguration och förhandsgranskning). Om du vill ta bort ett villkor klickar du på krysset efter etiketten.

   ![](assets/s_ncs_user_wizard_email02h.png)

### Välja externa mottagare {#selecting-external-recipients}

Du kan starta en leverans för mottagare som inte har sparats i databasen, men som har lagrats i en extern fil. Här skickar vi till exempel en leverans till mottagare som importerats från en textfil.

Så här gör du:

1. Klicka på **[!UICONTROL To]** länken för att välja mottagare av leveransen.
1. Välj **[!UICONTROL Defined in an external file]** alternativet.

   ![](assets/s_ncs_user_wizard_external_recipients.png)

1. Som standard importeras mottagarna i databasen. Du måste välja **[!UICONTROL Target mapping]**. Mer information om målmappningar finns i [Välja målmappning](../../delivery/using/selecting-a-target-mapping.md)

   Du kan också välja **[!UICONTROL Do not import the recipients into the database]**.

1. När du importerar mottagarna klickar du på **[!UICONTROL File format definition...]** länken för att markera och konfigurera den externa filen.

   Mer information om import av data finns i [det här avsnittet](../../platform/using/importing-data.md#step-2---source-file-selection).

1. Klicka **[!UICONTROL Finish]** och konfigurera leveransen som standardleverans.

>[!CAUTION]
>
>När du definierar innehållet i meddelandet för e-postleverans ska du inte inkludera länken till spegelsidan. den inte kan genereras i det här leveransläget.

### Ställa in undantagsinställningar {#customizing-exclusion-settings}

Adressfel och kvalitetsklassificeringar tillhandahålls av tjänstleverantören. Den här informationen uppdateras automatiskt i mottagarprofilen efter leveransåtgärder och med filer som returneras av tjänsteleverantörer. Den kan visas i profilen med skrivskydd.

Du kan välja att exkludera adresser som har nått ett visst antal efterföljande fel, eller vars kvalitetsklassificering är under ett tröskelvärde som anges i det här fönstret. Du kan också välja om du vill auktorisera icke-kvalificerade adresser som inga data har returnerats för.

>[!NOTE]
>
>Om två mottagare har samma förnamn, efternamn, postnummer och ort i en direktutskick uppstår ett dubbelt fel och dubbletten tas inte med i beräkningen.

Fliken **[!UICONTROL Exclusions]** används för att begränsa antalet meddelanden.

>[!NOTE]
>
>Standardparametrar rekommenderas, men du kan anpassa inställningarna efter dina behov. Dessa alternativ bör dock endast ändras av en expertanvändare för att undvika felanvändning och fel.

Klicka på **[!UICONTROL Edit...]** länken om du vill ändra standardkonfigurationen.

![](assets/s_ncs_user_wizard_email02i.png)

Följande alternativ är tillgängliga:

* **[!UICONTROL Exclude duplicate addresses during delivery]**. Det här alternativet är aktivt som standard: kan du ta bort dubbletter av e-postadresser under leveransen. Den strategi som tillämpas kan variera beroende på hur Adobe Campaign används och vilken typ av data som finns i databasen.

   Standardvärdet för alternativet kan konfigureras för varje leveransmall.

   Exempel:

   * Leverans av nyhetsbrev eller elektroniska dokument. I vissa fall finns det inget undantag för dubbletter om data inte har några inbyggda dubbletter. Ett par som prenumererar med samma e-postadress kan förvänta sig att få två specifika personliga e-postmeddelanden: en adresserad till varje enskild person efter namn. I det här fallet kan det här alternativet avmarkeras.
   * Leverera en marknadsföringskampanj: Duplicerad uteslutning är nödvändigt för att undvika att skicka för många meddelanden till samma mottagare. I det här fallet kan du välja det här alternativet.

      Om du avmarkerar det här alternativet får du tillgång till ytterligare ett alternativ: **[!UICONTROL Keep duplicate records (same identifier)]**. Det gör att ni kan auktorisera flera leveranser till mottagare som uppfyller flera målinriktningskriterier.

      ![](assets/s_ncs_user_wizard_email02j.png)

* **[!UICONTROL Exclude recipients who no longer want to be contacted]** , d.v.s. mottagare vars e-postadresser finns i en blockeringslista (&#39;opt out&#39;). Detta alternativ måste förbli valt för att man ska kunna följa e-handelns yrkesmässiga etik och lagstiftningen om e-handel.
* **[!UICONTROL Exclude quarantined recipients]**. Med det här alternativet kan du undanta profiler med en adress som inte svarar från målet. Vi rekommenderar starkt att du behåller det här alternativet markerat.

   >[!NOTE]
   >
   >Mer information om karantänhantering finns i [Förstå karantänhantering](../../delivery/using/understanding-quarantine-management.md).

* **[!UICONTROL Limit delivery]** till ett visst antal meddelanden. Med det här alternativet kan du ange maximalt antal meddelanden som ska skickas. Om målets innehåll överskrider antalet angivna meddelanden, tillämpas ett slumpmässigt urval på målet.

### Minska storleken på målpopulationen {#reducing-the-size-of-the-target-population}

Du kan minska storleken på målpopulationen. Det gör du genom att ange antalet mottagare som ska exporteras i **[!UICONTROL Requested quantity]** fältet.

![](assets/s_ncs_user_edit_del_exe_tab.png)

## Välja mottagare av korrekturmeddelanden {#selecting-the-proof-target}

Korrekturmeddelandet är ett särskilt meddelande där du kan testa en leverans innan du skickar den till huvudmålet. Korrekturmottagare ansvarar för att godkänna både meddelandets form och innehåll.

Följ stegen nedan för att välja provtryckets mål:

1. Klicka på **[!UICONTROL To]** länken.
1. Klicka på **[!UICONTROL Target of the proofs]** fliken.
1. Klicka på **[!UICONTROL Targeting mode]** fältet för att välja den metod som ska användas: **[!UICONTROL Definition of a specific proof target]** , **[!UICONTROL Substitution of the address]** , **[!UICONTROL Seed addresses]** eller **[!UICONTROL Specific target and seed addresses]**.

>[!NOTE]
>
>Vanligtvis kan provtryckets mål läggas till i huvudmålet. Det gör du genom att välja lämpligt alternativ i den nedre delen av **[!UICONTROL Main target]** fliken.

## Definiera ett specifikt korrekturmål {#defining-a-specific-proof-target}

När du väljer korrekturmålet kan du **[!UICONTROL Definition of a specific proof target]** välja korrekturmottagare från profilerna i databasen.

Välj det här alternativet om du vill välja mottagare med hjälp av **[!UICONTROL Add]** knappen, som när du definierar huvudmålet. Se [Markera huvudmålet](../../delivery/using/steps-defining-the-target-population.md#selecting-the-main-target).

![](assets/s_ncs_user_wizard_email01_143.png)

For more on proof sending, refer to [this section](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### Använda adressersättning i korrektur {#using-address-substitution-in-proof}

I stället för att välja dedikerade mottagare i databasen kan du använda **[!UICONTROL Substitution of the address]** alternativet.

Med det här alternativet kan du använda mottagarprofilerna för leveransen och ersätta deras e-postadresser med en eller flera andra adresser som kommer att ta emot korrekturet.

När det här alternativet är markerat fylls korrekturadresserna i via en särskild redigerare där du kan konfigurera ersättningsadresserna.

![](assets/s_ncs_user_wizard_email_bat_substitute.png)

Konfigurationen utförs enligt följande:

1. Klicka på **[!UICONTROL Add]** ikonen för att definiera en ersättning.
1. Ange den mottagaradress som ska användas eller välj den i listan.
1. Välj den profil som ska användas i korrekturet: spara **[!UICONTROL Random]** värdet i **[!UICONTROL Profile to use]** kolumnen för att använda data för målprofilen i korrekturet.

   ![](assets/s_ncs_user_wizard_email_bat_substitute_choose.png)

1. Klicka på **[!UICONTROL Detail]** ikonen för att välja en profil från huvudmålet, som i följande exempel:

   ![](assets/s_ncs_user_wizard_email_bat_substitute_select.png)

   Du kan definiera så många ersättningsadresser som behövs.

## Använda dirigerade adresser som bevis {#using-seed-addresses-as-proof}

Du kan använda **[!UICONTROL Seed addresses]** som mål för korrekturet: Med det här alternativet kan du använda eller importera en lista med befintliga dirigerade adresser.

![](assets/s_ncs_user_wizard_email_bat_control_address.png)

>[!NOTE]
>
>dirigeringsadresserna visas i [Om dirigeringsadresser](../../delivery/using/about-seed-addresses.md).

Du kan kombinera definitionen för ett specifikt korrekturmål och användningen av dirigerade adresser med hjälp av **[!UICONTROL Specific target and Seed addresses]** alternativet. De relaterade konfigurationerna definieras sedan i två separata underflikar.
