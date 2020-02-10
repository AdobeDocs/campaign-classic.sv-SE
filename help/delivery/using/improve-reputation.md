---
title: Förbättra ditt rykte med Adobe Campaign Classic
description: Läs mer om hur du kan förbättra ditt rykte med Adobe Campaign Classic.
page-status-flag: never-activated
uuid: 2681042b-3018-42ae-b252-2367b56616bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 6a394eeb-fbe1-4712-bb13-db5d7965fb73
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 68756f920fbc8658cff552615adbf023b4c5e3aa

---


# Förbättra ert rykte{#improve-reputation}

Du kan undvika att mottagarna blir trötta genom att ta bort dubbla e-postadresser från målet. Det här steget skyddar ditt sändningsrykte och garanterar en god karantänhantering. Adobe Campaign har de verktyg som krävs för att implementera dessa rekommendationer och undvika risken att bli svartlistad av Internet-leverantören.

För att så mycket som möjligt undvika dubbletter måste följande åtgärder utföras:

* Importerna måste konfigureras noggrant
* Var uppmärksam när du ändrar e-postadresser
* Var uppmärksam vid automatisk import
* Profilerna ska sorteras i olika mappar

Karantänhantering presenteras i [detta avsnitt](../../delivery/using/understanding-quarantine-management.md).

Här nedan hittar du information om hantering av dubbletter och karantän.

Du kan övervaka den skickade e-postvolymen med IP-adressen. Schematillägg krävs för detta. Du måste utöka utsändningstabellen för att lägga till den&quot;offentliga identifieraren&quot; och skapa ett arbetsflöde för att extrahera och visa data. Kontakta Adobe om du behöver detta.

## Dubbletter {#duplicates}

Att ha dubbla e-postadresser kan få flera följder:

* Samma meddelande skickas mer än en gång. Även om Campaign utför en dedupliceringsprocedur som standard innan det skickas, finns det inget som hindrar att samma meddelande skickas av olika åtgärder med samma innehåll när ett mål delas.
* Begäran om att avbryta prenumerationen har inte uppfyllts. Om en mottagare säger upp prenumerationen efter att ha fått ett meddelande, är deras duplicerade profil fortfarande berättigad till framtida meddelanden.

Förutom detta steg i anmälningsförfarandet kommer denna situation sannolikt att leda användarna till att betrakta meddelandena som skräppost och till att utlösa ett förfarande för svartlistning hos Internet.

Du måste vara särskilt försiktig när du utför åtgärder i databasen:

* Import måste konfigureras noggrant, särskilt när du väljer avstämningsnyckel.
* Ändrade e-postadresser kan också vara en källa till dubbletter. Två adresser med olika domäner kan dirigeras till samma postlåda, t.ex. för ett företag som har bytt namn och som har behållit den tidigare domänen under en viss tid: joe.doe@amce-co.com och joe.doe@acme-rebranded.com.
* Automatisk import, oavsett om den är en lista eller från andra databaser, är element som ska beaktas vid hantering av profiler. Vad händer när du tar bort eller flyttar en profil i en annan partition? Den kan återskapas i den inledande partitionen med en automatisk import, till exempel när en inköpsorder placeras.
* Det går att implementera lagring av profiler i olika mappar med hjälp av vyer i stället för partitioner. På så sätt är du säker på att profilerna finns i samma fysiska partition samtidigt som du fortfarande aktiverar rätt behörigheter för att visas och hanteras.

Det finns också fall där dubbletter mellan olika partitioner är normala. Om du till exempel skickar för tredje part eller olika företagsenheter är det logiskt att samma person är mottagare av olika anledningar. Det är dock sällan normalt att hitta dubbletter inom samma partition.

## Karantän {#quarantines}

Adobe Campaign hanterar en lista med adresser i karantän. Mottagare vars adresser sätts i karantän exkluderas som standard vid leveransanalysen: de inte är riktade. En e-postadress kan sättas i karantän när inkorgen är full eller om adressen inte finns. I samtliga fall motsvarar karantänsättningen de särskilda regler som anges nedan.

Karantänhantering presenteras i [detta avsnitt](../../delivery/using/understanding-quarantine-management.md).