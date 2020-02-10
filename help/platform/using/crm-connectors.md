---
title: CRM Connectors
seo-title: CRM Connectors
description: CRM Connectors
seo-description: null
page-status-flag: never-activated
uuid: ef3d88a1-b0fd-4790-b6e8-63fa339ef991
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dbe9080c-66e3-4ff6-8f16-959f9748f666
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# CRM Connectors{#crm-connectors}

## Om CRM-anslutningar {#about-crm-connectors}

Adobe Campaign innehåller olika CRM-anslutningar för att länka din Adobe Campaign-plattform till dina tredjepartssystem. Med dessa CRM-anslutningar kan du synkronisera kontakter, konton, inköp osv. De gör att du enkelt kan integrera ditt program med olika tredjeparts- och affärsprogram.

Dessa kopplingar möjliggör snabb och enkel dataintegrering: I Adobe Campaign finns en dedikerad guide för att samla in och välja bland tabellerna som finns i CRM. Detta garanterar dubbelriktad synkronisering för att säkerställa att data alltid är aktuella i alla system.

>[!NOTE]
>
>Den här funktionen är tillgänglig i Adobe Campaign via det dedikerade paketet med **CRM-anslutningar** .

Anslutningen till CRM sker via dedikerade arbetsflödesaktiviteter. Dessa aktiviteter beskrivs närmare i kapitlet i [detta avsnitt](../../workflow/using/crm-connector.md).

### Kompatibla CRM-system och -begränsningar {#compatible-crm-systems-and-limitations}

CRM:er som anges nedan kan integreras i Adobe Campaign.

Versioner som stöds finns i [kompatibilitetsmatrisen](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html).

