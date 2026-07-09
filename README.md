# 🎡 Roue d'événement — BeamNG.drive

Un outil web autonome (single-file) pour organiser des tirages au sort équitables lors d'événements communautaires : distribution de rôles, sélection de mods à tester, tirage de cartes, choix de participants, etc.

Conçu à l'origine pour la communauté **BeamNG.drive**, mais utilisable pour n'importe quel event Discord ou communautaire.

**[→ Ouvrir la démo](https://rpm-wheel.pages.dev/)**

---

## ✨ Fonctionnalités

- **100% client-side** — tout le calcul du tirage se fait dans le navigateur, aucune donnée n'est envoyée à un serveur
- **Tirage vérifiable** — utilise `Math.random()` natif du navigateur, probabilité strictement égale entre toutes les options
- **Personnalisation complète** : titre, auteur, date/heure, lien Discord, bannière, description/règles
- **Options illimitées** : pseudos, mods, cartes, règles — une option par ligne
- **Mode "retrait après tirage"** pour ne jamais retirer deux fois la même personne
- **Partage par lien** : toute la configuration est encodée en Base64 dans l'URL (`#d=...`), aucune base de données nécessaire
- **Mode présentation** : masque le panneau de configuration pour un affichage propre pendant l'event (stream, projection, etc.)
- **Panneau "Comment ça marche"** intégré, pour que les participants puissent vérifier eux-mêmes l'équité du tirage

---

## 🚀 Utilisation

### Option 1 — En local
Télécharge `beamng-wheel.html` et ouvre-le directement dans ton navigateur. Aucune installation, aucune dépendance.

### Option 2 — Hébergement statique (recommandé pour un event)
Ce fichier est un site statique à part entière. Tu peux le déployer gratuitement sur :

- **GitHub Pages** (Settings → Pages → déployer depuis la branche `main`)
- **Cloudflare Pages**
- **Netlify** / **Vercel** (glisser-déposer le fichier suffit)

### Générer un lien de tirage pour ton event
1. Ouvre le fichier (ou le site déployé)
2. Remplis le panneau de configuration à droite : titre, options, réglages
3. Clique sur **« Générer le lien »**
4. Partage ce lien dans ton Discord — il s'ouvre directement en mode présentation, roue prête à tourner

---

## 🔍 Équité du tirage — comment ça marche

Le tirage repose sur `Math.random()`, le générateur pseudo-aléatoire natif de JavaScript :

```js
const randomOffset = Math.random() * 360;   // angle aléatoire uniforme (0–360°)
rotation += extraTurns * 360 + randomOffset; // tours complets (visuel) + angle réel
```

L'angle final détermine directement la part gagnante — il n'existe **aucune pondération cachée**, aucun calcul serveur, aucune logique qui favorise une option plutôt qu'une autre. Le code entier est visible dans le fichier HTML : n'importe qui peut l'auditer via *Afficher le code source* ou les DevTools (`F12`).

> **Pourquoi c'est important** : un outil de tirage utilisé publiquement (Discord, stream, event) devrait toujours être vérifiable par ceux qui y participent. C'est le principe appliqué ici — pas de boîte noire, pas de serveur intermédiaire.

---

## 🛠️ Stack technique

- HTML / CSS / JavaScript vanilla — **aucune dépendance externe**
- Polices : [Rajdhani](https://fonts.google.com/specimen/Rajdhani), [Inter](https://fonts.google.com/specimen/Inter), [JetBrains Mono](https://fonts.google.com/specimen/JetBrains+Mono) (Google Fonts)
- Un seul fichier `.html` autonome, facilement modifiable ou intégrable ailleurs

---

## 📁 Structure du dépôt

```
.
├── beamng-wheel.html   # L'application complète (single-file)
└── README.md
```

---

## 🤝 Contribuer

Les PR et suggestions sont bienvenues, en particulier pour :
- de nouveaux thèmes visuels
- l'ajout d'animations sonores
- l'export/import de configurations en JSON
- l'accessibilité (navigation clavier, lecteurs d'écran)

---

## 📜 Licence

*(à définir — ex. MIT, si tu veux que le projet soit librement réutilisable et modifiable)*

---

## 🎮 À propos

Outil communautaire non officiel, sans lien avec BeamNG GmbH. Créé pour faciliter l'organisation de tirages au sort lors d'events BeamNG.drive et autres communautés de jeu.
