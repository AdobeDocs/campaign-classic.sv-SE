---
source-git-commit: 65d223acd23f26bd9c6979d11815d23f02ae2382
workflow-type: tm+mt
source-wordcount: '948'
ht-degree: 18%

---
# 📊 v7 - Dokumentationsomorganisering - översikt

**Genererad**: 2026-01-13\
**Totalt antal mappar**: 21\
**Totalt antal filer**: ~1 500

&#x200B;---

## Sammanfattning av 📈

| Mått | Antal | Procent |
|--------|-------|------------|
| 📄 **Totalt antal filer** | 1 500 | 100 % |
| ✅ **BEHÅLL (v7-specifik)** | 400 | 27 % |
| 🗑️ **DELETE (i v8)** | 800 | 53 % |
| ➡️ **FLYTTA (till v8)** | 200 | 13 % |
| 🔍 **GRANSKNING (oklar)** | 100 | 7 % |

**🎯beräknad reduktion**: 60-75 % (1 500 → 400-600 filer)

&#x200B;---

## Mappanalys för 📁 efter prioritet

### 🟢 Prioritet 1: 100 % BEHÅLLNING - Funktioner som endast är v7

| Mapp | Filer | Orsak | v8-status | Åtgärd |
|--------|-------|--------|-----------|--------|
| 📂 `/installation/` | 75 | Lokal/hybridinstallation | Endast molnet i v8 | ✅ BEHÅLL ALLA +-märke |
| 📂 `/mrm/` | 5 | Marknadsföringsresurshantering | INTE i FFDA | ✅ BEHÅLL ALLA +-märke |
| 📂 `/surveys/` | 8 | Onlineundersökningar | INTE i FFDA | ✅ BEHÅLL ALLA +-märke |
| 📂 `/distributed/` | 7 | Distribuerad marknadsföring | INTE i FFDA | ✅ BEHÅLL ALLA +-märke |
| 📂 `/response/` | 5 | Svarshantering | Oklar status | 🔍 VERIFY then KEEP |
| 📂 `/migration/` | 8 | v6.1 → v7-migrering | v7-specifik | ✅ BEHÅLL ALLA |
| **TOTALT** | **108** | **7 %** | - | **Märkordsbricka som endast v7** |

&#x200B;---

### 🔴 Prioritet 2: 60-70 % DELETE - hög duplicering

| Mapp | Totalt | BEHÅLL | DELETE | FLYTTA | GRANSKA | Anteckningar |
|--------|-------|------|--------|------|--------|-------|
| 📂 `/delivery/` | 111 | 18 (16 %) | 67 (60 %) | 8 (7 %) | 18 (17 %) | E-post/SMS/push in v8 |
| 📂 `/workflow/` | 121 | 24 (20 %) | 60 (50 %) | 12 (10 %) | 25 (20 %) | Vanliga aktiviteter i v8 |
| 📂 `/reporting/` | 32 | 3 (10 %) | 22 (70 %) | 2 (6 %) | 5 (14 %) | Rapporter omdesignade i v8 |
| 📂 `/platform/` | 61 | 12 (20 %) | 34 (55 %) | 5 (8 %) | 10 (17 %) | Vanliga funktioner i v8 |
| 📂 `/campaign/` | 11 | 2 (18 %) | 7 (64 %) | 1 (9 %) | 1 (9 %) | Kampanjhantering i v8 |
| **TOTALT** | **336** | **59** | **190** | **28** | **59** | **Hög reduceringspotential** |

&#x200B;---

### 🟡 Prioritet 3: 30-50 % BLANDADE - Detaljerad analys krävs

| Mapp | Totalt | BEHÅLL % | DELETE % | Anteckningar |
|--------|-------|--------|----------|-------|
| 📂 `/configuration/` | 69 | 65 % | 22 % | Schema-/DB-konfigurationer (oftast v7) |
| 📂 `/production/` | 43 | 65 % | 23 % | Serverhantering (oftast v7) |
| 📂 `/integrations/` | 37 | 40 % | 40 % | Kontrollera anslutningstillgänglighet |
| 📂 `/interaction/` | 39 | 51 % | 31 % | Erbjudandemotor (verifiera v8) |
| 📂 `/web/` | 26 | 92 % | 8 % | Webbprogram > Landningssidor v8 |
| 📂 `/message-center/` | 16 | 60 % | 30 % | Transaktionsmeddelanden |
| **TOTALT** | **230** | **~55%** | **~25%** | **Kräver en mapp-för-mapp-granskning** |

&#x200B;---

## 🎯 snabbvinster - vecka 1

### Borttagningar med hög exakthet (95-100 % v8-matchning)

