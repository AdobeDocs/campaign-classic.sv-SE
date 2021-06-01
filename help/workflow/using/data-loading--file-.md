---
product: campaign
title: Läsa in data (fil)
description: Läs mer om arbetsflödesaktiviteten Datainläsning (fil)
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: a380e486-a40c-4bf6-b7f4-7dcd76c34085
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1052'
ht-degree: 15%

---

# Läsa in data (fil){#data-loading-file}

## Använd {#use}

Med aktiviteten **[!UICONTROL Data loading (File)]** kan du komma åt en extern datakälla och använda den direkt i Adobe Campaign. Alla data som krävs för målinriktade åtgärder finns inte alltid i Adobe Campaign-databasen: den kan göras tillgänglig i externa filer.

Filen som ska läsas in kan anges av övergången eller beräknas under körningen av aktiviteten. Det kan till exempel vara en lista över en kunds 10 favoritprodukter vars inköp hanteras i en extern databas.

I det övre avsnittet av konfigurationsfönstret för den här aktiviteten kan du definiera filformatet. Om du vill göra det använder du en exempelfil med samma format som den som ska importeras. Filen kan lagras lokalt eller på servern.

>[!CAUTION]
>
>Endast &quot;platta&quot; strukturfiler stöds (t.ex. CSV, TXT). Du bör inte använda XML-formatet.

![](assets/s_advuser_wf_etl_file.png)

Du kan definiera en förprocess som ska utföras under filimport, t.ex. för att inte behöva packa upp filen på servern (och därför spara utrymme för den uppzippade filen) utan för att inkludera uppzippning i filbearbetningen. Välj alternativet **[!UICONTROL Pre-process the file]** och välj ett av tre alternativ: **[!UICONTROL None]**, **[!UICONTROL Decompression]** (zcat) eller **[!UICONTROL Decrypt]** (gpg).

![](assets/preprocessing-dataloading.png)

Mer information finns i följande avsnitt: [Zippa upp eller dekryptera en fil innan du bearbetar](../../platform/using/unzip-decrypt.md).

## Definiera filformatet {#defining-the-file-format}

När du läser in en fil identifieras kolumnformatet automatiskt med standardparametrarna för varje datatyp. Du kan ändra de här standardparametrarna för att ange vilka processer som ska tillämpas på din data särskilt när det finns ett fel eller ett tomt värde.

Det gör du genom att välja **[!UICONTROL Click here to change the file format...]** i huvudfönstret för aktiviteten **[!UICONTROL Data loading (file)]**. Fönstret Formatinformation öppnas.

![](assets/file_loading_columns_format.png)

Du kan sedan ändra den allmänna formateringen för filen samt formateringen för varje kolumn.

Med den allmänna filformateringen kan du definiera hur kolumnerna ska identifieras (filkodning, avgränsare, osv.).

Med kolumnformateringen kan du definiera värdebearbetningen för varje kolumn:

* **[!UICONTROL Ignore column]**: bearbetar inte den här kolumnen under datainläsning.
* **[!UICONTROL Data type]**: Anger den typ av data som förväntas för varje kolumn.
* **[!UICONTROL Allow NULLs]**: används för att ange hur tomma värden ska hanteras.

   * **[!UICONTROL Adobe Campaign default]**: genererar ett fel endast för numeriska fält. Annars läggs ett NULL-värde in.
   * **[!UICONTROL Empty value allowed]**: anger tomma värden.  Värdet NULL infogas därför.
   * **[!UICONTROL Always populated]**: genererar ett fel om ett värde är tomt.

* **[!UICONTROL Length]**: Anger det maximala antalet tecken för  **** strängdatatypen.
* **[!UICONTROL Format]**: definierar tids- och datumformatet.
* **[!UICONTROL Data transformation]**: definierar om en teckenskiftsprocess måste tillämpas på en  **sträng**.

   * **[!UICONTROL None]**: den importerade strängen ändras inte.
   * **[!UICONTROL First letter in upper case]**: den första bokstaven i varje ord i strängen börjar med ett versal.
   * **[!UICONTROL Upper case]**: alla tecken i strängen är i versaler.
   * **[!UICONTROL Lower case]**: alla tecken i strängen är i gemener.

