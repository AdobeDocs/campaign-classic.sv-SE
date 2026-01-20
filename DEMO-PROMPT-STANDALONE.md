---
source-git-commit: 65d223acd23f26bd9c6979d11815d23f02ae2382
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---
# 🚀 DEMO PROMPT - v7 till v8-dokumentationsanalys

**Kopiera och klistra in hela uppmaningen i Cursor/ChatGPT för att analysera alla v7-mappar**

&#x200B;---

## 📋 UPPMANINGEN (KOPIERA HÄR) ⬇️

```markdown
# Campaign v7 Documentation Analysis

Analyze the v7 documentation folder and generate a detailed Markdown report with recommendations.

---

## CONTEXT

**v7 Repository**: `/Users/florentvignes/Documents/GitHub/campaign-classic.en/`  
**v8 Repositories**:
- `/Users/florentvignes/Documents/GitHub/campaign.en/` (Campaign v8)
- `/Users/florentvignes/Documents/GitHub/campaign-web.en/` (Campaign Web UI v8)

---

## TARGET FOLDER

**Analyze this folder**: `/Users/florentvignes/Documents/GitHub/campaign-classic.en/help/delivery/using/`

*(Replace with any folder: workflow, web, platform, reporting, etc.)*

---

## FEATURE PARITY CONTEXT

### v7-Specific Features (NOT in v8 FFDA)
- **Coupons** (personalized-coupons.md)
- **MRM** (Marketing Resource Management)
- **Surveys** (online surveys)
- **Distributed Marketing**
- **Mid-sourcing** (on-premise setup)
- **SpamAssassin** (on-premise spam filtering)
- **On-premise/Hybrid** configurations

### v8 Documentation Structure
- **Campaign Web UI**: `/campaign-web.en/help/v8/` - https://experienceleague.adobe.com/en/docs/campaign-web/v8/
- **Campaign v8**: `/campaign.en/help/v8/` - https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/

---

## OUTPUT FORMAT

Generate a complete Markdown report with this structure:

### 1. HEADER & SUMMARY
\`\`\`markdown
# 📊 v7 [Folder Name] Analysis

**Folder**: `/help/[folder]/using/`  
**Generated**: [Date]  
**Total Files**: [X]

## 📈 Summary

| Metric | Count | Percentage |
|--------|-------|------------|
| 📄 Total Files | X | 100% |
| ✅ KEEP | X | X% |
| 🗑️ DELETE | X | X% |
| ➡️ MOVE | X | X% |
| 🔍 REVIEW | X | X% |
\`\`\`

### 2. FILE-BY-FILE ANALYSIS TABLE
\`\`\`markdown
## 📋 Complete File Analysis

### [Category Name] (X files)

| # | v7 File | v8 Match | Match % | Notes | Action |
|---|---------|----------|---------|-------|--------|
| 1 | filename.md | [v8 link](https://...) | 95% | Fully in v8 | 🗑️ DELETE |
| 2 | **filename.md** | NONE | 0% | **v7-specific** | ✅ **KEEP** |
| 3 | filename.md | [v8 link](https://...) | 70% | Migrate tips | ➡️ MOVE |

[Repeat for each category: Get Started, Email, SMS, etc.]
\`\`\`

### 3. MUST KEEP SECTION
\`\`\`markdown
## ✅ Must Keep - v7-Specific Features

| File | Reason | Badge Text |
|------|--------|------------|
| filename.md | Feature not in v8 FFDA | "This feature is not available..." |
\`\`\`

### 4. QUICK WINS SECTION
\`\`\`markdown
## 🗑️ Quick Wins - Safe to Delete Now

**[Category]** (X files):
- ✅ filename.md → 95% in v8/path
- ✅ filename.md → 90% in v8/path
\`\`\`

### 5. MIGRATION SECTION
\`\`\`markdown
## ➡️ Content to Migrate First

| v7 File | v8 Destination | Content to Migrate | Effort |
|---------|----------------|-------------------|--------|
| filename.md | /v8/path.md | Sections X, Y, Z | 2 hours |
\`\`\`

### 6. EXECUTION PLAN
\`\`\`markdown
## 🎯 Execution Plan

### Week 1: Quick Deletions
- [ ] Delete [category] files (X)
- [ ] Delete [category] files (X)
**Total**: X files deleted

### Week 2: Badging
- [ ] Badge v7-specific files (X)

### Week 3: Review
- [ ] Review partial matches (X)
\`\`\`

---

## ANALYSIS RULES

### For Each File, Determine:

1. **Match Percentage**:
   - 95-100% = Fully covered in v8 → DELETE
   - 70-90% = Mostly covered, check gaps → DELETE or MOVE
   - 40-70% = Partial coverage → REVIEW
   - 0-40% = Not in v8 → KEEP or REVIEW

2. **v7-Specific Indicators** (→ KEEP):
   - Mentions "on-premise", "hybrid", "mid-sourcing"
   - Coupons, MRM, Surveys, Distributed Marketing
   - SpamAssassin, nlserver configuration
   - Client Console specific features
   - Database schema/structure docs

3. **DELETE Criteria**:
   - Basic features (email, SMS, push creation)
   - Standard workflow activities (query, split, enrichment)
   - Common reports
   - Channel basics fully documented in v8

4. **MOVE Criteria**:
   - Troubleshooting tips not in v8
   - Best practices missing in v8
   - Advanced patterns useful for v8
   - Good examples/use cases

5. **REVIEW Criteria**:
   - Partial v8 coverage (50-70%)
   - Unclear if feature exists in v8
   - Complex mixed content

---

## IMPORTANT

- **Organize by category** (Get Started, Email, SMS, Push, etc.)
- **Include Experience League URLs** for v8 matches
- **Bold v7-specific files** that must be kept
- **Estimate match percentage** for each file
- **Provide clear reasoning** for each decision
- **Include effort estimates** for migrations

---

Generate the complete Markdown report now.
```

