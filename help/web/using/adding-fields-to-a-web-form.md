---
title: Lägga till fält i ett webbformulär
seo-title: Lägga till fält i ett webbformulär
description: Lägga till fält i ett webbformulär
seo-description: null
page-status-flag: never-activated
uuid: 33c6ab85-b021-422a-a224-c9eff27e6fc0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-forms
discoiquuid: d63892b3-260d-45e8-b99a-1e7c78353395
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Lägga till fält i ett webbformulär{#adding-fields-to-a-web-form}

I ett webbformulär gör fälten det möjligt för användare att ange information och välja alternativ. Webbformulär kan innehålla inmatningsfält, urvalsfält, statiskt och avancerat innehåll (bildtexter, prenumerationer osv.).

När du använder guiden för att lägga till fält identifieras fälttypen automatiskt baserat på det valda fältet eller lagringsvariabeln. Du kan redigera den i den **[!UICONTROL Type]** nedrullningsbara rutan på **[!UICONTROL General]** fliken.

![](assets/s_ncs_admin_webform_change_type.png)

När du använder knapparna i verktygsfältet markerar du den typ av fält som du vill lägga till.

Följande fälttyper är tillgängliga:

* Text-/sifferinmatning. Se [Lägga till inmatningsfält](#adding-input-fields).
* Välj nedrullningsbar lista. Se [Lägga till nedrullningsbara listor](#adding-drop-down-lists).
* Flera alternativ via kryssrutor. Se [Lägga till kryssrutor](#adding-checkboxes).
* Exklusivt val via alternativknappar. Se [Lägga till alternativknappar](#adding-radio-buttons).
* Rösta i ett alternativrutnät. Se [Lägga till stödraster](#adding-grids).
* Nummer och datum. Se [Lägga till datum och nummer](#adding-dates-and-numbers).
* Prenumeration/avprenumeration på en informationstjänst. Se [Kryssrutor](#subscription-checkboxes)för prenumeration.
* Captcha-validering. Se [Infoga en captcha](#inserting-a-captcha).
* Knappen Hämta. [Överför en fil](#uploading-a-file).
* Dold konstant. Se [Infoga en dold konstant](#inserting-a-hidden-constant).

Ange svarslagringsläget: uppdaterar ett fält i databasen (lagrar endast det senast sparade värdet) eller lagrar det i en variabel (svaret lagras inte). Mer information finns i [Svarslagringsfält](../../web/using/web-forms-answers.md#response-storage-fields).

>[!NOTE]
>
>Som standard infogas fältet längst ned i det aktuella trädet. Använd pilarna i verktygsfältet för att flytta det uppåt eller nedåt.

## Guiden Skapa fält {#field-creation-wizard}

För varje sida i formuläret kan du lägga till ett fält via den första knappen i verktygsfältet. Gå till **[!UICONTROL Add using the wizard]** menyn.

![](assets/s_ncs_admin_survey_add_field_menu.png)

Välj den typ av fält som du vill skapa: du kan välja att lägga till ett fält i databasen, en variabel eller att importera en grupp med fält som har skapats i ett annat formulär och samlats in i en behållare.

Klicka **[!UICONTROL Next]** och markera lagringsfältet eller variabeln, eller behållaren som du vill importera.

![](assets/s_ncs_admin_webform_wz_confirm_db.png)

Klicka **[!UICONTROL Finish]** för att infoga det markerade fältet på sidan.

![](assets/s_ncs_admin_webform_wz_insert_field.png)

## Lägga till inmatningsfält {#adding-input-fields}

Om du vill lägga till ett inmatningsfält klickar du på **[!UICONTROL Input control]** knappen och väljer den typ av fält som du vill lägga till.

![](assets/s_ncs_admin_webform_select_field.png)

### Typer av indatafält {#types-of-input-fields}

Fem olika typer av textfält kan infogas på en formulärsida:

* **Text**: gör att användaren kan skriva en text på en rad.

   ![](assets/s_ncs_admin_survey_txt_ex.png)

* **Antal**: gör att användaren kan ange ett nummer på en rad. Mer information finns i [Lägga till siffror](#adding-numbers).

   När sidan har godkänts kontrolleras fältinnehållet för att kontrollera att det angivna värdet är kompatibelt med fältet. Mer information finns i [Definiera kontrollinställningar](../../web/using/form-rendering.md#defining-control-settings).

* **Lösenord**: gör att användaren kan skriva text på en rad. Under textinmatning ersätts tecknen med punkter:

   ![](assets/s_ncs_admin_survey_passwd_ex.png)

   >[!CAUTION]
   >
   >Lösenord lagras okrypterade i databasen.

* **Flerradig text**: gör att användaren kan skriva text på flera rader.

   ![](assets/s_ncs_admin_survey_txtmulti_ex.png)

   >[!CAUTION]
   >
   >Flerradiga textfält är specifika fält som kan innehålla vagnreturer. Deras lagringsutrymme måste associeras med ett fält som är mappat till ett XML-element, inte ett XML-attribut. Mer information om datatyperna i scheman finns i kapitlet&quot;Schemareferens&quot; i [det här avsnittet](../../configuration/using/about-schema-reference.md).
   >   
   >Om du använder modulen **Undersökning** kan du lagra den här typen av fält i ett arkiverat fält som automatiskt anpassar sig till formatet. Mer information finns i [det här avsnittet](../../web/using/about-surveys.md).

* **Flerradig text**: gör att användaren kan skriva text med en layout som ska sparas i HTML-format.

   ![](assets/s_ncs_admin_survey_txthtmli_ex.png)

   Du kan välja vilken typ av redigerare som ska vara tillgänglig för användarna. Använd den nedrullningsbara rutan för **[!UICONTROL HTML editor]** fältet på **[!UICONTROL Advanced]** fliken för att göra detta.

   ![](assets/webapp_enrich_text_type.png)

   Hur många ikoner som visas varierar beroende på vilken typ av redigerare som används. För en **[!UICONTROL Advanced]** redigerare kommer återgivningen att se ut så här:

   ![](assets/webapp_enrich_text_max.png)

### Konfigurera inmatningsfält {#configure-input-fields}

Indatafält konfigureras alla baserat på samma läge med följande alternativ:

![](assets/s_ncs_admin_survey_txt_param.png)

På fliken **[!UICONTROL General]** kan du ange fältets namn och vid behov tilldela det ett standardvärde.

Svarslagringsläget kan ändras via **[!UICONTROL Edit storage...]** länken. Värdena kan lagras i ett befintligt fält i databasen. eller så kan du välja att inte spara information i databasen (använd en lokal variabel).

>[!NOTE]
>
>Lagringslägen anges i [svarslagringsfält](../../web/using/web-forms-answers.md#response-storage-fields)

På fliken **[!UICONTROL Advanced]** kan du definiera visningsparametrar för fältet (placering av etiketter, justering osv.). Se [Definiera webbformulärslayout](../../web/using/defining-web-forms-layout.md).

## Lägga till nedrullningsbara listor {#adding-drop-down-lists}

Du kan infoga en nedrullningsbar lista på en undersökningssida. På så sätt kan användaren välja ett värde bland dem som finns i en nedrullningsbar meny.

![](assets/s_ncs_admin_survey_dropdown_sample.png)

Om du vill lägga till en listruta på en formulärsida klickar du på **[!UICONTROL Selection controls > Drop-down list]** knappen i verktygsfältet i sidredigeraren.

![](assets/s_ncs_admin_survey_create_dropdown.png)

Välj svarslagringsläge och bekräfta ditt val.

Här definierar du etiketter och värden för listan i den nedre delen av **[!UICONTROL General]** fliken. Om informationen lagras i ett befintligt fält i databasen och det är ett uppräkningsfält, kan du fylla i värdena automatiskt genom att klicka på **[!UICONTROL Initialize the list of values from the database]** , vilket visas nedan:

![](assets/s_ncs_admin_survey_database_values.png)

>[!NOTE]
>
>Använd pilarna till höger om värdelistan för att ändra deras ordningsföljd.

Om data lagras i en länkad tabell kan du markera det fält där de värden som ska föreslås i listan sparas. Om du t.ex. markerar landstabellen klickar du på **[!UICONTROL Initialize the list of values from the database...]** och markerar det önskade fältet.

![](assets/s_ncs_admin_survey_preload_values.png)

Klicka sedan på **[!UICONTROL Load]** länken för att hämta värdena:

![](assets/s_ncs_admin_survey_load_button.png)

>[!CAUTION]
>
>Upprepa den här åtgärden när listan uppdateras för att uppdatera värdena i erbjudandet.

## Lägga till kryssrutor {#adding-checkboxes}

För att användaren ska kunna välja ett alternativ måste du använda en kryssruta.

![](assets/s_ncs_admin_survey_check_box.png)

Om du vill lägga till en kryssruta i ett formulär klickar du på **[!UICONTROL Selection controls > Checkbox...]** -ikonen i verktygsfältet i sidredigeraren.

Välj svarslagringsläge och bekräfta ditt val.

Ange etiketten för rutan i **[!UICONTROL Label]** fältet på **[!UICONTROL General]** fliken.

![](assets/s_ncs_admin_survey_check_box_edit.png)

Med en kryssruta kan du tilldela ett värde till lagringsfältet (eller värdet) beroende på om kryssrutan är markerad eller inte. I **[!UICONTROL Values]** avsnittet kan du ange det värde som ska tilldelas om rutan är markerad (i **[!UICONTROL Value]** fältet) och det värde som ska tilldelas om den inte är markerad (i **[!UICONTROL Empty value]** fältet). Dessa värden beror på datalagringsformatet.

Om lagringsfältet (eller variabeln) är booleskt, dras värdet som ska tilldelas om rutan inte är markerad automatiskt från. I det här fallet erbjuds endast **[!UICONTROL Value if checked]** fältet, vilket visas nedan:

![](assets/s_ncs_admin_survey_check_box_enum.png)

## Exempel: Tilldela ett värde till ett fält om en ruta är markerad {#example--assign-a-value-to-a-field-if-a-box-is-checked}

Vi vill infoga en kryssruta i ett formulär för att skicka en underhållsbegäran, som visas nedan:

![](assets/s_ncs_admin_survey_check_box_ex.png)

Informationen överförs till databasen och till ett befintligt fält (i det här fallet **[!UICONTROL Comment]** fältet):

![](assets/s_ncs_admin_survey_check_box_ex_list.png)

Om rutan &quot;Maintenance required&quot; (Underhåll krävs) är markerad kommer kolumnen att innehålla &quot;Maintenance required&quot; (Underhåll krävs). **[!UICONTROL Comment]** Om rutan inte är markerad visas &quot;Maintenance not required&quot; i kolumnen. Om du vill få det här resultatet använder du följande konfiguration i kryssrutan på formulärsidan:

![](assets/s_ncs_admin_survey_check_box_ex_edit.png)

## Lägga till alternativknappar {#adding-radio-buttons}

Med alternativknappar kan du erbjuda användaren en serie exklusiva alternativ att välja bland. Det här är olika värden för samma fält.

![](assets/s_ncs_admin_survey_radio_button.png)

Du kan skapa alternativknappar var för sig (enhetsknappar) eller via en flervalslista, men eftersom alternativknapparna är avsedda att markera ett alternativ skapar vi alltid minst ett par alternativknappar, aldrig bara en enda knapp.

>[!CAUTION]
>
>Om du vill göra markeringen obligatorisk måste du skapa en flervalslista.

### Lägg till enskilda knappar {#add-single-buttons}

Om du vill lägga till en alternativknapp på en formulärsida går du till **[!UICONTROL Selection controls > Radio button]** menyn i verktygsfältet i sidredigeraren och väljer ett lagringsläge.

![](assets/s_ncs_admin_survey_radio_button_sample.png)

Alternativknappar konfigureras på ungefär samma sätt som kryssrutor (se [Lägga till kryssrutor](#adding-checkboxes)). Inget värde tilldelas dock om alternativet inte är markerat. Om flera knappar ska vara beroende av varandra, d.v.s. om du markerar en av dem avmarkeras de andra automatiskt, måste de lagras i samma fält. Om de inte lagras i databasen måste samma lokala variabel användas för tillfällig lagring. Se [Svarslagringsfält](../../web/using/web-forms-answers.md#response-storage-fields).

### Lägga till en lista med knappar {#add-a-list-of-buttons}

Om du vill lägga till alternativknappar via en lista går du till **[!UICONTROL Selection controls>Multiple choice]** menyn i verktygsfältet i sidredigeraren.

![](assets/s_ncs_admin_survey_radio_button_sample2.png)

Lägg till så många alternativknappar som det finns etiketter för. Fördelen med den här funktionen är att du kan importera värden från ett befintligt fält (om det är ett specificerat fält) och låta användaren välja ett alternativ. Layouten för knappar är dock mindre flexibel.

>[!NOTE]
>
>Webbformulär tillåter inte att du väljer flera värden. Flera markeringar kan bara aktiveras för formulär av typen **Undersökning** . Mer information finns i [det här avsnittet](../../web/using/about-surveys.md).\
>Det är dock möjligt att infoga ett **[!UICONTROL Multiple choice]** typfält i ett webbprogram. men utan att godkänna valet av flera värden: alternativen kan väljas med alternativknappar.

## Lägga till stödraster {#adding-grids}

Rutnät används för att utforma röstsidor i webbprogram. På så sätt kan du erbjuda en lista med alternativknappar för att besvara enkät- eller utvärderingstyper på webbformulär, som visas nedan:

![](assets/s_ncs_admin_survey_vote_param.png)

Om du vill använda den här typen av element i ett formulär skapar du ett enkelt rutnät och lägger till en linje för varje element som ska utvärderas.

![](assets/s_ncs_admin_survey_vote_sample.png)

Antalet alternativknappar på varje rad i rutnätet matchar antalet värden som definieras i det enkla rutnätet.

![](assets/s_ncs_admin_survey_vote_ex.png)

Endast ett alternativ kan väljas per stödlinje.

>[!NOTE]
>
>I vårt exempel är rutnätets etikett dold. Om du vill göra det går du till **[!UICONTROL Advanced]** fliken och **[!UICONTROL Label position]** visar det som **[!UICONTROL Hidden]** . Se [Definiera placeringen av etiketter](../../web/using/defining-web-forms-layout.md#defining-the-position-of-labels).

## Lägga till datum och nummer {#adding-dates-and-numbers}

Innehållet i formulärfälten kan formateras så att de matchar data som lagras i databasen eller så att de uppfyller ett visst krav. Du kan skapa lämpliga fält för inmatning av siffror och datum.

### Lägga till datum {#adding-dates}

![](assets/s_ncs_admin_survey_date_calendar.png)

Om du vill att användaren ska kunna ange ett datum på en formulärsida väljer du **[!UICONTROL Add input field > Date...]** i verktygsfältet eller sidredigeraren.

Ange en etikett för fältet och konfigurera datalagringsläget.

![](assets/s_ncs_admin_survey_date_edit.png)

I fönstrets nedre del kan du välja datum- och tidsformat för de värden som lagras i det här fältet.

![](assets/s_ncs_admin_survey_date_edit_values.png)

Du kan också välja att inte visa datum (eller tid).

Du kan välja datum via en kalender eller listruta. Du kan också ange dem direkt i fältet, men de måste matcha det format som anges på skärmen ovan.

>[!NOTE]
>
>Som standard anges datum som används i formulär via en kalender. För flerspråkiga formulär bör du kontrollera att kalendrar finns tillgängliga på alla språk som används. Se [Översätta ett webbformulär](../../web/using/translating-a-web-form.md).

I vissa fall kan det dock vara enklare att använda nedrullningsbara listor (till exempel när du anger födelsedatum).

![](assets/s_ncs_admin_survey_date_list_select.png)

Det gör du genom att klicka på **[!UICONTROL Advanced]** fliken och välja indataläge med **[!UICONTROL Drop-down lists]**.

![](assets/s_ncs_admin_survey_date_selection.png)

Du kan sedan ange gränser för de värden som finns i listan.

![](assets/s_ncs_admin_survey_date_first_last_y.png)

### Lägga till tal {#adding-numbers}

Du kan skapa lämpliga fält för inmatning av tal.

![](assets/s_ncs_admin_survey_number.png)

I ett numeriskt fält kan användaren bara ange siffror. Inmatningskontrollen används automatiskt när sidan godkänns.

Beroende på i vilket fält data lagras i databasen kan särskild formatering eller vissa begränsningar användas. Du kan också ange högsta och lägsta värden. Den här fälttypen är konfigurerad på följande sätt:

![](assets/s_ncs_admin_survey_number_edit.png)

Standardvärdet är det värde som visas i fältet när formuläret publiceras. Den kan korrigeras av användaren.

Du kan lägga till ett prefix och/eller suffix till det numeriska fältet via **[!UICONTROL Advanced]** fliken enligt nedan:

![](assets/s_ncs_admin_survey_number_ex_conf.png)

I formuläret kommer återgivningen att se ut så här:

![](assets/s_ncs_admin_survey_number_ex.png)

## Kryssrutor för prenumeration {#subscription-checkboxes}

Du kan lägga till kontroller som tillåter användare att prenumerera på eller avbryta prenumerationen på en eller flera informationstjänster (nyhetsbrev, varningar, meddelanden i realtid osv.). Användaren kontrollerar motsvarande tjänst för att prenumerera.

Om du vill skapa en prenumeration klickar du på **[!UICONTROL Advanced controls>Subscription]**.

![](assets/s_ncs_admin_survey_subscription_edit.png)

Ange kryssrutans etikett och välj informationstjänst i **[!UICONTROL Service]** listrutan.

>[!NOTE]
>
>Informationstjänster finns på [den här sidan](../../delivery/using/managing-subscriptions.md).

Användaren prenumererar på tjänsten genom att markera det relevanta alternativet.

![](assets/s_ncs_admin_survey_subscribe.png)

>[!CAUTION]
>
>Om användaren redan prenumererar på en informationstjänst och kryssrutan som är länkad till den här tjänsten inte är markerad när han eller hon godkänner formuläret, kommer han/hon att avbeställa prenumerationen.

Exempel på prenumerationer och hänvisningar finns i [det här avsnittet](../../web/using/about-surveys.md).

## Infoga en captcha {#inserting-a-captcha}

Syftet med **captcha** -tester är att förhindra bedräglig användning av dina webbformulär.

>[!CAUTION]
>
>Om formuläret innehåller flera sidor måste Captcha alltid placeras på den sista sidan, precis före lagringsrutan, för att förhindra att säkerhetsåtgärder kringgås.

Om du vill infoga en Captcha i ett formulär klickar du på den första knappen i verktygsfältet och väljer **[!UICONTROL Advanced controls>Captcha]**.

![](assets/s_ncs_admin_survey_add_captcha.png)

Ange fältets etikett. Den här etiketten visas framför Captcha-visningsområdet. Du kan ändra placeringen av den här etiketten på **[!UICONTROL Advanced]** fliken.

![](assets/s_ncs_admin_survey_captcha_adv.png)

>[!NOTE]
>
>För **[!UICONTROL captcha]** typkontroller behöver du inte ange ett lagringsfält eller en variabel.

Captcha infogas på sidan med ett inmatningsfält under den visuella informationen. Dessa två element kan inte separeras och betraktas som ett objekt i sidlayouten (de upptar en enda cell).

![](assets/s_ncs_admin_survey_captcha_sample.png)

När sidan har bekräftats visas inmatningsfältet i rött om innehållet i Captcha inte har angetts korrekt.

![](assets/s_ncs_admin_survey_captcha_error.png)

Du kan skapa ett felmeddelande som ska visas. Det gör du genom att använda **[!UICONTROL Personalize the message]** länken på **[!UICONTROL General]** fliken.

![](assets/s_ncs_admin_survey_captcha_error_msg.png)

>[!NOTE]
>
>Bildtexter är alltid åtta tecken långa. Du kan inte ändra det här värdet.

## Överföra en fil {#uploading-a-file}

Du kan lägga till ett överföringsfält på en sida. Den här funktionen kan vara användbar för fildelning i intranät.

![](assets/s_ncs_admin_survey_download_file.png)

Om du vill infoga ett överföringsfält på en formulärsida väljer du **[!UICONTROL Advanced controls > File...]** menyn i verktygsfältet i sidredigeraren.

Som standard lagras de överförda filerna i resursfiler som är tillgängliga via **[!UICONTROL Resources > Online > Public resources]** menyn. Du kan använda ett skript för att ändra det här beteendet. Det här skriptet kan använda de funktioner som definieras i JSAPI-dokumentationen [för](http://docs.campaign.adobe.com/doc/AC/en/jsapi/index.html)Campaign, inklusive de som rör filhantering.

Du kan lagra länken till dessa filer i en lokal variabel eller i ett databasfält. Du kan till exempel utöka mottagarschemat för att lägga till en länk till filbaserade resurser.

>[!CAUTION]
>
>* Den här filtypen måste reserveras för formulär med säker åtkomst (med hjälp av autentiseringsuppgifter).
>* Adobe Campaign kontrollerar inte storleken eller typen av resurs som överförts: Därför rekommenderar vi att du endast använder överföringsfält för säkra intranätplatser.
>* Om flera servrar är länkade till instansen (belastningsutjämningsarkitektur) måste du se till att anrop till webbformuläret kommer fram på samma server.
>* Dessa implementeringar kräver hjälp av Adobe Campaign Consulting-teamet.
>



## Infoga en dold konstant {#inserting-a-hidden-constant}

Du kan markera ett fält när användaren skickar en av sidorna i formuläret. Det gör du genom att placera en konstant på sidan och ange värdet och lagringsplatsen.

Det här fältet är inte synligt för användaren, men kan användas för att utöka data i användarprofilen.

I följande exempel fylls mottagarprofilens **ursprungsfil** i automatiskt när en användare godkänner den här sidan. Konstanten visas inte på sidan.

![](assets/s_ncs_admin_survey_constante.png)