| Mapp | Filer som ska tas bort | Effekt | Insats |
|--------|----------------|--------|--------|
| 📂 `/delivery/` | 67 filer | 🔥🔥🔥 hög | 2 dagar |
| 📂 `/workflow/` | 60 filer | 🔥🔥🔥 hög | 2 dagar |
| 📂 `/reporting/` | 22 filer | 🔥🔥 Medium | 1 dag |
| 📂 `/platform/` | 34 filer | 🔥🔥 Medium | 1 dag |
| 📂 `/campaign/` | 7 filer | 🔥 låg | 0,5 dag |
| **TOTALT** | **190 filer** | **53 % minskning** | **6,5 dagar** |

**Exempel**:
- ✅ `about-email-channel.md` → `campaign-web/v8/email`
- ✅ `sms-channel.md` → `campaign-web/v8/msg/send-sms`
- ✅ `query.md` (arbetsflöde) → `campaign/v8/automation/workflow/query`
- ✅ `about-workflows.md` → `campaign/v8/automation/workflow`

&#x200B;---

## 📋 detaljerad mappuppdelning

### 📂 Leverans (`/help/delivery/using/`) - 111 filer

| Kategori | Filer | BEHÅLL | DELETE | FLYTTA | GRANSKA | Anteckningar |
|----------|-------|------|--------|------|--------|-------|
| Kom igång | 8 | 0 | 7 | 0 | 1 | Grunderna i v8 |
| E-post | 18 | 0 | 16 | 0 | 2 | Helt in v8 |
| SMS | 7 | 1 | 5 | 0 | 1 | Mid-sourcing = KEEP |
| Push | 9 | 0 | 8 | 0 | 1 | Helt in v8 |
| Direktutskick | 4 | 0 | 4 | 0 | 0 | In v8 |
| Personalization | 8 | 1 | 6 | 0 | 1 | Kuponger = KEEP |
| Mallar | 6 | 0 | 6 | 0 | 0 | In v8 |
| A/B-tester | 11 | 0 | 10 | 0 | 1 | In v8 |
| Övervakning | 14 | 0 | 12 | 1 | 1 | Mest i v8 |
| Felsökning | 9 | 2 | 4 | 2 | 1 | Håll tips |
| Levererbarhet | 8 | 3 | 4 | 0 | 1 | SpamAssassin = KEEP |
| Avancerat | 9 | 11 | 5 | 5 | 8 | Blandad |
| **TOTALT** | **111** | **18** | **67** | **8** | **18** | **60% kan tas bort** |

**Måste behålla**:
- ✅ `personalized-coupons.md` - INTE i v8 FFDA
- ✅ `sms-set-up-mid.md` - Mid-sourcing (lokal)
- ✅ `spamassassin.md` - skräppostfiltrering på plats

**Exempel på snabbborttagning**:
- 🗑️ `about-email-channel.md` → 95 % i `campaign-web/v8/email`
- 🗑️ `creating-an-email-delivery.md` → 95 % i `campaign-web/v8/email/create-email`
- 🗑️ `sms-channel.md` → 90 % i `campaign-web/v8/msg/send-sms`

&#x200B;---

### 📂-arbetsflöde (`/help/workflow/using/`) - 121 filer

| Kategori | Filer | BEHÅLL | DELETE | FLYTTA | GRANSKA | Anteckningar |
|----------|-------|------|--------|------|--------|-------|
| Kom igång | 12 | 2 | 9 | 0 | 1 | Grunderna i v8 |
| Målinriktning | 18 | 3 | 12 | 1 | 2 | Fråga/dela i v8 |
| Flödeskontroll | 15 | 2 | 10 | 1 | 2 | Vanligt i v8 |
| Verksamheter | 24 | 4 | 16 | 2 | 2 | Mest i v8 |
| Evenemangsaktiviteter | 8 | 1 | 6 | 0 | 1 | In v8 |
| MRM-aktiviteter | 5 | 5 | 0 | 0 | 0 | INTE i FFDA |
| Teknisk | 16 | 4 | 8 | 2 | 2 | Blandad |
| Avancerat | 12 | 3 | 4 | 3 | 2 | Mönster är användbara |
| Användningsexempel | 11 | 0 | 5 | 3 | 3 | Bra exempel |
| **TOTALT** | **121** | **24** | **60** | **12** | **25** | **50% kan tas bort** |

**Måste behålla**:
- ✅ Alla MRM-aktiviteter (5 filer) - INTE i v8 FFDA
- ✅ Lokala konfigurationer
- ✅ Avancerade tekniska arbetsflöden

**Exempel på snabbborttagning**:
- 🗑️ `query.md` → 95 % i `campaign/v8/automation/workflow/query`
- 🗑️ `split.md` → 95 % i `campaign/v8/automation/workflow/split`
- 🗑️ `enrichment.md` → 95 % i `campaign/v8/automation/workflow/enrichment`

