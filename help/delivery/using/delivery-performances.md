---
product: campaign
title: Bästa praxis för leveransprestanda
description: Läs mer om leveransresultat och bästa praxis
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Deliverability
role: User, Data Engineer
exl-id: cc793d7b-0a26-4a75-97ed-d79c87d9b3b8
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 5%

---

# Bästa praxis för leveransprestanda {#delivery-performances}

Vi rekommenderar att du följer riktlinjerna nedan för att försäkra dig om att leveranserna fungerar bra, samt de kontroller som utförs om leveransproblem uppstår.

**Relaterade ämnen:**

* [Kontrollpanel för leverans](delivery-dashboard.md)
* [Leveransfelsökning](delivery-troubleshooting.md)
* [Om levererbarhet](about-deliverability.md)

## Bästa tillvägagångssätt för prestanda {#best-practices-performance}

* Behåll inte leveranser i felaktigt tillstånd för instansen eftersom detta bevarar tillfälliga tabeller och påverkar prestandan.

* Ta bort leveranser som inte längre behövs.

* Inaktiva mottagare de senaste 12 månaderna som ska tas bort från databasen för att upprätthålla adresskvaliteten.

* Försök inte schemalägga stora leveranser tillsammans. Det finns ett mellanrum på 5-10 minuter för att sprida belastningen jämnt över systemet. Samordna schemaläggningen av leveranser med övriga medlemmar i teamet för att säkerställa bästa möjliga prestanda. När marknadsföringsservern hanterar många olika uppgifter samtidigt kan prestandan försämras.

* Håll storleken på era e-postmeddelanden så låg som möjligt. Den rekommenderade maximala storleken för ett e-postmeddelande är cirka 35 kB. Storleken på en e-postleverans genererar en viss volym på de avsändande servrarna.

* För stora leveranser, som leveranser till över en miljon mottagare, behövs utrymme i utskicksköerna. Detta är inget problem för servern, men om det kombineras med dussintals andra stora leveranser som alla går ut samtidigt kan det medföra en fördröjning.

* Personalization i e-postmeddelanden hämtar data från databasen för varje mottagare. Om det finns många personaliseringselement ökar detta mängden data som behövs för att förbereda leveransen.

* Indexadresser. För att optimera prestanda för SQL-frågor som används i programmet kan ett index deklareras från huvudelementet i dataschemat.

>[!NOTE]
>
>Internetleverantörer inaktiverar adresser efter en tids inaktivitet. Avvisade meddelanden skickas till avsändare för att informera dem om den nya statusen.

## Checklista för prestandaproblem {#performance-issues}

Om leveransresultaten är felaktiga kan du kontrollera:

* **Storleken på leveransen**: Stora leveranser kan ta längre tid att slutföra. MTA-underordnade är konfigurerade att hantera en standardbatchstorlek, som fungerar för de flesta instanser, men som måste kontrolleras när leveranserna är konstant långsamma.
* **Målet för leveransen**: Förbudet mot leveransprestanda påverkas av mjuka studsfel, som hanteras enligt konfigurationen för nya försök. Ju fler fel, desto fler försök.
* **Den totala plattformsinläsningen**: När flera stora leveranser skickas kan den övergripande plattformen påverkas. Du kan även kontrollera IP-adressens anseende och leveransproblem. Mer information finns i [det här avsnittet](about-deliverability.md) och i [Adobe Deliverability Best Practice Guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=sv).

Plattforms- och databasunderhåll kan också påverka leveransresultaten. Mer information finns på [den här sidan](../../production/using/database-performances.md).
