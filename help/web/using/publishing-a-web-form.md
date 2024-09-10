---
product: campaign
title: Publicera ett webbformulär
description: Publicera ett webbformulär
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Web Forms
exl-id: 1c66b8e8-7590-4767-9b2f-a9a509df4508
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '1284'
ht-degree: 0%

---

# Publicera ett webbformulär{#publishing-a-web-form}



## Läs in formulärdata i förväg {#pre-loading-the-form-data}

Om du vill uppdatera profilerna som lagras i databasen via ett webbformulär kan du använda en förinläsningsruta. I rutan för förinläsning kan du ange hur posten ska uppdateras i databasen.

Följande identifieringsmetoder är möjliga:

* **[!UICONTROL Adobe Campaign Encryption]**

  Den här krypteringsmetoden använder krypterad Adobe Campaign-identifierare (ID). Den här metoden kan bara användas på ett Adobe Campaign-objekt och det krypterade ID:t kan bara genereras av Adobe Campaign-plattformen.

  När du använder den här metoden måste du anpassa formulärets URL för att kunna leverera till e-postadressen genom att lägga till parametern **`<%=escapeUrl(recipient.cryptedId) %>`**. Mer information finns i [Leverera ett formulär via e-post](#delivering-a-form-via-email).

* **[!UICONTROL DES encryption]**

  ![](assets/s_ncs_admin_survey_preload_methods_001.png)

  Den här krypteringsmetoden använder en extern identifierare (ID) som är länkad till en nyckel som delas av Adobe Campaign och den externa providern. I fältet **[!UICONTROL Des key]** kan du ange den här krypteringsnyckeln.

* **[!UICONTROL List of fields]**

  Med det här alternativet kan du välja bland fälten i formulärets aktuella sammanhang, de som ska användas för att hitta motsvarande profil i databasen.

  ![](assets/s_ncs_admin_survey_preload_methods_002.png)

  Du kan lägga till fält i formuläregenskaperna via fliken **[!UICONTROL Parameters]** (se [Lägga till parametrar](defining-web-forms-properties.md#adding-parameters)). De placeras i formulärets URL-adress eller indatazoner.

  >[!CAUTION]
  >
  >Data i de markerade fälten är inte krypterade. Den får inte anges i krypterad form eftersom Adobe Campaign inte kan dekryptera den om alternativet **[!UICONTROL Field list]** har valts.

  I följande exempel baseras förinläsningen av profiler på e-postadressen.

  URL:en kan innehålla den okrypterade e-postadressen, och i så fall har användarna direkt åtkomst till de sidor som berör dem.

  ![](assets/s_ncs_admin_survey_preload_methods_003.png)

  Annars blir de ombedda att ange sitt lösenord.

  ![](assets/s_ncs_admin_survey_preload_methods_004.png)

  >[!CAUTION]
  >
  >Om flera fält anges i listan måste data för **ALLA FÄLT** matcha data som lagras i databasen för att profilen ska kunna uppdateras. I annat fall skapas en ny profil.
  > 
  >Den här funktionen är särskilt användbar för webbprogram, men rekommenderas inte för offentliga formulär. Det valda åtkomstkontrollalternativet måste vara &quot;Aktivera åtkomstkontroll&quot;.

Alternativet **[!UICONTROL Skip preloading if no ID]** måste vara markerat om du inte vill uppdatera profiler. I det här fallet läggs alla profiler som anges till i databasen när formuläret har godkänts. Det här alternativet används till exempel när formuläret publiceras på en webbplats.

Med alternativet **[!UICONTROL Auto-load data referenced in the form]** kan du automatiskt förhandsladda data som matchar inmatnings- och kopplingsfält i formuläret. Data som refereras i **[!UICONTROL Script]**- och **[!UICONTROL Test]**-aktiviteter berörs dock inte. Om det här alternativet inte är markerat måste du definiera fälten med alternativet **[!UICONTROL Load additional data]**.

Med alternativet **[!UICONTROL Load additional data]** kan du lägga till information som inte används på formulärets sidor, men som ändå kommer att läsas in i förväg.

Du kan till exempel förhandsladda mottagarens kön och automatiskt dirigera dem till rätt sida via en testruta.

![](assets/s_ncs_admin_survey_preload_ex.png)

## Hantera distribution och spårning av webbformulär {#managing-web-forms-delivery-and-tracking}

När formuläret har skapats, konfigurerats och publicerats kan du leverera det och spåra användarsvar.

### Formulärets livscykel {#life-cycle-of-a-form}

En forms livscykel består av tre steg:

1. **Redigeras**

   Detta är den inledande designfasen. När ett nytt formulär skapas är det i redigeringsfasen. Åtkomst till formuläret, endast i testningssyfte, kräver sedan att parametern **[!UICONTROL __uuid]** används i dess URL. Den här URL:en är tillgänglig på underfliken **[!UICONTROL Preview]**. Se [Parametrar för formulär-URL](defining-web-forms-properties.md#form-url-parameters).

   >[!CAUTION]
   >
   >Så länge formuläret redigeras är dess åtkomst-URL en en särskild URL.

1. **Väntande publikation**

   I vissa fall (till exempel när du [importerar ett formulär via ett paket](#import-web-packages)) kan ett webbformulär ha statusen **[!UICONTROL Pending publication]** tills det är live.

   >[!NOTE]
   >
   >För tekniska webbprogram (som är tillgängliga via menyn **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Web applications]**) blir ett formulär med statusen **[!UICONTROL Pending publication]** automatiskt [ publicerat](#publishing-a-form) och får statusen **[!UICONTROL Online]**.

1. **Online**

   När designfasen är klar kan blanketten skickas.

   När ett formulär har statusen **[!UICONTROL Being edited]** eller **[!UICONTROL Pending publication]** måste det [publiceras](#publishing-a-form) för att vara online och tillgängligt via webbformulärets URL i en webbläsare.

   När formuläret har publicerats kommer det att vara öppet tills det går ut.

   Formuläret kommer att vara **[!UICONTROL Live]** tills det förfaller.

   >[!CAUTION]
   >
   >Formulärets URL får inte innehålla parametern **[!UICONTROL __uuid]** för att kunna levereras.

1. **Stängd**

   När formuläret har stängts är leveransfasen slut och formuläret blir otillgängligt: det är inte längre tillgängligt för användarna.

   Utgångsdatumet kan definieras i fönstret för formuläregenskaper. Mer information finns i [Göra ett formulär tillgängligt online](#making-a-form-available-online).

Ett formulärs publiceringsstatus visas i formulärlistan.

![](assets/s_ncs_admin_survey_status.png)

### Publicera ett formulär {#publishing-a-form}

Om du vill ändra ett formulärs status måste du publicera det. Om du vill göra det klickar du på knappen **[!UICONTROL Publication]** ovanför listan med webbformulär och väljer läge i listrutan.

![](assets/webapp_publish_webform.png)

### Göra ett formulär tillgängligt online {#making-a-form-available-online}

För att användarna ska kunna komma åt formuläret måste det vara i produktion och ha startats, dvs. inom giltighetsperioden. Giltighetsdatumen anges via länken **[!UICONTROL Properties]** i formuläret.

* Använd fälten i avsnittet **[!UICONTROL Project]** för att ange start- och slutdatum för formuläret.

  ![](assets/webapp_availability_date.png)

* Klicka på länken **[!UICONTROL Personalize the message displayed if the form is closed...]** för att definiera felmeddelandet som ska visas om användaren försöker få åtkomst till formuläret medan det inte är giltigt.

  Se [Formulärets tillgänglighet](defining-web-forms-properties.md#accessibility-of-the-form).

### Leverera ett formulär via e-post {#delivering-a-form-via-email}

När du skickar en inbjudan via e-post kan du använda alternativet **[!UICONTROL Adobe Campaign Encryption]** för datavstämning. Det gör du genom att gå till leveransassistenten och anpassa länken till formuläret genom att lägga till följande parameter:

```
<a href="https://server/webApp/APP264?&id=<%=escapeUrl(recipient.cryptedId) %>">
```

I det här fallet måste avstämningsnyckeln för datalagring vara mottagarens krypterade identifierare. Mer information finns i [Förinläsning av formulärdata](#pre-loading-the-form-data).

I det här fallet måste du markera alternativet **[!UICONTROL Update the preloaded record]** i postrutan. Mer information finns i [Spara svar på webbformulär](web-forms-answers.md#saving-web-forms-answers).

![](assets/s_ncs_admin_survey_save_box_option.png)

### Loggsvar {#log-responses}

Svarsspårning kan aktiveras på en dedikerad flik för att övervaka effekten av webbformuläret. Det gör du genom att klicka på länken **[!UICONTROL Advanced parameters...]** i fönstret för formuläregenskaper och välja alternativet **[!UICONTROL Log responses]**.

![](assets/s_ncs_admin_survey_trace.png)

Fliken **[!UICONTROL Responses]** visas så att du kan visa svarandens identitet.

![](assets/s_ncs_admin_survey_trace_tab.png)

Välj en mottagare och klicka på knappen **[!UICONTROL Detail...]** för att visa de svar som ges.

![](assets/s_ncs_admin_survey_trace_edit.png)

Du kan bearbeta svarsloggarna i frågor, till exempel för att endast rikta sig till icke-svarande när du skickar påminnelser, eller för att endast erbjuda specifik kommunikation till svaranden.

### Importera webbformulärspaket {#import-web-packages}

När du exporterar och importerar ett paket som innehåller ett webbformulär från en instans till en annan instans (till exempel från scen till produktion) kan webbformulärstatusen för den nya instansen variera beroende på flera villkor. De olika fallen listas nedan.

Läs mer om de olika statusvärdena för ett webbformulär i [det här avsnittet](#life-cycle-of-a-form).

>[!NOTE]
>
>När du exporterar ett webbformulär via ett paket visas formulärstatusen i innehållet i det resulterande paketet.

* Om webbformulärets status var **[!UICONTROL Pending publication]** eller **[!UICONTROL Online]** när den exporterades från den första instansen:

   * Webbformuläret får statusen **[!UICONTROL Pending publication]** när det importeras till den nya instansen.

   * Om webbformuläret redan finns på den nya instansen ersätts det med den nya versionen av formuläret och får statusen **[!UICONTROL Pending publication]**, även om den gamla versionen av formuläret var **[!UICONTROL Online]**.

   * Oavsett om formuläret fanns eller inte måste formuläret vara [publicerat](#publishing-a-form) för att bli **[!UICONTROL Online]** på den nya instansen och tillgängligt via webbformulärets URL i en webbläsare.

* Om webbformulärets status var **[!UICONTROL Being edited]** vid export:

   * Om webbformuläret är nytt i den instans där paketet importeras får webbformuläret statusen **[!UICONTROL Being edited]**.

   * Om webbformuläret redan finns på den nya instansen är detta en ändring i ett befintligt formulär. Om den gamla versionen av formuläret var **[!UICONTROL Online]** är den gamla versionen fortfarande online tills den nya versionen av formuläret [publiceras](#publishing-a-form) igen på den nya instansen.

  >[!NOTE]
  >
  >Du kan kontrollera den senaste versionen av ditt webbformulär på fliken **[!UICONTROL Preview]**.

<!--For RN:
* Now, when a web form has the **Pending publication** status, it must be published before it becomes **Online** and accessible through the web form URL in a web browser. [Read more](../../web/using/publishing-a-web-form.md#life-cycle-of-a-form)
-->
