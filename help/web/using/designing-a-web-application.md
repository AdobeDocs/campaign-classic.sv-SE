---
title: Utforma ett webbprogram
seo-title: Utforma ett webbprogram
description: Utforma ett webbprogram
seo-description: null
page-status-flag: never-activated
uuid: 29c11154-f056-4047-849a-739ba0a2c615
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-applications
discoiquuid: 08efa472-d090-404d-9ad7-47adb3489c30
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c9c9d5f96856ce9e19571bad032d2bf04eaa60bd

---


# Utforma ett webbprogram{#designing-a-web-application}

Webbprogram skapas och hanteras enligt samma princip som [onlineundersökningar](../../web/using/about-surveys.md).

De funktionella skillnaderna är dock följande:

* Webbprogram använder inga arkiverade fält. Data kan därför bara lagras i databasfält eller lokala variabler.
* Det finns inga inbyggda rapporter om webbprogram.
* Ytterligare fält erbjuds, huvudsakligen för att skapa tabeller och diagram.

>[!CAUTION]
>
>Vi rekommenderar starkt att de konfigurationer som används kontrolleras kontinuerligt för att upptäcka eventuella fel tidigt i konstruktionsprocessen för webbapplikationer. Om du vill kontrollera återgivningen av en ändring sparar du programmet och klickar sedan på **[!UICONTROL Preview]** underfliken.
>
>Innan webbprogrammet har publicerats kan inte slutanvändaren se ändringarna.

## Infoga diagram i ett webbprogram {#inserting-charts-in-a-web-application}

Du kan inkludera diagram i webbprogram. Det gör du genom att använda listrutan med diagram i aktivitetsfältet för att välja vilken typ av diagram som ska infogas.

![](assets/s_ncs_admin_webapps_bar_graph.png)

Du kan också välja **[!UICONTROL Add a chart]** menyn.

![](assets/s_ncs_admin_webapps_graph.png)

## Infoga tabeller i ett webbprogram {#inserting-tables-in-a-web-application}

Om du vill lägga till en tabell använder du listrutan med tabeller i aktivitetsfältet för att välja vilken typ av tabell som ska användas.

![](assets/s_ncs_admin_webapps_bar_table.png)

Du kan också välja tabelltyp i listrutan.

![](assets/s_ncs_admin_webapps_table.png)

## Webbprogram av översiktstyp {#overview-type-web-applications}

I gränssnittet i Adobe Campaign används många webbprogram för att få tillgång till, hantera och interagera med mottagare, leveranser, kampanjer, lager med mera.

De visas i gränssnittet i form av kontrollpaneler med bara en sida.

De färdiga webbprogrammen sparas i **[!UICONTROL Administration > Configuration > Web applications]** noden.

## Redigera webbprogram av formulärtyp {#edit-forms-type-web-applications}

Redigera webbtillämpningar för ett extranät kännetecknas av:

* En förinläsningsruta

   I de flesta fall måste de data som ska visas vara förinlästa. Eftersom de användare som använder formulären identifieras (via en åtkomstkontroll) behöver inte förinläsningen krypteras.

* En sparruta
* Lägga till sidor

   Medan webbapplikationer av typen &quot;Översikt&quot; alla har en enda sida kan redigeringsformulären innehålla en serie sidor som bygger på specifika kriterier (tester, val, profil för ansluten operator osv.).

Åtgärden för den här typen av webbprogram liknar **Undersökningar**, men utan historikhantering eller fältarkivering. Användarna kommer vanligtvis åt den via en inloggningssida där de måste identifiera sig själva.
