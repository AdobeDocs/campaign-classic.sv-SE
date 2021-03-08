---
solution: Campaign Classic
product: campaign
title: Rapportens egenskaper
description: Läs mer om inställningarna för rapportegenskaper
audience: reporting
content-type: reference
topic-tags: creating-new-reports
translation-type: tm+mt
source-git-commit: 693e38477b318ee44e0373a04d8524ddf128fe36
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 1%

---


# Rapportens egenskaper{#properties-of-the-report}

Ni kan anpassa och konfigurera rapporten efter era behov. Om du vill göra det redigerar du egenskaperna för den. Rapportegenskaperna nås via knappen **[!UICONTROL Properties]** ovanför aktivitetssekvensdiagrammet.

![](assets/s_ncs_advuser_report_properties_01.png)

Allmänna egenskaper beskrivs nedan. Avancerade funktioner som konfigurerats på flikarna **[!UICONTROL Parameters]**, **[!UICONTROL Variables]** och **[!UICONTROL Scripts]** beskrivs [i det här avsnittet](../../reporting/using/advanced-functionalities.md).

## Allmänna egenskaper {#overall-properties}

På fliken **[!UICONTROL General]** i rapportegenskaperna kan du redigera inställningarna som listas nedan:

* Rapportens etikett och interna namn. **[!UICONTROL Internal name]** används i den slutliga URL:en för rapporten. Den ska inte ändras efter att rapporten har skapats.

* Rapporten **Mapp** markeras när rapporten skapas. Ett tips är att skapa en dedikerad mapp för anpassade rapporter så att de inte blandas med [inbyggda rapporter](../../reporting/using/about-campaign-built-in-reports.md).

* **Lagring** väljs när rapporten skapas. Om du vill ändra datatabellen för rapporten klickar du på ikonen **[!UICONTROL Select link]** till höger om fältet **[!UICONTROL Document type]**.

   ![](assets/s_ncs_advuser_report_properties_02.png)

* **Åtkomstkontrollens** parametrar. Dessa inställningar beskrivs nedan.

## Kontrollera åtkomst till rapporten {#report-accessibility}

En rapport kan nås via Adobe Campaign-konsolen eller en webbläsare. I så fall kan det vara nödvändigt att konfigurera åtkomstkontrollen för rapporten enligt nedan.

![](assets/s_ncs_advuser_report_properties_02b.png)

Möjliga alternativ är:

* **[!UICONTROL Anonymous access]**: det här alternativet ger obegränsad åtkomst till rapporten. Det går dock inte att manipulera något.

   Behörigheter för den tekniska operatorn&quot;webbapp&quot; används för att visa rapportelement. Läs mer [i det här avsnittet](../../platform/using/access-management-operators.md).

* **[!UICONTROL Access control]**: Med det här alternativet kan Adobe Campaign-operatörer få åtkomst till det när de har loggat in.
* **[!UICONTROL Specific account]**: Med det här alternativet kan du köra rapporten med rättigheter för den operator som är vald i  **[!UICONTROL Operator]** fältet.

## Hantera rapportlokalisering {#managing-report-localization}

Du kan konfigurera de språk som du vill att rapporten ska översättas till. Det gör du genom att klicka på fliken **[!UICONTROL Localization]**.

![](assets/s_ncs_advuser_report_properties_06.png)

Redigeringsspråket är det språk du skriver på. När du lägger till ett språk visas underfliken på rapportredigeringssidan.

![](assets/s_ncs_advuser_report_properties_05a.png)

>[!NOTE]
>
>Mer information om webbsideslokalisering i Campaign finns i [det här avsnittet](../../web/using/translating-a-web-form.md).

## Anpassa HTML-återgivning {#personalizing-html-rendering}

På fliken **[!UICONTROL Rendering]** kan du anpassa sidans datavisningsläge. Du kan välja:

* Diagramåtergivningsmotorn: som standard är återgivningsmotorn HTML 5.
* Navigeringstypen i rapporten: via knappar eller länkar.
* Standardpositionen för etiketter för rapportelement. Den här positionen kan laddas över för varje element.
* Den mall eller det tema som används för att generera rapportsidor.

![](assets/s_ncs_advuser_report_properties_08.png)

## Anpassa felsidan {#personalizing-the-error-page}

På fliken **[!UICONTROL Error page]** kan du konfigurera det meddelande som visas om ett fel uppstår i rapportvisningen.

Du kan definiera texter och länka dem till specifika identifierare för att hantera rapportlokalisering. Mer information finns i [Lägga till ett sidhuvud och en sidfot](../../reporting/using/element-layout.md#adding-a-header-and-a-footer).

![](assets/s_ncs_advuser_report_properties_11.png)
