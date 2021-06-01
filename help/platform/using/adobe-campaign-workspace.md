---
product: campaign
title: Arbetsyta i Adobe Campaign
description: Lär dig hur du använder och anpassar arbetsytan i Campaign
feature: Översikt
role: Data Engineer
level: Beginner
exl-id: 5f689679-7148-4abd-a9bf-185854c64b13
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '826'
ht-degree: 4%

---

# Arbetsyta i Adobe Campaign{#adobe-campaign-workspace}

## Utforska Adobe Campaign gränssnitt {#about-adobe-campaign-interface}

När du är ansluten till databasen kommer du till Adobe Campaign hemsida, som är en kontrollpanel: den består av länkar och genvägar som gör att du kan komma åt funktioner, beroende på installation och allmänna plattformskonfigurationer.

Från den centrala delen av startsidan kan du använda länkar för att få åtkomst till webbdokumentationsportalen för Campaign, forumet och supportwebbplatsen.

![](assets/d_ncs_user_interface_home.png)

![](assets/do-not-localize/how-to-video.png)[ Upptäck arbetsytan i Campaign via en video](#video)

>[!NOTE]
>
>Vilka Adobe Campaign-funktioner som är tillgängliga i din instans beror på vilka moduler och tillägg som är installerade. Vissa av dem kanske inte heller är tillgängliga, beroende på dina behörigheter och specifika konfigurationer.
>
>Innan du installerar en modul eller ett tillägg måste du kontrollera licensavtalet eller kontakta din kontoansvarige på Adobe.

### Konsol- och webbåtkomst {#console-and-web-access}

Adobe Campaign-plattformen är tillgänglig via en konsol eller en webbläsare.

Webbåtkomsten har ett gränssnitt som liknar konsolen men med en reducerad uppsättning funktioner.

För en viss operator visas en kampanj med följande alternativ i konsolen:

![](assets/operation_from_console.png)

Med tillgång till webben kommer man främst att kunna se

![](assets/operation_from_web.png)

### Språk {#languages}

Språket väljs när du installerar din Adobe Campaign Classic-instans.

![](assets/language.png)

Du kan välja mellan fem olika språk:

* Engelska (UK)
* Engelska (USA)
* Franska
* Tyska
* Japanska

Språket du valde för din Adobe Campaign Classic-instans kan påverka datum- och tidsformat. Mer information om detta hittar du i det här [avsnittet](../../platform/using/adobe-campaign-workspace.md#date-and-time).

Mer information om hur du skapar en instans finns på den här [sidan](../../installation/using/creating-an-instance-and-logging-on.md).

>[!CAUTION]
>
>Språket kan inte ändras efter att instansen har skapats.

## Navigeringsgrunder {#navigation-basics}

### Bläddra bland sidor {#browsing-pages}

Plattformens olika funktioner är uppdelade i kärnfunktioner: använd länkarna som visas i det övre avsnittet av gränssnittet för att komma åt dem.

![](assets/overview_home.png)

Listan över kärnfunktioner som du kan komma åt beror på vilka paket och tillägg du har installerat och på din åtkomstbehörighet.

Varje funktion innehåller en uppsättning funktioner som bygger på uppgiftsrelaterade behov och användningssammanhanget. Länken **[!UICONTROL Profiles and targets]** leder dig till mottagarlistor, prenumerationstjänster, befintliga arbetsflöden för målinriktning och genvägar för att skapa dessa element.

Listorna är tillgängliga via länken **[!UICONTROL Lists]** i den vänstra delen av gränssnittet **[!UICONTROL Profiles and Targets]**.

![](assets/recipient_list_overview.png)

### Använd tabbar {#using-tabs}

* När du klickar på en kärnfunktion eller en länk ersätter den relevanta sidan den aktuella sidan. Om du vill gå tillbaka till föregående sida klickar du på knappen **[!UICONTROL Back]** i verktygsfältet. Klicka på knappen **[!UICONTROL Home]** om du vill gå tillbaka till startsidan.

   ![](assets/d_ncs_user_interface_back_home_buttons.png)

* När det gäller en meny eller ett kortkommando för en visningsskärm (t.ex. ett webbprogram, program, leverans, rapport) visas den matchande sidan på en annan flik. På så sätt kan du bläddra mellan sidorna med hjälp av flikarna.

   ![](assets/d_ncs_user_interface_tabs.png)

### Skapa ett element {#creating-an-element}

I varje kärnfunktionsavsnitt kan du bläddra bland de tillgängliga elementen. Använd kortkommandona i avsnittet **[!UICONTROL Browsing]** för att göra detta. Med länken **[!UICONTROL Other choices]** kan du komma åt alla andra sidor, oavsett miljö.

Du kan skapa ett nytt element (leverans, webbprogram, arbetsflöde osv.) med kortkommandona i **[!UICONTROL Create]**-avsnittet till vänster på skärmen. Använd knappen **[!UICONTROL Create]** ovanför listan för att lägga till nya element i listan.

Använd till exempel knappen **[!UICONTROL Create]** på leveranssidan för att skapa en ny leverans.

![](assets/d_ncs_user_interface_tab_add_del.png)


## Format och enheter {#formats-and-units}

### Datum och tid {#date-and-time}

Språket i din Adobe Campaign Classic-instans påverkar datum- och tidsformat.

Språk väljs vid installation av Campaign och kan inte ändras efteråt. Du kan välja: Engelska (USA), engelska (EN), franska, tyska eller japanska. Se denna [sida](../../installation/using/creating-an-instance-and-logging-on.md) för mer information om detta.

De största skillnaderna mellan amerikansk engelska och brittisk engelska är:

<table> 
 <thead> 
  <tr> 
   <th> Format<br /> </th> 
   <th> Engelska (USA)<br /> </th> 
   <th> Engelska (EN)<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Datum<br /> </td> 
   <td> Veckan börjar på söndag<br /> </td> 
   <td> Veckan börjar på måndag<br /> </td> 
  </tr> 
  <tr> 
   <td> Kort datum<br /> </td> 
   <td> <p>%2M/%2D/%4Y</p><p><strong>ex: 09/25/2018</strong></p> </td> 
   <td> <p>%2D/%2M/%4Y</p><p><strong>ex: 25/09/2018</strong></p> </td> 
  </tr> 
  <tr> 
   <td> Kort datum med tid<br /> </td> 
   <td> <p>%2M/%2D/%4Y %I:%2N:%2S %P</p><p><strong>ex: 09/25/2018 10:47:25 PM</strong></p> </td> 
   <td> <p>%2D/%2M/%4Y %2H:%2N:%2S</p><p><strong>ex: 25/09/2018 22:47:25</strong></p> </td> 
  </tr> 
 </tbody> 
</table>

### Lägg till värden i en uppräkning {#add-values-in-an-enumeration}

Med hjälp av inmatningsfälten i en nedrullningsbar lista kan du ange ett uppräkningsvärde som kan lagras och sedan visas som ett alternativ i listrutan. I fältet **[!UICONTROL City]** på fliken **[!UICONTROL General]** för en mottagarprofil kan du till exempel ange London. När du trycker på Retur för att bekräfta det här värdet tillfrågas du om du vill spara det här värdet för uppräkningen som är associerad med fältet.

![](assets/s_ncs_user_wizard_email_bat_substitute_email.png)

Om du klickar på **[!UICONTROL Yes]** är det här värdet tillgängligt i kombinationsrutan för det relevanta fältet (i det här fallet: **[!UICONTROL London]**).

>[!NOTE]
>
>Uppräkningar (kallas även&quot;specificerade listor&quot;) hanteras av administratören via **[!UICONTROL Administration > Platform > Enumerations]**-avsnittet. Mer information finns i [Hantera uppräkningar](../../platform/using/managing-enumerations.md).

### Standardenheter {#default-units}

I de fält som uttrycker en varaktighet (t.ex. giltighetsperiod för resurserna för en leverans, sista datum för godkännande av en uppgift osv.) kan värdet uttryckas i följande **enheter**:

* **[!UICONTROL s]** i sekunder,
* **[!UICONTROL mn]** i minuter,
* **[!UICONTROL h]** i timmar,
* **[!UICONTROL d]** i dagar.

![](assets/enter_unit_sample.png)

## Videokurs {#video}

I den här videon visas arbetsytan i Campaign Classic.

>[!VIDEO](https://video.tv.adobe.com/v/35130?quality=12)

Ytterligare Campaign Classic-instruktionsvideor finns [här](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=sv).
