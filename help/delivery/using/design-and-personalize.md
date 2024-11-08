---
product: campaign
title: Skapa personaliserat innehåll
description: Lär dig skapa personaliserat innehåll i Adobe Campaign-leveranser
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Email Design, Personalization
role: User
exl-id: 5bf727d2-83b1-4a99-be25-041eee8d234c
source-git-commit: d34f75fadb02b4c03acc0c2d7be52df65320ec2d
workflow-type: tm+mt
source-wordcount: '1287'
ht-degree: 3%

---

# Skapa personaliserat innehåll {#build-personalized-content}

När du utformar meddelandeinnehållet bör du undvika vanliga problem som kan hindra dig från att utföra leveransen. Oftast är möjliga fel relaterade till [personalisering](about-personalization.md), [formatering](defining-the-email-content.md#message-content) och [bilder](defining-the-email-content.md#adding-images).

## Optimera personalisering {#optimize-personalization}

För att undvika vanliga problem som kan hindra dig från att utföra leveransen och för att förbättra mottagarnas upplevelse kan du anpassa dina meddelanden med Adobe Campaign.

Du kan använda mottagarnas data som lagras i Adobe Campaign-databasen, eller som samlats in via spårning, landningssidor, prenumerationer osv.
Grundläggande om Personalization presenteras i [det här avsnittet](personalization-fields.md).

Se till att meddelandeinnehållet är rätt utformat för att undvika fel, som vanligtvis är relaterade till personalisering.

**Tips**: I anpassningsfält som kommer från externa filer från tredjepartsleverantörer kan externt HTML-innehåll vara fel. Du undviker detta genom att kontrollera syntaxen, användning av taggar, tecken osv. En Adobe Campaign-personaliseringstagg har till exempel alltid följande format: &lt;%=table.field%>. Mer information finns i [det här avsnittet](about-personalization.md).

Felaktig användning av parametrar i personaliseringsblock kan vara ett problem. Variabler i JavaScript bör till exempel användas på följande sätt:

    &lt;%
    
    var brand = &quot;xxx&quot;
    
    %>

Mer information om anpassningsblock finns i [det här avsnittet](personalization-blocks.md).

Ni kan förbereda personaliseringsdata i ett arbetsflöde för att förbättra analysen av leveransförberedelser. Detta bör användas särskilt om personaliseringsdata kommer från en extern tabell via FDA (Federated Data Access). Det här alternativet beskrivs i det här [här avsnittet](personalization-fields.md#optimizing-personalization)

## Bygg optimerat innehåll {#optimize-content}

När du skapar e-postmeddelanden bör du tänka på de allmänna bästa metoderna nedan.

* Behåll designen enkel

* Tänk på mobilanvändare

* Undvik helt bildbaserade mejl

* Använda e-postsäkra teckensnitt

* Koda specialtecken

### Subject line

Arbeta på [ärenderaden](defining-the-email-content.md#message-content) för att förbättra öppna frekvenser:

* Undvik för långa motiv. Använd högst 50 tecken

* Undvik att använda upprepade ord som &quot;free&quot; eller &quot;offer&quot; som kan betraktas som spam

* Undvik versaler och specialtecken som &quot;!&quot;, &quot;£&quot;, &quot;€&quot;, &quot;$&quot;

### Spegelsida

Inkludera alltid en länk för spegelsida. Önskad position är högst upp i e-postmeddelandet. [Läs mer](sending-messages.md#generating-the-mirror-page)

### Länk för att avbryta prenumeration

Länken för att avbeställa prenumerationer är viktig. Den måste vara synlig och giltig och formuläret måste vara funktionellt. Som standard kontrollerar en [typologiregel](steps-validating-the-delivery.md#validation-process-with-typologies) om en avanmälningslänk har inkluderats och genererar en varning om den saknas när meddelandet analyseras.

**Tips**: Eftersom ett mänskligt fel alltid är möjligt bör du kontrollera att avanmälningslänken fungerar korrekt innan du skickar iväg den. När du t.ex. skickar ett bevis ska du kontrollera att länken är giltig, att formuläret är online och att fältet för att inte längre kontakta den här mottagaren har ändrats till Ja.

Lär dig hur du infogar en länk [för avanmälan i det här avsnittet](personalization-blocks.md#personalization-blocks-example).

### E-poststorlek

För att undvika problem med prestanda och leverans är den rekommenderade maximala storleken på ett e-postmeddelande cirka **35 kB**. Om du vill kontrollera meddelandestorleken går du till fliken **[!UICONTROL Preview]** och väljer en testprofil. När meddelandet har genererats visas meddelandestorleken i det övre högra hörnet.

Tänk på följande om du vill hålla din e-post under gränsen:

* Ta bort överflödiga eller oanvända format

* Flytta en del av e-postinnehållet till en landningssida

* Minimera koden

Kontrollera att du har testat alla ändringar innan du skickar det

### SMS-längd

Som standard uppfyller antalet tecken i ett SMS GSM-system (Global System for Mobile Communications). SMS-meddelanden som använder GSM-kodning kan innehålla högst 160 tecken eller 153 tecken per SMS för meddelanden som skickas i flera delar.

Translitterering består i att ersätta ett tecken i ett SMS med ett annat om det tecknet inte beaktas av GSM-standarden. Observera att om du infogar anpassningsfält i innehållet i SMS-meddelandet kan det medföra tecken som GSM-kodningen inte tar hänsyn till. Du kan godkänna teckentranskribering genom att markera motsvarande ruta på fliken SMPP-kanalinställningar i motsvarande **[!UICONTROL External account]**.
Läs mer [i det här avsnittet](sms-set-up.md#creating-an-smpp-external-account).

**Tips**:

* Om du vill behålla alla tecken i SMS-meddelanden som de är, ska du inte aktivera transkribering för att t.ex. inte ändra egennamn.

* Om dina SMS-meddelanden innehåller många tecken som inte beaktas av GSM-standarden kan du aktivera transkribering för att begränsa kostnaderna för att skicka meddelanden.

Läs mer [i det här avsnittet](sms-set-up.md#about-character-transliteration).

## Arbeta med formatering {#formatting}

Kontrollera följande element för att undvika vanliga formateringsfel:

* Korrigera **datumformatering**: Adobe Campaign tillhandahåller datumformateringsfunktioner för JavaScript-mallar och XSL-formatmallar. [Läs mer](formatting.md#date-display)

* Användning av **tillåtna tecken** i e-postmeddelanden: listan över giltiga tecken för e-postadresser definieras i alternativet XtkEmail_Characters. Lär dig hur du kommer åt Campaign-alternativen [i det här avsnittet](../../installation/using/configuring-campaign-options.md). För att specialtecken ska kunna hanteras på rätt sätt måste Adobe Campaign vara installerat i Unicode.

* Konfiguration av **E-postautentisering**: Kontrollera att e-posthuvudena innehåller DKIM-signaturen. Med DKIM-autentisering (Domain Keys Identified Mail) kan den mottagande e-postservern verifiera att ett meddelande verkligen skickades av den person eller enhet som det hävdades ha skickats av och om meddelandeinnehållet ändrades mellan den tidpunkt det ursprungligen skickades (och DKIM &quot;signerade&quot;) och den tidpunkt det togs emot. Den här standarden använder vanligtvis domänen i sidhuvudet Från eller Avsändare. Mer information finns i [Adobe Deliverability Best Practice Guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication).

### Responsiv e-postdesign

Responsiv design säkerställer att ett e-postmeddelande återges optimalt för den enhet där det öppnas.

* Använd responsiv e-post HTML i stället för web HTML

* Använd förhandsgranskningsläget och skicka provtryck för att testa återgivningen på så många enheter som möjligt

* Modulen Adobe Campaign Classic Digital Content Editor (DCE) innehåller responsiva designformaterade mallar för mobiler som är tillgängliga via **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Content templates]**.

## Hantera bilder {#manage-images}

Följ riktlinjerna nedan när det gäller att använda bilder.

### Förhindra blockering av bilder

Vissa e-postklienter blockerar bilder som standard, och vissa användare ändrar sina inställningar till blockbilder för att spara på dataanvändningen. Om bilderna inte hämtas kan därför hela meddelandet gå förlorat. Så här undviker du:

* Balansera innehållet med bild och text. Undvik helt bildbaserade e-postmeddelanden.

* Om texten måste finnas i en bild använder du alt- och titeltext för att vara säker på att meddelandet når fram. Formatera din alt-/titeltext för att förbättra utseendet.

* Undvik att använda bakgrundsbilder eftersom de inte stöds av vissa e-postklienter.

### Gör bilderna responsiva

Försök att göra bilderna responsiva och ändra storlek. Observera att detta kan ha en kostnadseffekt eftersom det tar längre tid att bygga.

### Använd absoluta bildreferenser

För att vara tillgängliga utifrån måste de bilder som används i e-postmeddelanden och offentliga resurser som är kopplade till kampanjer finnas på en externt tillgänglig server.

* Du kan kontrollera om instanskonfigurationen aktiverar offentlig resurshantering. [Läs mer](../../installation/using/deploying-an-instance.md#managing-public-resources)

* Från leveransassistenten kan du importera en HTML-sida som innehåller bilder eller infoga bilder direkt med redigeraren i HTML via ikonen **[!UICONTROL Image]**. [Läs mer](defining-the-email-content.md#adding-images)

* Om bilderna inte visas kontrollerar du att bilderna är tillgängliga på servern. Det gör du genom att klicka på fliken Source i leveransfönstret. Hitta bilderna och kopiera och klistra in URL:en för varje bild i en webbläsare. Om bilderna inte visas kontaktar du IT-administratören eller tredjepartsleverantören som tillhandahåller ditt leveransinnehåll.

## Förhandsgranska meddelandet {#preview-msg}

Adobe rekommenderar att du förhandsgranskar ditt meddelande för att kontrollera hur det är anpassat och hur mottagarna ser det.

* I leveransassistenten kan du på underfliken **[!UICONTROL Preview]** visa återgivningen av varje innehåll för en mottagare. Anpassningsfälten och de villkorliga elementen i innehållet ersätts med motsvarande information för den valda profilen. [Läs mer](defining-the-email-content.md#message-content)

* En automatisk skräppostkontroll utförs under varje förhandsgranskning. På underfliken **[!UICONTROL Preview]** kontrollerar du [SpamAssassin](spamassassin.md)-spampoäng.  Klicka på **[!UICONTROL More...]** om du vill veta mer om varningen.  Innan du gör det kontrollerar du att SpamAssets är korrekt installerat och konfigurerat på Adobe Campaign programserver. [Läs mer](../../installation/using/configuring-spamassassin.md)
