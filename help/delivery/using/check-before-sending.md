---
product: campaign
title: Kontrollera före sändning
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
exl-id: 50d326b0-3c23-4dbf-9df6-d32b48e30f69
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '861'
ht-degree: 4%

---

# Utför alla kontroller innan du skickar {#perform-all-checks}

![](../../assets/common.svg)

När meddelandet är klart ser du till att innehållet visas korrekt på alla enheter och att det inte innehåller fel som personalisering eller brutna länkar.

Innan du skickar meddelandet måste du se till att parametrarna och konfigurationen stämmer överens med leveransen.

## Varför validering är avgörande {#validation-is-key}

Innan du skickar en leverans måste du se till att mottagarna får det meddelande som du verkligen vill skicka. För att göra detta måste du validera meddelandets innehåll och leveransparametrar.

Med det här steget kan du identifiera eventuella fel och åtgärda dem innan du levererar till huvudmålet.

Stegen för validering av leverans visas [i det här avsnittet](steps-validating-the-delivery.md).

## Inkorgsåtergivning {#inbox-and-email-rendering}

Med inkorgsåtergivning kan du förhandsgranska meddelanden på större e-postklienter, skanna innehåll och anseende, upptäcka hur mottagarna läser meddelanden.

**Tips**:

* Du kan visa det skickade meddelandet i olika sammanhang där det kan tas emot: webbpost, meddelandetjänst, mobil osv.

* Återgivningsfunktioner för inkorgen är avgörande för att du ska kunna identifiera om dina e-postkampanjer fungerar som de ska med filtren hos viktiga internetleverantörer (Internet Service Providers) och webbposttjänster. Sådana verktyg skickar en kopia av ett e-postmeddelande till ett nätverk av testinkorgar, så att du kan se hur meddelandet kommer att visas, eller återges, i alla dessa tjänster. De kan även innehålla rapporter och kodkorrigeringsalternativ som hjälper dig att snabbt identifiera och göra korrigeringar som förbättrar leveransen.

Läs mer [i det här avsnittet](inbox-rendering.md).

## Korrekturmeddelanden {#proof-messages}

Genom att skicka korrektur kan du kontrollera länken för avanmälan, spegelsidan och alla andra länkar, validera meddelandet, verifiera att bilder visas, upptäcka eventuella fel osv. Du kanske också vill kontrollera din design och återgivning på olika enheter.

Läs mer [i det här avsnittet](steps-validating-the-delivery.md#sending-a-proof).

## Ställ in A/B-testleveranser {#a-b-testing-deliveries}

Om du har flera innehåll för en e-postleverans kan du använda A/B-testning för att ta reda på vilken version som har störst påverkan på målpopulationen.

**Tips**:

* Skicka olika versioner till vissa mottagare

* Välj den som har högst framgångsfrekvens och skicka den till resten av ditt mål

Läs mer [i det här avsnittet](get-started-a-b-testing.md).

## Se till att ditt meddelande levereras {#make-sure-your-message-is-delivered}

Som ett sista steg kan du maximera dina chanser och utnyttja kraften i Adobe Campaign Classic för att säkerställa att ditt budskap verkligen kommer att levereras till de relevanta mottagarna.

### Gå igenom en valideringsprocess

Du kan definiera en fullständig valideringsprocess där Adobe Campaign-operatorer och -grupper deltar för att validera både mål- och meddelandeinnehållet. Detta kommer att säkerställa full övervakning och kontroll av kampanjens olika processer: målgruppsanpassning, innehåll, budget, extrahering och utskick av ett bevis. Beroende på deras behörigheter meddelas användare, får korrektur och kan validera eller avvisa meddelandet. Läs mer [i det här avsnittet](../../campaign/using/marketing-campaign-approval.md).

### Använd vågor

Du kan stegvis öka volymen som skickas med vågor. På så sätt undviker du att meddelanden markeras som skräppost eller när du vill begränsa antalet meddelanden per dag. Med vågor kan du dela upp leveranser i flera grupper i stället för att skicka stora mängder meddelanden samtidigt. Läs mer [i det här avsnittet](steps-sending-the-delivery.md#sending-using-multiple-waves).

### Prioritera meddelanden

Du kan ange avsändarordning för leveranser genom att ange prioritetsnivå. För att göra detta:

1. Redigera leveransegenskaperna och välj fliken **[!UICONTROL Delivery]**.

1. Definiera prioritetsnivån för leveransen på en skala från **[!UICONTROL Very low]** till **[!UICONTROL Very high]**.

>[!NOTE]
>
>Det går inte att definiera ordningen för att skicka meddelanden från en leverans.

### Konfigurera IP-tillhörigheter

Om du vill ha bättre kontroll över utgående SMTP-trafik kan du hantera tillhörigheter genom att definiera vilka specifika IP-adresser som kan användas för varje tillhörighet. På så sätt kan du begränsa antalet e-postmeddelanden för specifika leveranser till maskiner eller utdatameddelanden. Du kan till exempel använda en affinitet per land eller underdomän. Du kan sedan skapa en typologi per land och länka varje tillhörighet till motsvarande typologi.

Du kan:

* Definiera IP-tillhörigheterna i konfigurationsfilen serverConf.xml. [Läs mer](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities)

* Deklarera de IP-adresser som kan användas för varje IPAfinity-element. [Läs mer](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

* I den [typologi](../../campaign-opt/using/about-campaign-typologies.md) du väljer använder du fältet **[!UICONTROL Managing affinities with IP addresses]** för att länka leveranser till leveransservern (MTA) som hanterar tillhörigheten. [Läs mer](../../campaign-opt/using/applying-rules.md#control-outgoing-smtp-traffic).

* När e-postmeddelandet har skickats kontrollerar du huvudet för att verifiera vilken IP-adress som leveransen skickades från. E-postadministratören bör hjälpa dig att få fram rubrikinformationen.

>[!NOTE]
>
>De flesta av dessa steg kan bara utföras av en expertanvändare.

### Använd typologier

Du kan använda typologiregler för att exkludera delar av målet baserat på specifika kriterier. Detta garanterar att de meddelanden som skickas bäst uppfyller kundernas behov och förväntningar i enlighet med företagets kommunikationspolicyer. Du kan till exempel filtrera de mottagare som är minderåriga från målet i nyhetsbrevet. Läs mer [i det här exemplet](../../campaign-opt/using/filtering-rules.md).

### Undvik bifogade filer

Bifogade filer är fortfarande en av de vanligaste vektorerna för spridning av skadlig kod, särskilt när de skickas satsvis. Inkludera en säker länk till dokumentet i stället för att bifoga det. Detta garanterar ett extra säkerhetslager för att förhindra oavsiktlig omdistribution och minskar avsevärt riskerna för att meddelandet kommer att refuseras vid inkommande e-postgatewayar av meddelandestorlek eller säkerhetsskäl.
