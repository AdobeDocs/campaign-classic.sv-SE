---
product: campaign
title: Anslutningsgränser
description: Anslutningsgränser
feature: Monitoring
badge-v7-prem: label="lokal och hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 4ee05559-e719-4e6e-b42c-1e82df428871
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 4%

---

# Anslutningsgränser{#connection-thresholds}



För servrar med stor belastning kan anslutningens tröskelvärde överskridas. I alla händelser är det bra att ta reda på varför.

Det finns tre olika tröskelvärden:

* The **Tröskelvärde för webbanslutning**, konfigurerad på webbservern. Kontakta systemadministratören om du vill ändra den.

* The **tröskelvärde för databasanslutning**. Kontakta databasadministratören om du vill ändra den.

* The **Tröskelvärde för Adobe Campaign-anslutning**, finns på två platser:

   * **Tomcat** sida: alla frågor som faktiskt kommer från Adobe Campaign Tomcat-klienten.

     Detta tröskelvärde konfigureras i **nl6/tomcat-8/conf/server.xml** -fil. The **maxThreads** kan du öka tröskelvärdet för antalet frågor som bearbetas samtidigt. Den kan till exempel ändras till 250.

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

   * **Databas**: en uppsättning av alla anslutningar som öppnas samtidigt i databasen av en process.

     Detta tröskelvärde är konfigurerat i filen **nl6/conf/serverConf.xml**. The **maxCnx** attribut finns i **datakällpool** Med kan du öka tröskelvärdet för frågor som behandlas samtidigt.

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
