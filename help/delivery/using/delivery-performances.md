---
product: campaign
title: Bästa praxis för leveransprestanda
description: Läs mer om leveransresultat och bästa praxis
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Deliverability
exl-id: cc793d7b-0a26-4a75-97ed-d79c87d9b3b8
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 6%

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

* Personalisering i e-postmeddelanden hämtar data från databasen för varje mottagare. Om det finns många personaliseringselement ökar detta mängden data som behövs för att förbereda leveransen.

* Indexadresser. För att optimera prestanda för SQL-frågor som används i programmet kan ett index deklareras från huvudelementet i dataschemat.

>[!NOTE]
>
>Internetleverantörer inaktiverar adresser efter en tids inaktivitet. Avvisade meddelanden skickas till avsändare för att informera dem om den nya statusen.

## Checklista för prestandaproblem {#performance-issues}

Om leveransresultaten är felaktiga kan du kontrollera:

* **Leveransens storlek**: Stora leveranser kan ta längre tid att slutföra. MTA-underordnade är konfigurerade att hantera en standardbatchstorlek, som fungerar för de flesta instanser, men som måste kontrolleras när leveranserna är konstant långsamma.
* **Målet för leveransen**: Förbud mot leveransprestanda påverkas av mjuka studsfel som hanteras enligt konfigurationen för nya försök. Ju fler fel, desto fler försök.
* **Den totala plattformsinläsningen**: När flera stora leveranser skickas kan den övergripande plattformen påverkas. Du kan även kontrollera IP-adressens anseende och leveransproblem. Mer information finns i [det här avsnittet](about-deliverability.md) och [Adobe Deliverability Best Practice Guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=sv).

Plattforms- och databasunderhåll kan också påverka leveransresultaten. Mer information finns på [den här sidan](../../production/using/database-performances.md).
