---
product: campaign
title: Synkronisera målgrupper
description: Lär dig synkronisera målgrupper med ACS Connector
feature: ACS Connector
hide: true
hidefromtoc: true
exl-id: 88e581cf-43cd-4c43-9347-d016c62fdf42
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1110'
ht-degree: 1%

---

# Synkronisera målgrupper{#synchronizing-audiences}



Ni kan skapa en avancerad lista med de avancerade funktionerna i Campaign v7 och dela den som en målgrupp direkt och i realtid med Campaign Standard (inklusive ytterligare data) på ett smidigt sätt. Din Campaign Standard kan sedan konsumera publiken i Adobe Campaign Standard.

Komplex målinriktning med ytterligare data som inte replikeras i Campaign Standard kan bara uppnås med Campaign v7.

Du kan också dela listor med mottagare eller data som kommer via en anslutning som Microsoft Dynamics med Campaign Standard.

Det här användningsexemplet visar hur du förbereder målet för leveransen i Campaign v7 och hur du återanvänder målet och dess ytterligare data i en leverans som skapas och skickas med Adobe Campaign Standard.

>[!NOTE]
>
>Du kan också utöka data med aggregat och samlingar i Adobe Campaign Standard om alla data du behöver redan har replikerats.

## Förhandskrav {#prerequisites}

För att uppnå detta behöver du:

* Mottagare lagrade i Campaign v7-databasen och synkroniserade med Campaign Standard. Se avsnittet [Synkronisera profiler](../../integrations/using/synchronizing-profiles.md).
* Ytterligare data, som prenumerationer eller transaktioner, lagras i tabeller som är relaterade till nms:mottagare i Campaign v7-databasen. Dessa data kan komma från OOB-scheman i Campaign v7 eller anpassade tabeller. De är som standard inte tillgängliga i Campaign Standarden eftersom de inte är synkroniserade.
* Rätt att köra arbetsflöden i både Campaign v7 och Campaign Standard.
* Rätt att skapa och köra en leverans i Campaign Standard.

## Skapa ett arbetsflöde för målinriktning med ytterligare data i Campaign v7 {#create-a-targeting-workflow-with-additional-data-in-campaign-v7}

Komplex målinriktning med ytterligare data som inte replikeras i Campaign Standard kan bara uppnås med Campaign v7.

När målet och dess ytterligare data har definierats kan du spara det som en lista som kan delas med Campaign Standard.

>[!NOTE]
>
>Detta är ett exempel. Beroende på dina behov kan du enkelt ställa frågor till en lista över mottagare och dela den med ACS utan vidare bearbetning. Du kan också använda andra datahanteringsaktiviteter för att förbereda det slutliga målet.

Så här får du den slutliga målgruppen och dess ytterligare data:

1. Skapa ett nytt arbetsflöde från **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Jobs]** > **[!UICONTROL Targeting workflows]**.
1. Lägg till en **[!UICONTROL Query]**-aktivitet och välj de mottagare som du vill skicka det slutliga e-postmeddelandet till. Exempel: alla mottagare mellan 18 och 30 år och bor i Frankrike.

   ![](assets/acs_connect_query1.png)

