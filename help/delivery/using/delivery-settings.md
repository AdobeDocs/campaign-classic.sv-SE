---
product: campaign
title: Om leveransinställningar
description: Upptäck de specifika leveransinställningarna för v7
feature: Channel Configuration
role: User
hide: true
hidefromtoc: true
exl-id: 66250817-f829-4b8b-92dd-2daa92a97fe0
source-git-commit: d3d731c64cb5a430de6adac3aeb326f74134c436
workflow-type: tm+mt
source-wordcount: '696'
ht-degree: 2%

---

# Leveransinställningar {#about-delivery-settings}

Följande inställningar är specifika för Campaign Classic. Andra leveransinställningar finns i [dokumentationen för Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/gs-message.html?lang=sv-SE){target="_blank"}.

## Leveransanalys {#delivery-analysis}

### Förbättra resultatet av leveransanalysen {#improving-delivery-analysis}

Om du vill påskynda leveransförberedelsen kan du kontrollera alternativet **[!UICONTROL Prepare the delivery parts in the database]** innan du startar analysen.

När det här alternativet är aktiverat utförs leveransförberedelsen direkt i databasen, vilket avsevärt kan snabba upp analysen.

För närvarande är det här alternativet endast tillgängligt när följande villkor är uppfyllda:

* Leveransen måste vara ett e-postmeddelande. De andra kanalerna stöds inte för tillfället.
* Du får inte använda medelstor eller extern routning, endast bulkleveransroutningstyp. Du kan kontrollera routningen som används på fliken **[!UICONTROL General]** i **[!UICONTROL Delivery properties]**.
* Du kan inte ange en målgrupp som kommer från en extern fil som mål. Klicka på länken **[!UICONTROL To]** i **[!UICONTROL Email parameters]** för en enskild leverans och kontrollera att alternativet **[!UICONTROL Defined in the database]** är markerat. Kontrollera att mottagarna är **[!UICONTROL Specified by the inbound event(s)]** på fliken **[!UICONTROL Delivery]** för en leverans som används i ett arbetsflöde.
* Du måste använda en PostgreSQL-databas.

### Konfigurera analysprioriteten {#analysis-priority-}

När leveransen är en del av en kampanj finns det ytterligare ett alternativ på fliken **[!UICONTROL Advanced]**. På så sätt kan du ordna bearbetningsordningen för leveranser i samma kampanj.

Innan leveransen skickas analyseras varje leverans. Analysens längd beror på leveransens extraheringsfil. Ju större filstorlek, desto längre tid tar analysen och följande leveranser väntar.

Med alternativen för **[!UICONTROL Message preparation by the scheduler]** kan du prioritera leveransanalysen i ett kampanjarbetsflöde.

![](assets/delivery_analysis_priority.png)

Om en leverans är för stor är det bättre att tilldela den en låg prioritet för att undvika att analysen av andra arbetsflödesleveranser går långsammare.

>[!NOTE]
>
>Om du vill vara säker på att de större leveransanalyserna inte gör arbetsflödena långsammare kan du schemalägga deras körningar genom att trycka på **[!UICONTROL Schedule execution for a time of low activity]**.

## Leveranssändning {#delivery-sending}

### Konfigurera återförsök {#configuring-retries}

Tillfälligt olevererade meddelanden på grund av ett fel av typen **Mjuk** eller **Ignorerad** kan återförsökas automatiskt. Leveransfeltyperna och anledningarna visas i det här [avsnittet](understanding-delivery-failures.md#delivery-failure-types-and-reasons).

>[!IMPORTANT]
>
>Om du har uppgraderat till [Förbättrat MTA](sending-with-enhanced-mta.md) för värdbaserade eller hybridinstallerade installationer används inte längre inställningarna för nya försök i leveransen av Campaign. Mjuka avhoppsförsök och hur lång tid det tar mellan dem bestäms av den förbättrade MTA-metoden baserat på typ och allvarlighetsgrad för de avhoppssvar som kommer tillbaka från meddelandets e-postdomän.

För lokala installationer och värdbaserade/hybridinstallationer som använder det äldre kampanjavtalet MTA, visar det centrala avsnittet på fliken **[!UICONTROL Delivery]** för leveransparametrar hur många försök som ska utföras dagen efter leveransen och den minsta fördröjningen mellan återförsök.

![](assets/s_ncs_user_wizard_retry_param.png)

Som standard schemaläggs fem återförsök till den första dagen i leveransen med ett minsta intervall på en timme som sprids ut över dygnets 24 timmar. Ett nytt försök per dag är programmerat efter detta och fram till leveransdatumet, som definieras på fliken **[!UICONTROL Validity]**. Se [Definiera giltighetsperioden](#defining-validity-period).

### Definiera giltighetsperioden {#defining-validity-period}

När leveransen har startats kan meddelandena (och eventuella försök) skickas till leveransdatumet. Detta anges i leveransegenskaperna via fliken **[!UICONTROL Validity]**.

![](assets/s_ncs_user_email_del_valid_period.png)

* I fältet **[!UICONTROL Delivery duration]** kan du ange gränsen för globala leveransförsök. Detta innebär att Adobe Campaign skickar meddelanden som börjar på startdatumet och sedan, för meddelanden som bara returnerar ett fel, kommer regelbundna, konfigurerbara försök att utföras tills giltighetsgränsen nås.

  Du kan också välja att ange datum. Välj **[!UICONTROL Explicitly set validity dates]** om du vill göra det. I det här fallet kan du även ange datum för leveransdatum och giltighetsgräns. Den aktuella tiden används som standard, men du kan ändra den direkt i indatafältet.

  >[!IMPORTANT]
  >
  >Om du har uppgraderat till [Förbättrat MTA](sending-with-enhanced-mta.md) för värdbaserade eller hybridbaserade installationer, kommer inställningen **[!UICONTROL Delivery duration]** i e-postleveranserna för Campaign endast att användas om den är inställd på **.5 dagar eller mindre**. Om du anger ett värde som är högre än 3,5 dagar kommer det inte att beaktas.

* **Giltighetsgräns för resurser**: Fältet **[!UICONTROL Validity limit]** används för överförda resurser, främst för spegelsidan och bilder. Resurserna på den här sidan är giltiga under en begränsad tid (för att spara diskutrymme).

  Värdena i det här fältet kan uttryckas i de enheter som visas i [det här avsnittet](../../platform/using/adobe-campaign-workspace.md#default-units).