* **Salesforce.com**

   Läs [det här avsnittet](#example-for-salesforce-com) för att lära dig hur du konfigurerar anslutningen med Salesforce.com.

   >[!CAUTION]
   >
   >När du ansluter Adobe Campaign till Salesforce.com är begränsningarna:
   >
   >    
   >    
   >    * Testproduktionsinstanser stöds.
   >    * Tilldelningsregler stöds.
   >    * Uppräkningar av flera markeringar stöds inte av Adobe Campaign.


* **Oracle On Demand**

   Läs [det här avsnittet](#example-for-oracle-on-demand) för att lära dig hur du konfigurerar anslutningen med Oracle On Demand.

   >[!CAUTION]
   >
   >När du ansluter Adobe Campaign till Oracle On Demand finns följande begränsningar:
   >
   >    
   >    
   >    * Adobe Campaign kan synkronisera alla objekt som finns i Oracle On Demand-standardmallarna. Om du har lagt till anpassade tabeller i Oracle On Demand, kommer de inte att återställas i Adobe Campaign.
   >    * Med API-version v1.0 kan du sortera eller filtrera data under en fråga, men du kan inte göra båda samtidigt.
   >    * Datumen som skickas av Oracle On Demand innehåller ingen tidszonsinformation.
   >    * Uppräkningar av flera markeringar stöds inte av Adobe Campaign.


* **MS Dynamics CRM** och **MS Dynamics Online**

   Läs [det här avsnittet](#example-for-microsoft-dynamics) för att lära dig hur du konfigurerar anslutningen med Microsoft Dynamics.

   Läs mer om hur integreringen mellan Adobe Campaign och Microsoft Dynamics fungerar i [den här videon](https://helpx.adobe.com/campaign/kt/acc/using/acc-integrate-dynamics365-with-acc-feature-video-set-up.html).

   >[!CAUTION]
   >
   >När du ansluter Adobe Campaign till Microsoft Dynamics är begränsningarna:
   >
   >    
   >    
   >    * Att installera plugin-program kan ändra CRM-beteendet, vilket kan leda till kompatibilitetsproblem med Adobe Campaign.
   >    * Uppräkningar av flera markeringar stöds inte av Adobe Campaign.


## Konfigurera anslutningen {#setting-up-the-connection}

Gör så här om du vill använda CRM-anslutningar i Adobe Campaign:

1. Skapa det externa kontot
1. Samla CRM-tabellerna
1. Synkronisera uppräkningar
1. Skapa synkroniseringsarbetsflödet

>[!NOTE]
>
>CRM-anslutningarna fungerar bara med en säker URL (https).

### Exempel på Salesforce.com {#example-for-salesforce-com}

Följ stegen nedan för att konfigurera **Salesforce.com** -anslutningen med Adobe Campaign:

1. Skapa ett nytt externt konto via noden **[!UICONTROL Administration > Platform > External accounts]** i Adobe Campaign-trädet.
1. Kör konfigurationsguiden för att generera tillgängliga CRM-tabeller.

   ![](assets/crm_connectors_sfdc_wz.png)

   Med konfigurationsguiden kan du samla in tabeller och skapa det matchande schemat.

   Klicka **[!UICONTROL Start]** för att köra körningen.

   ![](assets/crm_connectors_sfdc_launch.png)

   >[!NOTE]
   >
   >För att godkänna konfigurationen måste du logga ut och sedan logga in på Adobe Campaign-konsolen igen.

1. Kontrollera schemat som genererats i Adobe Campaign i **[!UICONTROL Administration > Configuration > Data schemas]** noden.

   ![](assets/crm_connectors_sfdc_table.png)

1. När schemat har skapats kan du synkronisera uppräkningar automatiskt via CRM till Adobe Campaign.

   Det gör du genom att klicka på **[!UICONTROL Synchronizing enumerations...]** länken och välja den Adobe Campaign-uppräkning som matchar CRM-uppräkningen.

   Du kan ersätta alla värden i en Adobe Campaign-uppräkning med dem i CRM: om du vill göra det markerar du **[!UICONTROL Yes]** i **[!UICONTROL Replace]** kolumnen.

   ![](assets/crm_connectors_sfdc_enum.png)

   Klicka på **[!UICONTROL Next]** och sedan **[!UICONTROL Start]** för att börja importera listan.

1. Kontrollera de importerade värdena på **[!UICONTROL Administration > Platform > Enumerations]** menyn.

   ![](assets/crm_connectors_sfdc_exe.png)

1. Om du vill importera Salesforce-data eller exportera Adobe Campaign-data till Salesforce måste du skapa ett arbetsflöde och använda **[!UICONTROL CRM connector]** aktiviteten.

   ![](assets/crm_connectors_sfdc_wf.png)

### Exempel på Oracle On Demand {#example-for-oracle-on-demand}

Så här konfigurerar du **Oracle On Demand** -kontakten så att den fungerar med Adobe Campaign:

1. Skapa ett nytt externt konto via noden **[!UICONTROL Administration > Platform > External accounts]** i Adobe Campaign-trädet.

   ![](assets/crm_connectors_ood_1.png)

1. Öppna konfigurationsguiden: Adobe Campaign visar automatiskt tabellerna för Oracles datamodell. Markera de tabeller som du vill samla in.

   ![](assets/crm_connectors_ood_2.png)

1. Klicka **[!UICONTROL Next]** för att börja skapa det matchande schemat.

   Det matchande dataschemat blir tillgängligt i Adobe Campaign.

   ![](assets/crm_connectors_ood_3.png)

1. Starta synkronisering av uppräkningar mellan Adobe Campaign och Oracle On Demand.

   ![](assets/crm_connectors_ood_4.png)

1. Om du vill importera Oracle On Demand-data till Adobe Campaign skapar du följande typ av arbetsflöde:

   ![](assets/crm_connectors_ood_5.png)

   Det här arbetsflödet importerar kontakter via Oracle On Demand, synkroniserar dem med befintliga Adobe Campaign-data, tar bort dubblettkontakter och uppdaterar Adobe Campaign-databasen.

   Aktiviteten måste **[!UICONTROL CRM Connector]** konfigureras enligt följande:

   ![](assets/crm_connectors_ood_6.png)

1. Om du vill exportera Adobe Campaign-data till Oracle On Demand skapar du följande arbetsflöde:

   ![](assets/crm_connectors_ood_7.png)

   Det här arbetsflödet samlar in relevanta data med hjälp av frågor och exporterar dem sedan till kontakttabellen för Oracle On Demand.

### Exempel för Microsoft Dynamics {#example-for-microsoft-dynamics}

Så här konfigurerar du Microsoft Dynamics-anslutningen så att den fungerar med Adobe Campaign:

1. Skapa ett nytt externt konto via noden **[!UICONTROL Administration > Platform > External accounts]** i Adobe Campaign-trädet.

   ![](assets/crm_connectors_msdynamics_01_4.png)

1. Välj **distributionstyp**: **[!UICONTROL On-premise]**, **[!UICONTROL Office 365]** eller **[!UICONTROL Web API]**, beroende på vilken koppling du vill konfigurera.

   Adobe Campaign Classic stöder Dynamics 365 REST-gränssnittet med OAuth-protokollet för autentisering.

   Om du väljer en **[!UICONTROL WebAPI]** distribution måste du registrera en app i Azure Directory och hämta **clientId** från Azure-katalogen. Registreringen finns på [den här sidan](https://msdn.microsoft.com/en-us/library/mt622431.aspx).

   >[!NOTE]
   >
   >Parametern redirectURL krävs inte av Adobe Campaign Classic.

   Värdet för **clientId** används med användarnamnet/lösenordet för att hämta innehavartoken med hjälp av lösenord för anslagstyp. Detta kallas **Resursägarens lösenordsbeviljande**. Mer information finns på [den här sidan](https://blogs.msdn.microsoft.com/wushuai/2016/09/25/resource-owner-password-credentials-grant-in-azure-ad-oauth/).

   ![](assets/crm_connectors_msdynamics_01_3.png)

   Mer information om kompatibilitet för CRM-versioner finns i [kompatibilitetsmatrisen](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html).

1. Öppna konfigurationsguiden. Adobe Campaign identifierar automatiskt tabellerna från datamallen i Microsoft Dynamics.

   ![](assets/crm_connectors_msdynamics_02.png)

   Markera de tabeller som ska återställas.

   ![](assets/crm_connectors_msdynamics_03.png)

1. Klicka **[!UICONTROL Next]** och börja skapa motsvarande schema.

   ![](assets/crm_connectors_msdynamics_04.png)

   >[!NOTE]
   >
   >Om du vill godkänna konfigurationen måste du koppla från/återansluta till Adobe Campaign-konsolen.

   Det matchande dataschemat blir tillgängligt i Adobe Campaign.

   ![](assets/crm_connectors_msdynamics_05.png)

1. Starta synkronisering av uppräkningar mellan Adobe Campaign och Microsoft Dynamics.

   ![](assets/crm_connectors_msdynamics_06.png)

1. Om du vill importera Microsoft Dynamics-data till Adobe Campaign skapar du följande typ av arbetsflöde:

   ![](assets/crm_connectors_msdynamics_07.png)

   Det här arbetsflödet importerar kontakterna via Microsoft Dynamics, synkroniserar dem med befintliga Adobe Campaign-data, tar bort dubblettkontakter och uppdaterar Adobe Campaign-databasen.

   Aktiviteten måste **[!UICONTROL CRM Connector]** konfigureras enligt nedan:

   ![](assets/crm_connectors_msdynamics_08.png)

## Datasynkronisering {#data-synchronization}

Synkroniseringen mellan Adobe Campaign och CRM utförs via en dedikerad arbetsflödesaktivitet: [CRM-koppling](../../workflow/using/crm-connector.md).

Med den här aktiviteten kan du:

* Importera från CRM (se [Importera från CRM](#importing-from-the-crm)),
* Exportera till CRM (se [Exportera till CRM](#exporting-to-the-crm)).
* Importera objekt som tagits bort i CRM (se [Importera objekt som tagits bort i CRM](#importing-objects-deleted-in-the-crm)),
* Ta bort objekt i CRM (se [Ta bort objekt i CRM](#deleting-objects-in-the-crm)).

![](assets/crm_task_select_op.png)

Välj det externa konto som matchar det CRM-konto som du vill konfigurera synkronisering med och välj sedan det objekt som ska synkroniseras (konton, affärsmöjligheter, leads, kontakter osv.).

![](assets/crm_task_select_obj.png)

Aktivitetens konfiguration beror på vilken process som ska utföras. Olika konfigurationer beskrivs nedan.

### Importera från CRM {#importing-from-the-crm}

Om du vill importera data via CRM i Adobe Campaign måste du skapa följande arbetsflöde:

![](assets/crm_wf_import.png)

Konfigurationsstegen för en import-aktivitet i **CRM Connector** är:

1. Välj en **[!UICONTROL Import from the CRM]** åtgärd.
1. Gå till den **[!UICONTROL Remote object]** nedrullningsbara listan och markera objektet som berörs av processen. Det här objektet sammanfaller med en av tabellerna som skapades i Adobe Campaign under konfigurationen av kopplingen.
1. Gå till **[!UICONTROL Remote fields]** avsnittet och ange fälten som ska importeras.

   Om du vill lägga till ett fält klickar du på **[!UICONTROL Add]** knappen i verktygsfältet och sedan på **[!UICONTROL Edit expression]** ikonen .

   ![](assets/crm_task_import_add_field.png)

   Om det behövs ändrar du dataformatet via listrutan för **[!UICONTROL Conversion]** kolumnerna. Möjliga konverteringstyper beskrivs i [dataformat](#data-format).

   >[!CAUTION]
   >
   >Identifieraren för posten i CRM är obligatorisk för att länka objekt i CRM och i Adobe Campaign. Den läggs till automatiskt när förpackningen godkänns.
   >
   >Det sista ändringsdatumet på CRM-sidan är också obligatoriskt för inkrementell dataimport.

1. Du kan även filtrera data som ska importeras efter dina behov. Klicka på **[!UICONTROL Edit the filter...]** länken om du vill göra det.

   I följande exempel kommer Adobe Campaign endast att importera kontakter för vilka viss aktivitet har registrerats sedan 1 november 2012.

   ![](assets/crm_task_import_filter.png)

   >[!CAUTION]
   >
   >Begränsningarna som är kopplade till datafiltreringslägen beskrivs i [Filtrera data](#filtering-data).

1. Med det här **[!UICONTROL Use automatic index...]** alternativet kan du automatiskt hantera inkrementell objektsynkronisering mellan CRM och Adobe Campaign, beroende på datum och senaste ändring.

   Mer information finns i [Variabelhantering](#variable-management).

#### Variabelhantering {#variable-management}

Om du aktiverar **[!UICONTROL Automatic index]** alternativet kan du bara samla in objekt som har ändrats sedan den senaste importen.

![](assets/crm_task_import_option.png)

Datumet för den senaste synkroniseringen lagras som standard i ett alternativ som anges i konfigurationsfönstret: **LASTIMPORT_&lt;%=instance.internalName%>_&lt;%=activityName%>**.

>[!NOTE]
>
>Denna anmärkning gäller endast den allmänna **[!UICONTROL CRM Connector]** aktiviteten. För andra CRM-aktiviteter är processen automatisk.
>
>Det här alternativet måste skapas manuellt och fyllas i under **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]**. Det måste vara ett textalternativ och dess värde måste matcha följande format: **yyyy/MM/dd hh:mm:ss**.
> 
>Du måste uppdatera det här alternativet manuellt för ytterligare import.

Du kan ange vilket CRM-fjärrfält som ska beaktas för att identifiera de senaste ändringarna.

Som standard används följande fält (i den angivna ordningen):

* För Microsoft Dynamics: **modifiedon**,
* För Oracle On Demand: **LastUpdated**, **ModifiedDate**, **LastLoggedIn**,
* För Salesforce.com: **LastModifiedDate**, **SystemModstamp**.

När du aktiverar **[!UICONTROL Automatic index]** alternativet genereras tre variabler som kan användas i synkroniseringsarbetsflödet via en **[!UICONTROL JavaScript code]** typaktivitet. Dessa verksamheter är följande:

* **vars.crmOptionName**: representerar namnet på alternativet som innehåller det senaste importdatumet.
* **vars.crmStartImport**: representerar startdatumet (inkluderat) för den senaste dataåterställningen.
* **vars.crmEndDate**: representerar slutdatumet (exkluderat) för den senaste dataåterställningen.

   >[!NOTE]
   >
   >Dessa datum visas i följande format: **yyyy/MM/dd hh:mm:ss**.

#### Filtrera data {#filtering-data}

För att de olika CRM-systemen ska fungera effektivt måste du skapa filter enligt följande regler:

* Varje filtreringsnivå får endast använda en typ av operator.
* Operatorn AND NOT stöds inte.
* Jämförelser kan bara gälla null-värden (&#39;är tom&#39;/&#39;är inte tom&#39;) eller tal. Detta innebär att värdet (högerkolumnen) bedöms och att resultatet av denna bedömning måste vara ett tal. JOBIN-typjämförelser stöds därför inte.
* Värdet i den högra kolumnen utvärderas i JavaScript.
* JOIN-jämförelser stöds inte.
* Uttrycket i den vänstra kolumnen måste vara ett fält. Det kan inte vara en kombination av flera uttryck, ett tal osv.

Följande filtreringsvillkor gäller till exempel INTE för en CRM-import eftersom OR-operatorn är placerad på samma nivå som AND-operatorerna:

* Operatorn OR placeras på samma nivå som operatorn AND
* Jämförelser görs av textsträngar.

![](assets/crm_import_wrong_filter.png)

#### Beställ av {#order-by}

I Microsoft Dynamics och Salesforce.com kan du sortera de fjärrfält som ska importeras i stigande eller fallande ordning.

Det gör du genom att klicka på **[!UICONTROL Order by]** länken och lägga till kolumnerna i listan.

Sorteringsordningen för kolumnerna i listan är:

![](assets/crm_import_order.png)

#### Registrerings-ID {#record-identification}

I stället för att importera element som ingår (och eventuellt filtreras) i CRM kan du använda en population som beräknas i förväg i arbetsflödet.

Det gör du genom att markera **[!UICONTROL Use the population calculated upstream]** alternativet och ange fältet som innehåller fjärr-ID:t.

Markera sedan fälten för den inkommande ifyllning som du vill importera, så som visas nedan:

![](assets/crm_wf_import_calculated_population.png)

### Exportera till CRM {#exporting-to-the-crm}

Genom att exportera Adobe Campaign-data till CRM kan du kopiera hela innehållet till en CRM-databas.

Om du vill exportera data till CRM måste du skapa följande arbetsflöde:

![](assets/crm_export_diagram.png)

För en export använder du följande konfiguration för aktiviteten **CRM Connector** :

1. Välj en **[!UICONTROL Export to CRM]** åtgärd.
1. Gå till den **[!UICONTROL Remote object]** nedrullningsbara listan och markera objektet som berörs av processen. Det här objektet sammanfaller med en av tabellerna som skapades i Adobe Campaign under konfigurationen av kopplingen.

   >[!CAUTION]
   >
   >Exportfunktionen för aktiviteten **CRM Connectors** kan infoga eller uppdatera fält på CRM-sidan. Om du vill aktivera fältuppdateringar i CRM måste du ange fjärrtabellens primärnyckel. Om nyckeln saknas infogas data (i stället för att uppdateras).

1. I **[!UICONTROL Mapping]** avsnittet anger du fälten som ska exporteras och deras mappning i CRM.

   ![](assets/crm_export_config.png)

   Om du vill lägga till ett fält klickar du på **[!UICONTROL Add]** knappen i verktygsfältet och sedan på **[!UICONTROL Edit expression]** ikonen .

   >[!NOTE]
   >
   >Om ingen matchning har definierats på CRM-sidan för ett givet fält kan värdena inte uppdateras: De infogas direkt i CRM.

   Om det behövs ändrar du dataformatet via listrutan för **[!UICONTROL Conversion]** kolumnerna. Möjliga konverteringstyper beskrivs i [dataformat](#data-format).

   >[!NOTE]
   >
   >Listan med poster som ska exporteras och resultatet av exporten sparas i en temporär fil som är tillgänglig tills arbetsflödet har slutförts eller startats om. Detta gör att du kan starta processen igen om fel uppstår utan att du riskerar att exportera samma post flera gånger eller förlora data.

### Ytterligare konfigurationer {#additional-configurations}

#### Dataformat {#data-format}

Du kan konvertera dataformat direkt när du importerar dem till eller från CRM.

Det gör du genom att välja den konvertering som ska användas i den matchande kolumnen.

![](assets/crm_task_import.png)

I **[!UICONTROL Default]** läget används automatisk datakonvertering, som i de flesta fall motsvarar en kopia/inklistring av data. Tidszonshantering används dock.

Andra konverteringar är:

* **[!UICONTROL Date only]**: I det här läget tas datum- och tidstypsfält bort.
* **[!UICONTROL Without time offset]**: I det här läget avbryts den tidszonshantering som används i standardläget.
* **[!UICONTROL Copy/Paste]**: I det här läget används rådata som strängar (ingen konvertering).

#### Felbearbetning {#error-processing}

Inom ramen för import och export av data kan du tillämpa en specifik process på fel och avslag. Det gör du genom att markera alternativen **[!UICONTROL Process rejects]** och **[!UICONTROL Process errors]** på **[!UICONTROL Behavior]** fliken.

![](assets/crm_export_options.png)

Dessa alternativ placerar de matchande utdataövergångarna.

![](assets/crm_export_transitions.png)

Placera sedan de aktiviteter som är relevanta för de processer du vill tillämpa.

Om du till exempel vill behandla fel kan du lägga till en vänteruta och schemalägga nya försök.

Avvisade registreras med sin felkod och det relaterade meddelandet, vilket innebär att du kan ställa in spårning av avvisade för att optimera synkroniseringsprocessen.

>[!NOTE]
>
>Även om **[!UICONTROL Process rejects]** alternativet inte är aktiverat genereras en varning för varje avvisad kolumn med en felkod och ett meddelande.

Med **[!UICONTROL Reject]** utdataövergången kan du komma åt utdataschemat som innehåller de specifika kolumner som är relevanta för felmeddelanden och koder. Följande kolumner är:

* För Oracle On Demand: errorLogFilename **(** loggfilens namn på Oracle-sidan), **errorCode** (felkod), **errorSymbol** (felsymbol, som inte är felkoden), **errorMessage** (beskrivning av felkontexten).
* För Salesforce.com: **errorSymbol** (felsymbol, skiljer sig från felkoden), **errorMessage** (beskrivning av felkontexten).

### Importera objekt som tagits bort i CRM {#importing-objects-deleted-in-the-crm}

Om du vill kunna konfigurera en omfattande datasynkroniseringsprocess kan du importera objekt som tagits bort i CRM till Adobe Campaign.

Gör så här:

1. Välj en **[!UICONTROL Import objects deleted in the CRM]** åtgärd.
1. Gå till den **[!UICONTROL Remote object]** nedrullningsbara listan och markera objektet som berörs av processen. Det här objektet sammanfaller med en av tabellerna som skapades i Adobe Campaign under konfigurationen av kopplingen.
1. Ange den borttagningsperiod som ska beaktas i **[!UICONTROL Start date]** och i **[!UICONTROL End date]** fälten. Dessa datum inkluderas i perioden.

   ![](assets/crm_import_deleted_obj.png)

   >[!CAUTION]
   >
   >Elementets raderingsperiod måste sammanfalla med de begränsningar som är specifika för CRM. Det innebär att för Salesforce.com kan element som togs bort för över 30 dagar sedan inte återställas.

### Ta bort objekt i CRM {#deleting-objects-in-the-crm}

Om du vill ta bort objekt på CRM-sidan måste du ange primärnyckeln för de fjärrelement som ska tas bort.

![](assets/crm_delete_in_crm.png)

På fliken **[!UICONTROL Behavior]** kan du aktivera bearbetning av avvisade. Det här alternativet genererar en andra utdataövergång för **[!UICONTROL CRM connector]** aktiviteten. Mer information finns i [Felbearbetning](#error-processing).

>[!NOTE]
>
>Även när **[!UICONTROL Process rejects]** alternativet är inaktiverat genereras en varning för varje avvisad kolumn.

