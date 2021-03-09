---
solution: Campaign Classic
product: campaign
title: Serverkonfiguration
description: Läs mer om de effektivaste strategierna för serverkonfiguration.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: f03554302c77a39a3ad68d47417ed930f43302b7
workflow-type: tm+mt
source-wordcount: '1186'
ht-degree: 3%

---


# Serverkonfiguration {#server-configuration}

## Konfigurera säkerhetszoner

>[!IMPORTANT]
>
>Från och med version 8977 är användargränssnittet för säkerhetszoner inte längre tillgängligt.
>
>* Om du är värd för AWS måste du lägga till IP till tillåtelselista på Kontrollpanelen. Se den [särskilda dokumentationen](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html) för mer information.
>* Om du inte är värd för AWS kan du kontakta Adobe supportteam för att lägga till IP i tillåtelselista.

>
>
Följ stegen i [det här avsnittet](https://experienceleague.adobe.com/docs/control-panel/using/faq.html) för att kontrollera om instanser har AWS som värd.

Mer information om hur du använder användargränssnittet för självbetjäning för säkerhetszoner för att hantera poster i konfigurationen för VPN-säkerhetszon finns i [den här tekniken](https://helpx.adobe.com/se/campaign/kb/configuring-security-zones-self-service.html).

* Kontrollera att din omvända proxy inte tillåts i subNetwork. Om så är fallet kommer **all**-trafik att identifieras från den här lokala IP-adressen, så den kommer att betraktas som tillförlitlig.

* Minimera användningen av sessionTokenOnly=&quot;true&quot;:

   * Varning: Om det här attributet är true kan operatorn exponeras för en **CRSF-attack**.
   * Dessutom har cookie sessionToken inte angetts med flaggan httpOnly, vilket innebär att viss javascript-kod på klientsidan kan läsa den.
   * Message Center i flera körningsceller behöver sessionTokenOnly: skapa en ny säkerhetszon med sessionTokenOnly inställd på &quot;true&quot; och lägg till **endast de IP-adresser som behövs** i den här zonen.

* När det är möjligt anger du att alla allowHTTP, showErrors ska vara false (inte för localhost) och markerar dem.

   * allowHTTP = &quot;false&quot;: tvingar operatorer att använda HTTPS
   * showErrors = &quot;false&quot;: Döljer tekniska fel (inklusive SQL-fel). Det förhindrar att alltför mycket information visas, men minskar marknadsförarens förmåga att åtgärda fel (utan att be om mer information från en administratör)

* Ange bara allowDebug till true för IP-adresser som används av marknadsföringsanvändare/administratörer som behöver skapa (faktiskt förhandsgranska) undersökningar, webApps och rapporter. Med den här flaggan kan dessa IP-adresser visa reläregler och felsöka dem.

* Ange aldrig allowEmptyPassword, allowUserPassword, allowSQLInjection till true. Attributen är bara här för att möjliggöra en smidig migrering från v5 och v6.0:

   * **Operatorer för** allowEmptyPassword har ett tomt lösenord. Om så är fallet ska du meddela alla operatorer att de måste ange ett lösenord med en tidsgräns. När den här tidsgränsen har passerats ändrar du attributet till false.

   * **Operatorer** allowUserPasswordlets skickar sina inloggningsuppgifter som parametrar (så att de loggas av apache/IIS/proxy). Den här funktionen har använts tidigare för att förenkla API-användningen. Du kan kontrollera i din cookbook (eller i specifikationen) om några tredjepartsprogram använder det här. I så fall måste du meddela dem att de ska ändra hur de använder vårt API och så snart som möjligt ta bort den här funktionen.

   * **Med** allowSQLInjection kan användaren utföra SQL-injektioner med en gammal syntax. Utför så snart som möjligt de korrigeringar som beskrivs i [den här sidan](../../migration/using/general-configurations.md) för att kunna ställa in attributet på false. Du kan använda /nl/jsp/ping.jsp?zone=true för att kontrollera säkerhetszonskonfigurationen. På den här sidan visas den aktiva statusen för säkerhetsåtgärder (beräknade med dessa säkerhetsflaggor) för den aktuella IP-adressen.

* HttpOnly cookie/useSecurityToken: referera till flaggan **sessionTokenOnly**.

* Minimera IP-adresser som läggs till i tillåtelselista: I säkerhetszoner har vi lagt till de tre intervallen för privata nätverk. Det är osannolikt att du kommer att använda alla dessa IP-adresser. Så behåll bara de du behöver.

* Uppdatera operatorn webApp/internal så att den bara är tillgänglig i localhost.

## Filöverföringsskydd

Kontrollera med de operativa användarna vilken typ av filer de överför till servern med hjälp av klientens/webbgränssnittet. Som en påminnelse kan affärsbehoven vara:

* bilder (jpg, gif, png, ...)
* innehåll (zip, html, css, ...)
* marknadsföringsmaterial (doc, xls, pdf, psd, tiff, ...)
* e-postbilaga (doc, pdf, ...)
* ETL (txt, csv, tab, ...)
* osv.

Lägg till alla i serverConf/shared/datastore/@uploadAllowlist (giltigt reguljärt java-uttryck). Läs mer i [den här sidan](../../installation/using/configuring-campaign-server.md#limiting-uploadable-files).

Adobe Campaign begränsar inte filstorleken. Men du kan göra det genom att konfigurera IIS/Apache. Läs mer i [det här avsnittet](../../installation/using/web-server-configuration.md).

## Relay

Mer information finns på [den här sidan](../../installation/using/configuring-campaign-server.md#dynamic-page-security-and-relays).

Som standard vidarebefordras alla dynamiska sidor automatiskt till den lokala Tomcat-servern på den dator vars webbmodul har startats. Du kan välja att inte vidarebefordra vissa av dem. Om du inte använder vissa Adobe Campaign-moduler (till exempel webbprogram, interaktion, vissa jsp) kan du ta bort dem från reläreglerna.

Från och med nu har vi tvingat fram möjligheten att visa slutanvändarresurser med http (httpAllowed=&quot;true&quot;). Eftersom dessa sidor kan visa vissa PII-sidor (som e-postinnehåll, adress), inlösenkupong och erbjudande, bör du tvinga HTTPS igen på dessa sökvägar.

Om du använder olika värdnamn (en offentlig och en för operatorer) kan du även förhindra att vissa resurser som behövs av operatorer skickas vidare över det offentliga DNS-namnet.

## Skydd för utgående anslutningar

Standardlistan med URL:er som kan anropas av JavaScript-koder (arbetsflöden osv.) är begränsad. Om du vill tillåta en ny URL måste administratören referera till den i filen [serverConf.xml](../../installation/using/the-server-configuration-file.md).

Det finns tre lägen för anslutningsskydd:

* **Blockering** : Alla URL:er som inte tillhör tillåtelselista blockeras, med ett felmeddelande. Det här är standardläget efter en efteruppgradering.
* **Tillstånd** : Alla URL:er som inte tillhör tillåtelselista tillåts.
* **Varning** : alla URL:er som inte finns på tillåtelselista tillåts, men JS-tolken genererar en varning så att administratören kan samla in dem. I det här läget läggs JST-310027-varningsmeddelanden till.

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

Nya klienter använder blockeringsläget. Om de vill tillåta en ny URL måste de kontakta sin administratör för att lägga till den i tillåtelselista.

Befintliga kunder som kommer från en migrering kan använda varningsläget en stund. Samtidigt måste de analysera den utgående trafiken innan de godkänner URL:er.

## Kommandobegränsning (på serversidan)

Flera kommandon är svartlistade och kan inte köras med funktionen execCommand. En extra säkerhetsfunktion tillhandahålls av en dedikerad Unix-användare för att köra externa kommandon. För värdbaserade installationer tillämpas den här begränsningen automatiskt. För lokala installationer kan du konfigurera begränsningen manuellt genom att följa instruktionerna från [den här sidan](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands). Dessutom är arbetsflödesaktiviteterna **[!UICONTROL Script]** och **[!UICONTROL External task]** inte tillgängliga (nyligen installerade instanser).

## Andra konfigurationer

Du kan lägga till extra HTTP-rubriker för alla sidor (mer information finns i [den här sidan](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands)):

* Du kan lägga till ytterligare rubriker som HSTS, X-FRAME-OPTIONS, CSP...
* Du måste testa dem i en testmiljö innan du använder dem i produktionen.

   >[!IMPORTANT]
   >
   >Adobe Campaign kan brytas genom att vissa sidhuvuden läggs till.

Med Adobe Campaign kan du ange ett vanligt lösenord i `<dbcnx .../>`-elementet. Använd inte den här funktionen.

Som standard fäster inte Adobe Campaign en session vid en viss IP-adress, men du kan aktivera den för att förhindra att sessionen blir stulen. I filen [serverConf.xml](../../installation/using/the-server-configuration-file.md) anger du attributet checkIPConsistent till **true** i noden `<authentication>`.

Som standard använder inte Adobe Campaign MTA en skyddad anslutning för att skicka innehåll till SMTP-servern. Du måste aktivera den här funktionen (kan minska leveranshastigheten). Det gör du genom att ange enableTLS till tr**ue i noden `<smtp ...>`.

Du kan minska livstiden för en session i autentiseringsnoden (attributet sessionTimeOutSec).
