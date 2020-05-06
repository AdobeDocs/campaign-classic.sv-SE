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
source-git-commit: a1192bc804e752d13af869da66ba0505c077ed19
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---


# Starta en ny plattform {#starting-new-platform}

Det är viktigt att du behåller domänens och IP-adressens anseende när du skapar en ny plattform.

* Att börja skicka e-post är ett känsligt steg eftersom plattformen inte har någon historik över användning och, när de avsändande IP-adresserna aldrig har använts för detta ändamål, inget anseende.

* Internetleverantörer misstänker naturligtvis IP-adresser som aldrig har använts för att skicka e-post och som plötsligt börjar skicka stora volymer e-posttrafik. För skräppost används i allmänhet&quot;okända&quot; IP-adresser (adresser som aldrig har svartlistats) för att skicka så många meddelanden som möjligt innan de upptäcks.

* Du kan inte förvänta dig att uppnå driftshastighet i form av utdata i början av produktionsfasen. Du bör inte heller försöka skicka meddelanden i den här hastigheten eftersom det kan leda till att internetleverantörerna blockerar sändningsadresserna och allvarligt äventyrar resten av startfasen.

Nedan anges de huvudprinciper som ska följas när en ny plattform startas:

* Om du har den här informationen **importerar du ogiltiga adresser till karantäntabellen**.
Det händer ofta att en plattform startas när en adresslista används för första gången och som kanske inte är fullständigt kvalificerad. Om du skickar till ogiltiga adresser eller till honeypoadresser kommer detta att bidra till att minska plattformens anseende.

   * Om du har en lista med ogiltiga adresser är det bäst för dig att importera den till karantäntabellen (tillgänglig via **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]** menyn) innan du skickar den första gången.
   * Om du ändå vill ange de ogiltiga adresserna är det bäst att göra detta när plattformens rykte har etablerats och bitvis för att &quot;tona ned&quot; användningen av dåliga adresser över tiden.
   Mer information finns i [Optimera leveransen via karantäner](../../delivery/using/understanding-quarantine-management.md#optimizing-your-delivery-through-quarantines).
* **Begränsa genomströmningshastigheten** genom att begränsa antalet matriser. Kontakta Adobe Campaign-administratören om du vill ha mer information om hur du justerar sådana tekniska inställningar.
* **Öka volymen som skickas** progressivt för att undvika att markeras som skräppost. Använd inte hela databasen som mål från början, utan lägg till en extra del av listan varje gång du skickar. Detta bör göra att du kan öka volymen i varje steg och samtidigt minska den totala hastigheten för ogiltiga adresser. För att säkerställa en smidig utveckling av startfasen kan du använda vågor. Mer information finns i [Skicka med flera vågor](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves).
* **Skicka regelbundet**. I viss utsträckning är det bättre att skicka små tagningar regelbundet i stället för stora kampanjer sporadiskt.
* **Var noga med leveransrapporterna**. Höga felindikatorer kan innebära att en teknisk inställning är felaktigt konfigurerad. Mer information finns i [Övervaka en leverans](../../delivery/using/monitoring-a-delivery.md).

**Relaterade ämnen**:
* [Öka e-postens anseende med IP-uppvärmning](https://helpx.adobe.com/campaign/kb/increase-email-rep-ip-warming.html)
* [Allt om Spam-svällningar](https://helpx.adobe.com/campaign/kb/spam-traps.html)