&#x200B;---

## 🎯 DEMO-INSTRUKTIONER

### Steg 1: Visa frågan1. Öppna filen (`DEMO-PROMPT-STANDALONE.md`)2. Bläddra till avsnittet&quot;FRÅGAN&quot;3. Säg: *&quot;Detta är vår automatiska analysfråga&quot;*

### Steg 2: Kopiera frågan1. Välj allt från # Campaign v7 Documentation Analysis till slutet2. Kopiera till Urklipp3. Säg: *&quot;Jag kopierar bara hela uppmaningen..&quot;*

### Steg 3: Klistra in och kör1. Öppna markör2. Klistra in uppmaningen3. Säg: *.. och klistra in den i markören*4. Träff

### Steg 4: Visa resultat1. Vänta på generering (~30-60 sekunder)2. Bläddra igenom den genererade rapporten3. Markera nyckelavsnitt:   - 📊 Sammanfattningsstatus   - 📋-tabell fil för fil   - ✅ måste spara avsnittet   - 🗑️ snabbvinner   - Körningsplan för 🎯

### Steg 5: Wow1. Visa förhandsgranskning av markering2. Peka ut:   - *&quot;111 filer har analyserats automatiskt&quot;*   - *&quot;67 filer kan tas bort (60 % minskning)&quot;*   - *&quot;18 v7-specifika filer identifierade&quot;*   - *&quot;Slutför körningsplanen med tidslinjer&quot;*

&#x200B;---

## 💡 DEMO-TIPS

### Gör det interaktivt&#x200B;**Fråga målgruppen**: *&quot;Vilken mapp ska vi analysera?&quot;*- leverans ✅ (111 filer - imponerande)- arbetsflöde ✅ (121 filer - ännu större)- webb ✅ (26 filer - snabbdemo)- rapporterar ✅ (32 filer - snabbt)

### Anpassa till flygresan&#x200B;**Visa flexibilitet**: Ändra mappsökvägen i frågan:

```
/help/workflow/using/  → Analyze workflows
/help/web/using/       → Analyze web apps
/help/platform/using/  → Analyze platform
```

