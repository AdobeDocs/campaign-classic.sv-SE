---
solution: Campaign Classic
product: campaign
title: Optimera meddelandeleveransen
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
exl-id: 24b2ee47-bec7-43ce-81b3-0b2d1a5cebae
source-git-commit: bce114f36d1ec4582fc79e750d48155ba0d7cd1f
workflow-type: tm+mt
source-wordcount: '729'
ht-degree: 6%

---

# Optimera leverans {#optimize-delivery}

Innan du ens börjar skapa leveranser kan du vidta flera åtgärder för att skydda och optimera sändningsprocessen uppströms.

I följande avsnitt beskrivs god praxis och rekommenderade procedurer för optimal konfiguration av Adobe Campaign. Om du följer dessa rutiner minimeras problem som kan uppstå längre fram i kedjan.

## Plattformsprestanda

Flera faktorer kan direkt påverka serverprestanda och göra plattformen långsammare:

* Antal och typ av personaliseringselement: personalisering i e-post hämtar data från databasen för varje mottagare. Om det finns många personaliseringselement ökar detta mängden data som behövs för att förbereda leveransen.  Läs mer om personalisering i [det här avsnittet](../../delivery/using/about-personalization.md)

* Serverbelastningen: när marknadsföringsservern hanterar många olika uppgifter samtidigt kan prestandan försämras. Marknadsföringsservern måste koordinera alla inkommande och utgående data för alla leveranser för att säkerställa att data är korrekta och i tid.

   **TIPS** - För att undvika detta bör du samordna schemaläggningen av leveranser med övriga medlemmar i teamet för att säkerställa bästa möjliga prestanda.

* Arbetsflödets körning: övervakning av arbetsflödena är avgörande för att undvika problem med plattformens prestanda. Följ riktlinjerna som anges [i det här dokumentet](../../workflow/using/workflow-best-practices.md#execution-and-performance).

* Om du är berättigad kan du använda [panelfunktionerna för kampanjkontroll](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html) för att övervaka plattformen med [funktioner för prestandaövervakning](https://experienceleague.adobe.com/docs/control-panel/using/performance-monitoring/about-performance-monitoring.html).

## Kontrollerar nätverkskonfigurationen {#network-config}

Om du vill optimera leveransen när du hanterar e-post i stora volymer och undvika att ta fel för en skräppost, kontrollerar du att du har en giltig nätverkskonfiguration som inte försöker dölja serverns identitet.

**Tips**: Använd en transparent avsändaradress som motsvarar ert varumärkes webbplats. Exempel: företaget TravelAgency hanterar hotellkedjan Valentino. Företaget äger domänen valentino.com för sin webbplats. För att marknadsföra alla hjärtans dag-hotell i Paris använder man underdomänen paris.valentino.com. Därför kan en relevant avsändaradress vara hotel@paris.valentino.com.

## Levererbarhetshantering {#deliverability-management}

Om du vill nå mottagarnas inkorg utan att studsa eller markeras som skräppost måste du förbättra leveransfrekvensen för dina meddelanden.

* Vad är leverans?

   * Det avser de faktorer i ett e-postmeddelande som avgör om det kan accepteras av en mottagares server. Internet-leverantörer (Internet Service Providers) filtrerar bort e-postmeddelanden som de identifierar som SPAM eller blockerar bilder från hämtning. Om de fastställer att en viss domän skickar för många e-postmeddelanden, kommer de att ange en gräns för hur många e-postmeddelanden de accepterar från den avsändaren.

   * När du kontrollerar om e-postmeddelandet kan levereras vill du fokusera på fyra huvudkategorier: datakvalitet, meddelande och innehåll, utskick av infrastruktur och anseende. Mer information om detta avsnitt finns i [det här avsnittet](../../delivery/using/about-deliverability.md).

* Använd de rekommendationer som är detaljerade [i det här dokumentet](../../delivery/using/about-deliverability.md).

* Kontakta din Adobe-representant om du behöver hjälp.

## Karantänhantering {#quarantine-management}

Det ligger i ditt bästa intresse att upprätthålla goda karantänhanteringsprocesser.

När du börjar skicka e-post på en ny plattform kan du använda en lista med adresser som inte är fullständigt kvalificerade. Om du skickar till ogiltiga adresser eller till honeypoadresser (postlådor som bara skapats för att lura skräppost) börjar detta minska din plattforms anseende. Goda rutiner för hantering av karantäner hjälper till att upprätthålla adresskvaliteten, undvika blockeringslista från internetleverantörer och minska felfrekvensen, snabba upp leveranser och dataflöde.

**Tips**

* Om du har en lista med ogiltiga adresser rekommenderar Adobe att du importerar den till karantäntabellen via **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Non deliverables and addresses]**.

* Mottagare vars adresser sätts i karantän exkluderas som standard vid leveransanalysen: de inte är riktade. Detta snabbar upp leveranserna eftersom felfrekvensen avsevärt påverkar leveranshastigheten. En e-postadress kan sättas i karantän när inkorgen är full eller om adressen inte finns. [Läs mer](#identifying-quarantined-addresses-for-a-delivery)

* Adobe Campaign hanterar felaktiga adresser beroende på vilken typ av fel som returneras. Mer information om detta finns i [det här avsnittet](../../delivery/using/understanding-quarantine-management.md).


* Vissa internetleverantörer betraktar automatisk e-post som skräppost om antalet ogiltiga adresser är för högt.  Med karantän kan du därför undvika att läggas till i blockeringslista av dessa leverantörer.

* Hantering av karantäner minskar också SMS-sändningskostnaderna eftersom felaktiga telefonnummer utesluts från leveranser.

## Dubbel anmälningsmekanism {#double-opt-in}

För att undvika att skicka meddelanden till ogiltiga adresser, begränsa felaktig kommunikation och förbättra avsändarens anseende rekommenderar Adobe att du använder en dubbel anmälningsmekanism för bekräftelse efter prenumeration. Detta bidrar till att säkerställa att mottagaren prenumererar avsiktligt.

Information om hur du implementerar den här mekanismen beskrivs i [det här avsnittet](../../web/using/use-cases--web-forms.md).
