---
title: Läslista
seo-title: Läslista
description: Läslista
seo-description: null
page-status-flag: never-activated
uuid: 34e28675-f28b-407f-8d60-41a5383af0db
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 96a7aea4-4799-4ac7-8dff-666b075a1c43
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Läslista{#read-list}

Data som bearbetas i ett arbetsflöde kan komma från listor där data har förberetts eller strukturerats i förväg (efter en tidigare segmentering eller filöverföring).

Med den här **[!UICONTROL Read list]** aktiviteten kan du kopiera data från en lista i arbetsflödets arbetstabell, till exempel data från en fråga. Den är sedan tillgänglig i hela arbetsflödet.

Listan som ska bearbetas kan anges explicit, beräknas av ett skript eller lokaliseras dynamiskt enligt valda alternativ och parametrar definierade i en **[!UICONTROL Read list]** aktivitet.

![](assets/list_edit_select_option_01.png)

Om listan inte uttryckligen anges måste du ange en lista som ska användas som mall för att ta reda på dess struktur.

![](assets/s_advuser_list_template_select.png)

När listmarkeringen har konfigurerats kan du lägga till ett filter med hjälp av alternativet att behålla en del av populationen för nästa arbetsflöde. **[!UICONTROL Edit query]**

![](assets/wf_readlist_1.png)

>[!CAUTION]
>
>För att kunna skapa ett filter i en läslisteaktivitet måste den relevanta listan vara av typen &quot;file&quot;.

Listorna kan skapas direkt i Adobe Campaign via länken **[!UICONTROL Profiles and Targets > Lists]** på startsidan. De kan också skapas i ett arbetsflöde med hjälp av **[!UICONTROL List update]** aktiviteten.

**Exempel: Uteslut en lista med sändningsadresser**

I följande exempel kan du använda en lista med e-postadresser som ska uteslutas från e-postleveransmålet.

![](assets/s_advuser_list_read_sample_1.png)

Profilerna i mappen **Nya kontakter** måste ha en leveransåtgärd som mål. De e-postadresser som ska uteslutas från målet lagras i en extern lista. I vårt exempel krävs bara information om e-postadresser för att exkludera.

1. Med frågan för val av mapp för **nya kontakter** måste du kunna läsa in de valda profilernas e-postadresser, för att kunna aktivera justering mot informationen i listan.

   ![](assets/s_advuser_list_read_sample_0.png)

1. Här lagras listan i mappen **Lists** och etiketten beräknas.

   ![](assets/s_advuser_list_read_sample_2.png)

1. Om du vill utesluta e-postadresserna för den externa listan från huvudmålet måste du konfigurera undantagsaktiviteten och ange att mappen **Nya kontakter** innehåller de data som ska behållas. Kopplingsdata mellan den här uppsättningen och andra inkommande uppsättningar från exkluderingsaktiviteten tas bort från målet.

   ![](assets/s_advuser_list_read_sample_3.png)

   Uteslutningsregler konfigureras i det centrala avsnittet i redigeringsverktyget. Klicka på **[!UICONTROL Add]** knappen för att definiera vilken typ av undantag som ska användas.

   Du kan definiera flera undantag beroende på antalet inkommande övergångar för aktiviteten.

1. Välj **[!UICONTROL Exclusion set]** aktivitet i **[!UICONTROL Read list]** fältet: uppgifterna i denna verksamhet ska uteslutas från huvudgruppen.

   I vårt exempel har vi ett undantag för kopplingar: uppgifterna i listan kommer att stämma överens med uppgifterna i huvuduppsättningen via fältet som innehåller e-postadressen. Om du vill konfigurera kopplingen väljer du **[!UICONTROL Joins]** i **[!UICONTROL Change dimension]** fältet.

   ![](assets/s_advuser_list_read_sample_4.png)

1. Markera sedan fältet som motsvarar e-postadressen i de två uppsättningarna (Källa och Mål). Kolumnerna länkas sedan och de mottagare vars e-postadress finns i listan över importerade adresser exkluderas från målet.

