---
product: campaign
title: Arbeta med datapaket
description: Arbeta med datapaket
feature: Data Management, Package Export/Import
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
audience: platform
content-type: reference
topic-tags: administration-basics
exl-id: d3369b63-a29b-43b7-b2ad-d36d4f46c82e
source-git-commit: 349c3dfd936527e50d7d3e03aa3408b395502da0
workflow-type: tm+mt
source-wordcount: '2474'
ht-degree: 2%

---

# Arbeta med datapaket{#working-with-data-packages}



## Om datapaket {#about-data-packages}

Med Adobe Campaign kan du exportera eller importera plattformskonfigurationen och data via ett paketsystem. Paket kan innehålla olika typer av konfigurationer, element, filtrerade eller inte.

Med datapaket kan enheter i databasen i Adobe Campaign visas via filer i XML-format. Varje entitet i ett paket representeras med alla dess data.

Principen för **datapaket** är att exportera en datakonfiguration och integrera den i ett annat Adobe Campaign-system. Lär dig hur du upprätthåller en konsekvent uppsättning datapaket i det här [avsnittet](#data-package-best-practices).

### Typ av paket {#types-of-packages}

Det finns tre typer av paket som kan exporteras: användarpaket, plattformspaket och administratörspaket.

* **Användarpaket**: du kan välja en lista över entiteter som ska exporteras. Den här typen av paket hanterar beroenden och verifierar fel.
* **Plattformspaket**: innehåller alla tillagda tekniska resurser (ej standard): scheman, JavaScript-kod osv.

  ![](assets/ncs_datapackage_package_platform.png)

* **Administrationspaket**: innehåller alla tillagda mallar och affärsobjekt (ej standard): mallar, bibliotek osv.

  ![](assets/ncs_datapackage_package_admin.png)

>[!CAUTION]
>
>Typerna **platform** och **admin** innehåller en fördefinierad lista med entiteter som ska exporteras. Varje entitet är länkad till filtervillkor som gör att du kan ta bort de färdiga resurserna i det skapade paketet.

## Datastruktur {#data-structure}

Beskrivningen av ett datapaket är ett strukturerat XML-dokument som är kompatibelt med grammatiken i dataramat **xrk:navtree**.

Exempel:

```
<package>
  <entities schema="nms:recipient">
    <recipient email="john.smith@adobe.com" lastName="Smith" firstName="John">      
      <folder _operation="none" name="nmsRootFolder"/>      
      <company _operation="none" name="Adobe"/>
    </recipient>
  </entities>
  <entities schema="sfa:company">
    <company name="Adobe">
      location city="London" zipCode="W11 2BQ"/>
    </company>
  </entities>
</package>
```

XML-dokumentet måste börja och sluta med elementet **`<package>`**. Alla **`<entities>`**-element som följer distribuerar data efter dokumenttyp.

Ett **`<entities>`**-element innehåller data från paketet i det format som datarammet som anges i attributet **schema** har.

Data i ett paket får inte innehålla interna nycklar som inte är kompatibla mellan baser, till exempel autogenererade nycklar (**autopk** -alternativ).

I det här exemplet har kopplingarna på länkarna &quot;mapp&quot; och &quot;företag&quot; ersatts med så kallade &quot;hög nivå&quot; i måltabellerna:

```
<recipient>
  <folder _operation="none" name="nmsRootFolder"/>
  <company _operation="none" name="Adobe"/>
</recipient>
```

Attributet **`operation`** med värdet &quot;none&quot; definierar en avstämningslänk.

Ett datapaket kan skapas manuellt från valfri textredigerare. Se bara till att XML-dokumentets struktur överensstämmer med dataschemat &quot;xtk:navtree&quot;. Adobe Campaign-konsolen har en export- och importmodul för datapaket.

## Exportera paket {#exporting-packages}

### Om paketexport {#about-package-export}

Paket kan exporteras på tre olika sätt:

* Med **[!UICONTROL Package Export Assistant]** kan du exportera en uppsättning objekt i ett enda paket. Mer information finns i [Exportera en uppsättning objekt i ett paket](#exporting-a-set-of-objects-in-a-package)
* Ett **enskilt objekt** kan exporteras direkt i ett paket genom att högerklicka på det och välja **[!UICONTROL Actions > Export in a package]**.
* Med **paketdefinitioner** kan du skapa en paketstruktur där du lägger till objekt som ska exporteras senare i ett paket. Mer information finns i [Hantera paketdefinitioner](#managing-package-definitions)

När ett paket har exporterats kan du importera det och alla tillagda enheter till en annan Campaign-instans.

### Exportera en uppsättning objekt i ett paket {#exporting-a-set-of-objects-in-a-package}

Paketexportassistenten är tillgänglig via menyn **[!UICONTROL Tools > Advanced > Export package...]** i Adobe Campaign klientkonsol.

![](assets/ncs_datapackage_typepackage.png)

För de tre typerna av paket erbjuder assistenten följande steg:

1. Lista de enheter som ska exporteras efter dokumenttyp:

   ![](assets/ncs_datapackage_export2.png)

   >[!CAUTION]
   >
   >Om du exporterar en **[!UICONTROL Offer category]**-, **[!UICONTROL Offer environment]**-, **[!UICONTROL Program]**- eller **[!UICONTROL Plan]**-typmapp ska du aldrig markera **xtk:folder** eftersom du kan förlora vissa data. Välj den entitet som motsvarar mappen: **nms:offerCategory** för erbjudandekategorier, **nms:offerEnv** för erbjudandemiljöer, **nms:program** för program och **nms:plan** för planer.

   Med listhantering kan du lägga till eller ta bort enheter för export från konfigurationen. Klicka på **[!UICONTROL Add]** för att välja en ny entitet.

   Knappen **[!UICONTROL Detail]** redigerar den valda konfigurationen.

   >[!NOTE]
   >
   >Beroendemekanismen styr entitetens exportsekvens. Mer information finns i [Hantera beroenden](#managing-dependencies).

1. Enhetskonfigurationsskärmen definierar filterfrågan för den typ av dokument som ska extraheras.

   Du måste konfigurera filtersatsen för dataextrahering.

   ![](assets/ncs_datapackage_export4.png)

   >[!NOTE]
   >
   >Frågeredigeraren visas i [det här avsnittet](../../platform/using/about-queries-in-campaign.md).

1. Klicka på **[!UICONTROL Next]** och markera sorteringskolumnerna för att sortera data under extraheringen:

   ![](assets/ncs_datapackage_export5.png)

1. Förhandsgranska de data som ska extraheras innan du kör exporten.

   ![](assets/ncs_datapackage_export6.png)

1. På den sista sidan i paketets exportassistent kan du starta exporten. Data lagras i den fil som anges i fältet **[!UICONTROL File]**.

   ![](assets/ncs_datapackage_export7.png)

### Hantera beroenden {#managing-dependencies}

Med exportfunktionen kan Adobe Campaign spåra länkarna mellan de olika exporterade elementen.

Den här mekanismen definieras av två regler:

* objekt som är länkade till en länk med en **egen** - eller **egen** -typintegritet exporteras i samma paket som det exporterade objektet.
* objekt som är länkade till en länk med en **neutral** - eller **definierad** -typografering (definierad länk) måste exporteras separat.

>[!NOTE]
>
>Integritetstyper som är länkade till schemaelement definieras i [det här avsnittet](../../configuration/using/database-mapping.md#links--relation-between-tables).

#### Exportera en kampanj {#exporting-a-campaign}

Här är ett exempel på hur du exporterar en kampanj. Marknadsföringskampanjen som ska exporteras innehåller en aktivitet (etikett:&quot;MyTask&quot;) och ett arbetsflöde (etikett:&quot;CampaignWorkflow&quot;) i en&quot;MyWorkflow&quot;-mapp (nod: Administration / Produktion / Tekniska arbetsflöden / Kampanjprocesser / MyWorkflow).

Uppgiften och arbetsflödet exporteras i samma paket som kampanjen eftersom matchande scheman kopplas samman med länkar med en egen typ av integritet.

Paketinnehåll:

```
<?xml version='1.0'?>
<package author="Administrator (admin)" buildNumber="7974" buildVersion="7.1" img=""
label="" name="" namespace="" vendor="">
 <desc></desc>
 <version buildDate="AAAA-MM-DD HH:MM:SS.954Z"/>
 <entities schema="nms:operation">
  <operation duration="432000" end="AAAA-MM-DD" internalName="OP1" label="MyCampaign"
  modelName="opEmpty" start="AAAA-MM-DD">
   <controlGroup>
    <where filteringSchema=""/>
   </controlGroup>
   <seedList>
    <where filteringSchema="nms:seedMember"></where>
    <seedMember internalName="SDM1"></seedMember>
   </seedList>
   <parameter useAsset="1" useBudget="1" useControlGroup="1" useDeliveryOutline="1"
   useDocument="1" useFCPValidation="0" useSeedMember="1" useTask="1"
   useValidation="1" useWorkflow="1"></parameter>
   <fcpSeed>
    <where filteringSchema="nms:seedMember"></where>
   </fcpSeed>
   <owner _operation="none" name="admin" type="0"/>
   <program _operation="none" name="nmsOperations"/>
   <task end="2023-01-17 10:07:51.000Z" label="MyTask" name="TSK2" start="2023-01-16 10:07:51.000Z"
   status="1">
    <owner _operation="none" name="admin" type="0"/>
    <operation _operation="none" internalName="OP1"/>
    <folder _operation="none" name="nmsTask"/>
   </task>
   <workflow internalName="WKF12" label="CampaignWorkflow" modelName="newOpEmpty"
   order="8982" scenario-cs="Notification of the workflow supervisor (notifySupervisor)"
   schema="nms:recipient">
    <scenario internalName="notifySupervisor"/>
    <desc></desc>
    <folder _operation="none" name="Folder4"/>
    <operation _operation="none" internalName="OP1"/>
   </workflow>
  </operation>
 </entities>
</package>   
```

Anslutning till en typ av paket har definierats i ett schema med attributen **@pkgAdmin och @pkgPlatform** . Båda dessa attribut får ett XTK-uttryck som definierar villkoren för anslutning till paketet.

```
<element name="offerEnv" img="nms:offerEnv.png" 
template="xtk:folder" pkgAdmin="@id != 0">
```

Slutligen kan du med attributet **@pkgStatus** definiera exportreglerna för dessa element eller attribut. Beroende på attributets värde finns elementet eller attributet i det exporterade paketet. De tre möjliga värdena för det här attributet är:

* **never**: exporterar inte fältet/länken
* **always**: tvingar export för det här fältet
* **preCreate**: auktoriserar skapande av den länkade entiteten

>[!NOTE]
>
>Värdet **preCreate** tillåts bara för länktypshändelser. Du kan skapa eller peka mot en enhet som ännu inte har lästs in i det exporterade paketet.

## Hantera paketdefinitioner {#managing-package-definitions}

Med paketdefinitioner kan du skapa en paketstruktur där du lägger till entiteter som ska exporteras senare i ett paket. Du kan sedan importera det här paketet och alla tillagda enheter till en annan Campaign-instans.

**Relaterade ämnen:**

* [Skapa en paketdefinition](#creating-a-package-definition)
* [Lägga till entiteter i en paketdefinition](#adding-entities-to-a-package-definition)
* [Konfigurera generering av paketdefinitioner](#configuring-package-definitions-generation)
* [Exportera paket från en paketdefinition](#exporting-packages-from-a-package-definition)

### Skapa en paketdefinition {#creating-a-package-definition}

Du kommer åt paketdefinitioner på menyn **[!UICONTROL Administration > Configuration > Package management > Package definitions]**.

Om du vill skapa en paketdefinition klickar du på knappen **[!UICONTROL New]** och fyller sedan i den allmänna paketdefinitionsinformationen.

![](assets/packagedefinition_create.png)

Du kan sedan lägga till enheter i paketdefinitionen och exportera den till ett XML-filpaket.

**Relaterade ämnen:**

* [Lägga till entiteter i en paketdefinition](#adding-entities-to-a-package-definition)
* [Konfigurera generering av paketdefinitioner](#configuring-package-definitions-generation)
* [Exportera paket från en paketdefinition](#exporting-packages-from-a-package-definition)

### Lägga till entiteter i en paketdefinition {#adding-entities-to-a-package-definition}

På fliken **[!UICONTROL Content]** klickar du på knappen **[!UICONTROL Add]** för att markera de enheter som ska exporteras med paketet. De bästa sätten att välja enheter visas i avsnittet [this](#exporting-a-set-of-objects-in-a-package).

![](assets/packagedefinition_addentities.png)

Enheter kan läggas till i en paketdefinition direkt från sin plats i instansen. Gör så här:

1. Högerklicka på önskad entitet och välj sedan **[!UICONTROL Actions > Export in a package]**.

   ![](assets/packagedefinition_singleentity.png)

1. Välj **[!UICONTROL Add to a package definition]** och välj sedan den paketdefinition som du vill lägga till entiteten i.

   ![](assets/packagedefinition_packageselection.png)

1. Entiteten läggs till i paketdefinitionen och exporteras med paketet (se [det här avsnittet](#exporting-packages-from-a-package-definition)).

   ![](assets/packagedefinition_entityadded.png)

### Konfigurera generering av paketdefinitioner {#configuring-package-definitions-generation}

Paketgenerering kan konfigureras från fliken för paketdefinitionen **[!UICONTROL Content]**. Klicka på länken **[!UICONTROL Generation parameters]** om du vill göra det.

![](assets/packagedefinition_generationparameters.png)

* **[!UICONTROL Include the definition]**: innehåller den definition som för närvarande används i paketdefinitionen.
* **[!UICONTROL Include an installation script]**: gör att du kan lägga till ett javascript-skript som ska köras vid paketimporten. När du väljer det här alternativet läggs en **[!UICONTROL Script]**-flik till på paketdefinitionsskärmen.
* **[!UICONTROL Include default values]**: lägger till värdena för alla entiteters attribut i paketet.

  Det här alternativet är inte markerat som standard för att undvika långa exporter. Det innebär att entiteternas attribut med standardvärden (tom sträng, 0 och false om de inte definieras på annat sätt i schemat) inte läggs till i paketet och därför inte exporteras.

  >[!CAUTION]
  >
  >Om du avmarkerar det här alternativet kan lokala och importerade versioner sammanfogas.
  >
  >Om instansen som paketet importeras till innehåller entiteter som är identiska med de i paketet (till exempel med samma externa ID) uppdateras inte deras attribut. Detta kan inträffa om attributen från den tidigare instansen har standardvärden eftersom de inte ingår i paketet.
  >
  >Om du i så fall väljer alternativet **[!UICONTROL Include default values]** förhindras versionssammanslagning, eftersom alla attribut från den tidigare instansen exporteras med paketet.

### Exportera paket från en paketdefinition {#exporting-packages-from-a-package-definition}

Om du vill exportera ett paket från en paketdefinition följer du stegen nedan:

1. Markera den paketdefinition som ska exporteras, klicka på knappen **[!UICONTROL Actions]** och välj **[!UICONTROL Export the package]**.
1. En XML-fil som motsvarar det exporterade paketet markeras som standard. Det namnges enligt paketdefinitionens namnutrymme och namn.
1. När paketnamnet och platsen har definierats klickar du på knappen **[!UICONTROL Start]** för att starta exporten.

   ![](assets/packagedefinition_packageexport.png)

## Importera paket {#importing-packages}

Paketimportassistenten är tillgänglig via huvudmenyn **[!UICONTROL Tools > Advanced > Import package]** i Adobe Campaign klientkonsol.

Du kan importera ett paket från en tidigare export, t.ex. från en annan Adobe Campaign-instans eller ett [inbyggt paket](../../installation/using/installing-campaign-standard-packages.md), beroende på villkoren i din licens.

![](assets/ncs_datapackage_import.png)

### Installera ett paket från en fil {#installing-a-package-from-a-file}

Om du vill importera ett befintligt datapaket markerar du XML-filen och klickar på **[!UICONTROL Open]**.

![](assets/ncs_datapackage_import_1.png)

Innehållet i det paket som ska importeras visas sedan i mitten av redigeraren.

Klicka på **[!UICONTROL Next]** och **[!UICONTROL Start]** för att starta importen.

![](assets/ncs_datapackage_import_2.png)

### Installera ett inbyggt paket {#installing-a-standard-package}

Standardpaket är inbyggda paket som installeras när Adobe Campaign konfigureras. Beroende på din behörighet och distributionsmodell kan du importera nya standardpaket om du skaffar nya alternativ eller tillägg, eller om du uppgraderar till ett nytt erbjudande.

Se licensavtalet för att se vilka paket du kan installera.

Mer information om inbyggda paket finns på [den här sidan](../../installation/using/installing-campaign-standard-packages.md).

## Bästa praxis för datapaket {#data-package-best-practices}

I det här avsnittet beskrivs hur du organiserar datapaket på ett konsekvent sätt under projektets hela livslängd.

Paket kan innehålla olika typer av konfigurationer och element, filtrerade eller inte. Om du saknar vissa element eller inte importerar element/paket i rätt ordning kan plattformskonfigurationen brytas.

Dessutom kan paketspecifikationsmappen snabbt bli komplex om flera personer arbetar på samma plattform med många olika funktioner.

Även om det inte är obligatoriskt att göra det erbjuder det här avsnittet en lösning för att ordna och använda paket i Adobe Campaign för storskaliga projekt.

De huvudsakliga begränsningarna är följande:
* Ordna paketen och håll reda på vad som ändrats och när
* Om en konfiguration uppdateras minimerar du risken för att något som inte är direkt kopplat till uppdateringen bryts

>[!NOTE]
>
>Mer information om hur du konfigurerar ett arbetsflöde för automatisk export av paket finns på [den här sidan](https://helpx.adobe.com/campaign/kb/export-packages-automatically.html).

### Rekommendationer {#data-package-recommendations}

Importera alltid i samma version av plattformen. Du måste kontrollera att du distribuerar dina paket mellan två instanser som har samma programversion. Tvinga aldrig importen och uppdatera alltid plattformen först (om bygget är annorlunda).

>[!IMPORTANT]
>
>Import mellan olika versioner stöds inte av Adobe.
<!--This is not allowed. Importing from 6.02 to 6.1, for example, is prohibited. If you do so, R&D won't be able to help you resolve any issues you encounter.-->

Var uppmärksam på schema- och databasstrukturen. Import av paket med schema måste följas av schemagenerering.

### Lösning {#data-package-solution}

#### Pakettyper {#package-types}

Börja med att definiera olika typer av paket. Endast fyra typer kommer att användas:

**Entiteter**
* Alla xtk- och nms-specifika element i Adobe Campaign som scheman, formulär, mappar, leveransmallar osv.
* Du kan betrakta en entitet som både ett admin- och plattformselement.
* Du bör inte inkludera mer än en enhet i ett paket när du överför det till en Campaign-instans.

<!--Nothing "works" alone. An entity package does not have a specific role or objective.-->

Om du behöver distribuera konfigurationen på en ny instans kan du importera alla enhetspaket.

**Funktioner**

Den här typen av paket:
* Besvarar ett klientbehov/en kundspecifikation.
* Innehåller en eller flera funktioner.
* Bör innehålla alla beroenden för att kunna köra funktionen utan något annat paket.

**Kampanjer**

Detta paket är inte obligatoriskt. Ibland kan det vara användbart att skapa en specifik typ för alla kampanjer, även om en kampanj kan ses som en funktion.

**Uppdateringar**

När en funktion har konfigurerats kan den exporteras till en annan miljö. Paketet kan till exempel exporteras från en utvecklingsmiljö till en testmiljö. I det här testet avslöjas en defekt. Först måste den korrigeras i utvecklingsmiljön. Sedan ska plåstret appliceras på testplattformen.

Den första lösningen skulle vara att exportera hela funktionen igen. Men för att undvika risker (uppdatera oönskade element) är det säkrare att ha ett paket som bara innehåller korrigeringen.

Därför rekommenderar vi att du skapar ett uppdateringspaket som bara innehåller en enhetstyp av funktionen.

En uppdatering kan inte bara vara en korrigering, utan även ett nytt element i ditt enhets-/funktions-/kampanjpaket. Du kan undvika att distribuera hela paketet genom att exportera ett uppdateringspaket.

### Namnkonventioner {#data-package-naming}

Nu när typerna är definierade bör vi ange en namnkonvention. Adobe Campaign tillåter inte att du skapar undermappar för paketspecifikationer, vilket innebär att tal är den bästa lösningen för att hålla ordning. Numreringsprefixpaketnamn. Du kan använda följande konvention:

* Enhet: från 1 till 99
* Funktion: från 100 till 199
* Kampanj: från 200 till 299
* Uppdatering: från 5 000 till 5 999

### Paket {#data-packages}

>[!NOTE]
>
>Det är bättre att ställa in regler för att definiera rätt antal paket.

#### Ordning för enhetspaket {#entity-packages-order}

För att underlätta importen bör entitetspaketen sorteras när de importeras. Exempel:
* 001 - Schema
* 002 - Formulär
* 003 - Bilder
* osv.

>[!NOTE]
>
>Forms bör endast importeras efter schemauppdateringar.

#### Package 200 {#package-200}

Paketnumret 200 ska inte användas för en viss kampanj: det här numret används för att uppdatera något som gäller alla kampanjer.

#### Uppdatera paket {#update-package}

Den sista punkten gäller uppdateringspaketnumreringen. Det är ditt paketnummer (enhet, funktion eller kampanj) med prefixet&quot;5&quot;. Exempel:
* 5001 för att uppdatera ett schema
* 5200 för att uppdatera alla kampanjer
* 5101 för att uppdatera funktionen 101

Uppdateringspaketet ska bara innehålla en specifik entitet för att vara enkelt att återanvända. Om du vill dela upp dem lägger du till ett nytt nummer (börja från 1). Det finns inga särskilda beställningsregler för dessa paket. Tänk dig att vi har en 101-funktion, en social tillämpning:
* Den innehåller en webApp och ett externt konto.
   * Paketetiketten är: 101 - Socialt program (socialApplication).
* Det finns en defekt i webApp.
   * The wepApp is correction.
   * Ett korrigeringspaket måste skapas med följande namn: 5101 - 1 - Webbapp för sociala program (socialApplication_webApp).
* Ett nytt externt konto måste läggas till för den sociala funktionen.
   * Ett externt konto skapas.
   * Det nya paketet är: 5101 - 2 - externt konto för sociala program (socialApplication_extAccount).
   * Parallellt uppdateras 101-paketet för att läggas till det externa kontot, men det distribueras inte.

     ![](assets/ncs_datapackage_best-practices-1.png)

#### Paketdokumentation {#package-documentation}

När du uppdaterar ett paket bör du alltid placera en kommentar i beskrivningsfältet för att beskriva eventuella ändringar och orsaker (till exempel&quot;lägg till ett nytt schema&quot; eller&quot;åtgärda ett fel&quot;).

![](assets/ncs_datapackage_best-practices-2.png)

Du bör också datera kommentaren. Rapportera alltid din kommentar om ett uppdateringspaket till det överordnade paketet (paket utan prefixet 5).

>[!IMPORTANT]
>
>Beskrivningsfältet får innehålla högst 2 000 tecken.
