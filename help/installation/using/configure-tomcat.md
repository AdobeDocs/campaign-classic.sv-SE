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
source-git-commit: fd4a815bca23b94590012c4883cfaa9c29b6f118
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# Konfigurera Apache Tomcat {#configuring-tomcat}

Adobe Campaign använder en **inbäddad webbserver som heter Apache Tomcat** för att bearbeta HTTP/HTTPS-begäranden mellan programmet och ett externt gränssnitt (inklusive Klientkonsol, spårade URL-länkar, SOAP anrop och andra). Det finns ofta en extern webbserver (vanligtvis IIS eller Apache) framför detta för alla externa Adobe Campaign-instanser.

Läs mer om Tomcat i Campaign och hur du hittar din Tomcat-version på [den här sidan](../../production/using/locate-tomcat-version.md).

>[!AVAILABILITY]
>
>
>* Med början från Campaign v7.4.1 är Tomcat 10.1 standardversionen.
>
>* Adobe Campaign Classic använder inte WebSocket- och HTTP2-protokoll.
>



## Standardport för Apache Tomcat {#default-port-for-tomcat}


>[!NOTE]
>
>Den här proceduren är begränsad till **lokala**-distributioner.
>

När Tomcat-serverns 8080-lyssningsport redan är upptagen med ett annat program som krävs för din konfiguration, måste du ersätta 8080-porten med en kostnadsfri port (till exempel 8090). Om du vill ändra den redigerar du filen **server.xml** som har sparats i katalogen **/tomcat-X/conf** i Adobe Campaign installationsmapp.

Ändra sedan porten för JSP-reläsidorna. Det gör du genom att ändra filen **serverConf.xml** som sparas i katalogen **/conf** i Adobe Campaign installationskatalog.

```xml
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...
```

## Mappa en mapp i Apache Tomcat {#mapping-a-folder-in-tomcat}


>[!NOTE]
>
>Den här proceduren är begränsad till **lokala**-distributioner.
>

Om du vill definiera kundspecifika inställningar kan du skapa en **user_contexts.xml** -fil i mappen **/tomcat-X/conf** , som även innehåller filen **contexts.xml** .

Filen kommer att innehålla följande typ av information:

```xml
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

Om det behövs kan den här åtgärden reproduceras på serversidan.

## Dölj Tomcat-felrapporten {#hide-tomcat-error-report}


>[!NOTE]
>
>Den här proceduren är begränsad till **lokala**-distributioner.
>
>Den här ändringen behövs inte längre när Campaign v7.4.1 startas.
>

Av säkerhetsskäl rekommenderar vi starkt att du döljer Tomcat-felrapporten. Följ de här stegen:

1. Öppna filen **server.xml** som finns i katalogen **/tomcat-X/conf** i installationsmappen för Adobe Campaign: `/usr/local/neolane/nl6/tomcat-X/conf`
1. Lägg till följande element längst ned efter alla befintliga kontextelement:

   ```xml
   <Valve className="org.apache.catalina.valves.ErrorReportValve" showReport="false" showServerInfo="false"/>
   ```

1. Starta om webbservrarna nlserver och Apache.
