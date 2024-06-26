---
product: campaign
title: Definiera egenskaper för webbformulär
description: Definiera egenskaper för webbformulär
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Web Forms
exl-id: 37aaaa03-0656-4a9b-bcae-74de33e3737b
source-git-commit: 1d4990917fea54e67ed23cd0771295de03a4f01a
workflow-type: tm+mt
source-wordcount: '1375'
ht-degree: 1%

---

# Definiera egenskaper för webbformulär{#defining-web-forms-properties}



Ni kan konfigurera och anpassa webbformulär helt efter era behov. Parametrarna måste anges i egenskapsfönstret.

Egenskapsfönstret är tillgängligt via **[!UICONTROL Properties]** i webbformulärets verktygsfält. I det här fönstret kan du komma åt en rad inställningar som är specifika för webbformuläret. Vissa inställningar kan härröra från mallkonfigurationen.

![](assets/s_ncs_admin_survey_properties_general.png)

## Övergripande formuläregenskaper {#overall-form-properties}

I **[!UICONTROL General]** -fliken i egenskapsfönstret kan du ändra **Etikett** av formuläret. Vi rekommenderar att du inte ändrar **Internt namn**.

![](assets/s_ncs_admin_survey_properties_general_tab.png)

Formulärmallen väljs när formuläret skapas. Den kan inte ändras senare. Mer information om hur du skapar och hanterar formulärmallar finns i [Använda en webbformulärmall](using-a-web-form-template.md).

## Lagring av formulärdata {#form-data-storage}

Fälten i webbformulär lagras som standard i mottagartabellen. Du kan ändra tabellen som används genom att välja en ny tabell i **[!UICONTROL Document type]** fält. The **[!UICONTROL Zoom]** kan du visa innehållet i den markerade tabellen.

Som standard lagras svaren i **Svara på ett mottagarformulär** tabell.

## Konfigurera en felsida {#setting-up-an-error-page}

Du kan konfigurera en felsida: den här sidan visas om det uppstår fel under formulärkörningen.

Felsidan definieras på motsvarande flik i fönstret för formuläregenskaper.

Som standard visas följande information:

![](assets/s_ncs_admin_survey_default_error_page.png)

Innehållet i strängarna som visas definieras i **[!UICONTROL Error page]** i egenskapsfönstret. The **[!UICONTROL HTML]** visas återgivningen och **[!UICONTROL Texts]** Med -fliken kan du ändra textsträngarna och lägga till text om det behövs:

![](assets/s_ncs_admin_survey_error_page.png)

## Formulärlokalisering {#form-localization}

The **[!UICONTROL Localization]** kan du välja design- och visningsspråk för webbformuläret.

Se [Översätta ett webbformulär](translating-a-web-form.md).

## Bläddra bland och återge formulär {#form-browsing-and-rendering}

The **[!UICONTROL Rendering]** Med -fliken kan du definiera vilken typ av bläddring som ska göras mellan sidorna i webbformuläret och den återgivningsmall som ska användas.

Du kan navigera via länkar eller knappar.

![](assets/s_ncs_admin_survey_wz_02_navig_type.png)

Knappar är navigeringselement som standard. De gör att du kan utföra följande åtgärder:

* Godkänn den aktuella sidan och visa nästa sida genom att klicka **[!UICONTROL Next]**. Den här knappen visas på alla sidor utom den sista.
* Visa föregående sida genom att klicka **[!UICONTROL Previous]**. Den här knappen visas på alla sidor utom den första.
* Spara formulärsvaren genom att klicka på **[!UICONTROL Approve]** -knappen. Den här knappen visas bara på den sista sidan.

Dessa element visas längst ned på varje sida. Deras positioner kan ändras. Om du vill göra det måste du ändra formatmallen.

