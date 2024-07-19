---
product: campaign
title: CRM Connectors-datasynkronisering
description: Hantera data mellan Campaign och CRM
feature: Microsoft CRM Integration, Salesforce Integration
exl-id: 7f9eda15-76e8-40a1-8302-004cea085778
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1529'
ht-degree: 0%

---

# Synkronisera data mellan Campaign och CRM {#data-synchronization}



Datasynkronisering mellan Adobe Campaign och CRM utförs via en dedikerad arbetsflödesaktivitet: [CRM-koppling](../../workflow/using/crm-connector.md).

Om du till exempel vill importera Microsoft Dynamics-data till Adobe Campaign skapar du följande arbetsflöde:

![](assets/crm_connectors_msdynamics_07.png)

Det här arbetsflödet importerar kontakterna via Microsoft Dynamics, synkroniserar dem med befintliga Adobe Campaign-data, tar bort dubblettkontakter och uppdaterar Adobe Campaign-databasen.

Aktiviteten **[!UICONTROL CRM Connector]** måste konfigureras för att synkronisera data.

![](assets/crm_connectors_msdynamics_08.png)

Med den här aktiviteten kan du

* Importera från CRM - [Läs mer](#importing-from-the-crm)
* Exportera till CRM - [Läs mer](#exporting-to-the-crm)
* Importera objekt som tagits bort i CRM - [Läs mer](#importing-objects-deleted-in-the-crm)
* Ta bort objekt i CRM - [Läs mer](#deleting-objects-in-the-crm)

![](assets/crm_task_select_op.png)

Välj det externa konto som matchar det CRM-konto som du vill konfigurera synkronisering med och välj sedan det objekt som ska synkroniseras: konton, affärsmöjligheter, leads, kontakter osv.

![](assets/crm_task_select_obj.png)

Aktivitetens konfiguration beror på vilken process som ska utföras. Olika konfigurationer beskrivs nedan.

## Importera från CRM {#importing-from-the-crm}

Om du vill importera data via CRM i Adobe Campaign måste du skapa följande arbetsflöde:

![](assets/crm_wf_import.png)

För en importaktivitet är stegen för aktivitetskonfigurationen **[!UICONTROL CRM Connector]**:

1. Välj en **[!UICONTROL Import from the CRM]**-åtgärd.
1. Gå till listrutan **[!UICONTROL Remote object]** och markera objektet som berörs av processen. Det här objektet sammanfaller med en av tabellerna som skapas i Adobe Campaign under anslutningskonfigurationen.
1. Gå till avsnittet **[!UICONTROL Remote fields]** och ange fälten som ska importeras.

   Om du vill lägga till ett fält klickar du på knappen **[!UICONTROL Add]** i verktygsfältet och sedan på ikonen **[!UICONTROL Edit expression]** .

   ![](assets/crm_task_import_add_field.png)

   Om det behövs ändrar du dataformatet via listrutan för kolumnerna **[!UICONTROL Conversion]**. Möjliga konverteringstyper beskrivs i [Dataformat](#data-format).

   >[!IMPORTANT]
   >
   >Identifieraren för posten i CRM är obligatorisk för att länka objekt i CRM och Adobe Campaign. Den läggs till automatiskt när lådan är godkänd.
   >
   >Det sista ändringsdatumet på CRM-sidan är också obligatoriskt för inkrementell dataimport.

1. Du kan även filtrera data som ska importeras efter dina behov. Klicka på länken **[!UICONTROL Edit the filter...]** om du vill göra det.

   I följande exempel kommer Adobe Campaign endast att importera kontakter för vilka viss aktivitet har registrerats sedan 1 november 2012.

   ![](assets/crm_task_import_filter.png)

   >[!IMPORTANT]
   >
   >Begränsningarna som är kopplade till datafiltreringslägen beskrivs i [Filtrera data](#filtering-data).

1. Med alternativet **[!UICONTROL Use automatic index...]** kan du automatiskt hantera inkrementell objektsynkronisering mellan CRM och Adobe Campaign, beroende på datum och senaste ändring.

   Mer information finns i [Variabelhantering](#variable-management).

### Hantera variabler {#variable-management}

Aktivera alternativet **[!UICONTROL Automatic index]** om du bara vill samla in objekt som har ändrats sedan den senaste importen.

![](assets/crm_task_import_option.png)

Datumet för den senaste synkroniseringen lagras som standard i ett alternativ som anges i konfigurationsfönstret: **LASTIMPORT_&lt;%=instance.internalName%>_&lt;%=activityName%>**.

>[!NOTE]
>
>Den här anteckningen gäller bara för den generiska **[!UICONTROL CRM Connector]**-aktiviteten. För andra CRM-aktiviteter är processen automatisk.
>
>Det här alternativet måste skapas och fyllas i manuellt under **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]**. Det måste vara ett textalternativ och dess värde måste matcha följande format: **`yyyy/MM/dd hh:mm:ss`**.
> 
>Du måste uppdatera det här alternativet manuellt för ytterligare import.

Du kan ange vilket fjärr-CRM-fält som ska beaktas för att identifiera de senaste ändringarna.

Som standard används följande fält (i den angivna ordningen):

* För Microsoft Dynamics: **modifiedon**,
* För Salesforce.com: **LastModifiedDate**, **SystemModstamp**.

När du aktiverar alternativet **[!UICONTROL Automatic index]** genereras tre variabler som kan användas i synkroniseringsarbetsflödet via en **[!UICONTROL JavaScript code]**-typaktivitet. Dessa verksamheter är följande:

* **vars.crmOptionName**: representerar namnet på alternativet som innehåller det senaste importdatumet.
* **vars.crmStartImport**: representerar startdatumet (inkluderat) för den senaste dataåterställningen.
* **vars.crmEndDate**: representerar slutdatumet (exkluderat) för den senaste dataåterställningen.

  >[!NOTE]
  >
  >Dessa datum visas i följande format: **`yyyy/MM/dd hh:mm:ss`**.

### Filtrera data {#filtering-data}

För att de olika CRM-systemen ska fungera effektivt måste du skapa filter enligt följande regler:

* För varje filtreringsnivå får endast en typ av operator användas.
* Operatorn AND NOT stöds inte.
* Jämförelser kan bara gälla null-värden (&#39;är tom&#39;/&#39;är inte tom&#39;) eller tal. Detta innebär att värdet (högerkolumnen) bedöms och att resultatet av denna bedömning måste vara ett tal. JOBIN-typjämförelser stöds därför inte.
* Värdet i högerkolumnen utvärderas i JavaScript.
* JOIN-jämförelser stöds inte.
* Uttrycket i den vänstra kolumnen måste vara ett fält. Det kan inte vara en kombination av flera uttryck, ett tal osv.

Följande filtreringsvillkor gäller till exempel INTE för en CRM-import eftersom OR-operatorn är placerad på samma nivå som AND-operatorerna:

* Operatorn OR placeras på samma nivå som operatorn AND
* Jämförelser utförs på textsträngar

![](assets/crm_import_wrong_filter.png)

### Beställ av {#order-by}

I Microsoft Dynamics och Salesforce.com kan du sortera de fjärrfält som ska importeras i stigande eller fallande ordning.

Det gör du genom att klicka på länken **[!UICONTROL Order by]** och lägga till kolumnerna i listan.

Sorteringsordningen för kolumnerna i listan är:

![](assets/crm_import_order.png)

### Registrerings-ID {#record-identification}

I stället för att importera element som ingår (och eventuellt filtreras) i CRM kan du använda en population som beräknas i förväg i arbetsflödet.

Det gör du genom att markera alternativet **[!UICONTROL Use the population calculated upstream]** och ange fältet som innehåller fjärr-ID:t.

Markera sedan fälten för den inkommande ifyllning som du vill importera, så som visas nedan:

![](assets/crm_wf_import_calculated_population.png)

## Exportera till CRM {#exporting-to-the-crm}

Genom att exportera Adobe Campaign-data till CRM kan du kopiera hela innehållet till en CRM-databas.

Om du vill exportera data till CRM måste du skapa följande arbetsflöde:

![](assets/crm_export_diagram.png)

Använd följande konfiguration för aktiviteten **[!UICONTROL CRM Connector]** för en export:

1. Välj en **[!UICONTROL Export to CRM]**-åtgärd.
1. Gå till listrutan **[!UICONTROL Remote object]** och markera objektet som berörs av processen. Det här objektet sammanfaller med en av tabellerna som skapas i Adobe Campaign under anslutningskonfigurationen.

   >[!IMPORTANT]
   >
   >Exportfunktionen för aktiviteten **[!UICONTROL CRM Connector]** kan infoga eller uppdatera fält på CRM-sidan. Om du vill aktivera fältuppdateringar i CRM måste du ange fjärrtabellens primärnyckel. Om nyckeln saknas infogas data (i stället för att uppdateras).

1. Kontrollera **[!UICONTROL Export in Batches]** om du behöver snabbare exporter.

   ![](assets/crm_export_config_2.png)

1. I avsnittet **[!UICONTROL Mapping]** klickar du på **[!UICONTROL New]** för att ange fälten som ska exporteras och deras mappning i CRM.

   ![](assets/crm_export_config.png)

   Om du vill lägga till ett fält klickar du på knappen **[!UICONTROL Add]** i verktygsfältet och sedan på ikonen **[!UICONTROL Edit expression]** .

   >[!NOTE]
   >
   >Om ingen matchning har definierats på CRM-sidan för ett givet fält kan värdena inte uppdateras: de infogas direkt i CRM.

   Om det behövs ändrar du dataformatet via listrutan för kolumnerna **[!UICONTROL Conversion]**. Möjliga konverteringstyper beskrivs i [Dataformat](#data-format).

   >[!NOTE]
   >
   >Listan med poster som ska exporteras och resultatet av exporten sparas i en temporär fil som är tillgänglig tills arbetsflödet har slutförts eller startats om. Detta gör att du kan starta processen igen om fel uppstår utan att du riskerar att exportera samma post flera gånger eller förlora data.

## Ytterligare konfigurationer {#additional-configurations}

### Dataformat {#data-format}

Du kan konvertera dataformat direkt när du importerar dem till eller från CRM.

Det gör du genom att välja den konvertering som ska användas i den matchande kolumnen.

![](assets/crm_task_import.png)

Läget **[!UICONTROL Default]** tillämpar automatisk datakonvertering, som i de flesta fall är lika med en kopia/inklistring av data. Tidszonshantering används dock.

Andra konverteringar är:

* **[!UICONTROL Date only]**: Det här läget tar bort fält av typen Datum + Tid.
* **[!UICONTROL Without time offset]**: Det här läget avbryter den tidszonshantering som används i standardläget.
* **[!UICONTROL Copy/Paste]**: I det här läget används rådata som strängar (ingen konvertering).

### Felbearbetning {#error-processing}

Inom ramen för import och export av data kan du tillämpa en specifik process på fel och avslag. Det gör du genom att välja alternativen **[!UICONTROL Process rejects]** och **[!UICONTROL Process errors]** på fliken **[!UICONTROL Behavior]**.

![](assets/crm_export_options.png)

Dessa alternativ placerar de matchande utdataövergångarna.

![](assets/crm_export_transitions.png)

Placera sedan de aktiviteter som är relevanta för de processer du vill tillämpa.

Om du till exempel vill bearbeta fel kan du lägga till en vänteruta och schemalägga nya försök.

Avvisade registreras med sin felkod och det relaterade meddelandet, vilket innebär att du kan ställa in spårning av avvisade för att optimera synkroniseringsprocessen.

>[!NOTE]
>
>Även om alternativet **[!UICONTROL Process rejects]** inte är aktiverat genereras en varning för varje avvisad kolumn med en felkod och ett meddelande.

Utdataövergången **[!UICONTROL Reject]** ger dig åtkomst till utdataschemat som innehåller de specifika kolumner som är relevanta för felmeddelanden och koder. I Salesforce.com är den här kolumnen **errorSymbol** (felsymbol, skiljer sig från felkoden), **errorMessage** (beskrivning av felkontexten).

## Importera objekt som tagits bort i CRM {#importing-objects-deleted-in-the-crm}

Om du vill kunna konfigurera en omfattande datasynkroniseringsprocess kan du importera objekt som tagits bort i CRM till Adobe Campaign.

Gör så här:

1. Välj en **[!UICONTROL Import objects deleted in the CRM]**-åtgärd.
1. Gå till listrutan **[!UICONTROL Remote object]** och markera objektet som berörs av processen. Det här objektet sammanfaller med en av tabellerna som skapas i Adobe Campaign under anslutningskonfigurationen.
1. Ange den borttagningsperiod som ska beaktas i fälten **[!UICONTROL Start date]** och **[!UICONTROL End date]**. Dessa datum inkluderas i perioden.

   ![](assets/crm_import_deleted_obj.png)

   >[!IMPORTANT]
   >
   >Elementets raderingsperiod måste sammanfalla med de begränsningar som är specifika för CRM. Det innebär att element som togs bort för över 30 dagar sedan inte kan återställas för Salesforce.com.

## Ta bort objekt i CRM {#deleting-objects-in-the-crm}

Om du vill ta bort objekt på CRM-sidan måste du ange primärnyckeln för de fjärrelement som ska tas bort.

![](assets/crm_delete_in_crm.png)

På fliken **[!UICONTROL Behavior]** kan du aktivera bearbetning av avslag. Det här alternativet genererar en andra utdataövergång för aktiviteten **[!UICONTROL CRM connector]**. Mer information finns i [Felbearbetning](#error-processing).

>[!NOTE]
>
>Även när alternativet **[!UICONTROL Process rejects]** är inaktiverat genereras en varning för varje avvisad kolumn.
>
