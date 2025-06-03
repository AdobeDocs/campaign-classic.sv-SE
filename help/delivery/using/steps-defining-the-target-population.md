---
product: campaign
title: Definiera målpopulationen
description: Lär dig definiera målpopulationen
feature: Audiences, Proofs
role: User
hide: true
hidefromtoc: true
exl-id: d0ed7be7-3147-4cb8-9ce7-ea51602e9048
source-git-commit: 42cec0e9bede94a2995a5ad442822512bda14f2b
workflow-type: tm+mt
source-wordcount: '1729'
ht-degree: 2%

---

# Definiera målpopulationen {#defining-the-target-population}

För varje leverans kan du definiera flera typer av målpopulationer:

* **Huvudmålgrupp**: profiler som tar emot meddelanden. [Läs mer](steps-defining-the-target-population.md#selecting-the-main-target)
* **Korrektur**: mottagare av korrekturmeddelanden som ingår i valideringscykeln. [Läs mer](steps-defining-the-target-population.md#defining-a-specific-proof-target)
* **Utdirigerade adresser**: mottagare som ligger utanför leveransmålet men som kommer att ta emot leveransen (endast i samband med en marknadsföringskampanj). [Läs mer](about-seed-addresses.md)
* **Kontrollgrupper**: fyllning som inte tar emot leveransen, används för att spåra beteende och kampanjpåverkan (endast i samband med en marknadsföringskampanj). [Läs mer](../../campaign/using/marketing-campaign-target.md#defining-a-control-group).

## Välj de huvudsakliga mottagarna av leveransen {#selecting-the-main-target}

I de flesta fall hämtas huvudmålet från Adobe Campaign-databasen (standardläge). Mottagarna kan dock också lagras i en extern fil. Läs mer i [det här avsnittet](steps-defining-the-target-population.md#selecting-external-recipients).

Följ stegen nedan för att välja mottagare av en leverans:

1. Välj **[!UICONTROL To]** i leveransredigeraren.
1. Om mottagarna lagras i databasen väljer du det första alternativet.

   ![](assets/s_ncs_user_wizard_email02a.png)

1. Välj målmappning i listrutan **[!UICONTROL Target mapping]**. Adobe Campaign standardmålmappning är **[!UICONTROL Recipients]**, baserat på schemat **nms:mottagare**.

   Andra målmappningar är tillgängliga, och vissa kan vara relaterade till din specifika konfiguration.[Läs mer](#select-a-target-mapping).

1. Klicka på knappen **[!UICONTROL Add]** för att definiera begränsningsfilter.

   Du kan sedan välja vilken typ av filtrering du vill använda:

   ![](assets/s_ncs_user_wizard_email02b.png)

   Du kan välja mottagare med hjälp av de typer av mål som definieras i databasen. Om du vill använda en måltyp markerar du den och klickar på **[!UICONTROL Next]**. För varje mål kan du visa de berörda mottagarna genom att klicka på fliken **[!UICONTROL Preview]**. För vissa typer av mål kan du med knappen **[!UICONTROL Refine target]** kombinera flera målinriktningskriterier.

   Följande måltyper erbjuds som standard:

   * **[!UICONTROL Filtering conditions]** : Med det här alternativet kan du definiera en fråga och visa resultatet. Metoden för att definiera frågor visas i [det här avsnittet](../../platform/using/creating-filters.md#creating-an-advanced-filter).
   * **[!UICONTROL Subscribers of an information service]** : Med det här alternativet kan du välja ett nyhetsbrev som mottagarna måste prenumerera på för att få det mål som den leverans som skapas har.

     ![](assets/s_ncs_user_wizard_email02c.png)

   * **[!UICONTROL Recipients of a delivery]** : Med det här alternativet kan du definiera mottagarna av en befintlig leverans som ett målinriktningskriterium. Du måste sedan välja leveransen i listan:

     ![](assets/s_ncs_user_wizard_email02d.png)

   * **[!UICONTROL Delivery recipients belonging to a folder]** : Med det här alternativet kan du välja en leveransmapp och ange mottagare för leveranserna i den mappen som mål.

     ![](assets/s_ncs_user_wizard_email02e.png)

     Du kan filtrera mottagarnas beteende genom att välja i listrutan:

     ![](assets/s_ncs_user_wizard_email02f.png)

     >[!NOTE]
     >
     >Med alternativet **[!UICONTROL Include sub-folders]** kan du även ange leveranser i mappar i trädstrukturen nedanför den valda noden som mål.

   * **[!UICONTROL Recipients included in a folder]** : Med det här alternativet kan du ange profiler i en viss mapp i trädet som mål.
   * **[!UICONTROL A recipient]** : Med det här alternativet kan du välja en specifik mottagare bland profilerna i databasen.
   * **[!UICONTROL A list of recipients]** : Med det här alternativet kan du ange en lista över mottagare som mål. Listor visas i [det här avsnittet](../../platform/using/creating-and-managing-lists.md).
   * **[!UICONTROL User filters]** : Med det här alternativet kan du komma åt de förkonfigurerade filtren och använda dem som filtreringsvillkor för profiler i databasen. Förkonfigurerade filter visas i [det här avsnittet](../../platform/using/creating-filters.md#saving-a-filter).
   * Med alternativet **[!UICONTROL Exclude recipients corresponding to this segment]** kan du rikta in dig på mottagare som inte uppfyller de definierade målvillkoren. Om du vill använda det här alternativet markerar du lämplig ruta och tillämpar sedan målinriktning, enligt definitionen ovan, för att utesluta de resulterande profilerna.

     ![](assets/s_ncs_user_wizard_email02g.png)

1. Ange ett namn för den här målsättningen i fältet **[!UICONTROL Label]**. Som standard kommer etiketten att vara etiketten för det första målinriktningskriteriet. För en kombination är det bättre att använda ett explicit namn.
1. Klicka på **[!UICONTROL Finish]** för att validera den konfigurerade målgruppen.

   De definierade målinriktningskriterierna sammanfattas i det centrala avsnittet på fliken för huvudmålkonfiguration. Klicka på ett villkor för att visa dess innehåll (konfiguration och förhandsgranskning). Om du vill ta bort ett villkor klickar du på krysset efter etiketten.

   ![](assets/s_ncs_user_wizard_email02h.png)

### Välj externa mottagare {#selecting-external-recipients}

Du kan starta en leverans för mottagare som inte har sparats i databasen, men som har lagrats i en extern fil. Här skickar vi till exempel en leverans till mottagare som importerats från en textfil.

Så här gör du:

1. Klicka på länken **[!UICONTROL To]** för att välja mottagare av leveransen.
1. Välj alternativet **[!UICONTROL Defined in an external file]**.

   ![](assets/s_ncs_user_wizard_external_recipients.png)

1. Som standard importeras mottagarna i databasen. Du måste välja **[!UICONTROL Target mapping]**. [Läs mer](#select-a-target-mapping)

   Du kan också välja **[!UICONTROL Do not import the recipients into the database]**.

1. När du importerar mottagarna klickar du på länken **[!UICONTROL File format definition...]** för att markera och konfigurera den externa filen.

   Mer information om dataimport finns i [det här avsnittet](../../platform/using/executing-import-jobs.md#step-2---source-file-selection).

1. Klicka på **[!UICONTROL Finish]** och konfigurera leveransen som en standardleverans.

>[!CAUTION]
>
>När du definierar innehållet i meddelandet för e-postleverans ska du inte inkludera länken till spegelsidan. Det kan inte genereras i det här leveransläget.

### Definiera exkluderingsinställningar {#define-exclusion-settings}

Adressfel och kvalitetsklassificeringar tillhandahålls av tjänstleverantören (IAP). Den här informationen uppdateras automatiskt i mottagarprofilen efter leveransåtgärder och med filer som returneras av tjänsteleverantörer. Den kan visas i profilen med skrivskydd.

Du kan välja att exkludera adresser som har nått ett visst antal efterföljande fel, eller vars kvalitetsklassificering är under ett tröskelvärde som anges i det här fönstret. Du kan också välja om du vill auktorisera icke-kvalificerade adresser som inga data har returnerats för.

>[!NOTE]
>
>Om två mottagare har samma förnamn, efternamn, postnummer och ort i en direktutskick uppstår ett dubbelt fel och dubbletten tas inte med i beräkningen.

Fliken **[!UICONTROL Exclusions]** används för att begränsa antalet meddelanden.

>[!NOTE]
>
>Standardparametrar rekommenderas, men du kan anpassa inställningarna efter dina behov. Dessa alternativ bör dock endast ändras av en expertanvändare för att undvika felanvändning och fel.

Klicka på länken **[!UICONTROL Edit...]** om du vill ändra standardkonfigurationen.

![](assets/s_ncs_user_wizard_email02i.png)

Följande alternativ är tillgängliga:

* **[!UICONTROL Exclude duplicate addresses during delivery]**. Det här alternativet är aktivt som standard: du kan ta bort dubbletter av e-postadresser under leverans. Den strategi som tillämpas kan variera beroende på hur Adobe Campaign används och vilken typ av data som finns i databasen.

  Standardvärdet för alternativet kan konfigureras för varje leveransmall.

  Exempel:

   * Leverans av nyhetsbrev eller elektroniska dokument. I vissa fall finns det inget undantag för dubbletter om data inte har några inbyggda dubbletter. Ett par som prenumererar med samma e-postadress kan förvänta sig att få två specifika personliga e-postmeddelanden: ett adresserat till varje enskild person per namn. I det här fallet kan det här alternativet avmarkeras.
   * Leverans av en marknadsföringskampanj: det är viktigt med dubblettundantag för att undvika att skicka för många meddelanden till samma mottagare. I det här fallet kan du välja det här alternativet.

     Om du avmarkerar det här alternativet kan du få åtkomst till ytterligare ett alternativ: **[!UICONTROL Keep duplicate records (same identifier)]**. Det gör att ni kan auktorisera flera leveranser till mottagare som uppfyller flera målinriktningskriterier.

     ![](assets/s_ncs_user_wizard_email02j.png)

* **[!UICONTROL Exclude recipients who no longer want to be contacted]**, d.v.s. mottagare vars e-postadresser är på blockeringslista (avanmäl dig). Detta alternativ måste förbli valt för att man ska kunna följa e-handelns yrkesmässiga etik och lagstiftningen om e-handel.
* **[!UICONTROL Exclude quarantined recipients]**. Med det här alternativet kan du undanta profiler med en adress som inte svarar från målet. Vi rekommenderar starkt att du behåller det här alternativet markerat.

  >[!NOTE]
  >
  >Mer information om karantänhantering finns i [Förstå karantänhantering](understanding-quarantine-management.md).

* **[!UICONTROL Limit delivery]** till ett visst antal meddelanden. Med det här alternativet kan du ange maximalt antal meddelanden som ska skickas. Om målets innehåll överskrider antalet angivna meddelanden, tillämpas ett slumpmässigt urval på målet.

### Minska storleken på målpopulationen {#reducing-the-size-of-the-target-population}

Du kan minska storleken på målpopulationen. Om du vill göra det anger du antalet mottagare som ska exporteras i fältet **[!UICONTROL Requested quantity]**.

![](assets/s_ncs_user_edit_del_exe_tab.png)

## Välj mottagare av korrekturmeddelanden {#selecting-the-proof-target}

Korrekturmeddelandet är ett särskilt meddelande där du kan testa en leverans innan du skickar den till huvudmålet. Korrekturmottagare ansvarar för att godkänna både meddelandets form och innehåll.

![](assets/do-not-localize/how-to-video.png) [Upptäck den här funktionen i en video](#seeds-and-proofs-video)


Följ stegen nedan för att välja provtryckets mål:

1. Klicka på länken **[!UICONTROL To]**.
1. Klicka på fliken **[!UICONTROL Target of the proofs]**.
1. Klicka på fältet **[!UICONTROL Targeting mode]** för att välja den metod som ska användas: **[!UICONTROL Definition of a specific proof target]**, **[!UICONTROL Substitution of the address]**, **[!UICONTROL Seed addresses]** eller **[!UICONTROL Specific target and seed addresses]**.

>[!NOTE]
>
>Vanligtvis kan provtryckets mål läggas till i huvudmålet. Om du vill göra det väljer du lämpligt alternativ i det nedre avsnittet på fliken **[!UICONTROL Main target]**.

## Definiera ett specifikt korrekturmål {#defining-a-specific-proof-target}

När du väljer korrekturmålet kan du med alternativet **[!UICONTROL Definition of a specific proof target]** välja korrekturmottagare från profilerna i databasen.

Välj det här alternativet om du vill välja mottagare med knappen **[!UICONTROL Add]**, som när du definierar huvudmålet. Se [Markera huvudmålet](steps-defining-the-target-population.md#selecting-the-main-target).

![](assets/s_ncs_user_wizard_email01_143.png)

Mer information om hur du skickar korrektur finns i [det här avsnittet](steps-validating-the-delivery.md#sending-a-proof).

### Använd adressersättning i korrektur {#using-address-substitution-in-proof}

I stället för att välja dedikerade mottagare i databasen kan du använda alternativet **[!UICONTROL Substitution of the address]**.

Med det här alternativet kan du använda mottagarprofilerna för leveransen och ersätta deras e-postadresser med en eller flera andra adresser som kommer att ta emot korrekturet.

När det här alternativet är markerat fylls korrekturadresserna i via en särskild redigerare där du kan konfigurera ersättningsadresserna.

![](assets/s_ncs_user_wizard_email_bat_substitute.png)

Konfigurationen utförs enligt följande:

1. Klicka på ikonen **[!UICONTROL Add]** för att definiera en ersättning.
1. Ange den mottagaradress som ska användas eller välj den i listan.
1. Välj den profil som ska användas i korrekturet: spara värdet **[!UICONTROL Random]** i kolumnen **[!UICONTROL Profile to use]** om du vill använda data för målprofilen i korrekturet.

   ![](assets/s_ncs_user_wizard_email_bat_substitute_choose.png)

1. Klicka på ikonen **[!UICONTROL Detail]** för att välja en profil från huvudmålet, som i följande exempel:

   ![](assets/s_ncs_user_wizard_email_bat_substitute_select.png)

   Du kan definiera så många ersättningsadresser som behövs.

## Använd dirigerade adresser som bevis {#using-seed-addresses-as-proof}

Du kan använda **[!UICONTROL Seed addresses]** som mål för korrektur: med det här alternativet kan du använda eller importera en lista med befintliga dirigerade adresser.

![](assets/s_ncs_user_wizard_email_bat_control_address.png)

>[!NOTE]
>
>Seed-adresserna visas i [Om dirigerade adresser](about-seed-addresses.md).

Du kan kombinera definitionen för ett specifikt korrekturmål och användningen av dirigerade adresser med alternativet **[!UICONTROL Specific target and Seed addresses]**. De relaterade konfigurationerna definieras sedan i två separata underflikar.

Se även:

* [Välj korrekturmål](#selecting-the-proof-target)
* [Om dirigerade adresser](about-seed-addresses.md)
* [Användningsfall: välj dirigerade adresser enligt villkor](use-case-selecting-seed-addresses-on-criteria.md)

## Välj en målmappning {#select-a-target-mapping}

Som standard är leveransmallar avsedda för **[!UICONTROL Recipients]**. Målmappningen använder därför fälten i tabellen **nms:receive**. Adobe Campaign erbjuder andra målmappningar för leveranser som kan användas utifrån dina behov.

![](assets/delivery_select_mapping.png)

Mappningarna är följande:

| Namn | Använd | Standardschema |
|---|---|---|
| Mottagare | Leverera till mottagare av Adobe Campaign-databasen | nms:mottagare |
| Besökare | Leverera till besökare vars profiler har samlats in via hänskjutning (viral marknadsföring) eller via sociala nätverk (Facebook, X - tidigare Twitter), till exempel. | mns:besökare |
| Prenumerationer | Leverera till mottagare som prenumererar på en informationstjänst som ett nyhetsbrev | nms:prenumeration |
| Prenumerationer på besökare | Skicka till besökare som prenumererar på en informationstjänst | nms:visitorSub |
| Tjänst | Publicera till ett X-konto eller en Facebook-sida | nms:service |
| Operatorer | Leverera till Adobe Campaign | nms:operator |
| Extern fil | Leverera via en fil som innehåller all information som behövs för leveransen | Inget länkat schema, inget mål har angetts |


## Självstudievideo {#seeds-and-proofs-video}

I den här videon får du lära dig hur du lägger till frön och korrektur i ett befintligt e-postmeddelande och hur du skickar det.

>[!VIDEO](https://video.tv.adobe.com/v/25606?quality=12)

Ytterligare Campaign Classic instruktionsvideor finns [här](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=sv).
