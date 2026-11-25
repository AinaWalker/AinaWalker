# ADR 0001 — Stack : Flutter + moteur Dart pur

- **Statut** : accepté
- **Date** : 2026-11-25

## Contexte

- Application mobile de Giretra (belote malgache), **Android en priorité**, iOS possible plus tard.
- Interface **bilingue français / malgache**.
- Méthode **SDD + TDD** : le moteur de règles doit être testable rapidement, sans interface.
- Cible probable : téléphones Android d'entrée de gamme.

## Options comparées

| Critère | Flutter (Dart) | React Native + Expo (TS) | Kotlin Multiplatform |
|---|---|---|---|
| Android + iOS, un seul code | ✅ | ✅ | ⚠️ UI iOS séparée ou Compose MP |
| Animations de cartes | ✅ moteur de rendu propre | ✅ avec Reanimated | ✅ Compose |
| TDD du moteur | ✅ `dart test`, package pur | ✅ Vitest / Jest | ✅ tests JVM |
| Téléphones modestes | ✅ (APK ~15-20 Mo) | ⚠️ selon les librairies | ✅ le plus léger |
| Malgache (`mg`) | ⚠️ pas dans les localisations intégrées → délégué de repli sur `fr` | ✅ i18next | ✅ ressources Android |
| Serveur multijoueur futur | ✅ Dart partagé | ✅ Node partagé | ✅ Ktor partagé |

## Décision

**Flutter**, avec le moteur de règles dans un **package Dart pur** (`packages/engine`), sans dépendance
à Flutter.

## Conséquences

- Le moteur est entièrement testé en TDD avec `dart test`, indépendamment de l'UI.
- Le même moteur pourra tourner côté serveur (multijoueur) sans réécriture.
- Il faut un `LocalizationsDelegate` qui replie sur `fr` pour les widgets Material quand la langue est `mg`.
- Les textes de l'app passent par des fichiers ARB (`app_fr.arb`, `app_mg.arb`).

## Structure prévue

```
specs/            # spec du jeu (source de vérité)
packages/engine/  # moteur Dart pur + tests
app/              # application Flutter (Android d'abord, iOS prêt)
docs/adr/         # décisions d'architecture
```
