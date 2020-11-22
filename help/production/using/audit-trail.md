---
solution: Campaign Classic
product: campaign
title: Verifieringskedja
description: Verifieringskedja
audience: production
content-type: reference
topic-tags: production-procedures
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 3%

---


# Verifieringskedja{#audit-trail}

I Adobe Campaign **[!UICONTROL Audit trail]** får du tillgång till den fullständiga historiken över ändringar som gjorts i instansen.

**[!UICONTROL Audit trail]** i realtid innehåller en omfattande lista över åtgärder och händelser som inträffar i din Adobe Campaign-instans. Det innehåller ett självbetjäningssätt att komma åt en datahistorik som kan hjälpa dig att besvara frågor som: vad som hände med dina arbetsflöden och vem som senast uppdaterade dem eller vad gjorde användarna i instansen.

>[!NOTE]
>
>Adobe Campaign granskar inte ändringar som gjorts i användarrättigheter, mallar, personalisering eller kampanjer.\
>Granskningsspårning kan bara hanteras av administratörer för instansen.

Granskningsspårning består av tre komponenter:

* **Schemagranskningsspår**: Kontrollera aktiviteterna och de senaste ändringarna av dina scheman.

   For more information on schemas, refer to this [page](../../configuration/using/data-schemas.md).

* **Arbetsflödets granskningsspår**: Kontrollera aktiviteter och de senaste ändringarna av arbetsflöden, och dessutom status för dina arbetsflöden, till exempel:

   * Starta
   * Pausa
   * Stoppa
   * Starta om
   * Rensa som är lika med åtgärden Rensa historik
   * Simulera vilket motsvarar åtgärden Starta i simuleringsläge
   * Aktivering som är lika med åtgärden Kör väntande uppgifter nu
   * Ovillkorligt stopp

   For more information on workflows, refer to this [page](../../workflow/using/about-workflows.md).

   Mer information om hur du övervakar arbetsflöden finns i det [dedikerade avsnittet](../../workflow/using/monitoring-workflow-execution.md).

* **Granskningsspår** för alternativ: Kontrollera aktiviteterna och de senaste ändringarna som du gjort.

   For more information on options, refer to this [page](../../installation/using/configuring-campaign-options.md).

## Åtkomst till granskningsspår {#accessing-audit-trail}

Så här kommer du åt instansens **[!UICONTROL Audit trail]** :

1. Öppna instansens **[!UICONTROL Explorer]** meny.
1. Välj **[!UICONTROL Administration]** **[!UICONTROL Audit]** .

   ![](assets/audit_trail_1.png)

1. Fönstret öppnas med en lista över **[!UICONTROL Audit trail]** dina enheter. Adobe Campaign granskar åtgärderna för att skapa, redigera och ta bort för arbetsflöden, alternativ och scheman.

   Välj en av enheterna om du vill veta mer om de senaste ändringarna.

   ![](assets/audit_trail_2.png)

1. I **[!UICONTROL Audit entity]** fönstret finns mer detaljerad information om den valda enheten:

   * **[!UICONTROL Type]** : Arbetsflöde, alternativ eller scheman.
   * **[!UICONTROL Entity]** : Internt namn på dina aktiviteter.
   * **[!UICONTROL Modified by]** : Användarnamn för den senaste personen som senast ändrade den här entiteten.
   * **[!UICONTROL Action]** : Senaste åtgärden som utfördes på den här entiteten, antingen Skapad, Redigerad eller Borttagen.
   * **[!UICONTROL Modification date]** : Datum för den senaste åtgärden som utfördes på den här entiteten.

   Kodblocket ger dig mer information om exakt vad som har ändrats i din enhet.

   ![](assets/audit_trail_3.png)

>[!NOTE]
>
>Som standard är kvarhållningsperioden 180 dagar för **[!UICONTROL Audit logs]** . Mer information om hur du ändrar kvarhållningsperioden finns på den här [sidan](../../production/using/database-cleanup-workflow.md#deployment-wizard).

## Aktivera/inaktivera granskningsspår {#enable-disable-audit-trail}

Granskningsspårning kan enkelt aktiveras eller inaktiveras för en viss aktivitet om du t.ex. vill spara utrymme i databasen.

För att göra detta:

1. Öppna instansens **[!UICONTROL Explorer]** meny.
1. Välj **[!UICONTROL Administration]** sedan **[!UICONTROL Platform]** under **[!UICONTROL Options]** menyn.

   ![](assets/audit_trail_4.png)

1. Välj något av följande alternativ beroende på vilken enhet du vill aktivera/inaktivera:

   * För arbetsflöde: **[!UICONTROL XtkAudit_Workflows]**
   * För scheman: **[!UICONTROL XtkAudit_DataSchema]**
   * För alternativ: **[!UICONTROL XtkAudit_Option]**
   * För varje enhet: **[!UICONTROL XtkAudit_Enable_All]**

   ![](assets/audit_trail_5.png)

1. Ändra **[!UICONTROL Value]** till 1 om du vill aktivera enheten eller till 0 om du vill inaktivera den.

   ![](assets/audit_trail_6.png)

1. Klicka på **[!UICONTROL Save]** .

