---
solution: Campaign Classic
product: campaign
title: Hantera uppräkningar
description: Hantera uppräkningar
audience: platform
content-type: reference
topic-tags: administration-basics
translation-type: tm+mt
source-git-commit: b05b8daad449aeb1f5226fdd76744776c6553b63
workflow-type: tm+mt
source-wordcount: '875'
ht-degree: 0%

---


# Hantera uppräkningar{#managing-enumerations}

En uppräkning (kallas även&quot;lista med specificerade värden&quot;) är en lista med värden som föreslås av systemet för att fylla i vissa fält. Med uppräkningar kan du standardisera värdena för dessa fält och hjälpa till med inmatning eller användning av data i frågor.

Värdelistan visas som en nedrullningsbar lista där du kan välja vilket värde som ska anges i fältet. Listrutan möjliggör även prediktiv inmatning, där operatorn anger de första bokstäverna och programmet fyller i resten.

Vissa konsolfält har definierats med den här typen av uppräkningar. Uppräkningar kallas&quot;öppna&quot; om du kan lägga till värden genom direktinmatning i motsvarande fält.

## Åtkomst till värden {#access-to-values}

Värdena för den här typen av fält definieras och den övergripande administrationen av dessa fält (genom att lägga till/ta bort ett värde) utförs via noden **[!UICONTROL Administration > Platform > Enumerations]** i trädet.

![](assets/s_ncs_user_itemized_list_node.png)

* I det övre avsnittet finns en lista med fält för vilka en specificerad lista har definierats.
* I det nedre avsnittet visas de föreslagna värdena. Dessa värden upprepas i redigerarna som använder det här fältet.

   ![](assets/s_ncs_user_itemized_list_values.png)

   Om du vill skapa ett nytt uppräkningsvärde klickar du på **[!UICONTROL Add]**.

   ![](assets/s_ncs_user_itemized_list.png)

   Om alternativet **[!UICONTROL Open]** är markerat kan användaren lägga till ett nytt specificerat listvärde direkt i motsvarande fält. Ett bekräftelsemeddelande låter dig skapa det här värdet.

   ![](assets/s_ncs_user_itemized_list_new_value.png)

* Om alternativet **[!UICONTROL Closed]** är markerat kan användarna inte skapa nya värden, utan bara välja bland de tillgängliga värdena.

## Standardisera data {#standardizing-data}

### Om aliasrensning {#about-alias-cleansing}

I de specificerade listfälten kan du ange andra värden än uppräkningsvärden. Dessa kan antingen lagras som de är eller rensas.

>[!CAUTION]
>
>Datarensning är en kritisk process som påverkar data i databasen. Adobe Campaign genomför massuppdateringar, vilket kan leda till att vissa värden tas bort. Den här åtgärden är därför reserverad för expertanvändare.

Det angivna värdet är då antingen:

* Tillagda till värden i den specificerade listan: i det här fallet måste alternativet **[!UICONTROL Open]** vara markerat,
* eller ersätts automatiskt av motsvarande alias: I det här fallet måste det definieras på fliken **[!UICONTROL Alias]** i den specificerade listan.
* eller lagras i listan över alias: ett alias som kan tilldelas det senare.

   >[!NOTE]
   >
   >Om du behöver använda datarensningsfunktionerna väljer du alternativet **[!UICONTROL Alias cleansing]** i den specificerade listan.

### Använda alias {#using-aliases}

Alternativet **[!UICONTROL Alias cleansing]** gör det möjligt att använda alias för den valda specificerade listan. När det här alternativet är markerat visas fliken **[!UICONTROL Alias]** längst ned i fönstret.

![](assets/s_ncs_user_itemized_list_alias_option.png)

#### Skapa ett alias {#creating-an-alias}

Om du vill skapa ett alias klickar du på **[!UICONTROL Add]**.

![](assets/s_ncs_user_itemized_list_alias_create.png)

Ange det alias som du vill konvertera och det värde som ska användas och klicka på **[!UICONTROL Ok]**.

![](assets/s_ncs_user_itemized_list_alias_create_2.png)

Kontrollera parametrarna innan du bekräftar åtgärden.

>[!CAUTION]
>
>När det här steget har bekräftats kan de tidigare angivna värdena inte återställas: de har ersatts.

![](assets/s_ncs_user_itemized_list_alias_create_3.png)

