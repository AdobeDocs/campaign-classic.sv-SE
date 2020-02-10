---
title: Loggprecision
seo-title: Loggprecision
description: Loggprecision
seo-description: null
page-status-flag: never-activated
uuid: 8396bc4f-2954-40bb-b511-61802e60e123
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: c6c39b7d-7bbd-4789-b1ea-b938153e9679
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 779d9162b7296339a796512838612ede1186ddcc

---


# Loggprecision{#log-precision}

Du kan använda den här processen på alla Adobe Campaign-moduler för att öka loggprecisionen.

Det handlar om att starta om processerna med en högre loggnivå.

>[!CAUTION]
>
>Den här proceduren avbryter pågående tjänster i den här modulen.

Adobe Campaign fungerar med två loggnivåer:

1. Läget **Detaljerad** är den första nivån efter standardnivån. Följande kommando aktiverar det:

   ```
   nlserver restart <MODULE_NAME> -verbose 
   ```

   Kontrollera att felet verkligen uppstod och starta sedan om processen på normalt sätt:

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

1. I **TraceFilter** -läget kan du spara så många loggar som möjligt. Den aktiveras med följande kommando:

   ```
   nlserver stop <MODULE_NAME>; nlserver <MODULE_NAME> -verbose -tracefilter:*
   ```

   >[!NOTE]
   >
   >Om du använder **spårningsfilter:*** aktiveras alla loggtyper: ncm, rdr, nms, jst, timing, wdbc, ldap, soap, xtk, xtkquery, session, xtkwriter, nätverk, pop3, inmail\
   De mest användbara loggtyperna är: **wdbc** (visar alla SQL-frågor), **soap** (visar alla SOAP-anrop), **ldap** (visar alla LDAP-frågor efter autentisering), **xtkquery** (visar listan över alla frågor).\
   Du kan använda dem var för sig (till exempel **tracefilter:soap,wdbc** ). Du kan också aktivera alla och välja att utesluta vissa andra: **-tracefilter:*,!soap**

   Kontrollera att felet verkligen uppstod och starta sedan om processen på normalt sätt:

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

>[!CAUTION]
Loggarna för dessa kommandon lagras i modulens loggfil.

Här är ett exempel som är specifikt för modulen Webb. De övriga modulerna fungerar enligt ovan.

Innan du skickar det här kommandot bör du kontrollera att inga pågående jobb påverkas.

```
nlserver pdump -who
```

Stäng sedan av och starta om modulen i **TraceFilter** -läge.

```
nlserver stop web; LD_PRELOAD=libjsig.so nlserver web -tomcat -verbose -tracefilter:* -tracefile:web_debug@default
```

Ett annat exempel:

```
nlserver stop mta@<INSTANCE_NAME>; nlserver mta -instance:<INSTANCE_NAME> -tracefilter:* -tracefile:mta_debug@<INSTANCE_NAME>
```

>[!NOTE]
I **spårfilsläget** kan du spara loggarna. I exemplen ovan sparas loggarna i **var/`<instance-name>`/mta_debug.log** och **var/default/web_debug.log** .

>[!CAUTION]
I Windows ska du inte lägga till alternativet LD_PRELOAD. Följande kommando är tillräckligt:\
nlserver web -tomcat -verbose -tracefilter:*

Kontrollera att problemet inträffar igen och starta sedan om modulen:

```
nlserver restart web -tomcat -noconsole
```

All information finns i filen **/usr/local/neolane/nl6/var/default/log/web.log**.
