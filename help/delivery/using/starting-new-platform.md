---
title: Starta en ny plattform med Adobe Campaign Classic
description: Läs mer om hur du hanterar slutprodukter när du startar en ny plattform med Adobe Campaign Classic.
page-status-flag: never-activated
uuid: 2681042b-3018-42ae-b252-2367b56616bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 6a394eeb-fbe1-4712-bb13-db5d7965fb73
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 68756f920fbc8658cff552615adbf023b4c5e3aa

---


# Starta en ny plattform {#starting-new-platform}

Det är viktigt att du behåller domänens och IP-adressens anseende. Nedan finns några tips om hur du konfigurerar en ny plattform.

Att börja skicka e-postmeddelanden på en ny plattform är ett känsligt steg eftersom plattformen inte har någon användarhistorik och inget anseende (när de avsändande IP-adresserna aldrig har använts för detta ändamål). Internetleverantörer misstänker naturligtvis IP-adresser som aldrig har använts för att skicka e-post och som plötsligt börjar skicka stora volymer e-posttrafik. Det innebär att skräppost i allmänhet använder&quot;okända&quot; IP-adresser (det vill säga adresser som aldrig har svartlistats) för att skicka så många meddelanden som möjligt innan de upptäcks.

Du kan inte förvänta dig att uppnå driftshastighet i form av utdata i början av produktionsfasen. Du bör inte heller försöka skicka meddelanden i den här hastigheten eftersom det kan leda till att internetleverantörerna blockerar sändningsadresserna och allvarligt äventyrar resten av startfasen.

Det händer ofta att en plattform startas när en adresslista används för första gången och som kanske inte är fullständigt kvalificerad. Om du skickar till ogiltiga adresser eller till honeypoadresser kommer detta att bidra till att minska plattformens anseende. Om du har en lista med ogiltiga adresser är det bäst att importera den till karantäntabellen (**[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**) innan du skickar den för första gången. Om du ändå vill ange de ogiltiga adresserna är det bäst att göra detta när plattformens rykte väl har etablerats och bitvis för att &quot;tona ned&quot; användningen av dåliga adresser över tiden.

Sammanfatta de principer som skall följas vid inledandet:

* Importerar ogiltiga adresser till karantäntabellen (om du har den här informationen)
* Begränsning av genomströmningshastigheten (teknisk inställning: begränsa antalet matriser)
* Progressiv ökning av skickade volymer: Använd inte hela databasen som mål från början, utan lägg till en extra del av listan varje gång du skickar. detta bör göra att du kan öka volymen i varje steg och samtidigt minska den totala hastigheten för ogiltiga adresser
* Skicka regelbundet: I viss utsträckning är det bättre att skicka små tagningar regelbundet än stora kampanjer sporadiskt
* Var noga med leveransrapporterna: högfelsindikatorer kan innebära att en teknisk inställning är dåligt konfigurerad.