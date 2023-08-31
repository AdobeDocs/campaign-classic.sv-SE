---
product: campaign
title: Dataschemats struktur
description: Dataschemats struktur
feature: Custom Resources
role: Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
exl-id: 86036f2f-ec7c-413e-b1e1-10a71a06cd6d
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 14%

---

# Dataschemats struktur{#structure-of-a-data-schema}

Strukturen i ett dataschema visas i form av en trädstruktur. Om du vill visa det grafiskt i Adobe Campaign klientkonsol väljer du målschemat och klickar på **[!UICONTROL Structure]** underflik.

![](assets/d_ncs_integration_schema_arbo.png)

Som standard visas fälten först (Aktiv, Aktiverad osv.) och i alfabetisk ordning. Struktureringselementen kommer sedan (Postadress, Plats) och slutligen länkarna (E-postinformation, Mapp, osv.).

Primära nycklar identifieras med en röd nyckel och utländska nycklar identifieras med en gul nyckel.

Länkarna urskiljs grafiskt beroende på om de tillhör tabellen eller inte. De som börjar i tabellen, d.v.s. har sekundärnyckeln i tabellen, visas först (e-postinformation, Mapp, Land). &quot;Invertera&quot; samlingslänkar (prenumeration, beställningar osv.) visas i slutet.
