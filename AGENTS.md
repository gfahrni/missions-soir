# AGENTS.md — hello-ghpages

## But du projet
Tester la compatibilité des webapps sur **iPad mini 4** (Safari ancien, max iPadOS 15.x).
Ce repo est un bac à sable minimal déployé sur **GitHub Pages**.

## Stack
- HTML/CSS/JS statique uniquement, dans `index.html`.
- Aucun build, aucune dépendance, aucun framework.
- Déploiement : push sur `main` → GitHub Pages (repo `gfahrni/hello-ghpages`).

## Structure
- `index.html` : seul fichier applicatif (page centrée, bouton JS inline).

## Contraintes iPad mini 4 (importantes)
- Rester compatible Safari iOS 15 : JS simple (pas de modules ES, optional chaining, etc. sauf si c'est le test visé).
- Garder les meta iOS : `viewport-fit=cover`, `apple-mobile-web-app-capable`, `apple-mobile-web-app-status-bar-style`.
- Tactile first : grosses zones de toucher, pas de hover-only.
- Tester en conditions réelles : ajout à l'écran d'accueil + mode plein écran.

## Conventions de travail
- Modifier `index.html` directement, garder le fichier petit et lisible.
- Un test = un commit clair (ex: `test: flex gap sur iOS 15`).
- Ne pas ajouter de tooling/build sans demande explicite.
- Langue UI : français.
