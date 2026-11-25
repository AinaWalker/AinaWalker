# Spécifications — Giretra (Belote malgache)

Ce dossier est la **source de vérité** du projet (Spec-Driven Development).

## Méthode : SDD + TDD

1. **Spec** — chaque règle est écrite ici avec un identifiant stable (`R-DEAL-02`, `R-SCORE-05`…).
   Aucun code n'est écrit pour une règle qui n'existe pas dans la spec.
2. **Exemples** — chaque règle importante a des exemples concrets (`EX-…`) au format
   *Étant donné / Quand / Alors*, validés par l'expert du jeu.
3. **Tests (rouge)** — chaque exemple devient un test automatisé qui cite l'ID de la règle
   et échoue d'abord.
4. **Code (vert)** — le minimum de code pour faire passer le test, puis refactor.
5. **Questions ouvertes** — toute ambiguïté va dans [`open-questions.md`](open-questions.md).
   Une règle marquée ⚠️ dépend d'une question non tranchée : on n'écrit pas son test avant la réponse.

## Fichiers

| Fichier | Rôle |
|---|---|
| [`giretra-rules.md`](giretra-rules.md) | Règles du jeu numérotées + exemples (spec du moteur) |
| [`open-questions.md`](open-questions.md) | Ambiguïtés à trancher, avec proposition par défaut |
| [`source/giretra-regles-synthese.md`](source/giretra-regles-synthese.md) | Synthèse d'origine (giretra.com/fr/learn) |

## Statut

| Version | Statut |
|---|---|
| v0.1 | Brouillon — en attente de relecture et réponses aux questions ouvertes |
