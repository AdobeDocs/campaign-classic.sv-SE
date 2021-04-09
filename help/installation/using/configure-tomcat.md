---
solution: Campaign Classic
product: campaign
title: Kampanjens Tomcat-konfiguration
description: Kampanjens Tomcat-konfiguration
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a2126458-2ae5-47c6-ad13-925f0e067ecf
translation-type: tm+mt
source-git-commit: b0a1e0596e985998f1a1d02236f9359d0482624f
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---


# Konfigurera Apache Tomcat {#configuring-tomcat}

Adobe Campaign använder en **inbäddad webbserver som heter Apache Tomcat** för att bearbeta HTTP/HTTPS-begäranden mellan programmet och ett externt gränssnitt (inklusive Klientkonsol, spårade URL-länkar, SOAP-anrop med flera). Det finns ofta en extern webbserver (vanligtvis IIS eller Apache) framför detta för alla externa Adobe Campaign-instanser.

Läs mer om Tomcat i Campaign och hur du hittar din Tomcat-version i [den här sidan](../../production/using/locate-tomcat-version.md).

## Standardport för Apache Tomcat {#default-port-for-tomcat}

När Tomcat-serverns 8080-lyssningsport redan är upptagen med ett annat program som krävs för din konfiguration, måste du ersätta 8080-porten med en kostnadsfri port (till exempel 8090). Om du vill ändra den redigerar du filen **server.xml** som har sparats i katalogen **/tomcat-8/conf** i installationsmappen för Adobe Campaign.

Ändra sedan porten för JSP-reläsidorna. Det gör du genom att ändra filen **serverConf.xml** som har sparats i katalogen **/conf** i Adobe Campaign installationskatalog.

```
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...
```

## Mappa en mapp i Apache Tomcat {#mapping-a-folder-in-tomcat}

Om du vill definiera kundspecifika inställningar kan du skapa en **user_contexts.xml**-fil i mappen **/tomcat-8/conf**, som även innehåller filen **contexts.xml**.

Filen kommer att innehålla följande typ av information:

```
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

Om det behövs kan den här åtgärden reproduceras på serversidan.