>[!NOTE]
>
>Det går att dölja **[!UICONTROL Previous]** på vissa sidor. Det gör du genom att gå till sidan och kontrollera **[!UICONTROL Disallow returning to the previous page]** alternativ. Det här alternativet är tillgängligt när sidträdets rot är markerat.

The **[!UICONTROL Template]** fält för **[!UICONTROL Rendering]** kan du välja ett tema bland de tillgängliga.

Teman sparas i **[!UICONTROL Administration>Configuration>Form rendering]** trädnod. Se [Välja formuläråtergivningsmall](form-rendering.md#selecting-the-form-rendering-template)

En exempelåtergivning visas i den nedre delen av egenskapsfönstret. The **[!UICONTROL Edit link]** Med -ikonen kan du visa konfigurationen för det valda temat.

![](assets/s_ncs_admin_survey_properties_render.png)

## Logotyp i formuläret {#logo-in-the-form}

Du kan ändra logotypen som används i formuläret med din egen logotyp.

I **[!UICONTROL Rendering]** -fliken i **[!UICONTROL Properties]** Klicka på glasikonen för din mall i webbappen:

![](assets/logo_glass.png)

Klicka på **[!UICONTROL Page layout]** link:

![](assets/logo_pagelayout.png)

Du kan ändra sökvägen för logotypbilden här:

![](assets/logo_path.png)

De tillgängliga bilderna finns under **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Images]**. Du kan lägga till din logotyp här.

Dessa bilder placeras i instansens bakomliggande katalog *datakit\nms\fra\img\activities* eller *datakit\nms\eng\img\activities* (ett eller flera, beroende på instansens språk).

Om du vill ha en ny bild tillgänglig i den här katalogen (och i Bilder) kontaktar du Adobe support för att göra ändringar i backend-katalogerna.

För lokala instanser kan du lägga till bilder i data själv.

Den överförda bilden behöver inte vara synlig från Campaign-klienten. Den rätta sökvägen räcker för att använda som ny logotyp.

## Texter i formuläret {#texts-in-the-form}

