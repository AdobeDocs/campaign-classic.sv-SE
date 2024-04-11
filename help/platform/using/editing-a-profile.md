---
product: campaign
title: Redigera en profil
description: Redigera en profil
feature: Profiles
audience: platform
content-type: reference
topic-tags: profile-management
exl-id: 0f3a5582-5c90-4393-bee8-d9e2f07e5982
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 4%

---

# Redigera en profil{#editing-a-profile}



Om du vill visa information om en profil klickar du på profilens namn i profillistan.

Profilinformationen visas på en ny flik.

![](assets/s_user_recipient_edit.png)

Data som rör profiler grupperas i flikar.

Flikar och deras innehåll beror på din konfiguration och installerade paket.

>[!CAUTION]
>
>XML-schemat och formuläret som gäller fälten i profiltabellen är tillgängliga via **[!UICONTROL Administration > Configuration > Data schemas]** noden i Adobe Campaign-trädet. Endast expertanvändare får göra ändringar i dessa scheman.
>
>Mer information finns i [den här sidan](../../configuration/using/about-schema-edition.md).

## fliken Allmänt {#general-tab}

Den här skärmen innehåller alla allmänna data om den valda profilen. Den innehåller i synnerhet efternamn, förnamn, e-postadress, e-postmottagningsformat osv. Det ser ut så här:

![](assets/s_ncs_user_profile_general_tab.png)

>[!NOTE]
>
>När **[!UICONTROL No longer contact (by any channel)]** om du väljer det här alternativet innebär det att profilen är på blockeringslista, dvs. att profilen har uttryckt en önskan om att inte bli kontaktad (till exempel genom att klicka på en länk för att avbryta prenumerationen i ett nyhetsbrev). De kommer inte längre att vara inriktade på leveranser i någon kanal (e-post, direktreklam osv.). Mer information finns på [den här sidan](../../delivery/using/understanding-quarantine-management.md).

## Fliken Kontaktinformation {#contact-information-tab}

Den här skärmen innehåller den valda profilens e-postadress. Det ser ut så här:

![](assets/s_ncs_user_profile_details_tab.png)

På den här skärmen visas adressens kvalitetsindex samt hur många fel adressen innehåller. Denna information används direkt av postföretaget baserat på antalet fel som påträffats under tidigare leveranser och kan inte ändras manuellt.

## Fliken Annan {#other-tab}

Den här skärmen innehåller användardefinierade fält som kan anpassas efter behov. Du kan också ändra fältnamnen och definiera deras format via **[!UICONTROL Field properties...]**, enligt nedan:

![](assets/s_ncs_user_profile_others_tab.png)

>[!NOTE]
>
>Mer information om fältegenskaper och om hur du lägger till fält finns i [den här sidan](../../configuration/using/new-field-wizard.md).

## Fliken Listor {#lists-tab}

På den här skärmen visas de grupper som den valda profilen tillhör. Klicka **[!UICONTROL Add]** om du vill prenumerera profilen på en lista. Klicka **[!UICONTROL Detail]** för att visa beskrivningen och listan med profiler i den markerade listan.

![](assets/s_ncs_user_profile_groups_tab_details.png)

Mer information finns i [Skapa och hantera listor](../../platform/using/creating-and-managing-lists.md).

## Fliken Prenumerationer {#subscriptions-tab}

Den här skärmen innehåller de informationstjänster som profilen har prenumererat på.

![](assets/s_ncs_user_profile_subscript_tab_details.png)

The **[!UICONTROL Detail]** visas egenskaperna för den valda prenumerationen. The **[!UICONTROL Add]** används för att lägga till en ny prenumeration manuellt.

Mer information finns på [den här sidan](../../delivery/using/managing-subscriptions.md).

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
>Mer information om spårningsfunktioner finns i [den här sidan](../../delivery/using/delivery-dashboard.md).
