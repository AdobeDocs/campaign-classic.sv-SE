---
title: Leveransvillkor i Adobe Campaign Classic
description: Läs mer om hur du hanterar leveranser i Adobe Campaign Classic.
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
source-git-commit: c687c8ad19560d4181c2db52a91e096cceea705e
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---


# Leverans{#about-deliverability}

Adobe Campaign erbjuder ett antal verktyg för att spåra plattformens leveransförmåga. I det här avsnittet beskrivs också de huvudprinciper som du bör tänka på när du hanterar och optimerar leveransen.

## Konfiguration {#configuration}

Den här funktionen är tillgänglig via ett dedikerat paket i Adobe Campaign. Paketet måste vara installerat för att du ska kunna använda det. När du är klar startar du om servern så att paketet kan användas.
* För hostingkunder och hybridklienter konfigureras **leveransövervakning** av Adobes tekniska support och konsulter. Kontakta er kontoansvarige på Adobe om du vill ha mer information.

* För lokala installationer måste du installera paketet **[!UICONTROL Deliverability monitoring (Email Deliverability)]** via menyn **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** . Mer information finns i [Installera standardpaket](../../installation/using/installing-campaign-standard-packages.md)för Campaign Classic.

I Adobe Campaign Classic hanteras **leveransövervakning** av **[!UICONTROL Refresh for deliverability]** arbetsflödet. Det installeras som standard på alla instanser och gör att du kan initiera listan över regler för studsmeddelanden, domänlistan och listan över MX:er. När paketet har installerats körs det här arbetsflödet i natt för att regelbundet uppdatera listan över regler och göra det möjligt att aktivt hantera plattformsleveransen. **[!UICONTROL Deliverability monitoring (Email Deliverability)]**

## Bakgrund {#background}

E-postleveransen utgör en stor utmaning för marknadsförarna, oavsett om de skickar några tusen meddelanden eller flera miljarder. Ett av fem meddelanden når aldrig inkorgen, eller den avsedda mottagaren.

När e-postleveransen väl betecknas som ett&quot;tekniskt problem&quot; för IT-avdelningen fortsätter e-postleveransen att hamna högre på marknadsföringsagendan. Det beror på att kunniga marknadsförare inser att även om många av elementen är av teknisk natur är leveransbarhet i slutändan ett affärsproblem med betydande intäktseffekter.

Ta en titt på e-postmarknadsföringstratten. Leveransen avgör antalet mottagna meddelanden, vilket i sin tur påverkar varje efterföljande fas av tratten. Färre e-postmeddelanden har fått färre öppningar, färre klick och färre konverteringar. **För företag med en stor databas kan skillnaden mellan genomsnittlig och stor leveransförmåga bokstavligen betyda hundratusentals till miljontals dollar i intäkter.**

![](assets/deliverability_overview_1.png)

Genom att betala för genomsnittlig (80 %) leverans lämnar marknadsförarna stora konverteringar - och dollar - på bordet.

Exakt vad är e-postleverans? Och hur kan marknadsförarna förbättra leveransmöjligheterna för att vidga trattens utlopp och få ut mer av sina e-postkampanjer?

E-postleverans är en uppsättning egenskaper som avgör hur ett meddelande kan nå sin destination via en personlig e-postadress inom en kort tid och med den förväntade kvaliteten i fråga om innehåll och format. Dessa egenskaper kan delas in i fyra huvudkategorier: datakvalitet, meddelande och innehåll, utskick av infrastruktur och anseende. Tillsammans utgör de grunden för ett framgångsrikt program för e-postleverans. I den här översikten beskrivs de fyra grundläggande aspekterna av e-postleverans och de bästa sätten att nå inkorgen och generera större intäkter från e-postmarknadsföringsprogram.

<!--![](assets/deliverability_overview_2.png)-->