The **[!UICONTROL Page]** Med -fliken kan du definiera innehållet i formulärhuvudet och sidfoten. Se [Definiera sidhuvuden och sidfötter](form-rendering.md#defining-headers-and-footers).

Du kan också hantera översättningar. Se [Översätta ett webbformulär](translating-a-web-form.md).

## Formulärets tillgänglighet {#accessibility-of-the-form}

Ett webbformulär är tillgängligt för användare om det **[!UICONTROL Online]** och om det aktuella datumet ligger inom giltighetsperioden. Formulärets status ändras under publiceringssteget (se [Publicera ett formulär](publishing-a-web-form.md#publishing-a-form)). Statusen visas i **Projekt** i **[!UICONTROL General]** i egenskapsfönstret.

Giltighetsperioden är från **[!UICONTROL Start]** datum till **[!UICONTROL End date]**. Om inga datum anges i dessa fält har formuläret permanent giltighet.

![](assets/s_ncs_admin_survey_properties_date.png)

>[!NOTE]
>
>Om formuläret är stängt och dess giltighetsperiod därför inte har nåtts eller löpt ut, eller om det stängts av Adobe Campaign-operatorn, visas ett meddelande när användaren försöker få åtkomst till det. Du kan anpassa meddelandet genom att klicka **[!UICONTROL Personalize the message displayed if the form is closed...]**.

## Åtkomstkontroll {#form-access-control}

Som standard ges åtkomst till webbformulär i anonymt läge: alla operatorer som har åtkomst till formuläret tilldelas behörigheter för WebApp-operatorn.

Du kan aktivera åtkomstkontroll för att visa formuläret, t.ex. när du levererar ett formulär på en intranätsplats, för att autentisera användare. Om du vill göra det visar du **[!UICONTROL Properties]** det berörda formulärets fönster och klicka på **[!UICONTROL Enable access control]** enligt nedan:

![](assets/s_ncs_admin_survey_access_ctrl.png)

När sidan öppnas visas följande autentiseringsformulär:

![](assets/s_ncs_admin_survey_access_login.png)

Inloggning och lösenord är de som används av Adobe Campaign-operatörer. Mer information om detta finns i [det här avsnittet](../../platform/using/access-management.md).

The **[!UICONTROL Use a specific account]** kan du begränsa läs- och skrivbehörigheten för den operator som öppnar formuläret. Använd listrutan för att välja en operator eller grupp med operatorer som ska ansvara för att bevilja dessa behörigheter.

![](assets/s_ncs_admin_survey_access_op_select.png)

## URL-parametrar för formulär {#form-url-parameters}

Du kan lägga till ytterligare parametrar i URL:en för ett formulär för att anpassa dess innehåll och initiera ett sammanhang (språk, krypterat mottagar-ID, företag, beräknad formel som lagras i en variabel osv.). Detta gör att du kan ge åtkomst till ett formulär via flera olika URL:er och anpassa sidinnehållet baserat på värdet på de parametrar som anges i URL:en.

Som standard har Adobe Campaign parametrar för att förhandsgranska formuläret och kontrollera fel. Du kan skapa nya inställningar som är länkade till formuläret, som kan använda värdena för ett fält i databasen eller en lokal variabel.

## Standardparametrar {#standard-parameters}

Följande parametrar är tillgängliga som standard:

* **id** för att ange den krypterade identifieraren.
* **lang** om du vill ändra visningsspråk.
* **ursprung** för att ange den svarande personens ursprung.
* **uuuid** aktiverar formulärvisning före publicering och felspårning. Den här parametern är avsedd för internt bruk (skapande och felsökning): när du öppnar webbformuläret via den här URL:en beaktas inte de skapade posterna i spårningen (rapporter). Ursprunget tvingas till **[!UICONTROL Adobe Campaign]** värde.

  Det används tillsammans med **förhandsgranska** parametrar och/eller **debug**:

  **förhandsgranska** för att visa den senast sparade versionen. Denna parameter får endast användas i testfasen.

  **debug** för att visa datainmatningens spårning eller beräknade på formulärets sidor. Detta används för att få mer information om fel, även när formuläret har publicerats.

  >[!CAUTION]
  >
  >När formuläret visas via en URL med **uuuid** parameter, värdet för **[!UICONTROL origin]** parametern måste **Adobe Campaign**.

## Lägga till parametrar {#adding-parameters}

Parametrar kan läggas till via **[!UICONTROL Parameters...]** i formulärets egenskapsfönster. De kan göras obligatoriska enligt nedan:

![](assets/s_ncs_admin_survey_properties_param.png)

Du måste ange en lagringsplats som parametervärdet hämtas från. Välj ett av lagringsalternativen och klicka sedan på **[!UICONTROL Storage]** för att markera fältet eller variabeln i fråga. Lagringsalternativen finns i [Svarslagringsfält](web-forms-answers.md#response-storage-fields).

Svarandens status (0, 1 eller något annat värde) kan sedan läggas till i URL:en för att komma åt formuläret. Informationen kan återanvändas på formulärets sidor eller i en testruta. De sidor som visas kan villkoras baserat på värdet för sammanhanget, vilket visas nedan:

1. Hemsida för kunder (**status=1**):

   ![](assets/s_ncs_admin_survey_test_client.png)

1. Startsida för potentiella kunder (**status=0**):

   ![](assets/s_ncs_admin_survey_test_prospect.png)

1. Hemsida för andra profiler (t.ex. **status=12**):

   ![](assets/s_ncs_admin_survey_test_other.png)

Om du vill konfigurera det här formuläret skapar du en testruta och placerar den i början av diagrammet, enligt nedan:

![](assets/s_ncs_admin_survey_test.png)

I testrutan kan du konfigurera sidordningsvillkoren:

![](assets/s_ncs_admin_survey_test_box.png)
