---
product: campaign
title: Kampanjens Tomcat-konfiguration
description: Kampanjens Tomcat-konfiguration
feature: Installation, Instance Settings
badge-v7-prem: label="Endast lokal/hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a2126458-2ae5-47c6-ad13-925f0e067ecf
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# Konfigurera Apache Tomcat {#configuring-tomcat}



Adobe Campaign använder **inbäddad webbserver som heter Apache Tomcat** för att bearbeta HTTP/HTTPS-begäranden mellan programmet och ett externt gränssnitt (inklusive klientkonsolen, spårade URL-länkar, SOAP-anrop med flera). Det finns ofta en extern webbserver (vanligtvis IIS eller Apache) framför detta för alla externa Adobe Campaign-instanser.

Läs mer om Tomcat i Campaign och hur du hittar din Tomcat-version i [den här sidan](../../production/using/locate-tomcat-version.md).

>[!NOTE]
>
>Detta förfarande är begränsat till **lokal** distributioner.
>

## Standardport för Apache Tomcat {#default-port-for-tomcat}

När Tomcat-serverns 8080-lyssningsport redan är upptagen med ett annat program som krävs för din konfiguration, måste du ersätta 8080-porten med en kostnadsfri port (till exempel 8090). Redigera **server.xml** som sparats i **/tomcat-8/conf** i installationsmappen för Adobe Campaign.

Ändra sedan porten för JSP-reläsidorna. Om du vill göra det ändrar du **serverConf.xml** som sparats i **/conf** katalog i Adobe Campaign installationskatalog.

```
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...
```

## Mappa en mapp i Apache Tomcat {#mapping-a-folder-in-tomcat}

Om du vill definiera kundspecifika inställningar kan du skapa en **user_context.xml** i **/tomcat-8/conf** som också innehåller **context.xml** -fil.

Filen kommer att innehålla följande typ av information:

```
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

Om det behövs kan den här åtgärden reproduceras på serversidan.

## Dölj Tomcat-felrapporten {#hide-tomcat-error-report}

Av säkerhetsskäl rekommenderar vi starkt att du döljer Tomcat-felrapporten. Här är stegen.

1. Öppna **server.xml** filen som finns i **/tomcat-8/conf** katalog i Adobe Campaign installationsmapp:  `/usr/local/neolane/nl6/tomcat-8/conf`
1. Lägg till följande element längst ned efter alla befintliga kontextelement:

   ```
   <Valve className="org.apache.catalina.valves.ErrorReportValve" showReport="false" showServerInfo="false"/>
   ```

1. Starta om webbservrarna nlserver och Apache.
