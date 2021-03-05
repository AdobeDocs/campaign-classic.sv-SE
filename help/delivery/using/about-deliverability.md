---
solution: Campaign Classic
product: campaign
title: Leveransbarhet i Campaign
description: Lär dig god praxis vad gäller leverans
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 87028ec81a8cae6793d45d7c840511b59cd0287c
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---


# Om leverans{#about-deliverability}

**Leveransmöjligheterna** består i att mäta framgången för era kampanjer som når mottagarnas inkorg utan att studsa, eller markeras som skräppost.

Adobe Campaign har ett antal verktyg för att spåra plattformens leveransförmåga. I det här avsnittet beskrivs också de huvudprinciper som du bör tänka på när du hanterar och optimerar leveransen.

## Konfiguration {#configuration}

Den här funktionen är tillgänglig via ett dedikerat paket i Adobe Campaign. Paketet måste vara installerat för att du ska kunna använda det. När du är klar startar du om servern så att paketet kan användas.
* För värdbaserade klienter och hybridklienter konfigureras **Leveransövervakning** av Adobe tekniska support och konsulter. Kontakta din kontoansvarige på Adobe om du vill ha mer information.

* För lokala installationer måste du installera **[!UICONTROL Deliverability monitoring (Email Deliverability)]**-paketet via **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]**-menyn. Mer information finns i [Installera inbyggda Campaign-paket](../../installation/using/installing-campaign-standard-packages.md).

I Adobe Campaign hanteras **Leveransövervakning** av arbetsflödet **[!UICONTROL Refresh for deliverability]**. Det installeras som standard på alla instanser och gör att du kan initiera listan över regler för studsmeddelanden, domänlistan och listan över MX:er. När **[!UICONTROL Deliverability monitoring (Email Deliverability)]**-paketet har installerats körs det här arbetsflödet varje natt för att regelbundet uppdatera listan över regler och göra det möjligt att aktivt hantera plattformsleveransen.

## Bakgrund {#background}

E-postleveransen utgör en stor utmaning för marknadsförarna, oavsett om de skickar några tusen meddelanden eller flera miljarder. Ett av fem meddelanden når aldrig inkorgen, eller den avsedda mottagaren.

När e-postleveransen väl betecknas som ett&quot;tekniskt problem&quot; för IT-avdelningen fortsätter e-postleveransen att hamna högre på marknadsföringsagendan. Det beror på att kunniga marknadsförare inser att även om många av elementen är av teknisk natur är leveransbarhet i slutändan ett affärsproblem med betydande intäktseffekter.

Ta en titt på e-postmarknadsföringstratten. Leveransen avgör antalet mottagna meddelanden, vilket i sin tur påverkar varje efterföljande fas av tratten. Färre e-postmeddelanden har fått färre öppningar, färre klick och färre konverteringar. **För företag med en stor databas kan skillnaden mellan genomsnittlig och stor leveransförmåga bokstavligen betyda hundratusentals till miljontals dollar i intäkter.**

![](assets/deliverability_overview_1.png)

Genom att betala för genomsnittlig (80 %) leverans lämnar marknadsförarna stora konverteringar - och dollar - på bordet.

Exakt vad är e-postleverans? Och hur kan marknadsförarna förbättra leveransmöjligheterna för att vidga trattens utlopp och få ut mer av sina e-postkampanjer?

E-postleverans är en uppsättning egenskaper som avgör hur ett meddelande kan nå sin destination via en personlig e-postadress inom en kort tid och med den förväntade kvaliteten i fråga om innehåll och format. Dessa egenskaper kan delas in i fyra huvudkategorier: datakvalitet, meddelande och innehåll, utskick av infrastruktur och anseende. Tillsammans utgör de grunden för ett framgångsrikt program för e-postleverans. I den här översikten beskrivs de fyra grundläggande aspekterna av e-postleverans och de bästa sätten att nå inkorgen och generera större intäkter från e-postmarknadsföringsprogram.

<!--![](assets/deliverability_overview_2.png)-->