### Markera nyckelfunktioner1. **Automatisering**: *&quot;Inget manuellt arbete krävs&quot;*2. **Noggrannhet**: *&quot;Använder v8-dokumentation för jämförelse&quot;*3. **Kan användas**: *&quot;Planen är klar att köras med kryssrutor&quot;*4. **Smart**: *&quot;Identifierar v7-specifika funktioner automatiskt&quot;*

### Tidsjämförelse&#x200B;**Före**: *&quot;Manuell analys = 2-3 dagar per mapp&quot;*\**Efter**: *&quot;Automatisk analys = 30 sekunder per mapp&quot;*

**ROI**: *&quot;21 mappar × 2 dagar = 42 dagar → 15 minuter&quot;*

&#x200B;---

## 📊 FÖRVÄNTADE FÖRHANDSVISNING AV UTDATA

```markdown
# 📊 v7 Delivery Analysis

**Total Files**: 111

## 📈 Summary
| Metric | Count | Percentage |
|--------|-------|------------|
| ✅ KEEP | 18 | 16% |
| 🗑️ DELETE | 67 | 60% |
| ➡️ MOVE | 8 | 7% |
| 🔍 REVIEW | 18 | 17% |

## 📋 File Analysis

### 📧 Email (18 files)
| # | v7 File | v8 Match | % | Action |
|---|---------|----------|---|--------|
| 1 | about-email-channel.md | campaign-web/v8/email | 95% | 🗑️ DELETE |
| 2 | creating-an-email-delivery.md | campaign-web/v8/email/create | 95% | 🗑️ DELETE |

### 📱 SMS (7 files)
| # | v7 File | v8 Match | % | Action |
|---|---------|----------|---|--------|
| 1 | sms-channel.md | campaign-web/v8/msg/send-sms | 90% | 🗑️ DELETE |
| 2 | **sms-set-up-mid.md** | NONE | 0% | ✅ **KEEP** |

[... continues for all categories ...]

## ✅ Must Keep (18 files)
- **personalized-coupons.md** - Coupons not in v8 FFDA
- **sms-set-up-mid.md** - Mid-sourcing (on-prem)
- **spamassassin.md** - On-prem spam filtering

## 🗑️ Quick Wins (67 files)
Email basics, SMS, Push, Direct mail → All in v8

## 🎯 Execution Plan
Week 1: Delete 67 files (60%)
Week 2: Badge 18 files
Week 3: Review 18 files
```

&#x200B;---

## 🎬 DEMO-SKRIPT

**Öppnar**:
> &quot;Idag ska jag visa hur vi automatiserade omorganiseringen av v7-dokumentationen med hjälp av AI. Det här brukade ta veckor, nu tar det några minuter.&quot;

**Problem**:
> &quot;Vi har över 1 500 dokumentationsfiler. Många dupliceras i v8. Vi måste identifiera vad vi ska behålla, ta bort eller migrera.&quot;

**Lösning**:
> &quot;Vi har skapat en smart prompt som analyserar alla mappar och genererar åtgärdbara rekommendationer.&quot;

**Demo**:
> &quot;Låt mig visa dig. Jag analyserar &#39;leveransmappen&#39; med 111 filer...&quot;
> 
> [Fråga, klistra in, kör]
> 
> &quot;... och om 30 sekunder får vi en komplett analys.&quot;

**Resultat**:
> &quot;Titta på det här:
> - 67 filer att ta bort (60 % minskning)
> - 18 v7-specifika filer har identifierats
> - 8 filer att migrera
> - Komplett 3-veckors exekveringsplan
> 
> Allt är automatiserat. Exakt.&quot;

**Stäng**:
> &quot;Samma process fungerar för alla 21 mappar. Det som brukade ta 6 veckor tar nu 15 minuter.&quot;

&#x200B;---

## 🚀 ÄR REDO FÖR DEMO!

**Bara**:
1. Öppna filen
2. Kopiera frågan
3. Klistra in i markören
4. Visa magin ✨

**Total demotid**: 3-5 minuter\
**Wow!**: 🔥🔥🔥

