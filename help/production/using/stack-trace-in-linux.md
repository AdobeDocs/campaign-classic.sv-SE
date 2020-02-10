---
title: Stackspårning i Linux
seo-title: Stackspårning i Linux
description: Stackspårning i Linux
seo-description: null
page-status-flag: never-activated
uuid: d839df47-902f-4b92-bc78-536fc4fb6c98
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 60f306ea-4593-4e56-896e-8933277ee26a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9482a99c3be164651b3428179388cb0a8a75783f

---


# Stackspårning i Linux{#stack-trace-in-linux}

En **stackspårning** representerar en spårning som finns i en **huvudtypsfil** . Den här filen genereras om ett datorfel inträffar. Den kan identifiera felets ursprung.

>[!NOTE]
>
>* En **kärnfil** heter **core.`<num>`**.
>* **gdb - GNU-felsökaren** måste vara installerad på datorn.
>



Adobe Campaign teknisk support kan be dig om den här **stackspårningen**. Hämta den genom att ange följande kommandon i Linux:

```
su - neolane
gdb nlserver <coreFile>
//You get lots of output but the stack trace (or Back trace) can be obtained with : 
(gdb) bt
// and forward all the output : 
#0 0x0836c189 in ObjectValue::SetPropertyTarget ()
#1 0x082623b3 in CXtkScriptProperty::VDeclareProperties ()
#2 0x0826a835 in CXtkScriptContext::OnGetProperty ()
#3 0x08370b3d in JavaScriptGetProperty ()
#4 0x557b8aa7 in js_Interpret () from /usr/local/neolane/nl6/lib/libmozjs.so
#5 0x557afb97 in js_Execute () from /usr/local/neolane/nl6/lib/libmozjs.so
#6 0x5578921f in JS_ExecuteScript () from /usr/local/neolane/nl6/lib/libmozjs.so
#7 0x08370468 in JavaScriptSource::Evaluate ()
#8 0x0848fa03 in JSTDeliveryContext::ProcessScript ()
#9 0x0848fcb6 in JSTDeliveryContext::ProcessTemplate ()
#10 0x08460d2b in CDeliveryToolbox::CreateMailMessage ()
#11 0x080d51fe in CMtaQueue::PrepareMessages ()
#12 0x080d2b07 in CMtaQueue::Prepare ()
#13 0x080dca38 in CMtaChild::OnRun ()
#14 0x0814792c in ThreadStartRoutine ()
#15 0x55575b63 in start_thread () from /lib/tls/libpthread.so.0
#16 0x5565918a in clone () from /lib/tls/libc.so.6
```

Den tekniska supporten för Adobe Campaign kan be dig köra det här kommandot med en specifik körbar fil (som ska tillhandahållas av oss).

I det här fallet kör du bara följande kommando genom att ersätta **nlserver** med den körbara filen från Adobe Campaign:

```
gdb nlserver <coreFile>
```

Till exempel:

```
gdb nlserver.1823 <coreFile>
```