När en användare anger värdet **NEILSEN** i ett&quot;företag&quot;-fält (i Adobe Campaign-konsolen eller i ett formulär) ersätts det automatiskt av värdet **NIELSEN Ltd**. Värderelsersättning utförs av arbetsflödet **Aliasrensning**. Se [Kör datarensning](#running-data-cleansing).

![](assets/s_ncs_user_itemized_list_alias_use.png)

#### Konverterar värden till alias {#converting-values-into-aliases}

Om du vill konvertera ett uppräkningsvärde till ett alias högerklickar du i listan med värden och väljer **[!UICONTROL Convert values into aliases...]**.

![](assets/s_ncs_user_itemized_list_alias_detail.png)

Välj de värden som du vill konvertera och klicka på **[!UICONTROL Next]**.

![](assets/s_ncs_user_itemized_list_alias_transform.png)

Klicka på **[!UICONTROL Start]** för att köra konverteringen.

![](assets/s_ncs_user_itemized_list_alias_detail1.png)

När körningen är klar läggs aliaset till i listan över alias.

![](assets/s_ncs_user_itemized_list_alias_detail2.png)

#### Hämta aliasträffar {#retrieving-alias-hits}

De värden som anges av användarna kan konverteras till alias. Det innebär att om användaren anger ett värde som inte finns med i den specificerade listan lagras värdet på fliken **[!UICONTROL Alias]**.

Det tekniska arbetsflödet för **Alias-rensning** återställer dessa värden varje kväll för att uppdatera den specificerade listan. Se [Kör datarensning](#running-data-cleansing)

Om det behövs kan kolumnen **[!UICONTROL Hits]** visa hur många gånger det här värdet har angetts. Det kan ta både tid och minne att beräkna det här värdet. Mer information finns i [Beräkna postförekomster](#calculating-entry-occurrences).

### Kör datarensning {#running-data-cleansing}

Datarensning utförs av det tekniska arbetsflödet **[!UICONTROL Alias cleansing]**. De konfigurationer som definieras för uppräkningar tillämpas under körningen. Mer information finns i [Aliasrensningsarbetsflöde](#alias-cleansing-workflow).

Rensningen kan aktiveras via länken **[!UICONTROL Cleanse values...]**.

![](assets/s_ncs_user_itemized_list_alias_start_normalize.png)

Med länken **[!UICONTROL Advanced parameters...]** kan du ange det datum från vilket insamlade värden ska beaktas.

![](assets/s_ncs_user_itemized_list_alias_normalize.png)

Klicka på knappen **[!UICONTROL Start]** för att köra datarensning.

#### Beräkna postförekomster {#calculating-entry-occurrences}

Underfliken **[!UICONTROL Alias]** för en specificerad lista kan visa antalet förekomster av ett alias bland alla värden som anges. Den här informationen är en uppskattning och kommer att visas i kolumnen **[!UICONTROL Hits]**.

>[!CAUTION]
>
>Det kan ta lång tid att beräkna aliaspostförekomster. Därför bör försiktighet iakttas när den här funktionen används.

Du kan köra träffberäkning manuellt via länken **[!UICONTROL Cleanse values...]**. Det gör du genom att klicka på länken **[!UICONTROL Advanced parameters...]** och välja önskade alternativ.

![](assets/s_ncs_user_itemized_list_alias_hits.png)

* **[!UICONTROL Update the number of alias hits]**: gör att du kan uppdatera träffar som redan har beräknats, baserat på det angivna datumet.
* **[!UICONTROL Recalculate the number of alias hits from the start]**: gör att du kan köra beräkningar på hela Adobe Campaign-plattformen.

Du kan också skapa ett dedikerat arbetsflöde så att beräkningen körs automatiskt för en viss period, till exempel en gång i veckan.

Det gör du genom att skapa en kopia av **[!UICONTROL Alias cleansing]**-arbetsflödet, ändra schemaläggaren och använda följande inställningar i **[!UICONTROL Enumeration value cleansing]**-aktiviteten:

* **-** updateHitsto för att uppdatera antalet aliasträffar,
* **-updateHits:** fullför att beräkna om alla aliasträffar.

#### Rensningsarbetsflöde för alias {#alias-cleansing-workflow}

Arbetsflödet för **Aliasrensning** kör uppräkningsvärderensning. Som standard utförs den dagligen.

Den nås via noden **[!UICONTROL Administration > Production > Technical workflows]**.

![](assets/s_ncs_user_itemized_list_alias_wf.png)

