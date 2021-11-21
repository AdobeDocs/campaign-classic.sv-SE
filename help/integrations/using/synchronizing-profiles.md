---
product: campaign
title: Synkronisera profiler
description: Synkronisera profiler
audience: integrations
content-type: reference
topic-tags: acs-connector
exl-id: 27970a6f-fb22-4418-b29c-c687fd62a78e
source-git-commit: 91dec9adb177aedc4a82879011371b54886166be
workflow-type: tm+mt
source-wordcount: '1195'
ht-degree: 3%

---

# Synkronisera profiler{#synchronizing-profiles}

![](../../assets/v7-only.svg)

ACS Connector replikerar data från Campaign v7 till Campaign Standard. Data som tas emot från Campaign v7 kan användas i Campaign Standard för att skapa leveranser. Du kan se hur profiler synkroniseras genom att utföra de åtgärder som listas nedan.

* **Lägg till nya mottagare**: Skapa en ny mottagare i Campaign v7 och bekräfta att en motsvarande profil har replikerats till Campaign Standarden. Se [Skapa en ny mottagare](#creating-a-new-recipient).
* **Uppdatera mottagare**: Redigera en ny mottagare i Campaign v7 och visa motsvarande profil i Campaign Standard för att bekräfta att uppdateringen har replikerats. Se [Redigera en mottagare](#editing-a-recipient).
* **Bygg ett arbetsflöde i Campaign Standard**: Skapa ett arbetsflöde i Campaign Standard som innehåller en fråga med en eller flera målgrupper som replikerats från Campaign v7. Se [Skapa ett arbetsflöde](#creating-a-workflow).
* **Skapa en leverans i Campaign Standard**: Följ arbetsflödet för att slutföra leveransen. Se [Skapa en leverans](#creating-a-delivery).
* **Verifiera avprenumerationslänken**: Använd ett Campaign v7-webbprogram för att kontrollera att mottagarens val att avbryta prenumerationen på en tjänst skickas till Campaign v7-databasen. Alternativet att sluta ta emot tjänsten replikeras till Campaign Standarden. Se [Ändra avprenumerationslänken](#changing-the-unsubscription-link).

## Förhandskrav {#prerequisites}

I följande avsnitt beskrivs hur ACS Connector hjälper dig att lägga till och redigera mottagare i Campaign v7 och sedan använda dem i en Campaign Standard. ACS Connector kräver följande:

* Mottagare i Campaign v7 replikerade till Campaign Standarden.
* Användarrättigheter för att köra arbetsflöden i både Campaign v7 och Campaign Standard.
* Användarrättigheter för att skapa och köra en leverans i Campaign Standard.

## Ändra avprenumerationslänken {#changing-the-unsubscription-link}

När en mottagare klickar på länken för att avbryta prenumerationen i ett e-postmeddelande som skickas av Campaign Standarden uppdateras motsvarande profil i Campaign Standarden. Om du vill vara säker på att en replikerad profil innehåller en användares val att avbryta prenumerationen på en tjänst, måste informationen skickas till Campaign v7 i stället för Campaign Standard. För att kunna utföra ändringen är tjänsten för avprenumeration länkad till ett Campaign v7-webbprogram i stället för Campaign Standard.

>[!NOTE]
>
>Be din konsult konfigurera webbprogrammet för avprenumerationstjänsten innan du följer stegen nedan.

## Skapa en ny mottagare {#creating-a-new-recipient}

1. Skapa en ny mottagare i Campaign v7 för replikering till Campaign Standard. Ange så mycket information som möjligt, inklusive mottagarens efternamn, förnamn, e-postadress och postadress. Välj dock inte en **[!UICONTROL Salutation]** eftersom det kommer att läggas till i nästa avsnitt, [Redigera en mottagare](#editing-a-recipient). Mer information finns i [Lägga till mottagare](../../platform/using/adding-profiles.md).

   ![](assets/acs_connect_profile_sync_01.png)

1. Bekräfta att den nya mottagaren har lagts till i Campaign Standarden. När du granskar profilen bör du kontrollera att de data du angav i Campaign v7 också är tillgängliga i Campaign Standard. Mer information om var du hittar profiler i Campaign Standarden finns i [Navigeringsgrunder](https://experienceleague.adobe.com/docs/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html?lang=sv).

   ![](assets/acs_connect_profile_sync_02.png)

   Som standard är den periodiska replikeringen för ACS Connector en gång var 15:e minut. Mer information finns i [Datareplikering](../../integrations/using/acs-connector-principles-and-data-cycle.md#data-replication).

## Redigera en mottagare {#editing-a-recipient}

Stegen nedan för att ändra en enda datapunkt ger ett enkelt exempel på hur Campaign v7 blir den primära databasen för Campaign Standard när datareplikering används. Att ändra eller ta bort replikerade data i Campaign v7 har samma effekt på motsvarande data i Campaign Standarden.

1. Välj den nya mottagaren från [Skapa en ny mottagare](#creating-a-new-recipient) och redigera mottagarens namn. Välj till exempel en **[!UICONTROL Salutation]** för mottagaren (t.ex. herr eller fru). Mer information finns i [Redigera en profil](../../platform/using/editing-a-profile.md).

   ![](assets/acs_connect_profile_sync_03.png)

1. Bekräfta att mottagarens namn har uppdaterats i Campaign Standard. Mer information om var du hittar profiler i Campaign Standarden finns i [Navigeringsgrunder](https://experienceleague.adobe.com/docs/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html).

   ![](assets/acs_connect_profile_sync_04.png)

   Som standard är den periodiska replikeringen för ACS Connector en gång var 15:e minut. Mer information finns i [Datareplikering](../../integrations/using/acs-connector-principles-and-data-cycle.md#data-replication).

## Skapa ett arbetsflöde {#creating-a-workflow}

Profiler och tjänster som replikerats från Campaign v7 är tillgängliga för digitala marknadsförare för att utnyttja Campaign Standardens omfattande data. Instruktionerna nedan visar hur du lägger till en Campaign Standard i ett arbetsflöde och sedan använder den med den replikerade databasen.

Mer information och fullständiga anvisningar om arbetsflöden för Campaign Standard finns i [Arbetsflöden](../../workflow/using/about-workflows.md).

1. Gå till Campaign Standarden och klicka på **[!UICONTROL Marketing Activities]**.
1. Klicka **[!UICONTROL Create]** uppe till höger.
1. Klicka på **[!UICONTROL Workflow]**.
1. Klicka **[!UICONTROL New workflow]** och **[!UICONTROL Next]**.
1. Ange ett namn för arbetsflödet i **[!UICONTROL Label]** fält och ytterligare information vid behov. Klicka på **[!UICONTROL Next]**.
1. Från **[!UICONTROL Targeting]** till vänster drar du en **[!UICONTROL Query]** för arbetsytan.

   ![](assets/acs_connect_profile_sync_05.png)

1. Dubbelklicka på **[!UICONTROL Query]** och väljer en parameter som kan användas med den replikerade databasen. Du kan till exempel:

   * Dra **[!UICONTROL Profiles]** till arbetsytan. Använd fältets nedrullningsbara meny för att välja **[!UICONTROL Is external resource]** för att hitta profiler som replikerats från Campaign v7.
   * Dra andra frågeparametrar om du vill ange de replikerade profilerna som mål ytterligare.

## Skapa en leverans {#creating-a-delivery}

>[!NOTE]
>
>Instruktionerna för att skapa leveransen fortsätter arbetsflödet som påbörjats med [Skapa ett arbetsflöde](#creating-a-workflow).

Digitala marknadsförare kan utnyttja ett Campaign v7-webbprogram för att försäkra sig om att en mottagares val att avbryta prenumerationen på en tjänst skickas till Campaign v7-databasen. När mottagaren klickar på länken för att avbryta prenumerationen replikeras alternativet att sluta ta emot tjänsten från Campaign v7 till Campaign Standard. Mer information finns i [Ändra avprenumerationslänken](#changing-the-unsubscription-link).

Följ stegen nedan för att lägga till en e-postleverans i ett befintligt arbetsflöde med den tjänst för avprenumeration som skapades i Campaign v7. Mer information och fullständiga instruktioner om arbetsflöden för Campaign Standard finns i [dokument](../../workflow/using/about-workflows.md).

>[!NOTE]
>
>Be din konsult konfigurera webbprogrammet för avprenumerationstjänsten innan du följer stegen nedan.

1. Klicka **[!UICONTROL Channels]** till vänster.
1. Dra **[!UICONTROL Email delivery]** till det befintliga arbetsflödet på arbetsytan.

   ![](assets/acs_connect_profile_sync_07.png)

1. Dubbelklicka på **[!UICONTROL Email delivery]** aktivitet och välj **[!UICONTROL Single send email]** eller **[!UICONTROL Recurring email]**. Välj alternativ och klicka på **[!UICONTROL Next]**.
1. Klicka **[!UICONTROL Send via email]** och klicka **[!UICONTROL Next]**.

   ![](assets/acs_connect_profile_sync_08.png)

1. Ange ett namn för leveransen i dialogrutan **[!UICONTROL Label]** fält och ytterligare information vid behov. Klicka på **[!UICONTROL Next]**.

   ![](assets/acs_connect_profile_sync_09.png)

1. I **[!UICONTROL Subject]** anger du det ämne som ska visas i mottagarens inkorg.
1. Klicka **[!UICONTROL Change content]** om du vill lägga till en HTML-mall.

   ![](assets/acs_connect_profile_sync_10.png)

1. Välj innehåll som innehåller länken för att avbryta prenumerationen på tjänsten. Klicka på **[!UICONTROL Confirm]**.

   ![](assets/acs_connect_profile_sync_11.png)

1. Den aktuella länken för att avbryta prenumerationen måste ersättas av en ny som använder webbprogrammet som skapats av din konsult. Leta upp länken för att avbryta prenumerationen längst ned i e-postinnehållet och klicka en gång på den. Klicka på papperskorgsikonen för att ta bort länken.

   ![](assets/acs_connect_profile_sync_12.png)

1. Klicka i samma innehållsområde och skriv **Länk för att avbryta prenumeration**.

   ![](assets/acs_connect_profile_sync_13.png)

1. Markera texten med markören och klicka på kedjeikonen.
1. Klicka på **[!UICONTROL Link to a landing page]**.

   ![](assets/acs_connect_profile_sync_14.png)

1. Klicka på mappikonen för att välja landningssidan.

   ![](assets/acs_connect_profile_sync_15.png)

1. Välj webbprogrammet som skapats av konsulten och klicka på **[!UICONTROL Confirm]**.

   ![](assets/acs_connect_profile_sync_16.png)

1. Klicka på **[!UICONTROL Create]**.
1. Återgå till arbetsflödet genom att klicka på leveransnamnet.

   ![](assets/acs_connect_profile_sync_17.png)

1. Klicka **[!UICONTROL Start]** för att skicka leveransen. Ikonen för e-postleverans blinkar för att visa att den förbereds för leverans.

   ![](assets/acs_connect_profile_sync_18.png)

1. Dubbelklicka på **[!UICONTROL Email delivery]** kanal och välj **[!UICONTROL Confirm]** för att skicka e-postmeddelandet. Klicka **[!UICONTROL OK]** för att skicka meddelanden.

   ![](assets/acs_connect_profile_sync_19.png)

## Verifiera avprenumerationstjänsten {#verifying-the-unsubscription-service}

Följ instruktionerna i [Skapa ett arbetsflöde](#creating-a-workflow) och [Skapa en leverans](#creating-a-delivery) innan du går till stegen nedan.

1. Mottagaren klickar på länken för att avbryta prenumerationen i e-postleveransen.

   ![](assets/acs_connect_profile_sync_20.png)

1. Mottagaren bekräftar avbeställningen.

   ![](assets/acs_connect_profile_sync_21.png)

1. Mottagardata i Campaign v7 uppdateras för att återspegla att användaren har avbrutit prenumerationen. Bekräfta att rutan **[!UICONTROL No longer contact (by any channel)]** är markerad för mottagaren. Mer information om hur du visar en mottagare i Campaign v7 finns i [Redigera en profil](../../platform/using/editing-a-profile.md).

   ![](assets/acs_connect_profile_sync_22.png)

1. Gå till Campaign Standarden och öppna profilinformationen för mottagaren. Bekräfta att en kryssruta visas bredvid **[!UICONTROL No longer contact (by any channel)]**. Mer information om var du hittar profiler i Campaign Standarden finns i [Navigeringsgrunder](https://experienceleague.adobe.com/docs/campaign-standard/using/getting-started/discovering-the-interface/interface-description.html).

   ![](assets/acs_connect_profile_sync_23.png)
