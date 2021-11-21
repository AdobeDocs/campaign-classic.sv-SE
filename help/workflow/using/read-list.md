---
product: campaign
title: Läslista
description: Learn more about the Read list workflow activity
audience: workflow
content-type: reference
topic-tags: targeting-activities
exl-id: 99f82e91-45cd-4dff-b8a4-3ad87f2f9639
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# Läslista{#read-list}

![](../../assets/common.svg)

Data som bearbetas i ett arbetsflöde kan komma från listor där data har förberetts eller strukturerats i förväg (efter en tidigare segmentering eller filöverföring).

The **[!UICONTROL Read list]** Med -aktivitet kan du kopiera data från en lista i arbetsflödets arbetstabell, som data från en fråga. It is then accessible throughout the workflow.

The list to be processed can be specified explicitly, computed by a script or localized dynamically, according to options selected and parameters defined in a **[!UICONTROL Read list]** activity.

![](assets/list_edit_select_option_01.png)

Om listan inte uttryckligen anges måste du ange en lista som ska användas som mall för att ta reda på dess struktur.

![](assets/s_advuser_list_template_select.png)

När listmarkeringen har konfigurerats kan du lägga till ett filter med **[!UICONTROL Edit query]** för att behålla en del av populationen för nästa arbetsflöde.

![](assets/wf_readlist_1.png)

>[!CAUTION]
>
>För att kunna skapa ett filter i en läslisteaktivitet måste den relevanta listan vara av typen &quot;file&quot;.

Listorna kan skapas direkt i Adobe Campaign via **[!UICONTROL Profiles and Targets > Lists]** startsidans länk. De kan också skapas i ett arbetsflöde med **[!UICONTROL List update]** aktivitet.

**Example: Exclude a list of send addresses**

I följande exempel kan du använda en lista med e-postadresser som ska uteslutas från e-postleveransmålet.

![](assets/s_advuser_list_read_sample_1.png)

Profilerna i **Nya kontakter** -mappen måste ha en leveransåtgärd som mål. De e-postadresser som ska uteslutas från målet lagras i en extern lista. In our example, only the information on email addresses is required for exclusion.

1. The **Nya kontakter** Mappvalsfrågan måste göra det möjligt att läsa in de valda profilernas e-postadresser för att kunna justera dem mot informationen i listan.

   ![](assets/s_advuser_list_read_sample_0.png)

1. Här lagras listan i **Listor** mappen och dess etikett beräknas.

   ![](assets/s_advuser_list_read_sample_2.png)

1. Om du vill utesluta e-postadresserna för den externa listan från huvudmålet måste du konfigurera undantagsaktiviteten och ange att **Nya kontakter** mappen innehåller de data som ska sparas. The joint data between this set and any other inbound set from the exclusion activity will be deleted from the target.

   ![](assets/s_advuser_list_read_sample_3.png)

   Uteslutningsregler konfigureras i det centrala avsnittet av redigeringsverktyget. Klicka på **[!UICONTROL Add]** för att definiera vilken typ av undantag som ska användas.

   Du kan definiera flera undantag beroende på antalet inkommande övergångar för aktiviteten.

1. I **[!UICONTROL Exclusion set]** välj **[!UICONTROL Read list]** aktivitet: uppgifterna i denna verksamhet ska uteslutas från huvudgruppen.

   I vårt exempel har vi ett undantag för kopplingar: uppgifterna i listan kommer att stämma överens med uppgifterna i huvuduppsättningen via fältet som innehåller e-postadressen. Om du vill konfigurera kopplingen väljer du **[!UICONTROL Joins]** i **[!UICONTROL Change dimension]** fält.

   ![](assets/s_advuser_list_read_sample_4.png)

1. Then select the field corresponding to the email address in the two sets (Source and Destination). Kolumnerna länkas sedan och de mottagare vars e-postadress finns i listan över importerade adresser exkluderas från målet.
