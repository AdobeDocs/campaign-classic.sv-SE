---
product: campaign
title: Skapa filter
description: Skapa filter
feature: Profiles
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
audience: platform
content-type: reference
topic-tags: filtering-data
exl-id: 58e54f67-dc87-42f1-8426-6f801e8e4fb6
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '1979'
ht-degree: 0%

---

# Skapa filter{#creating-filters}



När du navigerar i Adobe Campaign-trädet (från **[!UICONTROL Explorer]** på hemsidan) visas data i databasen i listor. Dessa listor kan konfigureras så att endast de data som krävs av operatorn visas. Åtgärder kan sedan startas på filtrerade data. Med filterkonfigurationen kan du välja data från en lista **[!UICONTROL dynamically]**. Om data ändras uppdateras de filtrerade data.

>[!NOTE]
>
>Konfigurationsinställningarna för användargränssnittet definieras lokalt på enhetsnivå. Ibland kan det vara nödvändigt att rensa upp dessa data, särskilt om det uppstår problem när data uppdateras. Om du vill göra det använder du **[!UICONTROL File > Clear the local cache]** -menyn.

## Typologi för tillgängliga filter {#typology-of-available-filters}

Med Adobe Campaign kan du använda filter på datalistor.

Dessa filter kan användas en gång eller så kan du spara dem för framtida bruk. Du kan använda flera filter samtidigt.

Följande filtertyper finns i Adobe Campaign:

* **Standardfilter**

  The **standardfilter** är tillgängligt via fälten ovanför listorna. Du kan filtrera efter fördefinierade fält (för mottagarprofiler är dessa som standard namn och e-postadress). Du kan använda fälten för att ange tecken som ska filtreras eller för att välja filtervillkor från en nedrullningsbar lista.

  ![](assets/filters_recipient_default_filter.png)
<!--
  >[!NOTE]
  >
  >The **%** character replaces any character string. For example, the string `%@yahoo.com` lets you display all the profiles with an email address in the domain "yahoo.com".
