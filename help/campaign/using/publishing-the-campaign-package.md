---
title: Publicera kampanjpaketet
seo-title: Publicera kampanjpaketet
description: Publicera kampanjpaketet
seo-description: null
page-status-flag: never-activated
uuid: f2d35a8d-191f-4c53-8682-7ccce2a94257
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: distributed-marketing
discoiquuid: 8653d4fc-e47f-451a-95f2-c9209a252664
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 3%

---


# Publicera kampanjpaketet{#publishing-the-campaign-package}

Operatörer av centralenheter publicerar kampanjer som de vill erbjuda lokala enheter i **[!UICONTROL list of campaign packages]**.

Kampanjpaketen måste godkännas av den centrala enheten innan de kan publiceras i kampanjpaketlistan. För att göra detta kan du ange en granskare eller grupp av granskare via **[!UICONTROL Approval parameters]** länken i kampanjpaketet.

## Tilldela en granskare {#assigning-a-reviewer}

Om du vill välja granskare klickar du på **[!UICONTROL Approval parameters]** länken i kampanjpaketet och väljer granskare i listrutan.

![](assets/s_advuser_mkg_dist_define_valid.png)

Du kan sedan starta godkännandeprocessen genom att klicka **[!UICONTROL Submit for approval]**.

![](assets/s_advuser_mkg_dist_valid_process.png)

Därefter skickas ett meddelande till granskaren som bekräftar att det här kampanjpaketet är tillgängligt. Meddelandet innehåller en länk för att godkänna eller avvisa godkännandet via webbåtkomst.

![](assets/s_advuser_mkg_dist_valid_process1.png)

>[!NOTE]
>
>På organisationsnivå kan du även ange granskare som ska godkänna order. For more on this, refer to [Organizational entities](../../campaign/using/about-distributed-marketing.md#organizational-entities).

## Lägga till andra granskare {#adding-other-reviewers}

Du kan lägga till andra granskare från **[!UICONTROL Edit...]** länken som finns på kampanjpaketets **[!UICONTROL Approval parameters...]** flik.

![](assets/s_advuser_mkg_dist_select_op_valid.png)

## Godkännandeperioder {#approval-periods}

Som standard får granskarna tre dagar på sig att bearbeta godkännandet.

I fönstret Redigera granskare kan du även ange påminnelser för att skicka ett eller flera meddelanden om ett kampanjpaket inte har godkänts. Det gör du genom att klicka på **[!UICONTROL Add reminder]** länken och sedan på **[!UICONTROL Add]** knappen.

Påminnelser kan skickas ut ett visst datum och/eller **x** dagar efter inlämningsdatumet. Typen av påminnelse kan konfigureras i den första kolumnen i tabellen med påminnelser. I exemplet nedan får granskarna ett påminnelsemeddelande den 29/01/2014, dvs. två dagar före det datum som markeras i **[!UICONTROL Date]** kolumnen, och en andra påminnelse en dag före godkännandeperiodens slut, dvs. två dagar efter det att ansökan om godkännande lämnats in.

![](assets/s_advuser_mkg_dist_reminder_planning.png)

När paketet har definierats och skickats för godkännande visas körningsschemat på **[!UICONTROL Audit]** fliken. Den visar bearbetningens tidsgräns som beräknats baserat på tidigare konfiguration samt datum för alla konfigurerade påminnelser.

## Godkännande via Adobe Campaign Console {#approving-via-the-adobe-campaign-console}

Om ingen granskare har angetts, eller om ingen av de anmälda operatorerna har godkänt paketet, kan du med knappen gå direkt till godkännandet från kampanjpaketet **[!UICONTROL Approve the package]** **[!UICONTROL Dashboard]** eller från paketöversikten.

![](assets/s_advuser_mkg_dist_valid_button.png)

Efter godkännande publiceras kampanjen, läggs till i listan och så snart som dess tillgänglighetsdatum har nåtts kan lokala enheter använda den. Om de lokala entiteterna angavs när kampanjen skapades skickas ett meddelande till operatörerna i meddelandegruppen för att meddela dem att kampanjen är tillgänglig. Om ingen entitet har angetts i förväg är kampanjen som standard tillgänglig för alla lokala entiteter. For more on this, refer to [Organizational entities](../../campaign/using/about-distributed-marketing.md#organizational-entities).
