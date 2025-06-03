---
product: campaign
title: Campaign - Salesforce CRM Connector
description: Lär dig hur du ansluter Campaign och Salesforce
feature: Salesforce Integration
exl-id: 94a1f00d-e952-4edd-9012-f71c87b897ca
hide: true
hidefromtoc: true
source-git-commit: 42cec0e9bede94a2995a5ad442822512bda14f2b
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---

# Connect Campaign och Salesforce.com{#connect-to-sfdc}



På den här sidan får du lära dig hur du ansluter Campaign Classic till **Salesforce**.

Datasynkronisering utförs via en dedikerad arbetsflödesaktivitet. [Läs mer](../../platform/using/crm-data-sync.md).


Med det externa kontot kan du importera och exportera Salesforce-data till Adobe Campaign.
Så här konfigurerar du CRM Connector för Salesforce:

1. Skapa ett nytt externt konto via noden **[!UICONTROL Administration > Platform > External accounts]** i Adobe Campaign-trädet.
1. Välj **[!UICONTROL Salesforce.com]**.
1. Ange inställningar för att aktivera anslutningen.

   ![](assets/ext_account_17.png)

   Om du vill konfigurera det externa Salesforce CRM-kontot så att det fungerar med Adobe Campaign måste du ange följande information:

   * **[!UICONTROL Account]**
Det konto som används för att logga in på Salesforce CRM.

   * **[!UICONTROL Password]**
Lösenord som används för att logga in på Salesforce CRM.

   * **[!UICONTROL Client identifier]**
Om du vill veta var du hittar din klient-ID kan du läsa den här [sidan](https://help.salesforce.com/articleView?id=000205876&amp;type=1) .

   * **[!UICONTROL Security token]**
Om du vill veta var du kan hitta din säkerhetstoken kan du läsa [sidan ](https://help.salesforce.com/articleView?id=000205876&amp;type=1) .

   * **[!UICONTROL API version]**
Välj version av API:t.
1. Kör konfigurationsassistenten för att generera den tillgängliga CRM-tabellen: med konfigurationsassistenten kan du samla in tabeller och skapa det matchande schemat.

   ![](assets/crm_connectors_sfdc_launch.png)

   >[!NOTE]
   >
   >För att godkänna installationen måste du logga ut och sedan logga in på Adobe Campaign Console igen.

1. Kontrollera schemat som genererats i Adobe Campaign i noden **[!UICONTROL Administration > Configuration > Data schemas]**.

   Exempel på **Salesforce**-schema:

   ![](assets/crm_connectors_sfdc_table.png)

1. När schemat har skapats kan du synkronisera uppräkningar automatiskt från Salesforce till Adobe Campaign.

   Om du vill göra det klickar du på länken **[!UICONTROL Synchronizing enumerations...]** och väljer den uppräkning av Adobe Campaign som matchar uppräkningen i Salesforce.



   ![](assets/crm_connectors_sfdc_enum.png)

   >[!NOTE]
   >
   >Du kan ersätta alla värden i en Adobe Campaign-uppräkning med dem i CRM: om du vill göra det väljer du **[!UICONTROL Yes]** i kolumnen **[!UICONTROL Replace]**.


   Klicka på **[!UICONTROL Next]** och sedan på **[!UICONTROL Start]** för att börja importera listan.

1. Kontrollera de importerade värdena på menyn **[!UICONTROL Administration > Platform > Enumerations]**.

   ![](assets/crm_connectors_sfdc_exe.png)

   >[!NOTE]
   >
   > Uppräkningar av flera markeringar stöds inte.

Campaign och Salesforce.com är nu sammankopplade. Du kan konfigurera datasynkronisering mellan de två systemen.

Om du vill synkronisera data mellan Adobe Campaign-data och SFDC måste du skapa ett arbetsflöde och använda aktiviteten **[!UICONTROL CRM connector]**.

![](assets/crm_connectors_sfdc_wf.png)

Läs mer om datasynkronisering [på den här sidan](../../platform/using/crm-data-sync.md).
