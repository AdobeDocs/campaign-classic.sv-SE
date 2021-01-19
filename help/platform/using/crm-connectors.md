---
solution: Campaign Classic
product: campaign
title: CRM-kopplingar
description: Kom igång med CRM Connectors i Campaign
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 2838ced5f5d562914c0791e6a0b8f02dd61006b4
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 24%

---


# CRM-kopplingar{#crm-connectors}

## Kom igång med CRM-anslutningar {#about-crm-connectors}

Adobe Campaign tillhandahåller olika CRM-kopplingar för att länka din plattform i Adobe Campaign till dina tredjepartssystem. Med dessa CRM-kopplingar kan du synkronisera kontakter, konton och inköp osv. De låter dig enkelt integrera din applikation med olika tredjeparts- och företagsapplikationer.

Dessa kopplingar möjliggör snabb och enkel dataintegrering. Adobe Campaign erbjuder en dedikerad guide för att samla in och välja bland tabellerna i CRM. Detta garanterar dubbelriktad synkronisering för att säkerställa att data alltid är aktuella i alla system.

>[!NOTE]
>
>Den här funktionen är tillgänglig i Adobe Campaign via **CRM-anslutningarna** dedikerade paket.


### Kompatibla system {#compatible-crm-systems-and-limitations}

CRM och versioner som stöds finns detaljerade i Campaign [Kompatibilitetsmatrisen](../../rn/using/compatibility-matrix.md).

>[!NOTE]
>
>CRM-anslutningarna fungerar bara med en säker URL (https).

### Implementeringssteg {#crm-implementation-steps}

Lär dig steg för steg hur du ansluter Campaign och Microsoft Dynamics [i det här avsnittet](../../platform/using/crm-ms-dynamics.md)

Om du vill använda CRM-anslutningar i Adobe Campaign gör du så här:

1. Skapa ett nytt externt konto via noden **[!UICONTROL Administration > Platform > External accounts]** i Adobe Campaign-trädet.
1. Välj det CRM-system som du vill ansluta Campaign till.
1. Ange inställningar för att aktivera anslutningen.
1. Kör konfigurationsguiden för att generera den tillgängliga CRM-tabellen: Med konfigurationsguiden kan du samla in tabeller och skapa det matchande schemat.

   Exempel på **konfigurationsguiden för Salesforce**:

   ![](assets/crm_connectors_sfdc_launch.png)

   >[!NOTE]
   >
   >För att godkänna installationen måste du logga ut och sedan logga in på Adobe Campaign Console igen.

1. Kontrollera schemat som genererats i Adobe Campaign i noden **[!UICONTROL Administration > Configuration > Data schemas]**.

   Exempel för **Salesforce**-schema:

   ![](assets/crm_connectors_sfdc_table.png)

1. När schemat har skapats kan du synkronisera uppräkningar automatiskt via CRM till Adobe Campaign.

   Det gör du genom att klicka på länken **[!UICONTROL Synchronizing enumerations...]** och välja den Adobe Campaign-uppräkning som matchar CRM-uppräkningen.

   >[!NOTE]
   >
   >Du kan ersätta alla värden i en Adobe Campaign-uppräkning med dem i CRM: Om du vill göra det väljer du **[!UICONTROL Yes]** i kolumnen **[!UICONTROL Replace]**.

   Exempel på **Salesforce**-uppräkningar:

   ![](assets/crm_connectors_sfdc_enum.png)

   Klicka på **[!UICONTROL Next]** och sedan på **[!UICONTROL Start]** för att börja importera listan.

1. Kontrollera de importerade värdena på **[!UICONTROL Administration > Platform > Enumerations]**-menyn.

   ![](assets/crm_connectors_sfdc_exe.png)

   >[!NOTE]
   >
   > Flera urvalsuppräkningar i Salesforce stöds inte.

1. Om du vill synkronisera data mellan Adobe Campaign-data och CRM-systemet måste du skapa ett arbetsflöde och använda aktiviteten **[!UICONTROL CRM connector]**.

   ![](assets/crm_connectors_sfdc_wf.png)

   Läs mer om datasynkronisering [på den här sidan](../../platform/using/crm-data-sync.md).
