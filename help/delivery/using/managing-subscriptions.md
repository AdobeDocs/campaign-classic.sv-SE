---
title: Hantera prenumerationer
seo-title: Hantera prenumerationer
description: Hantera prenumerationer
seo-description: null
page-status-flag: never-activated
uuid: a2c526fa-3080-4dd5-9628-f0e7040f93cd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: subscriptions-and-referrals
discoiquuid: 9a61fe74-f779-4f23-be25-3d9a8e95704a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Hantera prenumerationer{#managing-subscriptions}

## Om informationstjänster {#about-information-services}

En informationstjänst omfattar

* Registrering och prenumeration (deltagande),
* Avregistrering, frivillig avregistrering (avanmälan) eller automatisk avprenumeration (tidsbegränsad tjänst, t.ex. ett proverbjudande).
* Bekräftelsemekanismer för prenumeration och avprenumeration (enkla mekanismer med bekräftelse, dubbel anmälan osv.),
* Spårning av prenumerationshistorik.

Som standard innehåller dessa tjänster särskilda statistiska rapporter: abonnemangsspårning, lojalitetsnivå, trender för avanmälan osv.

För e-postmeddelanden genereras de obligatoriska länkarna för att avsluta prenumerationen automatiskt, och hela processen för att anmäla sig/avanmäla sig är helt automatiserad, med historikspårning för att garantera att gällande regler följs fullt ut.

Det finns tre olika sätt att prenumerera på/ta bort abonnemang:

1. manuell
1. genom import (endast prenumeration),
1. via ett webbformulär

>[!NOTE]
>
>Ett exempel på hur du skapar ett prenumerationsformulär med dubbel anmälan finns i [det här avsnittet](../../web/using/use-cases--web-forms.md#create-a-subscription--form-with-double-opt-in).

## Skapa en informationstjänst {#creating-an-information-service}

Du kan skapa och hantera prenumerationer på informationstjänster med tillhörande bekräftelsemeddelanden eller automatiska leveranser till prenumeranter.

Gå till **[!UICONTROL Profiles and Targets]** universum och klicka på **[!UICONTROL Services and Subscriptions]** länken för att få tillgång till informationstjänstkartan.

![](assets/s_ncs_user_services_new.png)

Om du vill redigera en befintlig tjänst klickar du på dess namn. Om du vill skapa en tjänst klickar du på **[!UICONTROL Create]** knappen ovanför listan.

![](assets/s_ncs_user_services_add.png)

* Ange namnet på tjänsten i **[!UICONTROL Label]** fältet och välj leveranskanal: e-post, mobil, Facebook, Twitter eller mobilappar.

   >[!NOTE]
   >
   >Prenumerationer på Facebook och Twitter beskrivs i [det här avsnittet](../../social/using/about-social-marketing.md). Prenumerationer på mobilappar beskrivs i [Om mobilappskanal](../../delivery/using/about-mobile-app-channel.md).

* För en tjänst av typen E-post väljer du **Leveransläge**. Möjliga lägen är: **[!UICONTROL Newsletter]** eller **[!UICONTROL Viral]**.
* Du kan skicka **bekräftelsemeddelanden** för en prenumeration eller en prenumeration. För att göra detta väljer du de leveransmallar som ska användas för att skapa motsvarande leveranser från **[!UICONTROL Subscription]** - och **[!UICONTROL Unsubscription]** fälten. Dessa mallar måste konfigureras med en **[!UICONTROL Subscription]** typmålmappning, utan ett definierat mål. Se avsnittet [Om e-postkanal](../../delivery/using/about-email-channel.md).
* Som standard är prenumerationerna obegränsade. Du kan avmarkera alternativet om du vill definiera en giltighetslängd för tjänsten. **[!UICONTROL Unlimited]** Längden kan anges i dagar (**[!UICONTROL d]** ) eller månader (**[!UICONTROL m]** ).

När tjänsten har sparats läggs den till i listan Tjänster och prenumerationer: Klicka på namnet för att redigera det. Flera flikar är tillgängliga. På fliken **[!UICONTROL Subscriptions]** kan du se en lista över prenumeranter på informationstjänsten (**[!UICONTROL Active subscriptions]** flik) eller historiken för prenumerationer/prenumerationer (**[!UICONTROL History]** flik). Du kan också lägga till och ta bort prenumeranter på den här fliken. Se [Lägga till och ta bort prenumeranter](#adding-and-deleting-subscribers).

![](assets/s_ncs_user_services_subscriptions.png)

Med **[!UICONTROL Detail...]** knappen kan du kontrollera prenumerationsegenskaperna för den valda mottagaren.

Du kan ändra prenumerationsegenskaperna för en mottagare.

![](assets/s_ncs_user_services_modify.png)

På kontrollpanelen klickar du på **[!UICONTROL Reports]** fliken för att spåra prenumerationer: förändringar i abonnemangsnivåer, totalt antal abonnenter osv. På den här fliken kan du arkivera rapporter och se historik.

## Lägga till och ta bort prenumeranter {#adding-and-deleting-subscribers}

På fliken **[!UICONTROL Subscriptions]** i en informationstjänst klickar du **[!UICONTROL Add]** för att lägga till prenumeranter. Du kan också högerklicka på listan med prenumeranter och välja **[!UICONTROL Add]**. Markera i vilken mapp profilerna som ska prenumereras lagras, markera profilerna som ska prenumereras och klicka sedan på **[!UICONTROL OK]** för att validera.

Om du vill ta bort prenumeranter markerar du dem och klickar på **[!UICONTROL Delete]**. Du kan också högerklicka på prenumerantlistan och välja **[!UICONTROL Delete]**.

I båda fallen kan du skicka ett bekräftelsemeddelande till de berörda användarna om en leveransmall för avanmälan har bifogats till tjänsten (se [Skapa en informationstjänst](#creating-an-information-service)). Med en varning kan du validera leveransen eller inte:

![](assets/s_ncs_user_services_update.png)

Se [Prenumerations- och](#subscription-and-unsubscription-mechanisms)avprenumerationsfunktioner.

## Leverera till abonnenterna av en tjänst {#delivering-to-the-subscribers-of-a-service}

Om du vill leverera till abonnenterna av en informationstjänst kan du rikta abonnenterna till den berörda informationstjänsten, som i följande exempel:

![](assets/s_ncs_user_wizard_target_is_a_service01.png)

>[!CAUTION]
>
>Målmappningen måste vara **[!UICONTROL Subscriptions]**.

Markera **[!UICONTROL Subscribers of an information service]** och klicka **[!UICONTROL Next]**.

![](assets/s_ncs_user_wizard_target_is_a_service02.png)

Markera den riktade informationstjänsten och klicka på **[!UICONTROL Finish]**.

![](assets/s_ncs_user_wizard_target_is_a_service03.png)

På fliken **[!UICONTROL Preview]** kan du visa en lista över prenumeranter på den valda informationstjänsten.

## Prenumerations- och avprenumerationsfunktioner {#subscription-and-unsubscription-mechanisms}

Du kan ställa in prenumerations- och avprenumerationsmekanismer för att automatisera processerna och prenumerationshanteringen.

>[!NOTE]
>
>Du kan skicka ett bekräftelsemeddelande till nya prenumeranter.\
>Innehållet i det här meddelandet definieras i informationstjänstens konfiguration via **[!UICONTROL Subscription]** - eller **[!UICONTROL Unsubscription]** -fälten.
>
>Bekräftelsemeddelandena skapas med de leveransmallar som anges i dessa fält. Dessa målmappningar måste vara **[!UICONTROL Subscriptions]**.

![](assets/s_ncs_user_subscribe_confirmation.png)

### Prenumerera på en tjänst {#subscribing-a-recipient-to-a-service}

Om du vill registrera mottagare för en informationstjänst kan du:

* Lägg till tjänsten manuellt: för att göra detta klickar du på **[!UICONTROL Subscriptions]** **[!UICONTROL Add]** och väljer den berörda informationstjänsten på fliken i deras profil.

   Mer information finns i avsnittet om profilredigering i [det här avsnittet](../../platform/using/editing-a-profile.md).

* Prenumerera automatiskt på en uppsättning mottagare för den här tjänsten. Listan med mottagare kan komma från en filtreringsåtgärd, en grupp, en mapp, en import eller en direktmarkering med hjälp av musen. Om du vill prenumerera på dessa mottagare markerar du profilerna och högerklickar. Välj **[!UICONTROL Actions > Subscribe selection to a service...]**, välj den aktuella tjänsten och starta åtgärden.
* Importera mottagare och prenumerera automatiskt på en informationstjänst. Det gör du genom att välja den berörda tjänsten i det sista steget i importguiden.

   Mer information finns i [det här avsnittet](../../platform/using/importing-data.md#import-wizard).

* Använd ett webbformulär så att mottagarna kan prenumerera på en tjänst.

   Mer information finns i [det här avsnittet](../../web/using/about-web-applications.md).

* Skapa ett målarbetsflöde och använda en **[!UICONTROL Subscription service]** ruta.

   ![](assets/s_ncs_user_subscribe_from_wf.png)

   Arbetsflöden och hur de används beskrivs i [det här avsnittet](../../workflow/using/about-workflows.md).

### Avbeställa en mottagares prenumeration på en tjänst {#unsubscribing-a-recipient-from-a-service}

#### Manuellt avabonnemang {#manual-unsubscribing}

e-postleveranser måste innehålla en länk för att avsluta prenumerationen enligt lag. Mottagarna kan klicka på den här länken för att uppdatera sin profil och uteslutas från målen för framtida leveranser.

Standardlänken för avprenumeration infogas via den sista knappen i verktygsfältet i innehållsredigeraren i leveransguiden (se [Om anpassning](../../delivery/using/about-personalization.md)). När mottagaren klickar på den här länken svartlistas profilen (avanmälan), vilket innebär att mottagaren inte längre kommer att omfattas av någon leveransåtgärd.

Mottagarna kan dock välja att avbryta prenumerationen på en tjänst utan att avbryta prenumerationen på alla tjänster. Om du vill tillåta detta kan du använda ett webbformulär (se [det här avsnittet](../../web/using/adding-fields-to-a-web-form.md#subscription-checkboxes)) eller infoga en anpassad avprenumerationslänk (se [Personaliseringsblock](../../delivery/using/personalization-blocks.md)).

Du kan också avbeställa en mottagares prenumeration manuellt från mottagarprofilen. För att göra detta klickar du på fliken **[!UICONTROL Subscriptions]** för den berörda mottagaren, markerar den eller de berörda informationstjänsterna och klickar på **[!UICONTROL Delete]**.

Du kan avsluta prenumerationen på en eller flera mottagare via den aktuella informationstjänsten. Det gör du genom att klicka på tjänstens **[!UICONTROL Subscriptions]** flik, markera mottagarna och klicka på **[!UICONTROL Delete]**.

#### Automatisk avprenumeration {#automatic-unsubscription}

En informationstjänst kan ha en begränsad varaktighet. Mottagarna kommer att avbeställa prenumerationen automatiskt när giltighetsperioden har gått ut. Den här perioden anges på fliken **[!UICONTROL Edit]** i serviceegenskaperna. Den uttrycks i dagar.

![](assets/s_ncs_user_services_delay.png)

Du kan också skapa ett avabonnemangsarbetsflöde för en population. Om du vill göra det följer du samma procedur som för ett prenumerationsarbetsflöde, men väljer **[!UICONTROL Unsubscription]** alternativet. Se [Prenumerera på en tjänst](#subscribing-a-recipient-to-a-service).

### Prenumerationsspårning {#subscriber-tracking}

Du kan spåra ändringar i prenumerationer på informationstjänster med hjälp av **[!UICONTROL Reports]** länken på kontrollpanelen.

![](assets/s_ncs_user_services_report.png)
