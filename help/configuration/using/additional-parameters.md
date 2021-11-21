---
product: campaign
title: Ytterligare parametrar för webbspårning
description: Läs mer om parametrar för webbspårning
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
exl-id: d14d94fd-b078-4893-be84-31d37a1d50f5
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 1%

---

# Ytterligare parametrar{#additional-parameters}

![](../../assets/v7-only.svg)

## Definition av parametrar {#definition-of-parameters}

På din Adobe Campaign-plattform finns två parametrar av typen TRANSACTION som standard för webbspårning:

* **amount**: represents the amount of a transaction,
* **artikel**: representerar antalet artiklar i en transaktion.

Dessa parametrar definieras i **nms:webTrackingLog** och är några av de indikatorer som visas i rapporteringen.

To define additional parameters, you must extend this schema.

**Exempel**:

```
<srcSchema extendedSchema="nms:webTrackingLog" label="Web Tracking"
           mappingType="sql" name="webTrackingLog" 
           namespace="cus" xtkschema="xtk:srcSchema">

  <element name="webTrackingLog">
    <attribute desc="Payment method" label="Payment method" length="10" name="mode" type="string"/>
    <attribute desc="Offer code" label="Offer code" length="5" name="code" type="string"/>
  </element>
</srcSchema>
```

You can display the values of these parameters by configuring the tracking log list (of a delivery or recipient).

## Redirection server configuration {#redirection-server-configuration}

I serverkonfigurationen kan du definiera det maximala antal tecken som ska beaktas för spårningsparametrarna för webben.

>[!IMPORTANT]
>
>Om du ökar det maximala antalet tecken som ska beaktas kan det påverka plattformens webbspårningsprestanda.

Om du vill göra det ändrar du **webTrackingParamSize** attributet för **`<trackinglogd>`** -elementet i **serverConf.xml** -fil. Den här filen sparas i **conf** underkatalogen till Adobe Campaign installationskatalog.

**Exempel**:

Standardvärdet är 64 tecken. Med det här värdet kan du ta hänsyn till **belopp** och **artikel** (&quot;amount=xxxxxx&amp;article=xxxxxx&quot;) standardparametrar.

Genom att ta hänsyn till båda parametrarna (storlek på namn + storlek på värde) som anges i exemplet ovan kan du ändra konfigurationen så att den tar 100 tecken (&quot;amount=xxxxxx&amp;article=xxxxxxxx&amp;mode=xxxxxxxxxx&amp;code=xxxxx&quot;).

```
<trackinglogd args="" autoStart="false" initScript="" maxCreateFileRetry="5" maxLogsSizeOnDiskMb="500"
maxProcessMemoryAlertMb="1800" maxProcessMemoryWarningMb="1600" maxSharedLogs="25000"
processRestartTime="06:00:00" purgeLogsPeriod="50000" runLevel="10"
webTrackingParamSize="64"/>
```

When the configuration has been modified, you must:

* Stop the web server that hosts the redirection module (Apache, IIS, etc.),
* Stoppa Adobe Campaign-servern: **net stop nlserver6** i Windows, **/etc/init.d/nlserver6 stop** i Linux,

   >[!NOTE]
   >
   >Från och med 20.1 rekommenderar vi att du använder följande kommando i stället (för Linux): **systemctl stop nlserver**

* In Linux, delete the shared memory segments using the **ipcrm** command,
* Starta om Adobe Campaign-servern: **net start nlserver6** i Windows, **/etc/init.d/nlserver6 - start** i Linux,

   >[!NOTE]
   >
   >Från och med 20.1 rekommenderar vi att du använder följande kommando i stället (för Linux): **systemctl start nlserver**

* Starta om webbservern.

**Exempel**: med hänsyn till konfigurationen under Linux.

```
adobe@selma:~$ systemctl stop nlserver
adobe@selma:~$ systemctl stop apache2
adobe@selma:~$ ipcs shm

------ Shared Memory Segments --------
key        shmid      owner      perms      bytes      nattch     status      
0x52020679 2097153    adobe   666        93608      8                       

------ Semaphore Arrays --------
key        semid      owner      perms      nsems     
0x52020678 4227081    adobe   666        1         

------ Message Queues --------
key        msqid      owner      perms      used-bytes   messages    

adobe@selma:~$ ipcrm shm 2097153                             
1 resource(s) deleted
adobe@selma:~$ systemctl start nlserver
adobe@selma:~$ systemctl start apache2
```

>[!NOTE]
>
>For Linux, if you increase the size of the **webTrackingParamSize** or **maxSharedLogs** parameters, you may need to increase the size of the shared memory (SHM).
