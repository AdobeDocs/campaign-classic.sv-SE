---
product: campaign
title: Personalisering och sekretess
description: Lär dig de effektivaste strategierna för säkerhet när det gäller sekretess och personalisering
feature: Installation, Privacy, Privacy Tools, URL Personalization
exl-id: 0a3473bf-0528-486d-a799-8db86fece522
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 1%

---

# Personalisering och sekretess {#privacy}

## URL-anpassning {#url-personalization}

När du lägger till anpassade länkar till ditt innehåll bör du alltid undvika att ha en personalisering i värdnamnsdelen av webbadressen för att undvika eventuella säkerhetsbrister. Följande exempel får aldrig användas i alla URL-attribut &lt;`a href="">` eller `<img src="">`:

* `<%= url >`
* `https://<%= url >`
* `https://<%= domain >/path`
* `https://<%= sub-domain >.domain.tld/path`
* `https://sub.domain<%= main domain %>/path`

### Rekommendation

Om du vill validera och se till att du inte använder ovanstående kör du en fråga i URL-spårningstabellen via [Kampanjgenerisk frågeredigerare](../../platform/using/steps-to-create-a-query.md) eller skapa ett arbetsflöde med filtervillkor i [frågeaktivitet](../../workflow/using/query.md).

Exempel:

1. Skapa ett arbetsflöde och lägga till en **Fråga** aktivitet. [Läs mer](../../workflow/using/query.md).

1. Öppna **Fråga** aktivitet och skapa ett filter på `nmsTrackingUrl` tabellen enligt följande:

   `source URL starts with http://<% or source URL starts with https://<%`

1. Kör arbetsflödet och kontrollera om det finns några resultat.

1. I så fall öppnar du utdataövergången för att visa en lista med URL-adresser.

   ![](assets/privacy-query-dynamic-url.png)


### URL-signatur

För att förbättra säkerheten har en signaturmekanism införts för att spåra länkar i e-postmeddelanden. Den är tillgänglig från och med byggena 19.1.4 (9032@3a9dc9c) och 20.2. Den här funktionen är aktiverad som standard.

>[!NOTE]
>
>När användaren klickar på en felformaterad signerad URL returneras följande fel: `Requested URL '…' was not found.`

Dessutom kan du använda en förbättring för att inaktivera URL:er som genererats i tidigare versioner. Den här funktionen är inaktiverad som standard. Du kan kontakta [Kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) för att aktivera den här funktionen.

Om du kör i version 19.1.4 kan du få problem med push-meddelandeleveranser med hjälp av spårningslänkar eller leveranser med ankartaggar. I så fall rekommenderar vi att du inaktiverar URL-signatur.

Som kampanjvärd, hanterad Cloud Service eller hybrid-kund måste ni kontakta [Kundtjänst](https://helpx.adobe.com/se/enterprise/using/support-for-experience-cloud.html) för att inaktivera URL-signatur.

Om du kör Campaign i en hybridarkitektur måste du se till att den värdbaserade mellankällinstansen har uppgraderats enligt följande innan du aktiverar URL-signatur:

* Först den lokala marknadsinstansen
* Uppgradera sedan till samma version som den lokala marknadsinstansen eller till en något högre version

I annat fall kan följande problem uppstå:

* Innan mellankällinstansen uppgraderas skickas URL:er utan signatur via den här instansen.
* När mellankällinstansen har uppgraderats och URL-signatur har aktiverats för båda instanserna, avvisas de URL:er som tidigare har skickats utan signatur. Orsaken är att en signatur begärs av de spårningsfiler som har tillhandahållits av marknadsinstansen.

Om du vill inaktivera URL:er som har skapats i tidigare versioner följer du de här stegen på alla Campaign-servrar samtidigt:

1. I serverkonfigurationsfilen (`serverConf.xml`), ändra **blockRedirectForUnsignedTrackingLink** alternativ till **true**.
1. Starta om `nlserver` service.
1. På `tracking` server, starta om `web` server (apache2 på Debian, httpd on CentOS/RedHat, IIS on Windows).

Om du vill aktivera URL-signering följer du de här stegen på alla Campaign-servrar samtidigt:

1. I serverkonfigurationsfilen (`serverConf.xml`), ändra **signEmailLinks** till **true**.
1. Starta om **nlserver** service.
1. På `tracking` server, starta om `web` server (apache2 på Debian, httpd on CentOS/RedHat, IIS on Windows).

## Databegränsning

Du måste se till att de krypterade lösenorden inte är tillgängliga för en autentiserad användare med låg behörighet. Det gör du genom att begränsa åtkomsten till endast lösenordsfält eller till hela entiteten (behöver ett build >= 8770).

Med den här begränsningen kan du ta bort lösenordsfält men låta det externa kontot vara tillgängligt från gränssnittet för alla användare. [Läs mer](../../configuration/using/restricting-pii-view.md).

Gör så här:

1. Gå till **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]** mapp för Campaign Explorer.

