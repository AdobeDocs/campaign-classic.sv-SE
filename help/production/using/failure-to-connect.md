---
solution: Campaign Classic
product: campaign
title: Det gick inte att ansluta
description: Det gick inte att ansluta
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 85fae38f864b031f069058dae79ce6753dc4bf03
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 2%

---


# Det gick inte att ansluta{#failure-to-connect}

Orsaken till ett anslutningsproblem kan vara flera och beror på olika sammanhang.

Du kan testa följande tester och om anslutningsfelet kvarstår kontaktar du **Adobe Campaign support**.



<table> 
<thead> 
<tr> 
<th>Kontroller<br /> </th> 
<th>Upplösning<br /> </th> 
</tr> 
</thead> 
<tbody> 
<tr> 
<td>Har du Internetåtkomst från datorn?</td> 
<td>Kontrollera att du kan ansluta till webbplatser på Internet (till exempel). Om du inte kan ansluta finns problemet på datorn. Kontakta systemadministratören.</td>
</tr>
<tr> 
<td>Kan du ansluta till servern som är värd för Adobe Campaign via en annan tjänst?</td> 
<td>Anslut till servern via SSH eller på något annat sätt. Om detta inte är möjligt har värdföretaget ett problem. Kontakta systemadministratören.</td>
</tr>
<tr> 
<td>svarar webbservern?</td> 
<td>Anslut till Adobe Campaign server access URL med en webbläsare: <b>http(s):// &lt;urlserver&gt;</b>. Om den inte svarar stoppas webbservern på datorn. Kontakta systemadministratören för värdföretaget för att starta om tjänsten.</td>
</tr>
<tr> 
<td>Har Adobe Campaign integrerats korrekt?</td> 
<td>Logga in på: <b>http(s)://&lt;urlserver&gt;/r/test</b> -URL. Servern ska returnera följande typ av meddelande: &lt;redir status='OK' date='YYY/MM/DD HH:MM:SS' build='XXXX' host='&lt;hostname&gt;' localHost='&lt;server&gt;'/&gt;Om du inte får detta resultat bör du kontrollera i webbserverkonfigurationen att integreringen har beaktats.</td>
</tr>
<tr> 
<td>Anslut till följande URL: <b>http(s)://&lt;URLSERVER&gt;/nl/jsp/logon.jsp</b></td>
<td>Om du får ett Tomcat Java-fel kontrollerar du om JAVA-integreringen är korrekt. Den är integrerad i filen [sökväg för programmet]/nl6/customer.sh</td>
</tr>
<tr> 
<td>Anslut till följande URL: <b>http(s)://&lt;URLSERVER&gt;/nl/jsp/logon.jsp</b></td>
<td>Om du får en tom sida kontrollerar du om Adobe Campaign webbmodul har startats. Kommandot nlserver pdump ska returnera Application Server för Adobe Campaign Classic (7.X YY.R build XXX@SHA1) av DD/MM/YYYY. Om inte startar du om modulen med kommandot nlserver som startar webben</td>
</tr>
<tr>
<td>Kontrollera den allmänna konfigurationen för säkerhetszonerna.</td>
<td>Mer information om hur du konfigurerar säkerhetszoner finns i <a href="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/additional-configurations/configuring-campaign-server.html?lang=en#configuring-campaign-server"/>det här avsnittet.</a></td>
</tr>
<tr>
<td>Kommandot nlserver pdump returnerar <b>Inga uppgifter</b></td>
<td>Du måste starta om hela Adobe Campaign-programmet. Använd följande kommando för att göra detta: <b>nlserver watchdog -svc -noconsole</b></td>
</tr>
</tbody> 
</table>