-->
Du kan ändra standardfiltret för en lista. Mer information finns i [Ändra standardfiltret](#altering-the-default-filter).

* **Enkla filter**

  **Enkla filter** är engångsfilter på kolumnerna. De definieras med ett eller flera enkla sökvillkor i de kolumner som visas.

  Du kan kombinera flera enkla filter i samma datalista för att begränsa sökningen. Filterfälten visas ett under det andra. De kan tas bort oberoende av varandra.

  ![](assets/filters_recipient_simple_filter.png)

  Enkla filter beskrivs i [Skapa ett enkelt filter](#creating-a-simple-filter).

* **Avancerade filter**

  **Avancerade filter** skapas med en fråga eller en kombination av frågor på data.

  Mer information om hur du skapar ett avancerat filter finns i [Skapa ett avancerat filter](#creating-an-advanced-filter).

  Du kan använda funktioner för att definiera filtrets innehåll. Mer information finns i [Skapa ett avancerat filter med funktioner](#creating-an-advanced-filter-with-functions).

  >[!NOTE]
  >
  >Mer information om hur du skapar frågor i Adobe Campaign finns i [det här avsnittet](../../platform/using/about-queries-in-campaign.md).

* **Användarfilter**

  An **programfilter** är ett avancerat filter som har sparats för att använda och dela dess konfiguration med andra operatorer.

  The **[!UICONTROL Filters]** finns ovanför listorna med en uppsättning programfilter som kan kombineras för att förfina filtreringen. Metoden för att skapa dessa filter beskrivs i [Spara ett filter](#saving-a-filter).

## Ändra standardfiltret {#altering-the-default-filter}

Om du vill ändra standardfilter för en mottagarlista klickar du på **[!UICONTROL Profiles and Targets > Pre-defined filters]** trädnod.

För alla andra typer av data konfigurerar du standardfiltret via **[!UICONTROL Administration > Configuration > Predefined filters]** nod.

Använd följande steg:

1. Markera det filter som du vill använda som standard.
1. Klicka på **[!UICONTROL Parameters]** och markera **[!UICONTROL Default filter for the associated document type]**.

   ![](assets/s_ncs_user_default_filter.png)

   >[!CAUTION]
   >
   >Om ett standardfilter redan används i listan måste du inaktivera det innan du använder ett nytt filter. Om du vill göra det klickar du på det röda krysset till höger om filterfälten.

1. Klicka **[!UICONTROL Save]** för att använda filtret.

   >[!NOTE]
   >
   >Filterdefinitionsfönstret beskrivs i [Skapa ett avancerat filter](#creating-an-advanced-filter) och [Spara ett filter](#saving-a-filter).

## Skapa ett enkelt filter {#creating-a-simple-filter}

Skapa en **enkelt filter** använder du följande steg:

1. Högerklicka på det fält som du vill filtrera och välj **[!UICONTROL Filter on this field]**.

   ![](assets/s_ncs_user_sort_this_field.png)

   Standardfilterfälten visas ovanför listan.

1. Välj filteralternativet i listrutan eller ange filtervillkoren som ska användas (metoden för att välja eller ange villkor beror på fälttypen: text, enumererad osv.).

   ![](assets/s_ncs_user_sort_fields.png)

1. Aktivera filtret genom att trycka på Enter på tangentbordet eller klicka på den gröna pilen till höger om filterfälten.

Om fältet som du vill filtrera data i inte visas som en profil kan du lägga till det i de kolumner som visas och sedan filtrera på den kolumnen. För att göra detta

1. Klicka på **[!UICONTROL Configure the list]** -ikon.

   ![](assets/s_ncs_user_configure_list.png)

1. Markera den kolumn som ska visas, t.ex. mottagarnas ålder.

   ![](assets/s_ncs_user_select_fields_to_display.png)

1. Högerklicka på **Ålder** -kolumn i mottagarlistan, och markera **[!UICONTROL Filter on this column]**.

   ![](assets/s_ncs_user_sort_this_column.png)

   Du kan sedan välja alternativ för åldersfiltrering.

   ![](assets/s_ncs_user_delete_filter.png)

## Skapa ett avancerat filter {#creating-an-advanced-filter}

Skapa en **avancerat filter** använder du följande steg:

1. Klicka på **[!UICONTROL Filters]** knapp och markera **[!UICONTROL Advanced filter...]**.

   ![](assets/filters_recipient_create_adv_filter.png)

   Du kan även högerklicka på listan med data som ska filtreras och välja **[!UICONTROL Advanced filter...]**.

   Definitionsfönstret för filtervillkor visas.

1. Klicka på **[!UICONTROL Expression]** -kolumn för att definiera indatavärdet.
1. Klicka **[!UICONTROL Edit expression]** för att markera det fält som filtret ska tillämpas på.

   ![](assets/s_user_filter_choose_field.png)

1. I listan markerar du det fält där data ska filtreras. Klicka på **[!UICONTROL Finish]** för att bekräfta.
1. Klicka på **[!UICONTROL Operator]** och välj den operator som ska användas i listrutan.
1. Välj ett förväntat värde från **[!UICONTROL Value]** kolumn. Du kan kombinera flera filter för att förfina frågan. Om du vill lägga till ett filtervillkor klickar du på **[!UICONTROL Add]**.

   ![](assets/s_ncs_user_filter_add_button_alone.png)

1. Du kan tilldela uttryck en hierarki eller ändra ordningen på frågeuttrycken med hjälp av pilarna i verktygsfältet.
1. Standardoperatorn mellan uttryck är **Och** men du kan ändra detta genom att klicka på fältet. Du kan välja en **eller** -operator.

   ![](assets/s_ncs_user_filter_operator.png)

1. Klicka **[!UICONTROL OK]** för att bekräfta att filter har skapats och för att använda det på listan.

Filtret som används visas ovanför listan.

![](assets/s_ncs_user_filter_adv_edit.png)

Om du vill redigera eller ändra det här filtret klickar du på filtrets etikett.

Om du vill avbryta filtret klickar du på **[!UICONTROL Remove this filter]** till höger om filtret.

![](assets/s_ncs_user_filter_adv_remove.png)

Du kan spara ett avancerat filter om du vill behålla det för framtida bruk. Mer information om den här typen av filter finns i [Spara ett filter](#saving-a-filter).

### Skapa ett avancerat filter med funktioner {#creating-an-advanced-filter-with-functions}

Avancerade filter kan använda funktioner; **filter med funktioner** skapas med en uttrycksredigerare där du kan skapa formler med hjälp av databasdata och avancerade funktioner. Om du vill skapa ett filter med funktioner upprepar du stegen 1, 2 och 3 för att skapa avancerade filter och fortsätter sedan enligt följande:

1. Klicka på **[!UICONTROL Advanced selection]**.
1. Välj formeltyp som ska användas: sammanställning, befintligt användarfilter eller uttryck.

   ![](assets/s_ncs_user_filter_formula_select.png)

   Följande alternativ är tillgängliga:

   * **[!UICONTROL Field only]** för att markera ett fält. Det här är standardläget.
   * **[!UICONTROL Aggregate]** för att välja den sammanställningsformel som ska användas (antal, summa, genomsnitt, maximum, minimum).
   * **[!UICONTROL User filter]** om du vill välja ett av de befintliga användarfiltren. Användarfilter beskrivs i [Spara ett filter](#saving-a-filter).
   * **[!UICONTROL Expression]** för att komma åt uttrycksredigeraren.

     Med uttrycksredigeraren kan du definiera ett avancerat filter. Det ser ut så här:

     ![](assets/s_ncs_user_create_exp_exple01.png)

     Här kan du välja fält i databastabellerna och bifoga avancerade funktioner till dem: Välj den funktion som ska användas i **[!UICONTROL List of functions]**. De tillgängliga funktionerna beskrivs i [Lista över funktioner](../../platform/using/defining-filter-conditions.md#list-of-functions). Markera sedan det eller de fält som berörs av funktionerna och klicka på **[!UICONTROL OK]** för att godkänna uttrycket.

     >[!NOTE]
     >
     >Ett exempel på hur du skapar filter baserat på ett uttryck finns i [det här avsnittet](../../workflow/using/sending-a-birthday-email.md#identifying-recipients-whose-birthday-it-is).

## Spara ett filter {#saving-a-filter}

Filter är specifika för varje operator och initieras om varje gång operatorn rensar cachen för sin klientkonsol.

Du kan skapa en **programfilter** genom att spara ett avancerat filter: det kan återanvändas genom att högerklicka i valfri lista eller via **[!UICONTROL Filters]** knappen ovanför listorna.

Dessa filter kan också nås direkt via leveransguiden i målurvalsfasen (se [det här avsnittet](../../delivery/using/creating-an-email-delivery.md) om du vill ha mer information om hur du skapar leveranser). Om du vill skapa programfiltret kan du:

* Konvertera ett avancerat filter till ett programfilter. Det gör du genom att klicka **[!UICONTROL Save]** innan du stänger den avancerade filterredigeraren.

  ![](assets/s_ncs_user_filter_save.png)

* Skapa detta programfilter via **[!UICONTROL Administration > Configuration > Predefined filters]** (eller **[!UICONTROL Profiles and targets > Predefined filters]** för mottagare) i trädet. Om du vill göra det högerklickar du på filterlistan och väljer **[!UICONTROL New...]**. Proceduren är densamma som när du skapar avancerade filter.

  The **[!UICONTROL Label]** I kan du ge filtret ett namn. Det här namnet visas i kombinationsfältet i **[!UICONTROL Filters...]** -knappen.

  ![](assets/user_filter_apply.png)

Du kan ta bort alla filter i den aktuella listan genom att högerklicka och välja **[!UICONTROL No filter]** eller via **[!UICONTROL Filters]** -ikonen som finns ovanför listan.

Du kan kombinera filter genom att klicka på **[!UICONTROL Filters]** och använda **[!UICONTROL And...]** -menyn.

![](assets/s_ncs_user_filter_combination.png)

## Filtrera mottagare {#filtering-recipients}

Fördefinierade filter (se [Spara ett filter](#saving-a-filter)) kan du filtrera profilerna för mottagarna i databasen. Du kan redigera filter på **[!UICONTROL Profiles and Targets > Predefined filters]** trädnod. Filtren visas i den övre delen av arbetsytan via **[!UICONTROL Filters]** -knappen.

Markera ett filter om du vill visa dess definition och få tillgång till en förhandsvisning av filtrerade data.

![](assets/s_ncs_user_segment_edit.png)

>[!NOTE]
>
>Ett detaljerat exempel på hur du skapar fördefinierade filter finns i [Använd skiftläge](../../platform/using/use-case.md).

De fördefinierade filtren är:

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etikett</strong><br /> </td> 
   <td> <strong>Fråga</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Öppnad<br /> </td> 
   <td> Väljer mottagare som har öppnat en leverans.<br /> </td> 
  </tr> 
  <tr> 
   <td> Öppnad men inte klickad<br /> </td> 
   <td> Väljer mottagare som har öppnat en leverans men inte klickat på en länk.<br /> </td> 
  </tr> 
  <tr> 
   <td> Inaktiva mottagare<br /> </td> 
   <td> Väljer mottagare som inte har öppnat en leverans på X månader.<br /> </td> 
  </tr> 
  <tr> 
   <td> Senaste aktivitet efter enhetstyp<br /> </td> 
   <td> Väljer mottagare som har klickat eller öppnat leveransadress Y med enhet X de senaste Z-dagarna.<br /> </td> 
  </tr> 
  <tr> 
   <td> Senaste aktivitet per enhetstyp (spårning)<br /> </td> 
   <td> Väljer mottagare som har klickat eller öppnat leveransadress Y med enhet X de senaste Z-dagarna.<br /> </td> 
  </tr> 
  <tr> 
   <td> Ej riktade mottagare<br /> </td> 
   <td> Väljer mottagare som aldrig har fått något mål via kanal Y på X månader.<br /> </td> 
  </tr> 
  <tr> 
   <td> Mycket aktiva mottagare<br /> </td> 
   <td> Väljer mottagare som har klickat på en leverans minst X gånger under de senaste Y-månaderna.<br /> </td> 
  </tr> 
  <tr> 
 <td> Blocklist e-postadress<br /> </td> 
    <td> Väljer mottagare vars e-postadress finns på blockeringslista.<br/> </td>
  </tr> 
  <tr> 
   <td> E-postadress i karantän<br /> </td> 
   <td> Väljer mottagare vars e-postadress är i karantän.<br /> </td> 
  </tr> 
  <tr> 
   <td> E-postadresser som är duplicerade i mappen<br /> </td> 
   <td> Väljer mottagare vars e-postadress är duplicerad i mappen.<br /> </td> 
  </tr> 
  <tr> 
   <td> Varken öppnad eller klickad<br /> </td> 
   <td> Väljer mottagare som inte har öppnat en leverans eller klickat i en leverans.<br /> </td> 
  </tr> 
  <tr> 
   <td> Nya mottagare (dagar)<br /> </td> 
   <td> Väljer mottagare som har skapats de senaste X dagarna.<br /> </td> 
  </tr> 
  <tr> 
   <td> Nya mottagare (minuter)<br /> </td> 
   <td> Väljer mottagare som har skapats de senaste X minuterna.<br /> </td> 
  </tr> 
  <tr> 
   <td> Nya mottagare (månader)<br /> </td> 
   <td> Väljer mottagare som har skapats de senaste X månaderna.<br /> </td> 
  </tr> 
  <tr> 
   <td> Efter prenumeration<br /> </td> 
   <td> Väljer mottagare efter prenumeration.<br /> </td> 
  </tr> 
  <tr> 
   <td> Genom att klicka på en specifik länk<br /> </td> 
   <td> Väljer mottagare som klickat på en viss URL i en leverans.<br /> </td> 
  </tr> 
  <tr> 
   <td> Beteende vid postleverans<br /> </td> 
   <td> Väljer mottagare utifrån deras beteende efter att de har tagit emot en leverans.<br /> </td> 
  </tr> 
  <tr> 
   <td> Efter skapad den<br /> </td> 
   <td> Väljer mottagare efter skapandedatum, över en period som sträcker sig från X månader (aktuellt datum minus n månader) till Y-månader (aktuellt datum minus n månader).<br /> </td> 
  </tr> 
  <tr> 
   <td> Per lista<br /> </td> 
   <td> Väljer mottagare efter lista.<br /> </td> 
  </tr> 
  <tr> 
   <td> Efter antal klick<br /> </td> 
   <td> Väljer mottagare som klickat på en leverans de senaste X månaderna.<br /> </td> 
  </tr> 
  <tr> 
   <td> Efter antal mottagna meddelanden<br /> </td> 
   <td> Väljer mottagare baserat på det antal meddelanden som de har fått.<br /> </td> 
  </tr> 
  <tr> 
   <td> Efter antal öppningar<br /> </td> 
   <td> Väljer mottagare som har öppnat mellan X- och Y-leveranser över Z tid.<br /> </td> 
  </tr> 
  <tr> 
   <td> Efter namn eller e-post<br /> </td> 
   <td> Väljer mottagare efter namn eller e-postadress.<br /> </td> 
  </tr> 
  <tr> 
   <td> Efter åldersintervall<br /> </td> 
   <td> Väljer mottagare efter deras ålder.<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Alla jämförelser som rör räkning och perioder ska förstås i vidare bemärkelse (mottagare som motsvarar frågegränserna inkluderas i jämförelsen).

Exempel på hur data beräknas:

* Väljer mottagare som är yngre än 30 år:

  ![](assets/predefined_filters_01.png)

* Väljer mottagare som är 18 år eller äldre:

  ![](assets/predefined_filters_03.png)

* Väljer mottagare mellan 18 och 30 år:

  ![](assets/predefined_filters_02.png)

## Avancerade inställningar för datafilter {#advanced-settings-for-data-filters}

Klicka på **[!UICONTROL Settings]** för att komma åt följande alternativ:

* **[!UICONTROL Default filter for the associated document type]**: Med det här alternativet kan du som standard föreslå det här filtret i redigeraren för de listor som berörs av sorteringen.

  Till exempel **[!UICONTROL By name or login]** filter används på operatorer. Det här alternativet är markerat och därför erbjuds filtret alltid i alla operatorlistor.

* **[!UICONTROL Filter shared with other operators]**: Med det här alternativet kan du göra filtret tillgängligt för alla andra operatorer i den aktuella databasen.
* **[!UICONTROL Use parameter entry form]**: Med det här alternativet kan du definiera de filterfält som ska visas ovanför listan när det här filtret är markerat. I dessa fält kan du definiera filterinställningarna. Det här formuläret måste anges i XML-format via **[!UICONTROL Form]** -knappen. Det förkonfigurerade filtret **[!UICONTROL Recipients who have opened]**, som finns i mottagarlistan, visar ett filterfält där du kan välja den leverans som filtret ska användas för.

  The **[!UICONTROL Preview]** visas resultatet av det valda filtret.

* The **[!UICONTROL Advanced parameters]** kan du definiera ytterligare inställningar. Du kan associera en SQL-tabell med filtret för att göra den gemensam för alla redigerare som delar tabellen.

  Välj **[!UICONTROL Do not restrict the filter]** om du vill hindra användaren från att åsidosätta det här filtret.

  Det här alternativet är aktiverat för filter för mottagare av en leverans och mottagare av leveranser som tillhör en mapp som finns i leveransguiden och som inte kan överladdas.

  ![](assets/s_ncs_user_filter_advanced_param.png)