1. Skapa ett dataschema som **[!UICONTROL Extension of a schema]**.

   ![](assets/privacy-data-restriction.png)

1. Välj **[!UICONTROL External Account]** (extAccount).

1. I den sista guideskärmen redigerar du ditt nya srcSchema för att begränsa åtkomsten till alla lösenordsfält:

   Du kan ersätta huvudelementet (`<element name="extAccount" ... >`) av:

   ```sql
   <element name="extAccount">
       <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
       <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
   
       <element name="s3Account">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="awsSecret"/>
       </element>
       <element name="wapPush">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
       </element>
       <element name="mms">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
       </element>
   </element>
   ```

   Så din utökade srcSchema kan se ut så här:

   ```sql
   <srcSchema _cs="External Accounts (cus)" created="2017-05-12 07:53:49.691Z" createdBy-id="0"
               desc="Definition of external accounts (Email, SMS...) used by the modules"
               entitySchema="xtk:srcSchema" extendedSchema="nms:extAccount" img="" label="External Accounts"
               labelSingular="External account" lastModified="2017-05-12 08:33:49.365Z"
               mappingType="sql" md5="E9BB0CD6A4375F500027C86EA854E101" modifiedBy-id="0"
               name="extAccount" namespace="cus" xtkschema="xtk:srcSchema">
       <createdBy _cs="Administrator (admin)"/>
       <modifiedBy _cs="Administrator (admin)"/>
       <element name="extAccount">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
   
           <element name="s3Account">
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="awsSecret"/>
           </element>
           <element name="wapPush">
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
           </element>
           <element name="mms">
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
           </element>
       </element>
   </srcSchema>    
   ```

   >[!NOTE]
   >
   >Du kan ersätta `$(loginId) = 0 or $(login) = 'admin'` med `hasNamedRight('admin')` för att tillåta alla användare med administratörsbehörighet att se dessa lösenord.

## Protect-sidor med PI

Vi rekommenderar starkt att kunder på plats skyddar sidor som kan innehålla personlig information (PI) som spegelsidor, webbapplikationer osv.

Målet med detta förfarande är att förhindra att dessa sidor indexeras, vilket förhindrar en potentiell säkerhetsrisk. Här är några användbara artiklar:

* [https://developers.google.com/search/reference/robots_txt](https://developers.google.com/search/reference/robots_txt)
* [https://developers.google.com/search/reference/robots_meta_tag](https://developers.google.com/search/reference/robots_meta_tag)

Följ de här stegen för att skydda sidorna:

1. Lägg till en `robots.txt` filen i webbserverns rot (Apache eller IIS). Här är filens innehåll:

   ```sql
   # Make changes for all web spiders
   User-agent:
   *Disallow: /
   ```

   Information om IIS finns i [den här sidan](https://docs.microsoft.com/en-us/iis/extensions/iis-search-engine-optimization-toolkit/managing-robotstxt-and-sitemap-files).

   För Apache kan du placera filen i **/var/www/robots.txt** (Debian).

1. Ibland lägger du till en **robots.txt** filen inte är tillräcklig vad gäller säkerhet. Om en annan webbplats till exempel innehåller en länk till sidan kan den visas i ett sökresultat.

   Förutom **robots.txt** bör du lägga till en **X-Robots-tag** header. Du kan göra det i Apache eller IIS och i **serverConf.xml** konfigurationsfil.

   Mer information finns i [den här artikeln](https://developers.google.com/search/reference/robots_meta_tag).


## Sekretessförfrågningar

Se [den här sidan](../../platform/using/privacy-management.md) om du vill ha allmän information om vad sekretesshantering är och implementeringsstegen i Adobe Campaign. Du hittar även bästa praxis och en översikt över användarprocessen och personifierna.
