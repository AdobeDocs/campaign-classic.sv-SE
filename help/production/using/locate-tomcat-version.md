---
product: campaign
title: Hitta Tomcat-versionen i Adobe Campaign
description: Lär dig hur du tar reda på den aktuella versionen av inbäddad Tomcat-webbserver som används i en instans av Adobe Campaign
feature: Monitoring
badge-v7-prem: label="Endast lokal/hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 76411b29-d300-4aaa-8d3b-d8ff74c3ce93
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---

# Sök efter Tomcat-version{#locate-tomcat-version}

Adobe Campaign använder en **inbäddad webbserver som heter Apache Tomcat** för att bearbeta HTTP/HTTPS-begäranden mellan programmet och ett externt gränssnitt (inklusive Klientkonsol, spårade URL-länkar, SOAP anrop och andra). Det finns ofta en extern webbserver (vanligtvis IIS eller Apache) framför detta för alla externa Adobe Campaign-instanser.

Följ proceduren nedan för att ta reda på den exakta versionen av Tomcat som används i en **Campaign Classic på plats** för att felsöka problem.

## Tomcat används i Adobe Campaign

Tomcat kör på Java och kräver att JDK är installerat. Mer information finns i Java Development Kit (JDK) i avsnittet [Kampanjkompatibilitetsmatris](../../rn/using/compatibility-matrix.md).

Tomcat som används i Adobe Campaign är en skräddarsydd inbäddad version som inte har alla funktioner i den fullständiga, allmänt tillgängliga versionen av Tomcat och som kanske inte har alla svagheter i den fullständiga versionen. Tomcat bör inte heller exponeras för det externa internet, och eventuella Adobe Campaign-instanser som exponeras bör ha en extern webbserver (IIS, Apache osv.) framför Tomcat för att skydda den.

Nya eller uppgraderade versioner av de inbäddade versionerna av Tomcat släpps endast med nya versioner av Adobe Campaign, inte som separata korrigeringsfiler utanför Adobe Campaign.

>[!AVAILABILITY]
>
>
>* Med början från Campaign v7.4.1 är Tomcat 10.1 standardversionen.
>
>* Adobe Campaign Classic använder inte WebSocket- och HTTP2-protokoll.
>


## Hitta versionen av inbäddad Tomcat

Följ stegen nedan för att hitta versionen av inbäddad Tomcat i en instans av Adobe Campaign.

>[!NOTE]
>
>Du måste ha tillgång till de filer på Adobe Campaign-servern som du behöver kontrollera. Den procedur som beskrivs nedan gäller endast **lokala värdmodeller**.

1. Navigera till undermappen *\tomcat-11\lib* i Adobe Campaign-installationsmappen (till exempel *C:\Program filer\ [Installation_folder]* i Windows eller */usr/local/neolane/nl6* i Linux).

1. Kopiera filen *catalina.jar* till en extern tillfällig mapp (till exempel skrivbordet) och byt namn på tillägget från .jar till .zip.

1. Zippa upp den kopierade filen. Det kommer att resultera i många undermappar och filer.

1. I de uppzippade filerna/mapparna öppnar eller läser du följande fil i en textredigerare: *org/apache/catalina/util/ServerInfo.properties*. Du kan behöva lägga till ett .txt-tillägg för att det ska gå att öppna med en textredigerare.

1. När du är klar tar du bort de temporära filerna som du skapade om de finns på en serverdator.

Filen *ServerInfo.properties* för Adobe Campaign innehåller till exempel följande information, som anger Tomcat v11.X:

*`server.info=Apache Tomcat/11.X`*

*`server.number=A.B.X.Y`*

*`server.built=MM DD YYY HH:MM:SS`*

När du kan fastställa den exakta versionen av Tomcat som används i en viss instans kan det hjälpa dig med felsökningen av Tomcat-relaterade problem.

>[!NOTE]
>
>Huvudversionen av den inbäddade Tomcat uppgraderas endast när huvudversionen av Adobe Campaign ändras (även om äldre versioner inte längre stöds officiellt kan informationen vara användbar eftersom vissa kunder fortfarande kör dessa versioner).
>

