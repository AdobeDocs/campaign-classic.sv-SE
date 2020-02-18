---
title: Spårningsläge för webben
seo-title: Spårningsläge för webben
description: Spårningsläge för webben
seo-description: null
page-status-flag: never-activated
uuid: 51b889d3-28f8-480a-a614-10c8eb3128ac
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: efeef54b-925d-4654-8601-52a73539b41f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# Spårningsläge för webben{#web-tracking-mode}

Med Adobe Campaign kan du välja ett webbspårningsläge som definierar hur spårningsloggar bearbetas i programmet.

Det finns tre tillgängliga spårningslägen: **&quot;Sessionsspårning&quot;**,**&quot;Permanent spårning&quot;** och **&quot;anonym spårning&quot;**.

![](assets/s_ncs_install_deployment_wiz_tracking_mode.png)

Varje läge har specifika egenskaper. Det &quot;permanenta&quot; läget för webbspårning omfattar egenskaperna för webbspårningsläget &quot;session&quot;, medan läget &quot;anonym&quot; omfattar egenskaperna för lägena &quot;permanent&quot; och &quot;session&quot;.

>[!IMPORTANT]
>
>Läget för anonym webbspårning är aktiverat som standard om paketet Leads är aktiverat. I alla andra fall är webbspårningsläget &quot;session&quot; aktiverat som standard.
>
>Du kan när som helst ändra standardläget i instansdistributionsguiden.

Observera, att om du använder **permanent webb** - eller **anonym** spårningsläge måste du lägga till ett index i kolumnen&quot;sourceID&quot; (uuid230) i spårningstabellerna (trackingLogXXX):

1. Identifiera spårningstabellerna som berörs av permanent spårning.
1. Utöka de scheman som matchar de här tabellerna genom att lägga till följande rader:

```
<dbindex name="sourceId">
 <keyfield xpath="@sourceId"/>
</dbindex>
```

**Det finns två olika lägen för permanent** och **anonym** webbspårning: **Tvingad leverans** och **senaste leverans**.

Med alternativet **Tvingad leverans** kan du ange identifieraren för leveransen (@jobid) under spårning.

Med alternativet **Senaste leverans** kan du länka den aktuella spårningsloggen till den senast spårade leveransen.

**Egenskaper för sessionswebbspårning:**

I det här läget skapas en spårningslogg för personer med en sessionscookie. Detta är personer som klickade på en URL i ett e-postmeddelande som skickats av Adobe Campaign, vilket gör att vi kan spåra följande information:

* Leverans-ID
* Kontakt-ID
* leveranslogg
* permanent cookie (uuid230)
* Spårnings-URL
* datum för spårningsloggen

I det här webbspårningsläget skapas ingen spårningslogg i programmet om en del av informationen saknas.

Det här läget är ekonomiskt när det gäller volym (begränsat antal poster i registret trackingLog) och beräkning (ingen avstämning).

**Egenskaper för permanent webbspårningsläge:**

I det här webbspårningsläget kan du skapa en spårningslogg baserat på förekomsten av den permanenta uid230-cookien. Om en besökare stänger sin session använder Adobe Campaign den permanenta cookien för att återställa information om dem från tidigare spårningsloggar. Adobe Campaign infogar en spårningslogg igen om uuid230 för den aktuella sessionen har samma värde som en uuid230 som redan lagrats i spårningstabellen.

Det innebär att besökaren måste ha identifierats tidigare i Adobe Campaign (via en leverans) för att kunna avstämma mot uid230-värden.

Som standard utförs sökningar i tidigare spårningsloggar i tabellen&quot;trackingLog&quot;. Om Leads-paketet är aktiverat söker Adobe Campaign igenom tabellen&quot;inkommandeLead&quot; för att hitta tidigare loggposter för spårning innan du söker i tabellen&quot;trackingLog&quot;.

Det här läget är kostsamt när det gäller beräkning vid loggavstämning.

**Egenskaper för det anonyma webbspårningsläget:**

I det här webbspårningsläget kan du hämta en spårningslogg som är länkad till anonym surfning i Adobe Campaign. En spårningslogg skapas automatiskt för varje klick på en spårad URL. Den här loggen har bara värdet uuid230. Under en marknadsföringskampanj skapas en spårningslogg automatiskt med all identifieringsinformation (se sessionsspårning). Adobe Campaign söker automatiskt i tidigare loggar efter ett uuid230-värde som är lika med värdet från spårningsloggen för den här marknadsföringskampanjen. Om identiska värden hittas, anges alla tidigare spårningsloggar tillsammans med all information från spårningsloggen för marknadsföringskampanjer.

Det här läget är det mest kostsamma när det gäller beräkning och volym.

>[!NOTE]
>
>Om paketet är installerat måste du göra samma sak med aktivitetstabellen ( **[!UICONTROL Leads]** crm:inkommandeLead ****)

I följande schema sammanfattas funktionerna för alla tre webbspårningslägena:

![](assets/s_ncs_install_deployment_wiz_tracking_schema_mode.png)

**Exempel på permanent webbspårning baserat på senaste leverans:**

Florence får en leverans, öppnar e-postmeddelandet, klickar på länken, bläddrar på webbplatsen för detaljhandeln men gör inga inköp. Dagen därpå kommer Florence tillbaka till butiken, letar upp och gör ett köp. Eftersom permanent webbspårning (senaste leverans) är aktiverat kommer alla loggar för hennes andra besök att länkas till leveransen som skickades till henne föregående dag.
