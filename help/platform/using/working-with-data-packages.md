---
title: Arbeta med datapaket
seo-title: Arbeta med datapaket
description: Arbeta med datapaket
seo-description: null
page-status-flag: never-activated
uuid: 867b2702-dbc4-4b71-a385-a2c7fd09d25e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: administration-basics
discoiquuid: 42867665-d0ca-486e-9110-91716c0d5c57
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Arbeta med datapaket{#working-with-data-packages}

## Om datapaket {#about-data-packages}

Med Adobe Campaign kan ni exportera eller importera plattformskonfigurationen och data via ett paketsystem. Paket kan innehålla olika typer av konfigurationer, element, filtrerade eller inte.

Med datapaket kan enheter i Adobe Campaign-databasen visas med filer i XML-format. Varje entitet i ett paket representeras med alla dess data.

Principen med **datapaket** är att exportera en datakonfiguration och integrera den i ett annat Adobe Campaign-system. Mer information om hur du upprätthåller en enhetlig uppsättning datapaket finns i den här [tekniken](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/Technotes/AdobeCampaign_How_to_maintain_a_consistent_set_of_data_packages.pdf).

### Typ av paket {#types-of-packages}

Det finns tre typer av paket som kan exporteras: användarpaket, plattformspaket och administratörspaket.

* **Användarpaket**: gör att du kan välja en lista över enheter som ska exporteras. Den här typen av paket hanterar beroenden och verifierar fel.
* **Plattformspaket**: Den innehåller alla tillagda tekniska resurser (inte standard): scheman, JavaScript-kod osv.

   ![](assets/ncs_datapackage_package_platform.png)

* **Administratörspaket**: innehåller alla tillagda mallar och affärsobjekt (inte standard): mallar, bibliotek osv.

   ![](assets/ncs_datapackage_package_admin.png)

>[!CAUTION]
>
>Typerna **Plattform** och **Administratör** innehåller en fördefinierad lista över enheter som ska exporteras. Varje entitet är länkad till filtervillkor som gör att du kan ta bort de färdiga resurserna i det skapade paketet.

## Datastruktur {#data-structure}

Beskrivningen av ett datapaket är ett strukturerat XML-dokument som överensstämmer med grammatiken i **xrk:navtree** -dataschemat.

Exempel på datapaket:

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

XML-dokumentet måste börja och sluta med **`<package>`** -elementet. Alla **`<entities>`** element som följer distribuerar data efter dokumenttyp.

Ett **`<entities>`** element innehåller data från paketet i det format som datarammet som anges i **schemaattributet** .

Data i ett paket får inte innehålla interna nycklar som inte är kompatibla mellan baser, t.ex. autogenererade nycklar (**autopk** -alternativ).

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

* Med den här funktionen kan du **[!UICONTROL Package Export Wizard]** exportera en uppsättning objekt i ett enda paket. Mer information finns i [Exportera en uppsättning objekt i ett paket](#exporting-a-set-of-objects-in-a-package)
* Ett **enskilt objekt** kan exporteras direkt i ett paket genom att högerklicka på det och välja **[!UICONTROL Actions > Export in a package]**.
* **Med paketdefinitioner** kan du skapa en paketstruktur där du lägger till objekt som ska exporteras senare i ett paket. Mer information finns i [Hantera paketdefinitioner](#managing-package-definitions)

När ett paket har exporterats kan du importera det och alla tillagda enheter till en annan Campaign-instans.

### Exportera en uppsättning objekt i ett paket {#exporting-a-set-of-objects-in-a-package}

Guiden för paketexport är tillgänglig via **[!UICONTROL Tools > Advanced > Export package...]** menyn i Adobe Campaign-klientkonsolen.

![](assets/ncs_datapackage_typepackage.png)

För de tre typerna av paket innehåller guiden följande steg:

1. Lista de enheter som ska exporteras efter dokumenttyp:

   ![](assets/ncs_datapackage_export2.png)

   >[!CAUTION]
   >
   >Om du exporterar en **[!UICONTROL Offer category]**-, **[!UICONTROL Offer environment]****[!UICONTROL Program]** - eller **[!UICONTROL Plan]** typmapp ska du aldrig markera mappen **xtk:folder** eftersom du kan förlora vissa data. Välj den enhet som motsvarar mappen: nms: **offerCategory** för erbjudandekategorier, **nms:offerEnv** för erbjudandemiljöer, **nms:program** för program och **nms:plan** för planer.

   Med listhantering kan du lägga till eller ta bort enheter för export från konfigurationen. Klicka **[!UICONTROL Add]** för att välja en ny enhet.

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

1. Klicka på **[!UICONTROL Next]** och markera sorteringskolumnerna för att ordna data under extraheringen:

   ![](assets/ncs_datapackage_export5.png)

1. Förhandsgranska de data som ska extraheras innan du kör exporten.

   ![](assets/ncs_datapackage_export6.png)

1. På den sista sidan i guiden för paketexport kan du starta exporten. Data lagras i den fil som anges i **[!UICONTROL File]** fältet.

   ![](assets/ncs_datapackage_export7.png)

### Hantera beroenden {#managing-dependencies}

Exportmekanismen gör att Adobe Campaign kan spåra länkarna mellan de olika exporterade elementen.

Den här mekanismen definieras av två regler:

* objekt som är länkade till en länk med en **egen** eller **egen** textintegritet exporteras i samma paket som det exporterade objektet.
* objekt som är länkade till en länk med en **neutral** eller **definierad** textintegritet (definierad länk) måste exporteras separat.

>[!NOTE]
>
>Integritetstyper som är länkade till schemaelement definieras i [det här avsnittet](../../configuration/using/database-mapping.md#links--relation-between-tables).

#### Exportera en kampanj {#exporting-a-campaign}

Här är ett exempel på hur du exporterar en kampanj. Marknadsföringskampanjen som ska exporteras innehåller en aktivitet (etikett: &quot;MyTask&quot;) och ett arbetsflöde (etikett: &quot;CampaignWorkflow&quot;) i mappen &quot;MyWorkflow&quot; (nod: Administration / produktion / Tekniska arbetsflöden / Kampanjprocesser / MittArbetsflöde).

Uppgiften och arbetsflödet exporteras i samma paket som kampanjen eftersom matchande scheman kopplas samman med länkar med en egen typ av integritet.

Paketinnehåll:

```
<?xml version='1.0'?>
<package author="Administrator (admin)" buildNumber="7974" buildVersion="6.1" img=""
label="" name="" namespace="" vendor="">
 <desc></desc>
 <version buildDate="2013-01-09 10:30:18.954Z"/>
 <entities schema="nms:operation">
  <operation duration="432000" end="2013-01-14" internalName="OP1" label="MyCampaign"
  modelName="opEmpty" start="2013-01-09">
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
   <task end="2013-01-17 10:07:51.000Z" label="MyTask" name="TSK2" start="2013-01-16 10:07:51.000Z"
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

Anslutning till en typ av paket definieras i ett schema med attributen **@pkgAdmin och @pkgPlatform** . Båda dessa attribut får ett XTK-uttryck som definierar villkoren för anslutning till paketet.

```
<element name="offerEnv" img="nms:offerEnv.png" 
template="xtk:folder" pkgAdmin="@id != 0">
```

Slutligen kan du med **@pkgStatus** -attributet definiera exportreglerna för dessa element eller attribut. Beroende på attributets värde finns elementet eller attributet i det exporterade paketet. De tre möjliga värdena för det här attributet är:

* **aldrig**: exporterar inte fältet/länken
* **always**: tvingar export för det här fältet
* **preCreate**: tillåter skapande av den länkade entiteten

>[!NOTE]
>
>Värdet **preCreate** tillåts bara för länktypshändelser. Du kan skapa eller peka mot en enhet som ännu inte har lästs in i det exporterade paketet.

## Hantera paketdefinitioner {#managing-package-definitions}

### Om paketdefinitioner {#about-package-definitions}

Med paketdefinitioner kan du skapa en paketstruktur där du lägger till entiteter som ska exporteras senare i ett paket. Du kan sedan importera det här paketet och alla tillagda enheter till en annan Campaign-instans.

**Relaterade ämnen:**

* [Skapa en paketdefinition](#creating-a-package-definition)
* [Lägga till enheter i en paketdefinition](#adding-entities-to-a-package-definition)
* [Konfigurera generering av paketdefinitioner](#configuring-package-definitions-generation)
* [Exportera paket från en paketdefinition](#exporting-packages-from-a-package-definition)

### Skapa en paketdefinition {#creating-a-package-definition}

Du kommer åt paketdefinitioner på **[!UICONTROL Administration > Configuration > Package management > Package definitions]** menyn.

Om du vill skapa en paketdefinition klickar du på **[!UICONTROL New]** knappen och fyller sedan i den allmänna paketdefinitionsinformationen.

![](assets/packagedefinition_create.png)

Du kan sedan lägga till enheter i paketdefinitionen och exportera den till ett XML-filpaket.

**Relaterade ämnen:**

* [Lägga till enheter i en paketdefinition](#adding-entities-to-a-package-definition)
* [Konfigurera generering av paketdefinitioner](#configuring-package-definitions-generation)
* [Exportera paket från en paketdefinition](#exporting-packages-from-a-package-definition)

### Lägga till enheter i en paketdefinition {#adding-entities-to-a-package-definition}

Klicka på **[!UICONTROL Content]** knappen på fliken **[!UICONTROL Add]** för att markera de enheter som ska exporteras med paketet. De bästa sätten att välja enheter visas i avsnittet [Exportera en uppsättning objekt i ett paketavsnitt](#exporting-a-set-of-objects-in-a-package) .

![](assets/packagedefinition_addentities.png)

Enheter kan läggas till i en paketdefinition direkt från sin plats i instansen. Gör så här:

1. Högerklicka på önskad enhet och välj sedan **[!UICONTROL Actions > Export in a package]**.

   ![](assets/packagedefinition_singleentity.png)

1. Markera **[!UICONTROL Add to a package definition]** och välj sedan den paketdefinition som du vill lägga till enheten i.

   ![](assets/packagedefinition_packageselection.png)

1. Entiteten läggs till i paketdefinitionen, den exporteras med paketet (se [Exportera paket från en paketdefinition](#exporting-packages-from-a-package-definition)).

   ![](assets/packagedefinition_entityadded.png)

### Konfigurera generering av paketdefinitioner {#configuring-package-definitions-generation}

Paketgenerering kan konfigureras på **[!UICONTROL Content]** fliken Paketdefinition. Klicka på **[!UICONTROL Generation parameters]** länken om du vill göra det.

![](assets/packagedefinition_generationparameters.png)

* **[!UICONTROL Include the definition]**: innehåller den definition som för närvarande används i paketdefinitionen.
* **[!UICONTROL Include an installation script]**: I kan du lägga till ett javascript-skript som ska köras vid paketimporten. När du väljer det här alternativet läggs en **[!UICONTROL Script]** flik till på paketdefinitionsskärmen.
* **[!UICONTROL Include default values]**: lägger till värdena för alla entiteters attribut i paketet.

   Det här alternativet är inte markerat som standard för att undvika långa exporter. Det innebär att entiteternas attribut med standardvärden (tom sträng, 0 och false om de inte definieras på annat sätt i schemat) inte läggs till i paketet och därför inte exporteras.

   >[!CAUTION]
   >
   >Om du avmarkerar det här alternativet kan lokala och importerade versioner sammanfogas.
   >
   >Om instansen som paketet importeras till innehåller entiteter som är identiska med de i paketet (till exempel med samma externa ID) uppdateras inte deras attribut. Detta kan inträffa om attributen från den tidigare instansen har standardvärden eftersom de inte ingår i paketet.
   >
   >Om du väljer det här alternativet **[!UICONTROL Include default values]** förhindrar du att versionerna sammanfogas, eftersom alla attribut från den tidigare instansen exporteras med paketet.

### Exportera paket från en paketdefinition {#exporting-packages-from-a-package-definition}

Om du vill exportera ett paket från en paketdefinition följer du stegen nedan:

1. Markera den paketdefinition som ska exporteras, klicka sedan på **[!UICONTROL Actions]** -knappen och välj **[!UICONTROL Export the package]**.
1. En XML-fil som motsvarar det exporterade paketet markeras som standard. Det namnges enligt paketdefinitionens namnutrymme och namn.
1. När paketnamnet och platsen har definierats klickar du på **[!UICONTROL Start]** knappen för att starta exporten.

   ![](assets/packagedefinition_packageexport.png)

## Importera paket {#importing-packages}

### Om paketimport {#about-package-import}

Guiden för paketimport är tillgänglig via huvudmenyn **[!UICONTROL Tools > Advanced > Package import...]** i Adobe Campaign-klientkonsolen.

Du kan importera ett paket från en tidigare export, t.ex. från en annan Adobe Campaign-instans eller ett standardpaket, beroende på villkoren i licensen.

![](assets/ncs_datapackage_import.png)

### Installera ett paket från en fil {#installing-a-package-from-a-file}

Om du vill importera ett befintligt datapaket markerar du XML-filen och klickar på **[!UICONTROL Open]**.

![](assets/ncs_datapackage_import_1.png)

Innehållet i det paket som ska importeras visas sedan i mitten av redigeraren.

Klicka på **[!UICONTROL Next]** och **[!UICONTROL Start]** starta importen.

![](assets/ncs_datapackage_import_2.png)

### Installera ett standardpaket {#installing-a-standard-package}

Standardpaket installeras när Adobe Campaign konfigureras. Beroende på din behörighet och distributionsmodell kan du importera nya standardpaket om du skaffar nya alternativ eller tillägg, eller om du uppgraderar till ett nytt erbjudande.

Se licensavtalet för att se vilka paket du kan installera.

Mer information om standardpaket finns på [den här sidan](../../installation/using/installing-campaign-standard-packages.md).