* **[!UICONTROL White space management]**: anger om vissa mellanslag måste ignoreras i en sträng. Värdet **[!UICONTROL Ignore spaces]** tillåter bara att blanksteg i början och i slutet av en sträng ignoreras.
* **[!UICONTROL Error processings]**: definierar beteendet om ett fel påträffas.

   * **[!UICONTROL Ignore the value]**: värdet ignoreras.  En varning genereras i arbetsflödets körningslogg.
   * **[!UICONTROL Reject line]**: hela raden bearbetas inte.
   * **[!UICONTROL Use a default value in case of error]**: ersätter det värde som orsakar felet med ett standardvärde som definieras i fältet **[!UICONTROL Default value]**.
   * **[!UICONTROL Reject the line when there is no remapping value]**: hela raden behandlas inte såvida inte en mappning har definierats för det felaktiga värdet (se  **[!UICONTROL Mapping]** alternativet nedan).
   * **[!UICONTROL Use a default value in case the value is not remapped]**: ersätter det värde som orsakar felet med ett standardvärde, som definieras i  **[!UICONTROL Default value]** fältet, såvida inte en mappning har definierats för det felaktiga värdet (se  **[!UICONTROL Mapping]** alternativet nedan).

* **[!UICONTROL Default value]**: anger standardvärdet enligt vald felbearbetning.
* **[!UICONTROL Mapping]**: det här fältet är endast tillgängligt i kolumndetaljkonfigurationen (nås via en dubbelklickning eller via alternativen till höger om kolumnlistan). Detta omformar vissa värden när de importeras. Du kan till exempel omvandla &quot;tre&quot; till &quot;3&quot;.

## Exempel: Samla in data och läsa in dem i databasen {#example--collecting-data-and-loading-it-in-the-database}

I följande exempel kan du samla in en fil på servern varje dag, läsa in dess innehåll och uppdatera data i databasen beroende på vilken information den innehåller. Den fil som ska samlas in innehåller information om kunder som kan ha gjort inköp (för mer eller mindre än 3 000 euro), begärt att få pengarna tillbaka på ett köp eller besökt butiken utan att köpa något. Beroende på den här informationen tillämpas olika processer på deras profil i databasen.

![](assets/s_advuser_load_file_sample_0.png)

1. Med filsamlaren kan du återställa filer som lagras i en katalog, beroende på den angivna frekvensen.

   Fliken **[!UICONTROL Directory]** innehåller information om de filer som ska återställas. I det här exemplet återställs alla filer i textformat vars namn innehåller ordet &quot;kunder&quot; och som lagras i katalogen tmp/Adobe/Data/files på servern.

   Användningen av **[!UICONTROL File collector]** beskrivs i avsnittet [Filinsamlare](../../workflow/using/file-collector.md).

   ![](assets/s_advuser_load_file_sample_1.png)

   På fliken **[!UICONTROL Schedule]** kan du schemalägga körningen av insamlaren, dvs. ange med vilken frekvens som förekomsten av dessa filer ska kontrolleras.

   Här vill vi aktivera samlaren varje arbetsdag klockan nio.

   ![](assets/s_advuser_load_file_sample_2.png)

   Det gör du genom att klicka på knappen **[!UICONTROL Change...]** längst ned till höger i redigeringsverktyget och konfigurera schemat.

   Mer information finns i [Schemaläggaren](../../workflow/using/scheduler.md).

1. Konfigurera sedan aktiviteten för inläsning av data (fil) för att ange hur de insamlade filerna ska läsas. Det gör du genom att markera en exempelfil med samma struktur som de filer som ska läsas in.

   ![](assets/s_advuser_load_file_sample_3.png)

   Här innehåller filen fem kolumner:

   * den första kolumnen innehåller en kod som sammanfaller med händelsen: inköp (mer eller mindre än 3 000 euro), inget inköp eller någon återbetalning för ett eller flera inköp.
   * De fyra följande kolumnerna innehåller klientens förnamn, efternamn, e-postadress och kontonummer.

   Formatkonfigurationen för filen som ska läsas in sammanfaller med den som definieras vid dataimport i Adobe Campaign. Mer information om detta hittar du i det här [avsnittet](../../platform/using/executing-import-jobs.md#step-2---source-file-selection).

1. I den delade aktiviteten anger du de delmängder som ska skapas enligt kolumnvärdet **Event**.

   Aktiviteten Dela är detaljerad i avsnittet.

   ![](assets/s_advuser_load_file_sample_4.png)

   För varje delmängd anger du ett av värdena i kolumnen **Event**.

   ![](assets/s_advuser_load_file_sample_5.png)

   Aktiviteten **[!UICONTROL Split]** kommer därför att innehålla följande information:

   ![](assets/s_advuser_load_file_sample_6.png)

1. Ange sedan de processer som ska utföras för varje typ av population. I vårt exempel kommer vi att **[!UICONTROL Update the data]** i databasen. Det gör du genom att placera en **[!UICONTROL Update data]**-aktivitet i slutet av varje utgående övergång från den delade aktiviteten.

   Aktiviteten **[!UICONTROL Update data]** beskrivs i avsnittet [Uppdatera data](../../workflow/using/update-data.md).
