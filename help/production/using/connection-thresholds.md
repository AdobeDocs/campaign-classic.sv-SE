---
solution: Campaign Classic
product: campaign
title: Anslutningsgränser
description: Anslutningsgränser
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 3%

---


# Anslutningsgränser{#connection-thresholds}

För servrar med stor belastning kan anslutningens tröskelvärde överskridas. I alla händelser är det bra att ta reda på varför.

Det finns tre olika tröskelvärden:

1. Tröskelvärdet för webbanslutning, konfigurerat på webbservern. Kontakta systemadministratören om du vill ändra den.
1. Tröskelvärde för databasanslutning. Kontakta databasadministratören om du vill ändra den.
1. Tröskelvärdet för Adobe Campaign-anslutning finns på två platser:

   * Tomcat side: alla frågor som faktiskt kommer från Adobe Campaign Tomcat-klienten.

      Detta tröskelvärde konfigureras i filen **nl6/tomcat-8/conf/server.xml**. Med attributet **maxThreads** kan du öka tröskelvärdet för antalet frågor som bearbetas samtidigt. Den kan till exempel ändras till 250.

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

   * Databas: alla anslutningar som är öppna samtidigt i databasen av en process.

      Detta tröskelvärde konfigureras i filen **nl6/conf/serverConf.xml**. Med attributet **maxCnx** i **datakällpoolen** kan du öka tröskeln för frågor som behandlas samtidigt.

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

