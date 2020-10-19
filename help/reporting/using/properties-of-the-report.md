---
title: Rapportens egenskaper
description: Läs mer om inställningarna för rapportegenskaper
page-status-flag: never-activated
uuid: 56163f53-d115-45b8-94a5-c173ac4c6533
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 5ec88743-be51-438c-9064-dd0196fdd7d3
translation-type: tm+mt
source-git-commit: b0b9a0714075474bf52c3eed78d45bcef25b44fc
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 1%

---


# Rapportens egenskaper{#properties-of-the-report}

Ni kan anpassa och konfigurera rapporten efter era behov. Om du vill göra det redigerar du egenskaperna för den. Rapportegenskaperna nås via knappen **[!UICONTROL Properties]** ovanför aktivitetssekvensdiagrammet.

![](assets/s_ncs_advuser_report_properties_01.png)

Allmänna egenskaper beskrivs nedan. Avancerade funktioner som har konfigurerats på flikarna **[!UICONTROL Parameters]**, **[!UICONTROL Variables]** och **[!UICONTROL Scripts]** beskrivs [i det här avsnittet](../../reporting/using/advanced-functionalities.md).

## Allmänna egenskaper {#overall-properties}

På fliken **[!UICONTROL General]** i rapportegenskaperna kan du redigera inställningarna som listas nedan:

* Rapportens etikett och interna namn. Den **[!UICONTROL Internal name]** används i rapportens slutliga URL. Den ska inte ändras efter att rapporten har skapats.

* Rapportmappen **** väljs när rapporten skapas. Ett tips är att skapa en dedikerad mapp för anpassade rapporter så att de inte blandas med [inbyggda rapporter](../../reporting/using/about-campaign-built-in-reports.md).

* Du väljer **Lagring** när du skapar rapporten. Om du vill ändra datatabellen i rapporten klickar du på **[!UICONTROL Select link]** ikonen till höger om **[!UICONTROL Document type]** fältet.

   ![](assets/s_ncs_advuser_report_properties_02.png)

* Parametrarna för **åtkomstkontroll** . Dessa inställningar beskrivs nedan.

## Controlling access to the report {#report-accessibility}

En rapport kan nås via Adobe Campaign-konsolen eller en webbläsare. I så fall kan det vara nödvändigt att konfigurera åtkomstkontrollen för rapporten enligt nedan.

![](assets/s_ncs_advuser_report_properties_02b.png)

Möjliga alternativ är:

* **[!UICONTROL Anonymous access]**: det här alternativet ger obegränsad åtkomst till rapporten. Det går dock inte att manipulera något.

   Rättigheterna för den tekniska operatorn &#39;webapp&#39; används för att visa rapportelement. Läs mer [i det här avsnittet](../../platform/using/access-management.md#default-operators).

* **[!UICONTROL Access control]**: Med det här alternativet kan Adobe Campaign-operatörer få åtkomst till det när de har loggat in.
* **[!UICONTROL Specific account]**: Med det här alternativet kan du köra rapporten med rättigheter för den operator som är markerad i **[!UICONTROL Operator]** fältet.

## Hantera rapportlokalisering {#managing-report-localization}

Du kan konfigurera de språk som du vill att rapporten ska översättas till. Klicka på **[!UICONTROL Localization]** fliken om du vill göra det.

![](assets/s_ncs_advuser_report_properties_06.png)

Redigeringsspråket är det språk du skriver på. När du lägger till ett språk visas underfliken på rapportredigeringssidan.

![](assets/s_ncs_advuser_report_properties_05a.png)

>[!NOTE]
>
>Mer information om webbsidelokalisering i Campaign finns i [det här avsnittet](../../web/using/translating-a-web-form.md).

## Anpassa HTML-återgivning {#personalizing-html-rendering}

På fliken **[!UICONTROL Rendering]** kan du anpassa sidans datavisningsläge. Du kan välja:

* Diagramåtergivningsmotorn: Adobe Campaign har två olika lägen för att generera diagramåtergivning. Som standard är återgivningsmotorn HTML 5. Om det behövs kan du välja Flash-återgivning.
* Navigeringstypen i rapporten: via knappar eller länkar.
* Standardpositionen för etiketter för rapportelement. Den här positionen kan laddas över för varje element.
* Den mall eller det tema som används för att generera rapportsidor.

![](assets/s_ncs_advuser_report_properties_08.png)

## Anpassa felsidan {#personalizing-the-error-page}

På fliken **[!UICONTROL Error page]** kan du konfigurera det meddelande som visas om ett fel uppstår i rapportvisningen.

Du kan definiera texter och länka dem till specifika identifierare för att hantera rapportlokalisering. Mer information finns i [Lägga till ett sidhuvud och en sidfot](../../reporting/using/element-layout.md#adding-a-header-and-a-footer).

![](assets/s_ncs_advuser_report_properties_11.png)
