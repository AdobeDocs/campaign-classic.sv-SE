---
product: campaign
title: Definiera målpopulationen
description: Lär dig definiera målpopulationen
feature: Audiences
exl-id: d0ed7be7-3147-4cb8-9ce7-ea51602e9048
source-git-commit: 1e11b7419388698f5de366cbeddf2be88ef12873
workflow-type: tm+mt
source-wordcount: '1598'
ht-degree: 2%

---

# Definiera målpopulationen {#defining-the-target-population}

![](../../assets/common.svg)

För varje leverans kan du definiera flera typer av målpopulationer:

* **Huvudmålgrupp**: profiler som tar emot meddelanden. [Läs mer](steps-defining-the-target-population.md#selecting-the-main-target)
* **Korrektur**: mottagare av korrekturmeddelanden som deltar i valideringscykeln. [Läs mer](steps-defining-the-target-population.md#defining-a-specific-proof-target)
* **Fröadresser**: mottagare som ligger utanför leveransmålet men som kommer att få leveransen (endast inom ramen för en marknadsföringskampanj). [Läs mer](about-seed-addresses.md)
* **Kontrollgrupper**: populationen som inte kommer att ta emot leveransen, används för att spåra beteenden och kampanjpåverkan (endast i samband med en marknadsföringskampanj). [Läs mer](../../campaign/using/marketing-campaign-target.md#defining-a-control-group).

## Välj de huvudsakliga mottagarna av leveransen {#selecting-the-main-target}

I de flesta fall extraheras huvudmålet från Adobe Campaign-databasen (standardläge). Mottagarna kan dock också lagras i en extern fil. Läs mer i [det här avsnittet](steps-defining-the-target-population.md#selecting-external-recipients).

Följ stegen nedan för att välja mottagare av en leverans:

1. Välj **[!UICONTROL To]**.
1. Om mottagarna lagras i databasen väljer du det första alternativet.

   ![](assets/s_ncs_user_wizard_email02a.png)

1. Välj målmappningen i **[!UICONTROL Target mapping]** nedrullningsbar lista. Adobe Campaign standardmålmappning är **[!UICONTROL Recipients]**, baserat på **nms:mottagare** schema.

   Andra målmappningar är tillgängliga, och vissa kan vara relaterade till din specifika konfiguration. Mer information om målmappningar finns i [Välj en målmappning](selecting-a-target-mapping.md).

1. Klicka på **[!UICONTROL Add]** för att definiera begränsningsfilter.

   Du kan sedan välja vilken typ av filtrering du vill använda:

   ![](assets/s_ncs_user_wizard_email02b.png)

   Du kan välja mottagare med hjälp av de typer av mål som definieras i databasen. Om du vill använda en måltyp markerar du den och klickar på **[!UICONTROL Next]**. För varje mål kan du visa de berörda mottagarna genom att klicka på **[!UICONTROL Preview]** -fliken. För vissa typer av mål **[!UICONTROL Refine target]** kan du kombinera flera målinriktningskriterier.

   Följande måltyper erbjuds som standard:

   * **[!UICONTROL Filtering conditions]** : Med det här alternativet kan du definiera en fråga och visa resultatet. Metoden för att definiera frågor visas i [det här avsnittet](../../platform/using/creating-filters.md#creating-an-advanced-filter).
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
      >The **[!UICONTROL Include sub-folders]** Med det här alternativet kan du även ange leveranser i mappar i trädstrukturen nedanför den valda noden som mål.

   * **[!UICONTROL Recipients included in a folder]** : Med det här alternativet kan du ange profiler i en viss mapp i trädet som mål.
   * **[!UICONTROL A recipient]** : Med det här alternativet kan du välja en viss mottagare bland profilerna i databasen.
   * **[!UICONTROL A list of recipients]** : Med det här alternativet kan du ange en lista över mottagare som mål. Listor visas i [det här avsnittet](../../platform/using/creating-and-managing-lists.md).
   * **[!UICONTROL User filters]** : Med det här alternativet kan du komma åt de förkonfigurerade filtren och använda dem som filtreringsvillkor för profiler i databasen. Förkonfigurerade filter visas i [det här avsnittet](../../platform/using/creating-filters.md#saving-a-filter).
   * Alternativet **[!UICONTROL Exclude recipients corresponding to this segment]** använder du för att ange mål för mottagare som inte uppfyller de definierade målvillkoren. Om du vill använda det här alternativet markerar du lämplig ruta och tillämpar sedan målinriktning, enligt definitionen ovan, för att utesluta de resulterande profilerna.

      ![](assets/s_ncs_user_wizard_email02g.png)

1. Ange ett namn för den här målsättningen i dialogrutan **[!UICONTROL Label]** fält. Som standard kommer etiketten att vara etiketten för det första målinriktningskriteriet. För en kombination är det bättre att använda ett explicit namn.
1. Klicka **[!UICONTROL Finish]** för att validera den konfigurerade målgruppsanpassningen.

   De definierade målinriktningskriterierna sammanfattas i det centrala avsnittet på fliken för huvudmålkonfiguration. Klicka på ett villkor för att visa dess innehåll (konfiguration och förhandsgranskning). Om du vill ta bort ett villkor klickar du på krysset efter etiketten.

   ![](assets/s_ncs_user_wizard_email02h.png)

### Välj externa mottagare {#selecting-external-recipients}

Du kan starta en leverans för mottagare som inte har sparats i databasen, men som har lagrats i en extern fil. Här skickar vi till exempel en leverans till mottagare som importerats från en textfil.

Så här gör du:

1. Klicka på **[!UICONTROL To]** för att välja mottagare.
1. Välj **[!UICONTROL Defined in an external file]** alternativ.

   ![](assets/s_ncs_user_wizard_external_recipients.png)

1. Som standard importeras mottagarna i databasen. Du måste välja **[!UICONTROL Target mapping]**. Mer information om målmappningar finns i [Välj en målmappning](selecting-a-target-mapping.md)

   Du kan också välja **[!UICONTROL Do not import the recipients into the database]**.

1. När du importerar mottagarna klickar du på **[!UICONTROL File format definition...]** för att välja och konfigurera den externa filen.

   Mer information om import av data finns i [det här avsnittet](../../platform/using/executing-import-jobs.md#step-2---source-file-selection).

1. Klicka **[!UICONTROL Finish]** och konfigurera leveransen som en standardleverans.

>[!CAUTION]
>
>När du definierar innehållet i meddelandet för e-postleverans ska du inte inkludera länken till spegelsidan. den inte kan genereras i det här leveransläget.

### Definiera exkluderingsinställningar {#define-exclusion-settings}

Adressfel och kvalitetsklassificeringar tillhandahålls av tjänstleverantören. Den här informationen uppdateras automatiskt i mottagarprofilen efter leveransåtgärder och med filer som returneras av tjänsteleverantörer. Den kan visas i profilen med skrivskydd.

Du kan välja att exkludera adresser som har nått ett visst antal efterföljande fel, eller vars kvalitetsklassificering är under ett tröskelvärde som anges i det här fönstret. Du kan också välja om du vill auktorisera icke-kvalificerade adresser som inga data har returnerats för.

>[!NOTE]
>
>Om två mottagare har samma förnamn, efternamn, postnummer och ort i en direktutskick uppstår ett dubbelt fel och dubbletten tas inte med i beräkningen.

The **[!UICONTROL Exclusions]** -fliken används för att begränsa antalet meddelanden.

>[!NOTE]
>
>Standardparametrar rekommenderas, men du kan anpassa inställningarna efter dina behov. Dessa alternativ bör dock endast ändras av en expertanvändare för att undvika felanvändning och fel.

Klicka på **[!UICONTROL Edit...]** om du vill ändra standardkonfigurationen.

![](assets/s_ncs_user_wizard_email02i.png)

Följande alternativ är tillgängliga:

* **[!UICONTROL Exclude duplicate addresses during delivery]**. Det här alternativet är aktivt som standard: kan du ta bort dubbletter av e-postadresser under leveransen. Den strategi som tillämpas kan variera beroende på hur Adobe Campaign används och vilken typ av data som finns i databasen.

   Standardvärdet för alternativet kan konfigureras för varje leveransmall.

   Exempel:

   * Leverans av nyhetsbrev eller elektroniska dokument. I vissa fall finns det inget undantag för dubbletter om data inte har några inbyggda dubbletter. Ett par som prenumererar med samma e-postadress kan förvänta sig att få två specifika personliga e-postmeddelanden: en adresserad till varje enskild person efter namn. I det här fallet kan det här alternativet avmarkeras.
   * Leverera en marknadsföringskampanj: Duplicerad uteslutning är nödvändigt för att undvika att skicka för många meddelanden till samma mottagare. I det här fallet kan du välja det här alternativet.

      Om du avmarkerar det här alternativet får du tillgång till ytterligare ett alternativ: **[!UICONTROL Keep duplicate records (same identifier)]**. Det gör att ni kan auktorisera flera leveranser till mottagare som uppfyller flera målinriktningskriterier.

      ![](assets/s_ncs_user_wizard_email02j.png)

* **[!UICONTROL Exclude recipients who no longer want to be contacted]** , d.v.s. mottagare vars e-postadresser är på blockeringslista (avanmäl dig). Detta alternativ måste förbli valt för att man ska kunna följa e-handelns yrkesmässiga etik och lagstiftningen om e-handel.
* **[!UICONTROL Exclude quarantined recipients]**. Med det här alternativet kan du undanta profiler med en adress som inte svarar från målet. Vi rekommenderar starkt att du behåller det här alternativet markerat.

   >[!NOTE]
   >
   >Mer information om karantänhantering finns i [Förstå karantänhantering](understanding-quarantine-management.md).

* **[!UICONTROL Limit delivery]** till ett visst antal meddelanden. Med det här alternativet kan du ange maximalt antal meddelanden som ska skickas. Om målets innehåll överskrider antalet angivna meddelanden, tillämpas ett slumpmässigt urval på målet.

### Minska storleken på målpopulationen {#reducing-the-size-of-the-target-population}

Du kan minska storleken på målpopulationen. Om du vill göra det anger du antalet mottagare som ska exporteras i **[!UICONTROL Requested quantity]** fält.

![](assets/s_ncs_user_edit_del_exe_tab.png)

## Välj mottagare av korrekturmeddelanden {#selecting-the-proof-target}

Korrekturmeddelandet är ett särskilt meddelande där du kan testa en leverans innan du skickar den till huvudmålet. Korrekturmottagare ansvarar för att godkänna både meddelandets form och innehåll.

![](assets/do-not-localize/how-to-video.png) [Upptäck den här funktionen i en video](#seeds-and-proofs-video)


Följ stegen nedan för att välja provtryckets mål:

1. Klicka på länken **[!UICONTROL To]**.
1. Klicka på **[!UICONTROL Target of the proofs]** -fliken.
1. Klicka på **[!UICONTROL Targeting mode]** fält där du väljer vilken metod som ska användas: **[!UICONTROL Definition of a specific proof target]** , **[!UICONTROL Substitution of the address]** , **[!UICONTROL Seed addresses]** eller **[!UICONTROL Specific target and seed addresses]**.

>[!NOTE]
>
>Vanligtvis kan provtryckets mål läggas till i huvudmålet. Det gör du genom att välja lämpligt alternativ i nedre delen av **[!UICONTROL Main target]** -fliken.

## Definiera ett specifikt korrekturmål {#defining-a-specific-proof-target}

När du väljer korrekturmålet visas **[!UICONTROL Definition of a specific proof target]** gör att du kan välja korrekturmottagare från profilerna i databasen.

Välj det här alternativet om du vill välja mottagare med hjälp av **[!UICONTROL Add]** -knappen, som när du definierar huvudmålet. Se [Välj huvudmålet](steps-defining-the-target-population.md#selecting-the-main-target).

![](assets/s_ncs_user_wizard_email01_143.png)

Mer information om att skicka korrektur finns i [det här avsnittet](steps-validating-the-delivery.md#sending-a-proof).

### Använd adressersättning i korrektur {#using-address-substitution-in-proof}

I stället för att välja dedikerade mottagare i databasen kan du använda **[!UICONTROL Substitution of the address]** alternativ.

Med det här alternativet kan du använda mottagarprofilerna för leveransen och ersätta deras e-postadresser med en eller flera andra adresser som kommer att ta emot korrekturet.

När det här alternativet är markerat fylls korrekturadresserna i via en särskild redigerare där du kan konfigurera ersättningsadresserna.

![](assets/s_ncs_user_wizard_email_bat_substitute.png)

Konfigurationen utförs enligt följande:

1. Klicka på **[!UICONTROL Add]** om du vill definiera en ersättning.
1. Ange den mottagaradress som ska användas eller välj den i listan.
1. Välj den profil som ska användas i korrekturet: spara **[!UICONTROL Random]** värdet i **[!UICONTROL Profile to use]** om du vill använda data från en profil för målet i korrekturet.

   ![](assets/s_ncs_user_wizard_email_bat_substitute_choose.png)

1. Klicka på **[!UICONTROL Detail]** -ikonen för att välja en profil från huvudmålet, som i följande exempel:

   ![](assets/s_ncs_user_wizard_email_bat_substitute_select.png)

   Du kan definiera så många ersättningsadresser som behövs.

## Använd dirigerade adresser som bevis {#using-seed-addresses-as-proof}

Du kan använda **[!UICONTROL Seed addresses]** som provtryckets mål: Med det här alternativet kan du använda eller importera en lista med befintliga dirigerade adresser.

![](assets/s_ncs_user_wizard_email_bat_control_address.png)

>[!NOTE]
>
>Seed-adresserna presenteras i [Om dirigeringsadresser](about-seed-addresses.md).

Du kan kombinera definitionen för ett specifikt korrekturmål och användningen av dirigerade adresser med **[!UICONTROL Specific target and Seed addresses]** alternativ. De relaterade konfigurationerna definieras sedan i två separata underflikar.

Se även:

* [Välj korrekturmål](#selecting-the-proof-target)
* [Om dirigerade adresser](about-seed-addresses.md)
* [Användningsfall: välj dirigerade adresser enligt villkor](use-case--selecting-seed-addresses-on-criteria.md)

## Videokurs {#seeds-and-proofs-video}

I den här videon får du lära dig hur du lägger till frön och korrektur i ett befintligt e-postmeddelande och hur du skickar det.

>[!VIDEO](https://video.tv.adobe.com/v/25606?quality=12)

Det finns fler instruktionsvideor för Campaign Classic [här](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=sv).
