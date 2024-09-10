---
product: campaign
title: Hantera prenumerationer
description: Lär dig hantera prenumerationer i Adobe Campaign
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Subscriptions
role: User
exl-id: 16dddd4a-2e1a-4c78-8168-f656657bb9b8
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '1117'
ht-degree: 2%

---

# Hantera prenumerationer{#managing-subscriptions}

## Om informationstjänster {#about-information-services}

En informationstjänst omfattar

* Registrering och prenumeration (deltagande),
* Avregistrering, frivillig avregistrering (avanmälan) eller automatisk avprenumeration (tidsbegränsad tjänst, t.ex. ett proverbjudande).
* Bekräftelsemekanismer för prenumeration och avprenumeration (enkla mekanismer med bekräftelse, dubbel anmälan osv.),
* Spårning av prenumerationshistorik.

Som standard innehåller de här tjänsterna specifika statistiska rapporter: abonnentspårning, lojalitetsnivå, trender för avprenumeration osv.

För e-postmeddelanden genereras de obligatoriska länkarna för att avsluta prenumerationen automatiskt, och hela processen för att anmäla sig/avanmäla sig är helt automatiserad, med historikspårning för att garantera att gällande regler följs fullt ut.

Det finns tre olika sätt att prenumerera på/ta bort abonnemang:

1. manuell
1. genom import (endast prenumeration),
1. via ett webbformulär

