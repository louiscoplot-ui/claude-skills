---
name: bot-analyzer
description: >
  Analyse complete d un bot, scraper, ou script Python uploade. Orchestre automatiquement tous
  les skills disponibles pour produire un rapport consolide avec fixes prioritises et prompts
  Claude Code prets a coller. Utiliser quand l utilisateur uploade un bot/scraper et dit
  "analyse ce bot", "qu est-ce qui ne va pas", "ameliore ce scraper", "repare ce bot",
  "audit ce script", "optimise ce code", ou uploade un fichier .py sans autre instruction.
  Couvre : bugs, securite, performance, longevite anti-strike, edge cases, architecture.
---

# Bot Analyzer

Analyse orchestree d un bot ou scraper. Lit le code complet puis passe en revue
chaque dimension dans l ordre de priorite.

## Processus

### Etape 1 : Cartographie
- But du bot, stack, architecture, inputs/outputs

### Etape 2 : Analyse par couche

CRITIQUE (code-reviewer + security-auditor)
- Secrets hardcodes, crash silencieux, logique incorrecte, None non gere

PERFORMANCE (bot-performance)
- Sync au lieu d async, pas de cache, N+1 requests, tout en RAM

LONGEVITE (scraper-longevity)
- UA fixe, pas de delai, pas de rotation, pas de gestion 429/403

ROBUSTESSE (debug-systematically)
- Pas de checkpoint, pas de retry, selecteurs fragiles, pagination cassee

ARCHITECTURE (code-reviewer)
- Monolithique, config hardcodee, nommage obscur

### Etape 3 : Rapport

## Analyse Bot : [nom]
### Ce que fait ce bot
### Score: Securite X/10 | Perf X/10 | Longevite X/10 | Robustesse X/10

CRITIQUE - A fixer MAINTENANT
[probleme] Ligne: N | Fix: [code]

PERFORMANCE - Gains rapides
[probleme] Impact: Xx plus lent | Fix: [code]

LONGEVITE - Strike dans [estimation]
[probleme] Risque: N requetes | Fix: [code]

ROBUSTESSE - Va crasher dans ces cas
[cas] Quand: [condition] | Fix: [code]

ARCHITECTURE - Prochaine version
[amelioration] Pourquoi: [benefice]

### Prompts Claude Code prets a coller
Prompt 1 - Fix critique (30min): [prompt complet]
Prompt 2 - Performance (1h): [prompt complet]
Prompt 3 - Longevite (1h): [prompt complet]

### Estimation: Critiques Xh | Perf Xh | Longevite Xh

## Regles
1. Lire 100% du code avant de commenter
2. Citer le numero de ligne
3. Toujours fournir le fix
4. Estimer l impact reel ("striker en 50 requetes" pas "risque de rate limit")
5. Prompts Claude Code complets et copiables sans modification

## Contexte Louis
REIWA/CoreLogic: priorite longevite, checkpoint obligatoire, output Excel openpyxl
SuburbDesk: coherence Flask backend, output SQLite compatible
