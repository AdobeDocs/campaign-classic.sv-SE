---
product: campaign
title: Anslutningsgränser
description: Anslutningsgränser
feature: Monitoring
badge-v7-prem: label="Endast lokal/hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 4ee05559-e719-4e6e-b42c-1e82df428871
source-git-commit: 757e3a5395f24e0bdd04737aba0458881e4ea780
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 4%

---

# Anslutningsgränser{#connection-thresholds}



För servrar med stor belastning kan anslutningens tröskelvärde överskridas. I alla händelser är det bra att ta reda på varför.

Det finns tre olika tröskelvärden:

* Tröskelvärdet **för webbanslutning**, konfigurerat på webbservern. Kontakta systemadministratören om du vill ändra den.

* Tröskelvärdet **för databasanslutning**. Kontakta databasadministratören om du vill ändra den.

* Tröskelvärdet **för Adobe Campaign-anslutningen**, finns på två platser:

   * **Tomcat** sida: alla frågor som verkligen kommer från Adobe Campaign Tomcat-klienten.

     Det här tröskelvärdet har konfigurerats i filen **nl6/tomcat-X/conf/server.xml**. Med attributet **maxThreads** kan du öka tröskelvärdet för antalet frågor som bearbetas samtidigt. Den kan till exempel ändras till 250.

     ```
     <Connector protocol="HTTP/1.1" port="8080"
                    maxThreads="75"
                    minSpareThreads="5"
                    enableLookups="true" redirectPort="8443"
                    acceptCount="100" connectionTimeout="20000"
                    disableUploadTimeout="true" />
         <Engine name="Tomcat-Standalone" defaultHost="localhost">
           <Host name="localhost" appBase="./"
                 unpackWARs="true" autoDeploy="true">
     ```

   * **Database**: set of all connections open at the same time on the database by a process.

     Det här tröskelvärdet har konfigurerats i filen **nl6/conf/serverConf.xml**. Med attributet **maxCnx** i **datakällpoolen** kan du öka tröskelvärdet för frågor som bearbetas samtidigt.

     ```
         <!-- Data source
              -->
           <dataSource name="default">
             <dbcnx NChar="" bulkCopyUtility="" dbSchema="" encrypted="" login="" password="" provider="" server="" timezone="" unicodeData="" useTimestampTZ=""/>
             <sqlParams funcPrefix="">
               <postConnectSQL/>
             </sqlParams>
             <pool aliveTestDelaySec="600" freeCnx="0" maxCnx="90" maxIdleDelaySec="1200"/>
           </dataSource>
     ```
