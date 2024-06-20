---
product: campaign
title: Support för TLS 1.0 och 1.1 upphör
description: Support för TLS 1.0 och 1.1 upphör
feature: Technote
audience: delivery
content-type: reference
topic-tags: tracking-messages
hide: true
hidefromtoc: true
exl-id: e18d43b6-2a77-4881-85e7-ca36248d4634
source-git-commit: 19b40f0b827c4b5b7b6484fe4953aebe61d00d1d
workflow-type: tm+mt
source-wordcount: '860'
ht-degree: 3%

---

# Support för TLS 1.0 och 1.1 upphör{#eol-tls-support}



Adobe stöder inte längre användarsystem och klientsystem som inte är kompatibla med TLS 1.2-protokollet (Transport Layer Security). Om du fortsätter att använda äldre versioner av TLS kan du förlora åtkomsten till alla produkter och tjänster från Adobe.

## Varför visas den här sidan?

Om följande meddelande visas: **Den här sidan kan inte visas** innebär det att de Adobe-program, webbsidor eller tjänster du försöker få åtkomst till kräver en säkrare nätverksanslutning till webbläsaren, operativsystemet eller appen. Den måste användas **TLS 1.2** för säker nätverkskommunikation och datautbyte mellan användarsystem, appar från Adobe och webbtjänster.

Adobe har ersatt stödet för lägre versioner av TLS (inklusive TLS 1.0 och 1.1). Teknisk information om TLS 1.2-protokollet finns på [Frågor och svar](#faq).

## Vad kan jag göra för att återuppta tjänsten?

Moderna webbläsare stöder TLS 1.2. Om du uppgraderar webbläsaren kan du få tillgång till dessa program och tjänster.

Du kan hämta och installera någon av följande populära webbläsare:

* [Google Chrome](https://www.google.com/chrome/)
* [Apple Safari](https://www.apple.com/safari/)
* [Firefox](https://www.mozilla.org/en-US/firefox/new/)
* [Microsoft Edge](https://www.microsoft.com/en-us/edge)

Om du använder en annan webbläsare måste den ha stöd för TLS 1.2.

Ditt operativsystem och dina programramverk måste också ha stöd för TLS 1.2. Om du inte löser problemet genom att uppgradera webbläsaren kontrollerar du att datorn uppfyller systemkraven i [Matris för kampanjkompatibilitet](../../rn/using/compatibility-matrix.md).

## Vanliga frågor och svar{#faq}

* **Vad är TLS?**

  [Säkerhet för transportlager](https://en.wikipedia.org/wiki/Transport_Layer_Security) (TLS) är ett säkerhetsprotokoll som ger sekretess och dataintegritet mellan två kommunikationsprogram. Den används ofta för webbläsare och andra program som kräver att data utbyts på ett säkert sätt över ett nätverk.

  Enligt protokollspecifikationen innehåller TLS två lager, TLS-protokollet Record och TLS-handskakningsprotokollet. Record-protokollet tillhandahåller anslutningssäkerhet. Med handskakningsprotokollet kan servern och klienten autentisera varandra och förhandla om krypteringsalgoritmer och kryptografiska nycklar före datautbyte.

* **Vad ändras?**

  Adobe säkerhetsstandarder kräver borttagning av äldre protokoll från och med maj 2018 och kräver att TLS 1.2 används som den senaste versionen. Om ditt system inte är kompatibelt med TLS 1.2 begränsas åtkomsten till vissa appar och tjänster i Adobe.

* **Hur påverkar TLS dig?**

  Du kan bara interagera med vissa appar och tjänster från Adobe via en säker nätverksanslutning. TLS säkerställer att anslutningen mellan webbläsaren och dessa appar och webbtjänster är säker och tillförlitlig.

  När nya webbläsare och operativsystem släpps uppgraderas säkerhetsstandarderna för att säkerställa högre sekretessnivåer och dataintegritet. Äldre versioner av dessa webbläsare eller operativsystem uppdateras dock inte med de senaste standarderna.

  När säkerhetsnivån ökar blir dessa äldre, mindre säkra webbläsarversioner och program kvar.

  Om du vill kunna ansluta till säkra webbplatser uppdaterar du operativsystemet och webbläsarversionerna.

* **Är TLS sårbart för hackare?**

  Det har förekommit dokumenterade attacker mot TLS 1.0 med en äldre krypteringsmetod och de äldre versionerna är mer utsatta än TLS 1.2. Mer information finns i Attacker mot TLS/SSL.

* **Varför inaktiverar Adobe stöd för TLS 1.0 och 1.1?**

  Adobe har standarder för säkerhetsefterlevnad som kräver att stöd för äldre protokoll inaktiveras. En sådan standard säkerställer överensstämmelse med betalkortsbranschen (PCI). PCI-anpassningsserver är en uppsättning säkerhetsstandarder som kräver att organisationer som godkänner, bearbetar, lagrar eller överför kreditkortsinformation upprätthåller en säker miljö.

  Enligt PCI-efterlevnaden ska TLS 1.1 eller senare användas från och med maj 2018.

* **Varför tillåter Adobe användning av TLS 1.2 i stället för att tillåta TLS 1.1 eller TLS 1.0?**

  De flesta förfrågningar om appar och webbtjänster från Adobe kommer från användarsystem som följer TLS 1.2, med låg trafik från TLS 1.1-system.

  Adobe har migrerat till TLS 1.2 så att appar och webbtjänster blir säkrare åtkomliga.

* **Vilket är det sista datumet då jag kan använda en äldre version av TLS?**

  Adobe uppmuntrar användare att snabbt överge de äldre versionerna för att undvika exponering för säkerhetsrisker. Mer information får du om du kontaktar Adobe kundtjänst eller en Customer Success Manager.

* **Vilket felmeddelande visas om jag använder en webbläsare som inte är konfigurerad för TLS 1.2?**

  Det beror på vilken webbläsare du använder. Alla webbläsare som nämns i [Matris för kampanjkompatibilitet](../../rn/using/compatibility-matrix.md) är konfigurerade att använda TLS 1.2. Uppdatera webbläsaren om du använder en webbläsare eller version som inte finns med i listan.

  Adobe kontrollerar inte felmeddelanden som genereras av SSL-kommunikationslagret. Webbläsaren genererar dessa meddelanden innan den ansluter till appar och tjänster från Adobe. Här följer ett exempel på fel som kan uppstå i Internet Explorer 11 i Windows 7:

  ![](assets/do-not-translate/page-not-displayed.png)

  TLS 1.2 är aktiverat som standard i Internet Explorer 11, men om det är inaktiverat kan du aktivera det. I så fall aktiverar du TLS 1.2 i dialogrutan för avancerade inställningar i stället för att använda andra alternativ. Andra fel, till exempel följande, kan också inträffa:

   * Det går inte att ansluta till tjänsten
   * Tjänsten är inte tillgänglig
   * Anslutningsfel
