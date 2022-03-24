---
product: campaign
title: Kampanjwebbkomponenter och version 100 i Chrome- och Firefox-webbläsare
description: Kampanjwebbkomponenter och version 100 i Chrome- och Firefox-webbläsare
hide: true
hidefromtoc: true
source-git-commit: 68049d1905524b644794799348bd6387b2afed0d
workflow-type: tm+mt
source-wordcount: '618'
ht-degree: 0%

---

# Kampanjwebbkomponenter och version 100 i Chrome- och Firefox-webbläsare {#version-100}

## Vad {#what-version-100}

Google och Mozilla varnar för att Chrome och Firefox kan bryta ned vissa webbplatser på grund av kommande 3-siffriga versioner.
Ändringen av versionsnumret från 2 till 3 siffror kan orsaka vissa problem när du besöker webbplatser som inte är förberedda för den här ändringen. Vissa webbsidor kan sluta visas korrekt i de nya webbläsarversionerna.

Mozilla och Google testar kompatibiliteten hos större webbplatser i förväg. Om det uppstår problem med webbplatser som de inte kan åtgärda innan de här versionerna har släppts, har båda planer för säkerhetskopiering som säkerställer att webbplatserna inte påverkas.

## Varför {#why-version-100}

Potentiella problem eller funktionsförlust på webbplatsen kommer från användaragentsträngen som webbläsare skickar till webbplatser som du besöker: användaragenten är en sträng som skickas av webbläsaren till webbplatsen för att tala om vilken webbläsare och version du använder samt tillhörande teknik. När webbläsaren skickar en begäran till en webbplats identifieras den med användaragentsträngen innan innehållet som du begärde hämtas. Data i användaragentsträngen hjälper webbplatsen att leverera innehållet i ett format som passar din webbläsare. Versionen av användaragenten ökas så att den matchar webbläsarens versionsnummer. Att gå från 2 till 3 siffror kan orsaka problem.

## When {#when-version-100}

Chrome v100 är inställd för release den **29 mars 2022** och Firefox v100 på **3 maj 2022**.

## Plats {#where-version-100}

Adobe rekommenderar att du testar dina Campaign-webbprogram, inklusive webbformulär och enkäter samt e-postspegelsidor, så att de fortfarande fungerar som de ska med de nya webbläsarversionerna.

Den här rekommendationen gäller alla webbprogram, särskilt om du har inkluderat JavaScript-kod.

Du måste kontrollera både med Firefox och Chrome, mobil och dator.

## Hur {#how-version-100}

I Chrome och Firefox Nightly kan du konfigurera webbläsaren så att den rapporterar versionen som 100 just nu och korrigera eventuella problem du stöter på.

### Firefox 100{#test-firefox-100}

Om du vill testa dina webbsidor med Mozilla Firefox 100 kan du simulera den kommande användaragentändringen i dina webbprogram genom att manuellt ändra användaragentsträngen.

1. Öppna Firefox, ange `about:config` i adressfältet och tryck på Retur.
1. Sök efter `general.useragent.override`.
1. Välj String och klicka sedan på plustecknet (+).

   ![](assets/force-user-agent-firefox.png)

1. Ange följande text i fältet:

   ```
   Mozilla/5.0 (Windows NT 10.0; rv:100.0) Gecko/20100101 Firefox/100.0
   ```

1. Klicka på den blå bockmarkeringsknappen för att spara inställningen.
1. Stäng och starta om webbläsaren.

Med de här inställningarna skickar webbläsaren den nya användaragentsträngen till webbplatser, vilket anger att webbläsaren är Firefox 100. Om du stöter på problem med dina webbformulär bör du skapa en ny felrapport för Mozilla. Överväg att återskapa dessa webbformulär innan den här ändringen är allmänt tillgänglig.

Gå tillbaka till `about:config` och söka efter `general.useragent.override` igen.  När den visas klickar du på papperskorgsikonen för att ta bort inställningen och startar om webbläsaren.

### Krom 100{#test-chrome-100}

Om du vill testa Google Chrome 100-användaragenten i dina egna webbprogram kan du aktivera det här testet genom att följa de här stegen:

1. Öppna Chrome, ange `chrome://flags` i adressfältet och tryck på Retur.
1. Sök `Force major version to 100 in User-Agent` i sökfältet och aktivera det så som visas nedan.

   ![](assets/force-user-agent-chrome.png)

1. Stäng och starta om webbläsaren.
1. Stäng `chrome://flags` skärm.

Med de här inställningarna skickar webbläsaren den nya användaragentsträngen till webbplatser, vilket anger att webbläsaren är Chrome 100. Om du stöter på problem med de webbplatser du besöker bör du skapa en ny felrapport för Google. Överväg att återskapa dessa webbformulär innan den här ändringen är allmänt tillgänglig.

Om du vill ändra användaragenten tillbaka till standardinställningen följer du bara den här processen och ändrar flaggans inställning till `Default` och starta om webbläsaren.