>[!NOTE]
>
>Ett exempel på hur du skapar ett prenumerationsformulär med dubbel anmälan finns i [det här avsnittet](../../web/using/use-cases-web-forms.md#create-a-subscription--form-with-double-opt-in).

## Skapa en informationstjänst {#creating-an-information-service}

Du kan skapa och hantera prenumerationer på informationstjänster med tillhörande bekräftelsemeddelanden eller automatiska leveranser till prenumeranter.

Öppna fliken **[!UICONTROL Profiles and Targets]** och klicka på länken **[!UICONTROL Services and Subscriptions]** för att få åtkomst till informationstjänstkartan.

![](assets/s_ncs_user_services_new.png)

Om du vill redigera en befintlig tjänst klickar du på dess namn. Om du vill skapa en tjänst klickar du på knappen **[!UICONTROL Create]** ovanför listan.

![](assets/s_ncs_user_services_add.png)

* Ange namnet på tjänsten i fältet **[!UICONTROL Label]** och markera leveranskanalen: e-post, mobil, Facebook, X (tidigare Twitter) eller mobilprogram.

  >[!NOTE]
  >
  >Facebook- och X-prenumerationer beskrivs i [det här avsnittet](../../social/using/about-social-marketing.md). Prenumerationer på mobilappar beskrivs i [Om mobilappskanalen](about-mobile-app-channel.md).

* Välj **Leveransläge** för en e-posttjänst. Möjliga lägen är: **[!UICONTROL Newsletter]** eller **[!UICONTROL Viral]**.
* Du kan skicka **bekräftelsemeddelanden** för en prenumeration eller en prenumeration. Om du vill göra det väljer du de leveransmallar som ska användas för att skapa motsvarande leveranser från fälten **[!UICONTROL Subscription]** och **[!UICONTROL Unsubscription]**. Dessa mallar måste konfigureras med en målmappning av typen **[!UICONTROL Subscription]**, utan ett definierat mål. Se avsnittet [Om e-postkanal](about-email-channel.md).
* Som standard är prenumerationerna obegränsade. Du kan avmarkera alternativet **[!UICONTROL Unlimited]** om du vill definiera en giltighetslängd för tjänsten. Längden kan anges i dagar (**[!UICONTROL d]**) eller månader (**[!UICONTROL m]**).

När tjänsten har sparats läggs den till i listan Tjänster och prenumerationer: Klicka på namnet för att redigera den. Flera flikar är tillgängliga. På fliken **[!UICONTROL Subscriptions]** kan du visa en lista över prenumeranter på informationstjänsten (**[!UICONTROL Active subscriptions]** -fliken) eller historiken för prenumerationer/prenumerationer (**[!UICONTROL History]** -fliken). Du kan också lägga till och ta bort prenumeranter på den här fliken. Se [Lägga till och ta bort prenumeranter](#adding-and-deleting-subscribers).

![](assets/s_ncs_user_services_subscriptions.png)

Med knappen **[!UICONTROL Detail...]** kan du kontrollera prenumerationsegenskaperna för den valda mottagaren.

Du kan ändra prenumerationsegenskaperna för en mottagare.

![](assets/s_ncs_user_services_modify.png)

På kontrollpanelen klickar du på fliken **[!UICONTROL Reports]** för att spåra prenumerationer: ändringar i prenumerationsnivåer, totalt antal prenumeranter osv. Du kan arkivera rapporter och titta på historik på den här fliken.

## Lägga till och ta bort prenumeranter {#adding-and-deleting-subscribers}

På fliken **[!UICONTROL Subscriptions]** i en informationstjänst klickar du på **[!UICONTROL Add]** för att lägga till prenumeranter. Du kan också högerklicka på listan med prenumeranter och välja **[!UICONTROL Add]**. Markera i vilken mapp profilerna som ska prenumereras lagras, markera profilerna som ska prenumereras och klicka sedan på **[!UICONTROL OK]** för att validera.

Om du vill ta bort prenumeranter markerar du dem och klickar på **[!UICONTROL Delete]**. Du kan också högerklicka på prenumerantlistan och välja **[!UICONTROL Delete]**.

I båda fallen kan du skicka ett bekräftelsemeddelande till de berörda användarna om en leveransmall för avanmälan har bifogats till tjänsten (se [Skapa en informationstjänst](#creating-an-information-service)). Med en varning kan du validera leveransen eller inte:

![](assets/s_ncs_user_services_update.png)

Se [Prenumerations- och avprenumerationsmekanismer](#subscription-and-unsubscription-mechanisms).

## Leverera till abonnenterna av en tjänst {#delivering-to-the-subscribers-of-a-service}

Om du vill leverera till abonnenterna av en informationstjänst kan du rikta abonnenterna till den berörda informationstjänsten, som i följande exempel:

![](assets/s_ncs_user_wizard_target_is_a_service01.png)

>[!CAUTION]
>
>Målmappningen måste vara **[!UICONTROL Subscriptions]**.

Markera **[!UICONTROL Subscribers of an information service]** och klicka på **[!UICONTROL Next]**.

![](assets/s_ncs_user_wizard_target_is_a_service02.png)

Välj målinformationstjänsten och klicka på **[!UICONTROL Finish]**.

![](assets/s_ncs_user_wizard_target_is_a_service03.png)

På fliken **[!UICONTROL Preview]** kan du visa en lista över prenumeranter på den valda informationstjänsten.

## Prenumerations- och avprenumerationsfunktioner {#subscription-and-unsubscription-mechanisms}

Du kan ställa in prenumerations- och avprenumerationsmekanismer för att automatisera processerna och prenumerationshanteringen.

>[!NOTE]
>
>Du kan skicka ett bekräftelsemeddelande till nya prenumeranter.\
>Innehållet i det här meddelandet definieras i informationstjänstkonfigurationen via fälten **[!UICONTROL Subscription]** eller **[!UICONTROL Unsubscription]**.
>
>Bekräftelsemeddelandena skapas med de leveransmallar som anges i dessa fält. Dessa målmappningar måste vara **[!UICONTROL Subscriptions]**.

![](assets/s_ncs_user_subscribe_confirmation.png)

### Prenumerera på en tjänst {#subscribing-a-recipient-to-a-service}

Om du vill registrera mottagare för en informationstjänst kan du:

* Lägg till tjänsten manuellt: om du vill göra det klickar du på **[!UICONTROL Add]** på fliken **[!UICONTROL Subscriptions]** i profilen och väljer den aktuella informationstjänsten.

  Mer information finns i avsnittet om profilredigering i [det här avsnittet](../../platform/using/editing-a-profile.md).

* Prenumerera automatiskt på en uppsättning mottagare för den här tjänsten. Listan med mottagare kan komma från en filtreringsåtgärd, en grupp, en mapp, en import eller en direktmarkering med musen. Om du vill prenumerera på dessa mottagare markerar du profilerna och högerklickar. Välj **[!UICONTROL Actions > Subscribe selection to a service...]**, markera den aktuella tjänsten och starta åtgärden.
* Importera mottagare och prenumerera automatiskt på en informationstjänst. Det gör du genom att välja den berörda tjänsten i det sista steget i importassistenten.

  Mer information om detta finns i [det här avsnittet](../../platform/using/executing-import-jobs.md).

* Använd ett webbformulär så att mottagarna kan prenumerera på en tjänst.

  Mer information om detta finns i [det här avsnittet](../../web/using/about-web-applications.md).

* Skapar ett målarbetsflöde och använder en **[!UICONTROL Subscription service]**-ruta.

  ![](assets/s_ncs_user_subscribe_from_wf.png)

  Arbetsflöden och hur du använder dem beskrivs i [det här avsnittet](../../workflow/using/about-workflows.md).

### Avbryta prenumerationen på en mottagare från en tjänst {#unsubscribing-a-recipient-from-a-service}

#### Manuellt avabonnemang {#manual-unsubscribing}

e-postleveranser måste innehålla en länk för att avsluta prenumerationen enligt lag. Mottagarna kan klicka på den här länken för att uppdatera sin profil och uteslutas från målen för framtida leveranser.

Standardlänken för avprenumeration infogas via den sista knappen i verktygsfältet i innehållsredigeraren som finns i leveransassistenten (se [Om anpassning](about-personalization.md)). När mottagaren klickar på den här länken läggs profilen till i blockeringslista (avanmälan), vilket innebär att mottagaren inte längre kommer att omfattas av någon leveransåtgärd.

Mottagarna kan dock välja att avbryta prenumerationen på en tjänst utan att avbryta prenumerationen på alla tjänster. Om du vill tillåta detta kan du använda ett webbformulär (se [det här avsnittet](../../web/using/adding-fields-to-a-web-form.md#subscription-checkboxes)) eller infoga en anpassad avprenumerationslänk (se [Personaliseringsblock](personalization-blocks.md)).

Du kan också avbeställa en mottagares prenumeration manuellt från mottagarprofilen. Det gör du genom att klicka på fliken **[!UICONTROL Subscriptions]** för den berörda mottagaren, markera den eller de berörda informationstjänsterna och klicka på **[!UICONTROL Delete]**.

Slutligen kan du avbeställa en eller flera mottagare via den aktuella informationstjänsten. Det gör du genom att klicka på fliken **[!UICONTROL Subscriptions]** för tjänsten, markera de berörda mottagarna och klicka på **[!UICONTROL Delete]**.

#### Automatisk avprenumeration {#automatic-unsubscription}

En informationstjänst kan ha en begränsad varaktighet. Mottagarna avbeställer prenumerationen automatiskt när giltighetsperioden har löpt ut. Den här perioden anges på fliken **[!UICONTROL Edit]** i tjänstegenskaperna. Den uttrycks i dagar.

![](assets/s_ncs_user_services_delay.png)

Du kan också skapa ett avabonnemangsarbetsflöde för en population. Om du vill göra det följer du samma procedur som för ett prenumerationsarbetsflöde, men väljer alternativet **[!UICONTROL Unsubscription]**. Se [Prenumerera på en tjänst](#subscribing-a-recipient-to-a-service).

### Prenumerationsspårning {#subscriber-tracking}

Du kan spåra ändringar i prenumerationer på informationstjänster med hjälp av länken **[!UICONTROL Reports]** på instrumentpanelen.

![](assets/s_ncs_user_services_report.png)
