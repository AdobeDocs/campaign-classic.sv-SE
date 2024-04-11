---
product: campaign
title: Rapportens egenskaper
description: Läs mer om inställningarna för rapportegenskaper
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Reporting, Monitoring
exl-id: dfa9d329-1086-4f6d-9d03-df159cad5495
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 1%

---

# Rapportens egenskaper{#properties-of-the-report}



Ni kan anpassa och konfigurera rapporten efter era behov. Om du vill göra det redigerar du egenskaperna för den. Rapportegenskaper nås via **[!UICONTROL Properties]** ovanför aktivitetssekvensdiagrammet.

![](assets/s_ncs_advuser_report_properties_01.png)

Allmänna egenskaper beskrivs nedan. Avancerade funktioner som konfigurerats i **[!UICONTROL Parameters]**, **[!UICONTROL Variables]** och **[!UICONTROL Scripts]** beskrivs [i det här avsnittet](../../reporting/using/advanced-functionalities.md).

## Allmänna egenskaper {#overall-properties}

I **[!UICONTROL General]** på fliken med rapportegenskaperna kan du redigera inställningarna som listas nedan:

* Rapportens etikett och interna namn. The **[!UICONTROL Internal name]** används i rapportens slutliga URL. Den ska inte ändras efter att rapporten har skapats.

* Rapporten **Mapp** väljs när rapporten skapas. Det bästa sättet är att skapa en dedikerad mapp för anpassade rapporter så att de inte blandas med [inbyggda rapporter](../../reporting/using/about-campaign-built-in-reports.md).

* The **Lagring** väljs när rapporten skapas. Om du vill ändra datatabellen i rapporten klickar du på **[!UICONTROL Select link]** ikonen till höger om **[!UICONTROL Document type]** fält.

  ![](assets/s_ncs_advuser_report_properties_02.png)

* The **Åtkomstkontroll** parametrar. Dessa inställningar beskrivs nedan.

## Kontrollera åtkomst till rapporten {#report-accessibility}

En rapport kan nås via Adobe Campaign-konsolen eller en webbläsare. I så fall kan det vara nödvändigt att konfigurera åtkomstkontrollen för rapporten enligt nedan.

![](assets/s_ncs_advuser_report_properties_02b.png)

Möjliga alternativ är:

* **[!UICONTROL Anonymous access]**: det här alternativet ger obegränsad åtkomst till rapporten. Det går dock inte att manipulera något.

  Behörigheter för den tekniska operatorn&quot;webbapp&quot; används för att visa rapportelement. Läs mer [i det här avsnittet](../../platform/using/access-management-operators.md).

* **[!UICONTROL Access control]**: Med det här alternativet kan Adobe Campaign-operatorer få åtkomst till det när de har loggat in.
* **[!UICONTROL Specific account]**: det här alternativet gör att du kan köra rapporten med rättigheterna för den operator som valts i **[!UICONTROL Operator]** fält.

## Översätt din rapport {#report-localization}

Du kan konfigurera de språk som du vill att rapporten ska översättas till. Klicka på **[!UICONTROL Localization]** -fliken.

![](assets/s_ncs_advuser_report_properties_06.png)

Redigeringsspråket är det språk du skriver på. När du lägger till ett språk visas underfliken på rapportredigeringssidan.

![](assets/s_ncs_advuser_report_properties_05a.png)

>[!NOTE]
>
>Mer information om webbsidelokalisering i Campaign finns i [det här avsnittet](../../web/using/translating-a-web-form.md).

## Anpassa rendering av HTML {#personalizing-html-rendering}

I **[!UICONTROL Rendering]** kan du anpassa sidans datavisningsläge. Du kan välja:

* Navigeringstypen i rapporten: via knappar eller länkar.
* Standardpositionen för etiketter för rapportelement. Den här positionen kan laddas över för varje element.
* Den mall eller det tema som används för att generera rapportsidor.

![](assets/s_ncs_advuser_report_properties_08.png)

## Anpassa felsidan {#personalizing-the-error-page}

The **[!UICONTROL Error page]** Med -fliken kan du konfigurera det meddelande som visas om ett fel uppstår i rapportvisningen.

Du kan definiera texter och länka dem till specifika identifierare för att hantera rapportlokalisering. Mer information finns i [Lägga till ett sidhuvud och en sidfot](../../reporting/using/element-layout.md#adding-a-header-and-a-footer).

![](assets/s_ncs_advuser_report_properties_11.png)
