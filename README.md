# 🚗 Pickup Minecraft — Prairie Meuh Meuh

Un jeu 3D style Minecraft, en HTML + JavaScript avec Three.js, fait pour un enfant de 9 ans.
La voiture gravit un **volcan** : montée à flanc, demi-tour au sommet autour du cratère, redescente, demi-tour en bas — toujours en avançant !

## 🎮 Jouer

Ouvre simplement le fichier `index.html` dans un navigateur.
Three.js est chargé via CDN : il faut juste une connexion internet.

## 🕹️ Commandes

| Touche | Action |
|--------|--------|
| ⬆️ | Avancer |
| ⬇️ | Freiner / reculer |
| ⬅️ ➡️ | Tourner (vrai virage : la voiture change de direction) |
| Espace | Klaxon (canard) 🦆 |

## 🌋 Le jeu

- Le circuit est une **route en épingle au-dessus d'un volcan** : montée à flanc (voie ouest), **demi-tour au sommet** autour du cratère de lave, redescente (voie est), **demi-tour en bas** pour repartir.
- **Ligne de départ/arrivée en damier** : chaque passage = un tour de plus (compteur en haut).
- Si tu sors de la piste, l'herbe **ralentit** le pickup — reviens sur l'asphalte !
- Décor : **vaches 🐄**, arbres et maisons dans la prairie, ferme en bas du volcan.

## 🚗 Showroom Peugeot 408 (`peugeot.html`)

Ouvre `peugeot.html` dans un navigateur (ou en ligne via GitHub Pages :
`https://fmery-iena.github.io/mine-truck/peugeot.html`) : une **Peugeot 408 2025 Allure Pack noire**,
modélisée en 3D détaillée (Three.js), pivote lentement sur elle-même façon Gran Turismo,
sur fond noir avec éclairage zénithal et sol miroir.
- **Souris** : glisser = pivoter, molette = zoomer
- **Tactile** : un doigt = pivoter, pincement = zoomer

## 🛠️ Modifier le jeu

Tout le code est dans `index.html`, découpé en sections commentées :

1. Scène, caméra, lumières
2. Le circuit (la boucle fermée + la ligne de damier)
3. Le décor (arbres, maisons, vaches)
4. La voiture (pickup + creeper en armure d'or)
5. La conduite (position, cap, sortie de piste)
6. Le compteur de tours et le chrono
7. Le klaxon canard

### Créer un nouveau circuit 🗺️

Le tracé est défini par la liste `POINTS_CIRCUIT` (des points `[x, z, h]` reliés
en douceur, `h` = hauteur). Change ces points et le circuit change ! Astuce :
garde une bonne distance entre les tronçons qui se longent (au moins 30 blocs
avec une route de 20 de large), sinon la détection de la piste peut confondre
les deux voies.

`CONFIG.largeurRoute` (20 par défaut) règle la largeur de la route :
accotements, lignes blanches, poteaux et ligne de damier suivent
automatiquement (tout est calculé à partir de cette valeur).

Chaque section est marquée par `/* ---------- N. ... ---------- */` dans le fichier.
