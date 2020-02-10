---
title: Hantera svar
seo-title: Hantera svar
description: Hantera svar
seo-description: null
page-status-flag: never-activated
uuid: 329e2f4a-c5bc-4654-bdef-71a0818fc2b7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: online-surveys
discoiquuid: affecd87-00a3-4d50-92d3-31ac6228948b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Hantera svar{#managing-answers}

## Lagra insamlade svar {#storing-collected-answers}

Förutom de vanliga lagringslägena som är gemensamma för alla webbformulär i Adobe Campaign (databasfält och lokal variabel) möjliggör enkäter den dynamiska utökningen av datamodellen med hjälp av arkiverade fält.

>[!CAUTION]
>
>Det här alternativet är endast tillgängligt för webbprogram av typen **Undersökning** . Det finns inte för andra typer av webbformulär.

### Lagra i ett arkiverat fält {#storing-in-an-archived-field}

Det är enkelt att utöka datamallen genom att lägga till nya lagringsutrymmen för att spara svaren från undersökningar. Det gör du genom att välja **[!UICONTROL Store answers to a question]** alternativet när du skapar inmatningsfältet. Klicka på **[!UICONTROL New field...]** länken och ange dess egenskaper:

![](assets/s_ncs_admin_survey_new_space.png)

Ange fältets etikett och namn och välj fälttyp: Text, booleskt, heltal eller decimaltal, datum osv.

Den valda fälttypen innefattar en kontroll av data när användarna anger svar. För **textfält** kan du lägga till en begränsning (skiftläge, format) eller länka till en befintlig uppräkning för att framtvinga markering.

Om du vill lägga till en begränsning markerar du den i listrutan. Det finns två typer av begränsningar:

1. Skiftläge för tecken

   Den angivna informationen kan lagras i fältet i följande format: enbart versaler, endast gemener, eller med inledande versaler. Den här begränsningen kräver inte att användaren anger data i det valda formatet, men innehållet som anges i fältet konverteras när det sparas.

1. Dataformat

Om det här fältet används i en lista kan uppräkningsvärdena hämtas automatiskt i värdetabellen med hjälp av länken **[!UICONTROL Initialize the list of values from the database]** ovanför värdelistan.

Du kan till exempel skapa en listruta där användaren kan välja sitt modersmål. Motsvarande arkiverade fält kan associeras med **språkuppräkningen** som innehåller en lista med språk:

![](assets/s_ncs_admin_survey_database_values_2b.png)

Med **[!UICONTROL Edit link]** ikonen till höger om fältet kan du redigera innehållet i den här uppräkningen:

![](assets/s_ncs_admin_survey_database_values_2c.png)

På fliken **[!UICONTROL General]** i fältet kan du med hjälp av **[!UICONTROL Initialize the list of values from the database]** länken automatiskt mata in listan med etiketter.

![](assets/s_ncs_admin_survey_database_values_2.png)

**Exempel**: lagra en mottagares kontrakt i ett fält

Om du vill lagra olika typer av kontrakt i ett fält skapar du ett **[!UICONTROL Text]** inmatningsfält och väljer **[!UICONTROL Store answers to a question]** alternativet.

Klicka på **[!UICONTROL New field...]** länken och ange fältegenskaperna. Markera **[!UICONTROL Multiple values]** alternativet om du vill aktivera flera värden som ska lagras.

![](assets/s_ncs_admin_survey_storage_multi_ex1.png)

Skapa inmatningsfält för de andra kontrakten och lagra data i samma arkiverade fält.

![](assets/s_ncs_admin_survey_storage_multi_ex2.png)

När användarna godkänner undersökningen lagras deras svar i **[!UICONTROL Contracts]** fältet.

I vårt exempel finns följande svar:

![](assets/s_ncs_admin_survey_storage_multi_ex3.png)

Svarandens profil innehåller de fyra angivna kontrakten.

De kan visas på fliken **[!UICONTROL Answers]** i undersökningen genom att visa relevanta kolumner.

![](assets/s_ncs_admin_survey_storage_multi_ex4.png)

Du kan även filtrera mottagare baserat på svar så att endast de användare som intresserar dig visas. Det gör du genom att skapa ett målarbetsflöde och använda **[!UICONTROL Survey responses]** rutan.

![](assets/s_ncs_admin_survey_read_responses_wf.png)

Skapa din fråga baserat på de profiler som du vill återställa. I följande exempel kan du med frågan välja profiler med minst två kontrakt, inklusive ett A-typkontrakt.

![](assets/s_ncs_admin_survey_read_responses_edit.png)

För varje formulär kan svaren användas i fält eller etiketter. Använd följande syntax för innehåll som lagras i ett arkiverat fält:

```
<%= ctx.webAppLogRcpData.name of the archived field %
```

>[!NOTE]
>
>För andra typer av fält beskrivs syntaxen i [det här avsnittet](../../platform/using/about-queries-in-campaign.md).

### Lagringsinställningar {#storage-settings}

Man kan arkivera svaren på enkäter i XML-format. På så sätt kan du spara en rå kopia av de insamlade svaren, vilket kan vara användbart om data standardiseras för mycket i en specificerad lista (mer information finns i [Standardisera data](../../web/using/publish--track-and-use-collected-data.md#standardizing-data)).

>[!CAUTION]
>
>Arkivering av råsvar ökar lagringsutrymmet avsevärt. Använd det här alternativet med försiktighet.

Så här gör du:

* Redigera undersökningsegenskaperna med **[!UICONTROL Properties]** knappen på **[!UICONTROL Edit]** fliken.
* Klicka på **[!UICONTROL Advanced parameters]** länken och markera **[!UICONTROL Save a copy of raw answers]** alternativet.

![](assets/s_ncs_admin_survey_xml_archive_option.png)

Du kan aktivera det som standard för alla undersökningar (det här alternativet används när undersökningen publiceras). Det gör du genom att skapa **[!UICONTROL NmsWebApp_XmlBackup]** alternativet och tilldela det ett värde **[!UICONTROL 1]** enligt nedan:

![](assets/s_ncs_admin_survey_xml_global_option.png)

## Poänghantering {#score-management}

Du kan tilldela ett poängvärde till de alternativ som finns på formulärets sidor. Bakgrundsmusik kan bara länkas till stängda frågor: kryssruta, värde från en nedrullningsbar lista, prenumeration osv.

>[!CAUTION]
>
>Enbart för **enkäter** .

![](assets/s_ncs_admin_survey_score_create.png)

Poängen samlas och sparas på serversidan när sidan bekräftas, dvs. när användaren klickar på **[!UICONTROL Next]** - eller **[!UICONTROL Finish]** -knappen.

>[!NOTE]
>
>Du kan använda positiva eller negativa värden, heltal eller icke-heltal.

Bakgrundsmusik kan användas i tester och skript.

>[!CAUTION]
>
>Det går inte att använda bakgrundsmusik i synlighetsvillkoren för fält som finns på samma sida. De kan dock användas på efterföljande sidor.

* Om du vill använda poäng i tester använder du **[!UICONTROL Score]** fältet i testberäkningsformeln enligt nedan:

   ![](assets/s_ncs_admin_survey_score_in_a_test.png)

* Du kan använda poängen i ett skript.

**Exempel**: beräkna en poäng och använda den som villkor för att visa nästa sida:

* I en undersökning kan du på nästa sida tilldela användare olika poäng beroende på vilket värde som valts i listrutan:

   ![](assets/s_ncs_admin_survey_score_exa.png)

* Du kan kombinera den här poängen med ett andra värde, beroende på vilket alternativ du har valt:

   ![](assets/s_ncs_admin_survey_score_exb.png)

* När användaren klickar på **[!UICONTROL Next]** knappen läggs de två värdena till.

   ![](assets/s_ncs_admin_survey_score_exe.png)

* Villkoren kan användas för sidan som ska visas enligt poängen. Detta är konfigurerat enligt följande:

   ![](assets/s_ncs_admin_survey_score_exd.png)

   ![](assets/s_ncs_admin_survey_score_exg.png)

