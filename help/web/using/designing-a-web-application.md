---
product: campaign
title: Designa en webbapplikation
description: Designa en webbapplikation
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Web Apps
exl-id: dcdf6afc-321e-4027-a350-fff6bbf22e71
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 4%

---

# Designa en webbapplikation{#designing-a-web-application}



Webbprogram skapas och hanteras enligt samma princip som [webbformulär](about-web-forms.md).

>[!CAUTION]
>
>Använd **[!UICONTROL Preview]** underflik för att kontrollera fel under utformningen av webbprogram. Observera att det profiltest som används för att förhandsgranska webbprogrammet måste finnas i en mapp med **[!UICONTROL Access rights]** för **[!UICONTROL Web application agent]** -operator. </br>Ändringarna visas inte för slutanvändarna förrän webbprogrammet har publicerats.

## Infoga diagram i ett webbprogram {#inserting-charts-in-a-web-application}

Du kan inkludera diagram i webbprogram. Det gör du genom att använda listrutan med diagram i aktivitetsfältet för att välja vilken typ av diagram som ska infogas.

![](assets/s_ncs_admin_webapps_bar_graph.png)

Du kan också välja **[!UICONTROL Add a chart]** -menyn.

![](assets/s_ncs_admin_webapps_graph.png)

## Infoga tabeller i ett webbprogram {#inserting-tables-in-a-web-application}

Om du vill lägga till en tabell använder du listrutan med tabeller i aktivitetsfältet för att välja vilken typ av tabell som ska användas.

![](assets/s_ncs_admin_webapps_bar_table.png)

Du kan också välja tabelltyp i den nedrullningsbara menyn.

![](assets/s_ncs_admin_webapps_table.png)

## Webbprogram av översiktstyp {#overview-type-web-applications}

Adobe Campaign gränssnitt använder många webbprogram för att få åtkomst till, hantera och interagera med mottagare, leveranser, kampanjer, lager med mera.

De visas i gränssnittet i form av kontrollpaneler med bara en sida.

De färdiga webbprogrammen lagras i **[!UICONTROL Administration > Configuration > Web applications]** nod.

## Redigera webbprogram av formulärtyp {#edit-forms-type-web-applications}

Redigera webbtillämpningar för ett extranät kännetecknas av:

* En förinläsningsruta

  I de flesta fall måste de data som ska visas vara förinlästa. Eftersom de användare som använder formulären identifieras (via en åtkomstkontroll) behöver inte förinläsningen krypteras.

* En sparruta
* Lägga till sidor

  Medan webbapplikationer av typen &quot;Översikt&quot; alla har en enda sida kan redigeringsformulären innehålla en serie sidor som bygger på specifika kriterier (tester, val, profil för ansluten operator osv.).