&#x200B;---

### 📂 Installation (`/help/installation/using/`) - 75 filer

| Kategori | Filer | Åtgärd | Anteckningar |
|----------|-------|--------|-------|
| Serverinstallation | 18 | ✅ BEHÅLL | Endast lokalt |
| Databasinställningar | 12 | ✅ BEHÅLL | Endast lokalt |
| Konfiguration | 15 | ✅ BEHÅLL | nlserver osv. |
| Nätverk | 8 | ✅ BEHÅLL | Säkerhetszoner |
| Integrering | 10 | ✅ BEHÅLL | LDAP osv. |
| Felsökning | 8 | ✅ BEHÅLL | Problem på plats |
| Allmän dokumentation | 4 | 🗑️ DELETE | Startguide för v8 |
| **TOTALT** | **75** | **71 BEHÅLL/4 DELETE** | **95% v7-specifik** |

**Orsak**: v8 är endast för molnet, alla installationsdokument på plats är v7-specifika.

&#x200B;---

### 📂 webb (`/help/web/using/`) - 26 filer

| Kategori | Filer | BEHÅLL | DELETE | Anteckningar |
|----------|-------|------|--------|-------|
| Webbprogram | 14 | 14 | 0 | Avancerade funktioner som inte finns i v8 |
| Webbformulär | 8 | 8 | 0 | Fler än v8 landningssidor |
| Landningssidor | 2 | 0 | 2 | Grundläggande sidor i v8 |
| HTML Editor | 2 | 2 | 0 | Annat än v8 |
| **TOTALT** | **26** | **24** | **2** | **92% v7-specifik** |

**Orsak**: v7 har ett fullständigt ramverk för webbprogram, v8 har förenklat landningssidor.

&#x200B;---

## Åtgärdsplan för ✅

### Vecka 1: Högeffektsborttagningar- [ ] `/delivery/`: Ta bort 67 filer (e-post, SMS, push-grunder)- [ ] `/workflow/`: Ta bort 60 filer (vanliga aktiviteter)- [ ] `/reporting/`: Ta bort 22 filer (standardrapporter)- [ ] `/platform/`: Ta bort 34 filer (vanliga funktioner)- [ ] `/campaign/`: Ta bort 7 filer (kampanjhantering)- **Totalt**: 190 filer har tagits bort (13 % minskning)

### Vecka 2: v7-specifik märkning- [ ] `/installation/`: Badge 71-filer som&quot;v7 endast lokalt&quot;- [ ] `/mrm/`: Badge 5-filer är inte tillgängliga i v8 FFDA- [ ] `/surveys/`: Badge 8-filer är inte tillgängliga i v8 FFDA- [ ] `/distributed/`: Badge 7-filer är inte tillgängliga i v8 FFDA- [ ] `/web/`: Visa 24 filer som&quot;v7-webbprogram&quot;- **Totalt**: 115 filer har badats

### Vecka 3: Innehållsmigrering- [ ] Migrera felsökningstips från `/delivery/` till v8- [ ] Migrera arbetsflödets bästa praxis till v8- [ ] Migrera avancerade mönster från `/platform/` till v8- **Totalt**: 40 filer har migrerats och tagits bort

### Vecka 4: Manuell granskning- [ ] Granska `/configuration/` blandat innehåll- [ ] Granska `/integrations/`-anslutningstillgänglighet- [ ] Granska `/interaction/`, erbjudandemotortäckning- [ ] Granska `/response/`-funktionsstatus- **Totalt**: 50 filer granskades och beslutades

&#x200B;---

## 📊 förväntade resultat

| Fas | Filer som påverkas | Kumulativ % |
|-------|----------------|--------------|
| Vecka 1: Borttagningar | 190 | 13 % |
| Vecka 2: Märkning | 115 | 20 % |
| Vecka 3: Migrering | 40 | 23 % |
| Vecka 4: Granska | 50 | 26 % |
| **TOTALT** | **395** | **26% har bearbetats** |

**Återstående**: ~1 100 filer att bearbeta i efterföljande faser

**Slutligt mål**: 1 500 → 400-600 filer (60-73 % minskning)

&#x200B;---

## 🎯 framgångsmått

| Mått | Mål | Status |
|--------|--------|--------|
| Borttagna filer | 800+ (53 %) | ⏳ väntar |
| Filer märkta | 200+ (13 %) | ⏳ väntar |
| Migrerade filer | 200+ (13 %) | ⏳ väntar |
| Brutna länkar | 0 | ⏳ väntar |
| Intressentgodkännande | ✅ | ⏳ väntar |

&#x200B;---

**Senast uppdaterad**: 2026-01-13\
**Nästa granskning**: Efter körning av vecka 1

