---
product: campaign
title: Hitta Tomcat-versionen i Adobe Campaign
description: Lär dig hur du tar reda på den aktuella versionen av inbäddad Tomcat-webbserver som används i en instans av Adobe Campaign
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 76411b29-d300-4aaa-8d3b-d8ff74c3ce93
source-git-commit: acfe0c4139671fc3df69ff434ba307aaaaf70676
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# Sök efter Tomcat-version{#locate-tomcat-version}



Adobe Campaign använder **inbäddad webbserver som heter Apache Tomcat** för att bearbeta HTTP/HTTPS-begäranden mellan programmet och ett externt gränssnitt (inklusive klientkonsolen, spårade URL-länkar, SOAP-anrop med flera). Det finns ofta en extern webbserver (vanligtvis IIS eller Apache) framför detta för alla externa Adobe Campaign-instanser.

Följ proceduren nedan för att ta reda på exakt vilken version av Tomcat som används i en **Campaign Classic lokal instans** för att hjälpa till att felsöka problem.

## Tomcat används i Adobe Campaign

Tomcat kör på Java och kräver att JDK är installerat. Mer information finns i Java Development Kit (JDK) i [Matris för kampanjkompatibilitet](../../rn/using/compatibility-matrix.md) -avsnitt.

Tomcat som används i Adobe Campaign är en skräddarsydd inbäddad version som inte har alla funktioner i den fullständiga, allmänt tillgängliga versionen av Tomcat och som kanske inte har alla svagheter i den fullständiga versionen. Tomcat bör inte heller exponeras för externa Internet, och alla Adobe Campaign-instanser som visas bör ha en extern webbserver (IIS, Apache osv.) framför Tomcat för att skydda den.

Nya eller uppgraderade versioner av de inbäddade versionerna av Tomcat släpps endast med nya versioner av Adobe Campaign, inte som separata korrigeringsfiler utanför Adobe Campaign.

## Hitta versionen av inbäddad Tomcat

Följ stegen nedan för att hitta versionen av inbäddad Tomcat i en instans av Adobe Campaign.

>[!NOTE]
>
>Du måste ha tillgång till de filer på Adobe Campaign-servern som du behöver kontrollera. Det förfarande som beskrivs nedan gäller endast för **lokala värdmodeller**.

1. Navigera till *\tomcat-7\lib* undermapp i installationsmappen för Adobe Campaign (till exempel *C:\Program Files\ [Installation_folder]* i Windows, eller */usr/local/neolane/nl6* i Linux).

1. Kopiera filen *catalina.jar* till en extern tillfällig mapp (till exempel skrivbordet) och ändra namnet på tillägget från .jar till .zip.

1. Zippa upp den kopierade filen. Det kommer att resultera i många undermappar och filer.

1. I de uppzippade filerna/mapparna öppnar eller läser du följande fil i en textredigerare: *org/apache/catalina/util/ServerInfo.properties*. Du kan behöva lägga till ett .txt-tillägg för att det ska gå att öppna med en textredigerare.

1. När du är klar tar du bort de temporära filerna som du skapade om de finns på en serverdator.

Som ett exempel *ServerInfo.properties* filen för Adobe Campaign kommer att innehålla följande information, som anger Tomcat v8.5.X:

*server.info=Apache Tomcat/8.5.X*

*server.number=8.5.X.Y*

*server.built=MM DD YY HH:MM:SS*

När du kan fastställa den exakta versionen av Tomcat som används i en viss instans kan det hjälpa dig med felsökningen av Tomcat-relaterade problem.

>[!NOTE]
>
>Huvudversionen av den inbäddade Tomcat uppgraderas endast när huvudversionen av Adobe Campaign ändras (även om äldre versioner inte längre stöds officiellt kan informationen vara användbar eftersom vissa kunder fortfarande kör dessa versioner).

