---
title: Filinsamlare
seo-title: Filinsamlare
description: Filinsamlare
seo-description: null
page-status-flag: never-activated
uuid: 57ef7b2b-f257-4d76-970f-55aece719cec
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: event-activities
discoiquuid: 9b937d4d-55ae-4bd4-8dc6-eea42f15b69f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b1a961822224ab0a9551f51942a5f94cf201c8ee
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%

---


# Filinsamlare{#file-collector}

Insamlaren **för** filer övervakar en eller flera filers ankomst till en katalog och aktiverar övergången för varje mottagen fil. För varje händelse innehåller en **[!UICONTROL filename]** variabel det fullständiga namnet på den mottagna filen. De insamlade filerna flyttas till en annan katalog för arkivering och för att säkerställa att de bara räknas en gång.

Som standard är filinsamlaren en beständig uppgift som testar förekomsten av filer vid de tidpunkter som anges i schemat.

Filerna måste finnas på den server där den servermodul som ansvarar för det här arbetsflödet körs. Om flera wfserver-moduler distribueras på en enda instans måste tillhörigheten för de aktiviteter som använder dessa filer eller arbetsflödets totala tillhörighet anges.

## Egenskaper {#properties}

På aktivitetens första flik kan du välja källkatalogen och vid behov filtrera de insamlade filerna. **[!UICONTROL File collector]** De andra flikarna finns i [Inkommande e-postmeddelanden](../../workflow/using/inbound-emails.md) (**[!UICONTROL Schedule]** och **[!UICONTROL Expiry]** på flikar).

![](assets/file_collect_edit.png)

1. **Hämtar filer**

   * **[!UICONTROL Directory]**

      Katalog som innehåller de filer som ska hämtas. Den här katalogen måste skapas i förväg på servern: Om den inte finns genereras ett fel.

   * **[!UICONTROL Filter]**

      Endast filer som matchar det här filtret tas med i beräkningen. De andra filerna i katalogen ignoreras. Om filtret är tomt beaktas alla filer i katalogen. Exempel på filter: ***.zip**, **import-*.txt**.

   * **[!UICONTROL Stop as soon as a file has been processed]**

      Om det här alternativet är aktiverat avslutas aktiviteten när den första filen har tagits emot. Om det finns flera filer som motsvarar filtret i katalogen kommer endast en att tas med i beräkningen. Det här alternativet garanterar att endast en händelse skickas. Den fil som tas med i beräkningen är den första i listan i alfabetisk ordning.

      Om det inte finns någon fil som matchar filtret i den angivna katalogen för en aktivitet som inte är schemalagd, och om alternativet inte är aktiverat, genereras ett fel. **[!UICONTROL Process file nonexistence]**

   * **[!UICONTROL Execution schedule]**

      Anger frekvensen för filens visningskontroll via parametrarna på **[!UICONTROL Schedule]** fliken.

1. **Felhantering**

   Följande två alternativ är tillgängliga:

   * **[!UICONTROL Process file nonexistence]**

      Det här alternativet startar en speciell övergång varje gång ingen fil som matchar filtret hittas i den angivna katalogen.

      Om aktiviteten inte är schemalagd kommer den här övergången endast att aktiveras en gång.

   * **[!UICONTROL Processing errors]**

      Med det här alternativet visas en speciell övergång som aktiveras om ett fel genereras. I det här fallet ändras inte arbetsflödet till felstatus och körningen fortsätter

      Fel som beaktas är filsystemfel (filen kunde inte flyttas, katalogen kunde inte nås osv.).

      Det här alternativet bearbetar inte fel relaterade till aktivitetskonfigurationen, dvs. ogiltiga värden.

1. **Historik**

   Se **[!UICONTROL File historization]** steget här: [Webbnedladdning](../../workflow/using/web-download.md).

Filbearbetningsordningen kan inte bestämmas. Om du vill bearbeta en uppsättning filer sekventiellt använder du alternativet och skapar en slinga **[!UICONTROL Stop as soon as a file has been processed]** . I så fall bearbetas filerna i alfabetisk ordning. Med det här **[!UICONTROL Process file nonexistence]** alternativet kan du slutföra iterationen.

![](assets/file_collect_loop.png)

## Utdataparametrar {#output-parameters}

* filnamn: Fullständigt filnamn. Det här är filnamnet när det har flyttats till historikkatalogen. Sökvägen är därför annorlunda, men namnet är också annorlunda om det redan finns en fil med samma namn i katalogen. Utbyggnaden behålls.
