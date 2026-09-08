# AGENTS.md — missions-soir

## But du projet
App **« Missions du soir »** pour enfants sur **iPad mini 4** (Safari ancien, max iPadOS 15.x).
Deux colonnes coopératives (👑 Peach / 🍄 Mario), cases missions cochables au doigt, étoile débloquée seulement si les 2 colonnes sont pleines.
Déployé sur **GitHub Pages**.

## Stack
- HTML/CSS/JS statique uniquement, sans build, sans dépendance, sans framework.
- Déploiement : push sur `main` → GitHub Pages (repo `gfahrni/missions-soir`).

## Structure
- `index.html` : layout 2 colonnes + logique (JS simple, tout inline).
- `mario-peach-v1.css` : thème versionné (rose Peach / rouge Mario). Renommer à chaque changement visuel (ex: `mario-peach-v2.css`) pour forcer le cache Safari.
- `missions.json` : liste des missions `{id, label, emoji}` (fallback en dur dans le JS si fetch échoue).

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
