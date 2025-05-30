---
product: campaign
title: Loggprecision
description: Loggprecision
feature: Monitoring
badge-v7-prem: label="Endast lokal/hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: c2470098-62f3-4fee-b1c5-800ed0e91f75
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 2%

---

# Loggprecision{#log-precision}



Du kan använda den här processen på alla Adobe Campaign-moduler för att öka loggprecisionen.

Det handlar om att starta om processerna med en högre loggnivå.

>[!IMPORTANT]
>
>Den här proceduren avbryter pågående tjänster i den här modulen.

Adobe Campaign kan arbeta med två loggnivåer:

1. Läget **Detaljerad** är den första nivån efter standardnivån. Följande kommando aktiverar det:

   ```
   nlserver restart <MODULE_NAME> -verbose 
   ```

   Kontrollera att felet verkligen uppstod och starta sedan om processen på normalt sätt:

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

1. Läget **TraceFilter** som gör att du kan spara så många loggar som möjligt. Den aktiveras med följande kommando:

   ```
   nlserver stop <MODULE_NAME>; nlserver <MODULE_NAME> -verbose -tracefilter:*
   ```

   >[!NOTE]
   >
   >Om du använder **tracefilter:&#42;** aktiveras alla loggtyper: ncm, rdr, nms, jst, timing, wdbc, ldap, soap, xtk, xtkquery, session, xtkwriter, network, pop3, inmail\
   >De mest användbara loggtyperna är: **wdbc** (visar alla SQL-frågor), **soap** (visar alla SOAP anrop), **ldap** (visar alla LDAP-frågor efter autentisering), **xtkquery** (visar listan över alla frågor).\
   >Du kan använda dem individuellt (**tracefilter:soap,wdbc** till exempel). Du kan också aktivera alla och välja att exkludera vissa andra: **-tracefilter: &#42;,!soap**

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

Stäng sedan av och starta om modulen i läget **TraceFilter**:

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
>nlserver web -tomcat -verbose -tracefilter:&#42;

Kontrollera att problemet inträffar igen och starta sedan om modulen:

```
nlserver restart web -tomcat -noconsole
```

All information finns i filen **/usr/local/neolane/nl6/var/default/log/web.log**.
