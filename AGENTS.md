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
- `mario-peach-v4.css` : thème versionné. Renommer à chaque changement visuel (ex: `mario-peach-v5.css`) pour forcer le cache Safari. Les fonds dégradés sont calculés en JS (`THEMES` start→end, étalés sur N cases) : ajouter des missions ne touche ni le CSS ni le JS.
- `missions.json` : objet `{peach: [...], mario: [...]}` avec les missions `{id, label, emoji}` (fallback en dur dans le JS si fetch échoue).

## Contraintes iPad mini 4 (importantes)
- Rester compatible Safari iOS 15 : JS simple (pas de modules ES, optional chaining, etc. sauf si c'est le test visé).
- Garder les meta iOS : `viewport-fit=cover`, `apple-mobile-web-app-capable`, `apple-mobile-web-app-status-bar-style`.
- Tactile first : grosses zones de toucher, pas de hover-only.
- Tester en conditions réelles : ajout à l'écran d'accueil + mode plein écran.

## Conventions de travail
- Modifier `index.html` directement, garder le fichier petit et lisible.
- Reset global par créneau : `resetIfNewSlot()` / `clearAll()` (`index.html`) efface tout (missions, timers, pauses) à chaque ouverture dans une nouvelle tranche — matin 4h-11h, midi 11h-16h, soir 16h-4h (journée logique, fixé sur 11h pour les petits déj tardifs). Clé `mario-peach-v1-slot`.
- Minuteur par joueur (topbar) : durée réglable via `TIMER_MS` dans `index.html` ; clés sous `mario-peach-v1-timer-*`, effacées par le reset de créneau.
- Pause par joueur (bouton danger sur la carte Toilettes/Bain) : overlay limité à la colonne du joueur, minuteur figé via `pausedAt` (clé `mario-peach-v1-pause-*`), reprise en décalant la date de fin.
- Un test = un commit clair (ex: `test: flex gap sur iOS 15`).
- Ne pas ajouter de tooling/build sans demande explicite.
- Langue UI : français.
