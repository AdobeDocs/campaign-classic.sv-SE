---
product: campaign
title: Arbetsytan i Adobe Campaign
description: Lär dig hur du använder och anpassar arbetsytan i Campaign
feature: Overview
role: Data Engineer
level: Beginner
exl-id: 5f689679-7148-4abd-a9bf-185854c64b13
source-git-commit: 0db6f107d2c161b07f42dcf7a932d319130b31e0
workflow-type: tm+mt
source-wordcount: '858'
ht-degree: 0%

---

# Arbetsytan i Adobe Campaign{#adobe-campaign-workspace}

## Utforska Adobe Campaign gränssnitt {#about-adobe-campaign-interface}

När du är ansluten till databasen kommer du åt Adobe Campaign hemsida, som är en kontrollpanel: den består av länkar och genvägar som gör att du kan komma åt funktioner, beroende på installation och allmänna plattformskonfigurationer.

Från den centrala delen av startsidan kan du använda länkar för att få åtkomst till webbdokumentationsportalen för Campaign, forumet och supportwebbplatsen.

![](assets/d_ncs_user_interface_home.png)

![](assets/do-not-localize/how-to-video.png) Upptäck arbetsytan Campaign i [video](#video)

>[!NOTE]
>
>Vilka Adobe Campaign-funktioner som är tillgängliga i din instans beror på vilka moduler och tillägg som är installerade. Vissa av dem kanske inte heller är tillgängliga, beroende på dina behörigheter och specifika konfigurationer.
>
>Innan du installerar en modul eller ett tillägg måste du kontrollera licensavtalet eller kontakta din kontoansvarige på Adobe.

### Konsol- och webbåtkomst {#console-and-web-access}

Adobe Campaign-plattformen är tillgänglig via en konsol eller en webbläsare. Se kompatibla webbläsare i [kompatibilitetsmatrisen](../../rn/using/compatibility-matrix.md#Browsers).

Webbgränssnittet liknar konsolgränssnittet. Från en webbläsare kan du använda samma navigerings- och visningsfunktioner som i konsolen, men du kan bara utföra en reducerad uppsättning åtgärder på kampanjer. Du kan till exempel visa och avbryta kampanjer, men du kan inte ändra dem. För en viss operator visas en kampanj med följande alternativ i konsolen:

![Operatören kan visa och avbryta en kampanj på kontrollpanelen för en kampanj, men även ändra den och lägga till leveranser, dokument och uppgifter i den.](assets/operation_from_console.png)

När det gäller webbåtkomst kommer alternativen främst att göra det möjligt att se

![Från en webbläsare kan samma operator bara visa och avbryta kampanjen.](assets/operation_from_web.png)

Läs mer om [med webbgränssnittet](../../campaign/using/accessing-marketing-campaigns.md#using-the-web-interface-).

### Språk {#languages}

Språket väljs när du installerar din Adobe Campaign Classic-instans.

![](assets/language.png)

Du kan välja mellan fem olika språk:

* Engelska (UK)
* Engelska (USA)
* Franska
* Tyska
* Japanska

Språket du valde för din Adobe Campaign Classic-instans kan påverka datum- och tidsformat. Mer information finns i [dokumentationen för Campaign v8 (konsol)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/new/campaign-ui){target=_blank}.

Mer information om hur du skapar en instans finns på [sidan](../../installation/using/creating-an-instance-and-logging-on.md).

>[!CAUTION]
>
>Språket kan inte ändras efter att instansen har skapats.

## Navigeringsgrunder {#navigation-basics}

### Bläddra bland sidor {#browsing-pages}

Plattformens olika funktioner är uppdelade i kärnfunktioner: använd länkarna som visas i det övre avsnittet av gränssnittet för att komma åt dem.

![](assets/overview_home.png)

Listan över kärnfunktioner som du kan komma åt beror på vilka paket och tillägg du har installerat och på din åtkomstbehörighet.

Varje funktion innehåller en uppsättning funktioner som bygger på uppgiftsrelaterade behov och användningssammanhanget. Länken **[!UICONTROL Profiles and targets]** ger dig till exempel till mottagarlistor, prenumerationstjänster, befintliga arbetsflöden för målinriktning och genvägar för att skapa dessa element.

Listorna är tillgängliga via länken **[!UICONTROL Lists]** i den vänstra delen av gränssnittet i **[!UICONTROL Profiles and Targets]**.

![](assets/recipient_list_overview.png)

### Använda tabbar {#using-tabs}

* När du klickar på en kärnfunktion eller en länk ersätter den relevanta sidan den aktuella sidan. Om du vill gå tillbaka till föregående sida klickar du på knappen **[!UICONTROL Back]** i verktygsfältet. Klicka på knappen **[!UICONTROL Home]** om du vill gå tillbaka till startsidan.

  ![](assets/d_ncs_user_interface_back_home_buttons.png)

* När det gäller en meny eller ett kortkommando för en visningsskärm (t.ex. ett webbprogram, program, leverans, rapport) visas den matchande sidan på en annan flik. På så sätt kan du bläddra mellan sidorna med hjälp av flikarna.

  ![](assets/d_ncs_user_interface_tabs.png)

### Skapa ett element {#creating-an-element}

I varje kärnfunktionsavsnitt kan du bläddra bland de tillgängliga elementen. Använd kortkommandona i avsnittet **[!UICONTROL Browsing]** för att göra detta. Med länken **[!UICONTROL Other choices]** kan du komma åt alla andra sidor, oavsett miljö.

Du kan skapa ett nytt element (leverans, webbprogram, arbetsflöde osv.) med hjälp av genvägarna i avsnittet **[!UICONTROL Create]** till vänster på skärmen. Använd knappen **[!UICONTROL Create]** ovanför listan för att lägga till nya element i listan.

Använd till exempel knappen **[!UICONTROL Create]** på leveranssidan för att skapa en ny leverans.

![](assets/d_ncs_user_interface_tab_add_del.png)


## Använda Adobe Campaign Explorer {#using-adobe-campaign-explorer}

Utforskaren i Adobe Campaign är tillgänglig via verktygsfältsikonen. Du får tillgång till Adobe Campaign alla funktioner, konfigurationsskärmar och en mer detaljerad översikt över några av plattformselementen.

Mer information om Adobe Campaign Explorer finns på följande sidor i dokumentationen för Campaign v8 (konsol):

* [Kampanjanvändargränssnittet - översikt](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/new/campaign-ui#ac-explorer-ui){target=_blank}

* [Inställningar för kampanjgränssnitt](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/config/configuration/ui-settings){target=_blank}

* [Hantera mappar och vyer i Utforskaren](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/config/configuration/folders-and-views){target=_blank}.


## Arbeta med listor {#manage-and-customize-lists}

I Campaign-klientkonsolen visas data i listor. Du kan anpassa listorna efter dina behov. Du kan till exempel lägga till kolumner, filtrera data, räkna poster, spara och dela inställningarna.

>[!NOTE]
>
>Mer information om hur du hanterar och anpassar listor i Adobe Campaign finns i [dokumentationen för Campaign v8 (konsol)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/config/configuration/ui-settings#customize-lists){target=_blank}.

## Hantera uppräkningar{#managing-enumerations}

En uppräkning (kallas även för en specificerad lista) är en fördefinierad lista med värden som du kan använda för att fylla i vissa fält. Uppräkningar hjälper till att standardisera fältvärden, vilket gör datainmatningen mer konsekvent och förenklar frågor.

När du har definierat värden visas de i en nedrullningsbar lista. Ett värde kan väljas direkt eller anges med prediktiv inmatning, vilket föreslår och slutför matchande poster. Vissa fält innehåller fördefinierade uppräkningar och ytterligare uppräkningar kan skapas om det behövs.

Läs mer om hur du **arbetar med uppräkningar** i [Adobe Campaign v8-dokumentationen (konsolen)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/config/settings/enumerations){target=_blank}.

## Självstudievideo {#video}

I den här videon visas Campaign Classic arbetsyta.

>[!VIDEO](https://video.tv.adobe.com/v/35130?quality=12)
