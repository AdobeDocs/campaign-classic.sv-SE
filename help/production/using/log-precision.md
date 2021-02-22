---
solution: Campaign Classic
product: campaign
title: Loggprecision
description: Loggprecision
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 1fdee02e98ce66ec184d8587d0838557f027cf75
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 1%

---


# Loggprecision{#log-precision}

Du kan använda den här processen på alla Adobe Campaign-moduler för att öka loggprecisionen.

Det handlar om att starta om processerna med en högre loggnivå.

>[!IMPORTANT]
>
>Den här proceduren avbryter pågående tjänster i den här modulen.

Adobe Campaign kan arbeta med två loggnivåer:

1. Läget **Fullständig** är den första nivån efter standardnivån. Följande kommando aktiverar det:

   ```
   nlserver restart <MODULE_NAME> -verbose 
   ```

   Kontrollera att felet verkligen uppstod och starta sedan om processen på normalt sätt:

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

1. Läget **TraceFilter**, som gör att du kan spara så många loggar som möjligt. Den aktiveras med följande kommando:

   ```
   nlserver stop <MODULE_NAME>; nlserver <MODULE_NAME> -verbose -tracefilter:*
   ```

   >[!NOTE]
   >
   >Om du använder **spårningsfilter:*** aktiveras alla loggtyper: ncm, rdr, nms, jst, timing, wdbc, ldap, soap, xtk, xtkquery, session, xtkwriter, nätverk, pop3, inmail\
   >De mest användbara loggtyperna är: **wdbc** (visar alla SQL-frågor), **soap** (visar alla SOAP-anrop), **ldap** (visar alla LDAP-frågor efter autentisering), **xtkquery** (visar listan över alla frågor).\
   >Du kan använda dem var för sig (**tracefilter:soap,wdbc** till exempel). Du kan också aktivera alla och välja att utesluta vissa andra: **-tracefilter:*,!soap**

   Kontrollera att felet verkligen uppstod och starta sedan om processen på normalt sätt:

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

>[!IMPORTANT]
>
>Loggarna för dessa kommandon lagras i modulens loggfil.

Här är ett exempel som är specifikt för modulen Webb. De övriga modulerna fungerar enligt ovan.

Innan du skickar det här kommandot bör du kontrollera att inga pågående jobb påverkas:

```
nlserver pdump -who
```

Stäng sedan av och starta om modulen i **TraceFilter**-läge:

```
nlserver stop web; LD_PRELOAD=libjsig.so nlserver web -tomcat -verbose -tracefilter:* -tracefile:web_debug@default
```

Ett annat exempel:

```
nlserver stop mta@<INSTANCE_NAME>; nlserver mta -instance:<INSTANCE_NAME> -tracefilter:* -tracefile:mta_debug@<INSTANCE_NAME>
```

>[!NOTE]
>
>I **spårfilsläget** kan du spara loggarna. I exemplen ovan sparas loggarna i filerna **var/`<instance-name>`/mta_debug.log** och **var/default/web_debug.log**.

>[!IMPORTANT]
>
>I Windows ska du inte lägga till alternativet LD_PRELOAD. Följande kommando är tillräckligt:\
>nlserver web -tomcat -verbose -tracefilter:*

Kontrollera att problemet inträffar igen och starta sedan om modulen:

```
nlserver restart web -tomcat -noconsole
```

All information finns i filen **/usr/local/neolane/nl6/var/default/log/web.log**.
