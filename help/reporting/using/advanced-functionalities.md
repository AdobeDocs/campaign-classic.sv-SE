---
title: Avancerade funktioner
seo-title: Avancerade funktioner
description: Avancerade funktioner
seo-description: null
page-status-flag: never-activated
uuid: 4dbf4750-0226-4f96-98d8-ec49b20374ac
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 0c264783-2775-4ec6-8d49-cd9a45a18d60
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: af768da6ee8cc0ca2ea1f24f297239b974c113a5

---


# Avancerade funktioner{#advanced-functionalities}

## Lägga till ett skript {#adding-a-script}

### Skriptaktivitet {#script-activity}

Med den här aktiviteten kan du bearbeta data och enkelt skapa komplexa frågor som inte aktiverar SQL-språk.

Skriv bara in frågan i skriptfönstret.

På fliken **[!UICONTROL Texts]** kan du definiera textsträngar. De kan sedan användas med följande syntax: **$(identifierare)**. Mer information om hur du använder texter finns i [Lägga till ett sidhuvud och en sidfot](../../reporting/using/element-layout.md#adding-a-header-and-a-footer).

>[!CAUTION]
>
>Vi rekommenderar INTE att du använder JavaScript-kod för att skapa aggregat.

Om du vill skapa en historik för rapporten lägger du till följande rad i JavaScript-frågan för att spara dina arkiverade data:

```
if( ctx.@_historyId.toString().length == 0 )
```

I annat fall visas aktuella data.

### Externt skript {#external-script}

Det går att använda ett externt skript som körs på servern och/eller klientsidan. Så här gör du:

1. Redigera rapportegenskaperna och klicka på **[!UICONTROL Scripts]**.
1. Klicka **[!UICONTROL Add]** och välj det skript som ska refereras.
1. Välj sedan körningsläge.

   Om du lägger till flera skript använder du pilarna i verktygsfältet för att definiera deras körningssekvens.

   ![](assets/reporting_custom_js.png)

## Anropa en annan rapport {#calling-up-another-report}

### Hoppaktivitet {#jump-activity}

Ett hopp är som en övergång utan en pil: kan du gå från en aktivitet till en annan eller komma åt en annan rapport.
