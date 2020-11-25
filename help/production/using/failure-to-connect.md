---
solution: Campaign Classic
product: campaign
title: Det gick inte att ansluta
description: Det gick inte att ansluta
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: eb7e1c98f69ba20ef4222bfefea74fdaf6072397
workflow-type: tm+mt
source-wordcount: '349'
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
   <td>Logga in på: <b>http(s)://&lt;urlserver&gt;/r/test</b> -URL. Servern ska returnera följande typ av meddelande:

    &lt;pre>
    &lt;redir status=&#39;OK&#39; date=&#39;YYY/MM/DD HH:MM:SS&#39; build=&#39;XXXX&#39; host=&#39;&lt;hostname>&#39; localHost=&#39;&lt;server>&#39;/>
    &lt;/pre>
    
    Om du inte får detta resultat bör du kontrollera i webbserverkonfigurationen att integreringen har beaktats.&lt;/td>
</tr>
  <tr> 
   <td>Har Adobe Campaign webbmodul startats?</td> 
   <td>
   Anslut till följande URL: <b>http(s)://&gt;URLSERVER&lt;/nl/jsp/logon.jsp</b>* Om du får ett Tomcat Java-fel:

    Är JAVA-integreringen korrekt genomförd? Adobe Campaign kräver SUN JDK.
    
    Den är integrerad i filen [sökväg till program]/nl6/customer.sh
    
    * Om du får en tom sida:
    
    Har Adobe Campaign webbmodul startats? Du bör hämta:
    
    &lt;pre>
    nlserver
    pdumpHH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
    [...]
    web@default (27515) - 55,2 Mb
    [...]
    &lt;/pre>
    
    * Om inte, starta om den med följande kommando:
    
    &lt;pre>
    
    
    nlserver start web¥&lt;/pre>&lt;/td>
</tr>
  <tr>
  	<td>Kontrollera den allmänna konfigurationen för säkerhetszonerna.</td>
  	<td>Mer information om hur du konfigurerar säkerhetszoner finns i [det här avsnittet](../../installation/using/configuring-campaign-server.md#defining-security-zone)</td>
  </tr>
 </tbody> 
</table>