1. Lägg till ytterligare data från frågan. Mer information finns i avsnittet [Lägga till data](../../workflow/using/query.md#adding-data).

   I det här exemplet visas hur du lägger till en mängd för att räkna antalet leveranser som en mottagare har fått under ett år.

   I **[!UICONTROL Query]** väljer du **[!UICONTROL Add data...]**.

   ![](assets/acs_connect_query2.png)

1. Markera **[!UICONTROL Data linked to the filtering dimension]** och klicka på **[!UICONTROL Next]**.

   ![](assets/acs_connect_query3.png)

1. Välj **[!UICONTROL Data linked to the filtering dimension]**, markera sedan noden **[!UICONTROL Recipient delivery logs]** och klicka på **[!UICONTROL Next]**.

   ![](assets/acs_connect_query4.png)

1. Välj **[!UICONTROL Aggregates]** i fältet **[!UICONTROL Data collected]** och klicka på **[!UICONTROL Next]**.

   ![](assets/acs_connect_query5.png)

1. Lägg till ett filtreringsvillkor om du bara vill ta hänsyn till loggar som skapats under de senaste 365 dagarna och klicka på **[!UICONTROL Next]**.

   ![](assets/acs_connect_query6.png)

1. Definiera utdatakolumner. Här är den enda kolumn som behövs en som räknar antalet leveranser. Så här gör du:

   * Välj **[!UICONTROL Add]** till höger om fönstret.
   * Klicka på **[!UICONTROL Advanced selection]** i fönstret **[!UICONTROL Select field]**.
   * Välj **[!UICONTROL Aggregate]** och sedan **[!UICONTROL Count]**. Markera alternativet **[!UICONTROL Distinct]** och klicka på **[!UICONTROL Next]**.
   * I listan med fält väljer du det fält som används för funktionen **Antal**. Välj ett fält som alltid ska fyllas i, till exempel fältet **[!UICONTROL Primary key]**, och klicka på **[!UICONTROL Finish]**.
   * Ändra uttrycket i kolumnen **[!UICONTROL Alias]**. Med det här aliaset kan du enkelt hämta den nya kolumnen i den slutliga leveransen. Till exempel **NBdelifts**.
   * Klicka på **[!UICONTROL Finish]** och spara aktivitetskonfigurationen **[!UICONTROL Query]**.

   ![](assets/acs_connect_query7.png)

1. Spara arbetsflödet. I nästa avsnitt visas hur du delar populationen med ACS.

## Dela målet med Campaign Standard {#share-the-target-with-campaign-standard}

När målpopulationen har definierats kan du dela den med ACS via en **[!UICONTROL List update]**-aktivitet.

1. Lägg till en **[!UICONTROL List update]**-aktivitet i det arbetsflöde som skapats tidigare och ange listan som du vill uppdatera eller skapa.

   Ange i vilken mapp du vill spara listan i Campaign v7. Listor omfattas av mappmappmappningen som definieras under implementeringen, vilket kan påverka deras synlighet när de delas i Campaign Standard. Se avsnittet [Rättighetskonvertering](../../integrations/using/acs-connector-principles-and-data-cycle.md#rights-conversion).

1. Kontrollera att alternativet **[!UICONTROL Share with ACS]** är markerat. Den är markerad som standard.

   ![](assets/acs_connect_listupdate1.png)

1. Spara och kör arbetsflödet.

   Målet och dess ytterligare data sparas i en lista i Campaign v7 och delas omedelbart som en listmålgrupp i Campaign Standard. Endast de profiler som har replikerats delas med ACS.

Om ett fel inträffar för aktiviteten **[!UICONTROL List update]** betyder det att synkroniseringen med Campaign Standarden kan ha misslyckats. Om du vill se mer information om vad som gick fel går du till **[!UICONTROL Administration]** > **[!UICONTROL ACS Connector]** > **[!UICONTROL Process]** > **[!UICONTROL Diagnosis]**. Den här mappen innehåller synkroniseringsarbetsflöden som har utlösts av aktivitetskörningen **[!UICONTROL List update]**. Se avsnittet [Felsöka ACS Connector](../../integrations/using/troubleshooting-the-acs-connector.md).

## Hämta data i Campaign Standard och använd dem i en leverans {#retrieve-the-data-in-campaign-standard-and-use-it-in-a-delivery}

När målarbetsflödet har körts i Campaign v7 kan du hitta listmålgruppen i skrivskyddat läge på Campaign Standardens **[!UICONTROL Audiences]**-meny.

![](assets/acs_connect_deliveryworkflow_audience.png)

Genom att skapa ett leveransarbetsflöde i Campaign Standard är det sedan möjligt att använda den här målgruppen samt de ytterligare data som den innehåller i en leverans.

1. Skapa ett nytt arbetsflöde på menyn **[!UICONTROL Marketing activities]**.
1. Lägg till en **[!UICONTROL Read audience]**-aktivitet och välj den målgrupp som du tidigare delade från Campaign v7.

   Den här aktiviteten används för att hämta data för den valda målgruppen. Du kan också tillämpa ytterligare **[!UICONTROL Source Filtering]** om det behövs genom att använda aktivitetens flik enligt.

1. Lägg till en **[!UICONTROL Email delivery]**-aktivitet och konfigurera den som en annan [e-postleveransaktivitet](https://experienceleague.adobe.com/docs/campaign-standard/using/managing-processes-and-data/channel-activities/email-delivery.html?lang=sv-SE).
1. Öppna leveransinnehållet.
1. Lägg till ett personaliseringsfält.  Leta reda på noden **[!UICONTROL Additional data (targetData)]** på popup-menyn. Den här noden innehåller ytterligare data om målgruppen som beräknades i det inledande målarbetsflödet. Du kan använda dem som vilket annat personaliseringsfält som helst.

   I det här exemplet är de ytterligare data som kommer från det ursprungliga arbetsflödet för målinriktning antalet leveranser som skickats till varje mottagare under de senaste 365 dagarna. Det NBdeliver-alias som anges i målarbetsflödet visas här.

   ![](assets/acs_connect_deliveryworkflow_targetdata.png)

1. Spara leverans och arbetsflöde.

   Arbetsflödet är nu klart att köras. Leveransen analyseras och kan skickas.

   ![](assets/acs_connect_deliveryworkflow_ready.png)

## Skicka och övervaka leveransen {#send-and-monitor-your-delivery}

När leveransen och innehållet är klara skickar du leveransen:

1. Kör leveransarbetsflödet. I det här steget förbereds e-postmeddelandet för att skickas.
1. Bekräfta manuellt att leveransen kan skickas från kontrollpanelen för leverans.
1. Övervaka rapporter och loggar för leveransen:

   * **I Campaign Standard**: Åtkomst till [rapporter](https://experienceleague.adobe.com/docs/campaign-standard/using/reporting/about-reporting/about-dynamic-reports.html?lang=sv-SE) och [loggar](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/monitoring-a-delivery.html?lang=sv-SE) som relaterar till leveransen som för alla leveranser.
   * **i Campaign v7 och Campaign Standard**: Leverans-ID, breda e-postloggar och loggar för e-postspårning synkroniseras med Campaign v7. Sedan kan ni få en helhetsbild av era marknadsföringskampanjer från Campaign v7.

     Kvartalanger synkroniseras automatiskt tillbaka till Campaign v7. På så sätt kan information som inte kan levereras beaktas vid nästa målgruppsanpassning som utförs i Campaign v7.

     Mer information om karantänhantering finns i Campaign Standard i [det här avsnittet](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html?lang=sv-SE).
