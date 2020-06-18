---
title: Redigera en profil
seo-title: Redigera en profil
description: Redigera en profil
seo-description: null
page-status-flag: never-activated
uuid: ad3cd54e-b22f-4fae-8d2a-3e0d3e45fffb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: profile-management
discoiquuid: 93dd29e8-cf0a-4010-a3cc-f68c52c0d9ef
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: fecfff477b0750782c87c017a15e306acac4c61d
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---


# Redigera en profil{#editing-a-profile}

Om du vill visa information om en profil klickar du på profilens namn i profillistan.

Profilinformationen visas på en ny flik.

![](assets/s_user_recipient_edit.png)

Data som rör profiler grupperas i flikar.

Flikar och deras innehåll beror på din konfiguration och installerade paket.

>[!CAUTION]
>
>XML-schemat och formuläret som gäller fälten i profiltabellen nås via noden **[!UICONTROL Administration > Configuration > Data schemas]** i Adobe Campaign-trädet. Endast expertanvändare får göra ändringar i dessa scheman.
>
>Mer information finns på [den här sidan](../../configuration/using/about-schema-edition.md).

## Fliken Allmänt {#general-tab}

Den här skärmen innehåller alla allmänna data om den valda profilen. Den innehåller i synnerhet efternamn, förnamn, e-postadress, e-postmottagningsformat osv. Det ser ut så här:

![](assets/s_ncs_user_profile_general_tab.png)

>[!NOTE]
>
>När du väljer **[!UICONTROL No longer contact (by any channel)]** alternativet innebär det att profilen finns i blocklistan, dvs. att profilen har uttryckt en önskan om att inte bli kontaktad (t.ex. genom att klicka på en länk för att avbryta prenumerationen i ett nyhetsbrev). De kommer inte längre att vara inriktade på leveranser i någon kanal (e-post, direktreklam osv.). For more on this, refer to [this page](../../delivery/using/understanding-quarantine-management.md).

## Fliken Kontaktinformation {#contact-information-tab}

Den här skärmen innehåller den valda profilens e-postadress. Det ser ut så här:

![](assets/s_ncs_user_profile_details_tab.png)

På den här skärmen visas adressens kvalitetsindex samt hur många fel adressen innehåller. Denna information används direkt av postföretaget baserat på antalet fel som påträffats under tidigare leveranser och kan inte ändras manuellt.

## Fliken Annan {#other-tab}

Den här skärmen innehåller användardefinierade fält som kan anpassas efter behov. Du kan också ändra namn på fälten och definiera deras format via **[!UICONTROL Field properties...]** enligt nedan:

![](assets/s_ncs_user_profile_others_tab.png)

>[!NOTE]
>
>Mer information om fältegenskaper och om hur du lägger till fält finns på [den här sidan](../../configuration/using/new-field-wizard.md).

## Fliken Listor {#lists-tab}

På den här skärmen visas de grupper som den valda profilen tillhör. Klicka **[!UICONTROL Add]** för att prenumerera på profilen i en lista. Klicka **[!UICONTROL Detail]** för att visa beskrivningen och listan med profiler i den markerade listan.

![](assets/s_ncs_user_profile_groups_tab_details.png)

Mer information finns i [Skapa och hantera listor](../../platform/using/creating-and-managing-lists.md).

## Fliken Prenumerationer {#subscriptions-tab}

Den här skärmen innehåller de informationstjänster som profilen har prenumererat på.

![](assets/s_ncs_user_profile_subscript_tab_details.png)

Knappen **[!UICONTROL Detail]** visar egenskaperna för den valda prenumerationen. Knappen **[!UICONTROL Add]** används för att lägga till en ny prenumeration manuellt.

For more on this, refer to [this page](../../delivery/using/managing-subscriptions.md).

## Fliken Leveranser {#deliveries-tab}

På den här skärmen visas leveransloggarna för den valda profilen. Du kan även visa etiketter, datum och status för leveransåtgärder som adresserats till profilen via alla kanaler.

![](assets/s_ncs_user_profile_delivery_tab.png)

## Fliken Spårning {#tracking-tab}

På den här skärmen kan du visa spårningsloggarna för den valda profilen. Den här informationen används för att spåra profilbeteende efter leveranser.

![](assets/s_ncs_user_profile_tracking_tab.png)

På den här fliken visas den kumulativa summan av alla URL:er som spåras i leveranser.

Listan är konfigurerbar och innehåller vanligtvis: klickad URL-adress, datum och tid för klickningen samt dokumentet som innehöll URL-adressen.

>[!NOTE]
>
>Mer information om spårningsfunktioner finns på [den här sidan](../../delivery/using/monitoring-a-delivery.md).

