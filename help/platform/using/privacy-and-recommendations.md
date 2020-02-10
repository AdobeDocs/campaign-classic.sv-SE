---
title: Sekretess och rekommendationer
seo-title: Sekretess och rekommendationer
description: Sekretess och rekommendationer
seo-description: null
page-status-flag: never-activated
uuid: a044bbea-521d-4c1e-8aab-7d51a87fc94b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 14369acf-9149-4649-947a-c16289e35eb6
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: ed5390b4f620c3cddaf9b856f3354dc5f06f4d98

---


# Sekretess och rekommendationer{#privacy-and-recommendations}

## Om sekretess och samtycke {#about-privacy-and-consent}

Adobe Campaign är ett kraftfullt verktyg för att samla in och behandla mycket stora mängder data, inklusive personuppgifter. Vi uppmuntrar alla användare av Adobe Campaign att arbeta inom lagstiftning (DPA, CAN-SPAM, European Directive on Privacy and Electronic Communications, European GDPR, osv.), att göra ansvarsfull och etisk användning av personuppgifter och att avstå från att skicka oönskade e-postmeddelanden, push-meddelanden och SMS-meddelanden (&quot;spam&quot;). Vi tror starkt på principerna om tillståndsmarknadsföring när det gäller att främja kundens livstidsvärde och lojalitet, och vi förbjuder därför strikt användning av Adobe Campaign när det gäller att skicka oönskade meddelanden.

Mer information finns i [Adobe Experience Cloud-sekretess](https://www.adobe.com/privacy/marketing-cloud.html).

Adobe Campaign innehåller de verktyg och funktioner, samt bästa praxis, som hjälper er att uppfylla er GDPR-policy när ni använder vår tjänst. Se [det här dokumentet](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/ACC_GDPR.html).

Ta dig tid att gå igenom checklistan [för](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html) säkerhet och integritet för att lära dig grunderna för att kontrollera säkerhet och integritet.

## Cookies och spårningsfunktioner {#cookies-and-tracking-capabilities}

Tack vare spårningsfunktionerna i Adobe Campaign kan ni spåra hur mottagarna surfar på en webbplats. För att göra detta använder Adobe Campaign sessionscookies och permanenta cookies.

I det europeiska direktivet 2009/136/CE om sekretess och elektronisk kommunikation och den europeiska allmänna dataskyddsförordningen (GDPR) anges att företag kräver godkännande av webbplatsanvändare innan de installerar cookies. Du måste informera användare om att dina webbplatser är utrustade med verktyg för webbspårning via en auktoriseringsbegäran (som visas på sidan till exempel) med en kryssruta för att godkänna installation av cookies, eller lägga till en banderoll högst upp på den första sidan som de landar på, osv. Popup-fönster bör undvikas eftersom de ofta blockeras av webbläsare.

Konfigurationen av hanteringen av användarspårning är tillgänglig för webbprogram och landningssidor med en avanmälningsbanderoll. Se [den här sidan](../../web/using/web-application-tracking-opt-out.md).

Adobe Campaign använder två typer av cookies:

1. En sessionscookie (nlid): den innehåller identifieraren för e-postmeddelandet som skickas till kontakten (broadlogId) och identifieraren för meddelandemallen (deliveryId). Den läggs till när kontakten klickar på en URL som ingår i ett e-postmeddelande som skickas av Adobe Campaign och gör att du kan spåra deras beteende på webben. Denna sessionscookie raderas automatiskt när webbläsaren stängs. Kontakten kan konfigurera sin webbläsare så att den inte tillåter cookies.
1. En permanent cookie (uuid230): kan ni identifiera de användare som interagerar med Adobe Campaign när de besöker en webbplats. Det används av Adobe Campaign för att räkna antalet klick och beräkna överföringshastigheten under en marknadsföringskampanj. Den placeras när kontakten klickar i ett e-postmeddelande och fyller i ett formulär i Adobe Campaign eller under anropet till den inkommande interaktionsmotorn. Användaren kan konfigurera webbläsaren så att den tas bort eller nekas.

## Databasintegritet {#database-integrity}

Adobe Campaign har en mängd funktioner. Därför används en komplex databasstruktur. Databasen innehåller många tabeller, fält, länkar och index. Vissa mellanliggande tabeller visas inte i gränssnittet. Programmet skapar, tar bort eller ändrar automatiskt vissa länkar, fält och index. Endast Adobe Campaign-gränssnitt (grafiskt gränssnitt, importprogram, servermodul, webbmodul, leveransservrar, tilläggsfält, databastillägg osv.) kan ändra innehållet i databasen samtidigt som databasens integritet bevaras.

**Ändra aldrig databasens innehåll eller struktur med något annat verktyg än det här programmet**. Sådana ändringar skulle sannolikt medföra att databasen skadas, vilket resulterar i: oavsiktlig ändring eller förlust av länkar, skapande av spökposter eller länkar, allvarliga felmeddelanden osv. samt återgivning av garantiavtalet och det tekniska supportavtalet från Adobe Campaign null och void.

I Adobe Campaign-systemet lagras alla data i databasen. Korrekt användning av hela Adobe Campaign-systemet beror på tillgängligheten av dessa data för: webbmoduler för prenumeration, administration och avprenumeration, administrationsskärmar, leveransköer, leveransoptimeringsmekanismer osv.

## Apache Tomcat {#apache-tomcat}

Adobe Campaign innehåller Apache Tomcat, som utvecklats av Apache Software Foundation ( [https://www.apache.org/](https://www.apache.org/)).
