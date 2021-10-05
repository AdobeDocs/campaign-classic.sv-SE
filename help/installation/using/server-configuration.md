---
product: campaign
title: Säkerhetskonfiguration för server
description: Läs mer om de effektivaste strategierna för serverkonfiguration
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: e1aff73a-54fb-444e-b183-df11c9b3df31
source-git-commit: 4661a65c83f3b9b7da9ea902f387155c5933e59f
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 3%

---

# Serverns säkerhetsinställningar {#server-configuration}

![](../../assets/v7-only.svg)

## Filöverföringsskydd

Kontrollera med de operativa användarna vilken typ av filer de överför till servern med Campaign Client Console eller webbgränssnittet. Som en påminnelse kan affärsbehoven vara:

* bilder (jpg, gif, png, ...)
* innehåll (zip, html, css, ...)
* marknadsföringsmaterial (doc, xls, pdf, psd, tiff, ...)
* e-postbilaga (doc, pdf, ...)
* ETL (txt, csv, tab, ...)
* osv.

Lägg till alla i serverConf/shared/datastore/@uploadAllowlist (giltigt reguljärt java-uttryck). Läs mer i [den här sidan](../../installation/using/file-res-management.md).

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

Befintliga kunder som kommer från en migrering kan använda varningsläget en stund. Under tiden måste de analysera utgående trafik innan de godkänner URL:er.

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

Som standard använder inte Adobe Campaign MTA en skyddad anslutning för att skicka innehåll till SMTP-servern. Du måste aktivera den här funktionen (kan minska leveranshastigheten). Om du vill göra det anger du **enableTLS** till **true** i noden `<smtp ...>`.

Du kan minska livstiden för en session i autentiseringsnoden (attributet sessionTimeOutSec).
