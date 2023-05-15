---
product: campaign
title: Kampanj - Salesforce CRM Connector
description: Lär dig hur du ansluter Campaign och Salesforce
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Salesforce Integration
exl-id: 94a1f00d-e952-4edd-9012-f71c87b897ca
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# Connect Campaign och Salesforce.com{#connect-to-sfdc}



På den här sidan får du lära dig att ansluta Campaign Classic till **Salesforce**.

Datasynkronisering utförs via en dedikerad arbetsflödesaktivitet. [Läs mer](../../platform/using/crm-data-sync.md).


Med det externa kontot kan du importera och exportera Salesforce-data till Adobe Campaign.
Så här konfigurerar du CRM Connector för Salesforce:

1. Skapa ett nytt externt konto via **[!UICONTROL Administration > Platform > External accounts]** noden i Adobe Campaign-trädet.
1. Välj **[!UICONTROL Salesforce.com]**.
1. Ange inställningar för att aktivera anslutningen.

   ![](assets/ext_account_17.png)

   Om du vill konfigurera det externa Salesforce CRM-kontot så att det fungerar med Adobe Campaign måste du ange följande information:

   * **[!UICONTROL Account]**
Det konto som används för att logga in i Salesforce CRM.

   * **[!UICONTROL Password]**
Lösenord som används för att logga in i Salesforce CRM.

   * **[!UICONTROL Client identifier]**
Om du vill veta var du kan hitta din klientidentifierare kan du läsa detta [page](https://help.salesforce.com/articleView?id=000205876&amp;type=1).

   * **[!UICONTROL Security token]**
Om du vill veta var du hittar din säkerhetstoken kan du läsa detta [page](https://help.salesforce.com/articleView?id=000205876&amp;type=1).

   * **[!UICONTROL API version]**
Välj version av API:t.
1. Kör konfigurationsguiden för att generera den tillgängliga CRM-tabellen: Med konfigurationsguiden kan du samla in tabeller och skapa det matchande schemat.

   ![](assets/crm_connectors_sfdc_launch.png)

   >[!NOTE]
   >
   >För att godkänna installationen måste du logga ut och sedan logga in på Adobe Campaign Console igen.

1. Kontrollera schemat som genererats i Adobe Campaign i **[!UICONTROL Administration > Configuration > Data schemas]** nod.

   Exempel på **Salesforce** schema:

   ![](assets/crm_connectors_sfdc_table.png)

1. När schemat har skapats kan du synkronisera uppräkningar automatiskt från Salesforce till Adobe Campaign.

   Om du vill göra det klickar du på **[!UICONTROL Synchronizing enumerations...]** och välj den Adobe Campaign-uppräkning som matchar Salesforce-uppräkningen.



   ![](assets/crm_connectors_sfdc_enum.png)

   >[!NOTE]
   >
   >Du kan ersätta alla värden i en Adobe Campaign-uppräkning med dem i CRM: för att göra detta väljer du **[!UICONTROL Yes]** i **[!UICONTROL Replace]** kolumn.


   Klicka **[!UICONTROL Next]** och sedan **[!UICONTROL Start]** för att börja importera listan.

1. Kontrollera de importerade värdena i dialogrutan **[!UICONTROL Administration > Platform > Enumerations]** -menyn.

   ![](assets/crm_connectors_sfdc_exe.png)

   >[!NOTE]
   >
   > Uppräkningar av flera markeringar stöds inte.

Campaign och Salesforce.com är nu anslutna. Du kan konfigurera datasynkronisering mellan de två systemen.

Om du vill synkronisera data mellan Adobe Campaign-data och SFDC måste du skapa ett arbetsflöde och använda **[!UICONTROL CRM connector]** aktivitet.

![](assets/crm_connectors_sfdc_wf.png)

Läs mer om datasynkronisering [på den här sidan](../../platform/using/crm-data-sync.md).
