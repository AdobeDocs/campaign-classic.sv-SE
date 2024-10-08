---
product: campaign
title: Inkommande SMS-arbetsflödesaktivitet för mid-sourcingsinfrastruktur
description: Inkommande SMS-arbetsflödesaktivitet för mid-sourcingsinfrastruktur
feature: Technote, SMS
exl-id: 756039b2-5f57-4dc5-8166-a421206b886b
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 5%

---

# Inkommande SMS-arbetsflödesaktivitet för mid-sourcingsinfrastruktur {#inbound-sms-wf}

## Begränsningar {#limitations}

* Det här användningsexemplet gäller bara för marknadsinstansen där du samlar in in InSMS-data från instansen/instanserna för Mid-sourcing.
* Implementera inte det här användningsexemplet på Mid-sourcing-instansen.
* Endast ett anpassat arbetsflöde per externt MID-källkonto.

## Implementering {#implementation}

1. Lägg till ett tillägg i schemat `nms:inSMS` på din Marketing-instans. Tillägget lägger till ett nytt attribut i `nms:inSMS`-schemat och håller reda på primärnyckeln för inSMS-posten som kommer från Mid-sourcing-instansen.

   ```xml
   <element img="nms:miniatures/mini-sms.png" label="Incoming SMS"
          labelSingular="Incoming SMS" name="inSMS">
   <dbindex name="midInSMSId" unique="false">
     <keyfield xpath="@extAccount-id"/>
     <keyfield xpath="@midInSMSId"/>
   </dbindex>
   
   <attribute label="External Mid SMS ID" name="midInSMSId" type="long"/>
   </element>
   ```

1. Om du vill använda ändringarna i scheman startar du databasuppdateringsassistenten. Den här assistenten är tillgänglig via **Verktyg** > **Avancerat** > **Uppdatera databasstrukturen**. Den kontrollerar om databasens fysiska struktur matchar dess logiska beskrivning och kör SQL-uppdateringsskripten. [Läs mer](../../configuration/using/updating-the-database-structure.md)

1. Stoppa och säkerhetskopiera arbetsflödet som innehåller aktiviteten **Inkommande SMS**.

   Säkerhetskopiera motsvarande alternativpekare med följande format: `SMS_MO_INDEX_{internal name of the workflow}_{name of the insms workflow activity}_{internal name of the external account to access the mid}`.

[Läs mer om säkerhetskopiering](../../production/using/backup.md)

1. (**VALFRITT**) Om du redan använder en Scheduler-aktivitet öppnar du arbetsflödet och konfigurerar om det enligt följande:

   1. Replikera de aktuella inställningarna från fliken **Schema** i din **inkommande SMS**-aktivitet till din externa **Schemaläggaren**-aktivitet.

   1. Inaktivera den aktuella inställningen på fliken **Schema** i aktiviteten **Inkommande SMS**.

      ![](assets/inbound_sms_1.png)

1. Uppdatera det anpassade skriptet **Inbound SMS**.

   Ersätt nedanstående block. Observera att skriptet kan variera om du tidigare har anpassat den här koden.

   ```Javascript
   var lastSynchKey = getOption('SMS_MO_INDEX_WKF1105_inSmsUS_smsmidus');
   
   var smsId = application.getNewIds(1);
   
   xtk.session.Write(<inSMS xtkschema="nms:inSMS" _operation="insert"
       id={smsId}
       origin={smsMessage.origin}
       message={smsMessage.message}
       providerId={smsMessage.messageId}/>);
   
   return 2;
   ```

   Med följande nya anpassade skript för att uppdatera inSMS-data baserat på en sammansatt nyckel, som kombinerar primärnyckeln för posten för Mid-sourcing och det externa konto-ID:t för SMS-routningen för marknadsföring.

   Följ förfrågorna nedan:

   * Ange det verkliga värdet för `<EXTERNAL_ACCOUNT_ID>`, t.ex. `var iExtAccountId=72733155`.
   * Se till att du behåller följande element i det anpassade skriptet:
      * `_operation="insertOrUpdate"`
      * `_key="@midInSMSId,@extAccount-id"`
      * `midInSMSId={smsMessage.id}`
      * `inSms.@["extAccount-id"] = iExtAccountId;{}`

   ```Javascript
   // please enter real external account ID to replace <EXTERNAL ACCOUNT ID>
   var iExtAccountId=<EXTERNAL_ACCOUNT_ID>;
   
   var inSms = <inSMS xtkschema="nms:inSMS" _operation="insertOrUpdate"
   
               _key="@midInSMSId,@extAccount-id"
               midInSMSId={smsMessage.id}
               message={smsMessage.message}
               origin={smsMessage.origin}
               providerId={smsMessage.providerId}
               alias={smsMessage.alias}
               messageDate = {smsMessage.messageDate}
               receivalDate = {smsMessage.receivalDate}
               deliveryDate = {smsMessage.deliveryDate}
               largeAccount = {smsMessage.largeAccount}
               countryCode = {smsMessage.countryCode}
               operatorCode = {smsMessage.operatorCode}
               linkedSmsId={smsMessage.linkedSmsId}
               separator = {smsMessage.separator}/>
   
   inSms.@["extAccount-id"] = iExtAccountId;
   
   xtk.session.Write(inSms);
   
   return 2;
   ```

1. Uppdatera det avancerade initieringsskriptet för inkommande SMS med följande skript.

   Skriptet återställer pekaren för primärnyckeln till 24 timmar före. Arbetsflödet kommer att försöka bearbeta om alla inSMS-data från Mid-sourcing-instansen under de senaste 24 timmarna och lägga till saknade data i Marketing-instansen.

   ```Javascript
   // please enter real external account ID to replace <EXTERNAL_ACCOUNT_ID>
   // please enter real pointer option name to replace '<POINTER_OPTION_NAME>'
   // OPTION NAME format: SMS_MO_INDEX_{internal name of the workflow}_inSms_{internal name of the external account to access the mid}
   
   var queryDef = xtk.queryDef.create(
       <queryDef operation="getIfExists" schema="nms:inSMS" lineCount="1">
       <select>
           <node expr="@midInSMSId" alias="@midInSMSId"/>
       </select>
       <where>
           <condition expr="@midInSMSId != 0"/>
           <condition expr={"@created > SubHours(GetDate(), 24)"}/>
           <condition expr={"[@extAccount-id]=<EXTERNAL_ACCOUNT_ID>"}/>
       </where>
       <orderBy>
           <node expr="@midInSMSId"/>
       </orderBy>
       </queryDef>);
   
   var res = parseInt(queryDef.ExecuteQuery().@midInSMSId.toString());
   
   if( !isNaN(res) )
   setOption('<POINTER_OPTION_NAME>', res);
   ```

   >[!WARNING]
   >
   > * Om flera SMS-routningskonton är länkade till samma instans av Mid-sourcing tillåts bara ett arbetsflöde per instans av Mid-sourcing.
   > * Du kan använda valfritt externt konto-ID. Den externa nyckelns roll är att upprätthålla dataavstämningsintegriteten i scenarier där olika MID-källservrar ingår, där SMS-ID:t för MID-källkod kan vara identiskt i andra MID-källkodsinstanser.
   > * Om det finns flera inSMS-arbetsflöden per instans av Mid-sourcing kan dataduplicering ske eftersom SMS-ID:t från mellanleverantörer förblir konstant medan ID:n för det externa kontot varierar.

1. Spara och starta om arbetsflödet.
