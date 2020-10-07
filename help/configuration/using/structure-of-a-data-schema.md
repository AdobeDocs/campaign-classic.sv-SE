---
title: Dataschemats struktur
seo-title: Dataschemats struktur
description: Dataschemats struktur
seo-description: null
page-status-flag: never-activated
uuid: 83e3995d-fa31-4cb5-acf2-83f17329c99c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: a1a39eaa-6d6f-42c5-a36b-bd1cb3a77dcb
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 13%

---


# Dataschemats struktur{#structure-of-a-data-schema}

Strukturen i ett dataschema visas i form av en trädstruktur. Om du vill visa det grafiskt i Adobe Campaign klientkonsol markerar du målschemat och klickar på **[!UICONTROL Structure]** underfliken.

![](assets/d_ncs_integration_schema_arbo.png)

Som standard visas fälten först (Aktiv, Aktiverad osv.) och i alfabetisk ordning. Struktureringselementen kommer sedan (Postadress, Plats) och slutligen länkarna (E-postinformation, Mapp, osv.).

Primära nycklar identifieras med en röd nyckel och utländska nycklar identifieras med en gul nyckel.

Länkarna urskiljs grafiskt beroende på om de tillhör tabellen eller inte. De som börjar i tabellen, d.v.s. har sekundärnyckeln i tabellen, visas först (e-postinformation, Mapp, Land). &quot;Invertera&quot; samlingslänkar (prenumeration, beställningar osv.) visas i slutet.
