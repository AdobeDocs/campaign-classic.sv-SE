---
source-git-commit: 65d223acd23f26bd9c6979d11815d23f02ae2382
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---
# 📚 v7 Documentation Reorganiation Kit

**2 prompts pour analyser et réorganizer la doc v7 → v8**

---

## 📁 Fichiers

### 🔍 frågor (instruktioner)

| Fichier | Beskrivning | Utdata |
|---------|-------------|--------|
| `PROMPT-1-OVERVIEW-ALL-FOLDERS.md` | Vue d&#39;ensemble de TOUS les folders v7 | `v7-reorganization-overview.md` |
| `PROMPT-2-DETAILED-FOLDER.md` | Analysera détaillée d&#39;UN folder avec % match | `[folder]-detailed-analysis.md` |

---

## 🚀-användning

### 1️⃣ Vue d&#39;Ensemble (tous les folders)

```bash
# 1. Ouvrir le prompt
open PROMPT-1-OVERVIEW-ALL-FOLDERS.md

# 2. Copier tout le contenu du bloc "COPIER CE PROMPT"
# 3. Coller dans Cursor/ChatGPT
# 4. Obtenir : v7-reorganization-overview.md
```

**Génère** :
- 📊 Sammanfattning (global statistik)
- 📁 Analysera 21 mappar
- 🎯 Matrisprioritet
- ✅ åtgärdsobjekt
- ⚠️ risques
- 📈 Métriques

**Taille** : ~50-60 pages Markdown

---

### 2️⃣ Analyze Détaillée d&#39;un Folder

```bash
# 1. Ouvrir le prompt
open PROMPT-2-DETAILED-FOLDER.md

# 2. Modifier la ligne :
📁 **Analyze**: /Users/.../help/delivery/using/

# 3. Remplacer par le folder souhaité :
# - /help/delivery/using/
# - /help/workflow/using/
# - /help/web/using/
# - etc.

# 4. Copier tout le contenu du bloc "COPIER CE PROMPT"
# 5. Coller dans Cursor/ChatGPT
# 6. Obtenir : [folder]-detailed-analysis.md
```

**Génère** :
- 📊 Stats du folder
- 📋 Tableau détaillé organisé komma Experience League
- 🔗 linjerar klientfiler (v7 + Experience League)
- 📈 Jusqu&#39;à 3 matchs v8 par fichier avec %
- 📄 Mappa om fil par-fil
- 🎯 Plan de réorganization
- ✅ Kryssrutor för lastspårning

**Taille** : ~30-40 pages Markdown

---

## 📊 undantagna d&#39;Output

### Fråga 1 (översikt)

```markdown
# 📊 v7 Documentation Reorganization Overview

**Total Files**: 1,500
**KEEP**: 400 (27%)
**DELETE**: 800 (53%)
**MOVE**: 200 (13%)
**REVIEW**: 100 (7%)

## 📁 Folder Analysis

### 🟢 100% KEEP - v7-Only Content
| Folder | Files | Reason |
|--------|-------|--------|
| /installation/ | 75 | On-premise setup |
| /mrm/ | 5 | Not in v8 FFDA |
...
```

### Fråga 2 (detaljerad mapp)

```markdown
# 📊 v7 Folder Analysis: Delivery

**Total Files**: 111

| # | v7 File | v8 Match 1 | % | v8 Match 2 | % | Notes | Action |
|---|---------|------------|---|------------|---|-------|--------|
| 1 | about-email-channel.md | campaign-web/v8/email | 95% | - | - | Fully in v8 | 🗑️ DELETE |
| 9 | sms-set-up-mid.md | NONE | 0% | - | - | Mid-sourcing (on-prem) | ✅ KEEP |
...
```

---

## 🎯 arbetsflödesrekommendation

### Semaine 1: Vue d&#39;ensemble
1. Exécuter **Fråga 1** → Obtenir `v7-reorganization-overview.md`
2. Identifieraren anger mappprioritet
3. Partager avec-intressenter

### Semaine 2-4: Analyze détaillée
1. Prioritet för Pour Chque-mappen:
   - Exécuter **Fråga 2**
   - Objekt `[folder]-detailed-analysis.md`
   - Valider les décisions
   - Funktioner för Commencer les

### Semain 5+: Exektion
1. Supprimer les fichiers identifiés (DELETE)
2. Badger les fichiers v7-only (KEEP)
3. Migrer le contenu manquant (MOVE)
4. Reviewer les cas ambigus (REVIEW)

---

## 💡 tips

### Pour les prompts
- ✅ Copier/coller l&#39;intégralité du prompt
- ✅ Nytt format för punktmodifierare
- ✅ Adapter seulement le chemin du folder (Prompt 2)

### Pour les outputs
- 📝 Utdata en Markdown (pas HTML)
- 🔗 avlyssnar urklippsautomatik
- ✅ Kryssrutor för lastspårning
- 📊 statistik och procenttal
- 🎨 Emojis et icônes

### Pour l&#39;analyze
- 🎯 Commencer par les grupperar mappar (leverans, arbetsflöde)
- ⚡ Prioriseraren får mindre snabbvinster (95-100 % matchning)
- 🔍 Reviewer Manual les cas ambigus (&lt;70% match)
- ✅ Valider avec SME avant suppression massiv

---

## ⚠️ viktigt

### Avant de supprimer
1. ✅ Vérifier l&#39;équivalent v8
2. ✅ Vérifier qu&#39;il n&#39;y a pas de content v7-specific
3. ✅ Mettre à jour `redirects.csv`
4. ✅ Valider avec un expert (pour les premiers)

### Pour les fichiers v7 only
1. ✅ Ajouter un badge au début du fichier
2. ✅ Expliquer pourquoi c&#39;est v7 only
3. ✅ Linjen innehåller mindre begränsningar v8

---

## 🆘 support

**Frågor** ?
- Prompt ne fonctionne pas → Vérifier les chemins des repos
- Utdatatruppen är lång → Demander un résumé
- Besoin d&#39;aide → Ping l&#39;équipe doc

---

**Dernière mise à jour** : 2026-01-13

