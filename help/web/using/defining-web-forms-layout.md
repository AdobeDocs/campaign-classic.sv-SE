---
title: Definiera webbformulärslayout
seo-title: Definiera webbformulärslayout
description: Definiera webbformulärslayout
seo-description: null
page-status-flag: never-activated
uuid: ae8659d0-3608-44dd-93ec-33c418a66ad0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-forms
discoiquuid: 67d1d39b-3a5f-4ed6-8fcf-570891043b10
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# Definiera webbformulärslayout{#defining-web-forms-layout}

## Skapar behållare {#creating-containers}

Med behållare kan du kombinera fälten på en sida och konfigurera deras layout; för att ordna elementen på sidan.

För varje sida i formuläret skapas behållare med knappen **[!UICONTROL Containers]** i verktygsfältet.

![](assets/s_ncs_admin_survey_containers_add.png)

Använd en behållare för att gruppera element på sidan utan att lägga till en etikett till den slutliga återgivningen. Elementen grupperas i behållarens underträd. Med standardbehållare kan du hantera layouten.

Till exempel:

![](assets/s_ncs_admin_survey_containers_std_arbo.png)

Etikettens placering tillämpas på element som placeras under behållaren i hierarkin. Den kan vid behov laddas över för varje element. Lägg till eller ta bort kolumner för att ändra layouten. Se [Placera fälten på sidan](#positioning-the-fields-on-the-page).

I exemplet ovan återges följande:

![](assets/s_ncs_admin_survey_containers_std_ex.png)

## Placera fälten på sidan {#positioning-the-fields-on-the-page}

Webbformulärets layout definieras sida för sida i varje behållare och kan överladdas för varje kontroll.

Sidorna är uppdelade i kolumner: varje sida innehåller ett visst antal kolumner. Varje fält på sidan upptar **n** celler. Behållare upptar också ett visst antal kolumner och fälten som de innehåller upptar ett visst antal celler

Som standard byggs sidorna på en enda kolumn och varje element upptar en cell. Det innebär att fält visas under varandra, där var och en tar upp en hel rad, vilket visas nedan:

![](assets/s_ncs_admin_survey_container_ex.png)

I följande exempel har standardkonfigurationen behållits. Sidan upptar en enda kolumn som innehåller fyra behållare.

![](assets/s_ncs_admin_survey_container_ex0.png)

Varje behållare upptar en kolumn och varje element upptar en cell:

![](assets/s_ncs_admin_survey_container_ex0a.png)

Återgivningen är följande:

![](assets/s_ncs_admin_survey_container_ex0_rend.png)

Du kan anpassa visningsparametrarna för att få följande återgivning:

![](assets/s_ncs_admin_survey_container_ex1_rend.png)

I det ovanstående återgivningsexemplet upptar varje inmatningsfält, rubrik och bild en cell i behållarens kolumner.

Du kan ändra formateringen i varje behållare. I vårt exempel kan du sprida innehållet i container 4 över två kolumner och distribuera elementen.

![](assets/s_ncs_admin_survey_container_ex2_rend.png)

Titeln och listan upptar en cell var (och därmed en hel rad i behållaren) och kryssrutan sträcker sig över två celler. Antalet celler som är kopplade till indatafältet definieras på **[!UICONTROL General]** fliken eller på **[!UICONTROL Advanced]** fliken, beroende på fälttypen:

![](assets/s_ncs_admin_survey_container_ex2.png)

## Definiera placeringen av etiketter {#defining-the-position-of-labels}

Du kan definiera justeringen av fält och etiketter i formuläret.

Som standard ärvs visningsparametrarna för fält och annat innehåll på sidan från formulärets allmänna konfiguration, sidans konfiguration eller den överordnade behållarens konfiguration, om sådan finns.

De globala visningsparametrarna för hela formuläret anges i rutan för formuläregenskaper. På fliken **[!UICONTROL Rendering]** kan du välja placering av etiketter.

![](assets/s_ncs_admin_survey_label_position.png)

Den här positionen kan laddas över för varje sida, varje behållare och varje fält via **[!UICONTROL Advanced]** fliken.

Följande justeringar stöds:

* Ärvd: justeringen ärvs från det överordnade elementet (standardvärde), dvs. den överordnade behållaren om sådan finns, eller i annat fall sidan.
* Vänster/höger: etiketten placeras till höger eller till vänster om fältet,
* Över/under: Etiketten är placerad ovanför eller under fältet.
* Dold: etiketten inte visas.

