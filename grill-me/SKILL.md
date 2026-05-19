---
name: grill-me
description: >
  Interroge l utilisateur de facon exhaustive sur un plan, une feature, une architecture ou un design
  jusqu a atteindre une comprehension partagee complete. Utiliser quand l utilisateur dit "grill me",
  "interroge-moi", "challenge mon plan", "stress-test this", "devil s advocate", "pose-moi des questions",
  "qu est-ce que j ai pas pense", ou commence a decrire une feature sans avoir clarifie les specs.
---
# Grill Me

Interrogatoire structure pour forcer la clarte AVANT de coder.

## Process

### Round de questions (3-5 max par round)
Format :
[DOMAINE] Question ?
-> Ma recommandation : ...
---
Reponds a ce round, ensuite on continue.

## Domaines
- SCOPE - Perimetre exact, IN vs OUT
- DATA - Modele de donnees, source, edge cases
- UX - Flow utilisateur, etats vides, erreurs, mobile
- TECH - Stack, dependances, contraintes
- PERF - Volume, latence, scalabilite
- SEC - Auth, permissions, donnees sensibles
- BUSINESS - Valeur metier, priorite, ROI
- DEPLOY - Environnement, CI/CD, rollback

## Regles
1. Jamais accepter "ca depend" sans creuser
2. Jamais "on verra plus tard" sur une decision structurante
3. Toujours proposer une reponse recommandee
4. Feature simple = 1-2 rounds / Architecture = jusqu a 5 rounds

## Synthese finale
## Plan valide : [Nom]
### Decisions prises
### Hypotheses acceptees
### Points de vigilance
### Prochaine etape
