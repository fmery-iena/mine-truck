# 🚗 Pickup Minecraft — Prairie Meuh Meuh

Un jeu 3D style Minecraft, en HTML + JavaScript avec Three.js, fait pour un enfant de 9 ans.
La voiture roule sur un vrai **circuit fermé avec des virages**, inspiré de la Prairie Meuh Meuh de Mario Kart Wii !

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

## 🏁 Le jeu

- Le circuit est une **boucle fermée** : grandes courbes, virages en S, retour en épingle douce.
- **Ligne de départ/arrivée en damier** : chaque passage = un tour de plus (compteur en haut).
- **Diamants 💎** flottent au-dessus de la piste : touche-les pour les ramasser et monter le score.
- Si tu sors de la piste, l'herbe **ralentit** le pickup — reviens sur l'asphalte !
- Décor de prairie : **vaches 🐄**, arbres et maisons tout autour de la piste.

## 🛠️ Modifier le jeu

Tout le code est dans `index.html`, découpé en sections commentées :

1. Scène, caméra, lumières
2. Le circuit (la boucle fermée + la ligne de damier)
3. Le décor (arbres, maisons, vaches)
4. La voiture (pickup + creeper en armure d'or)
5. La conduite (position, cap, sortie de piste)
6. Les diamants et le compteur de tours
7. Le klaxon canard

### Créer un nouveau circuit 🗺️

Le tracé est défini par la liste `POINTS_CIRCUIT` (des points `[x, z]` reliés
en douceur). Change ces points et le circuit change ! Astuce : garde une
bonne distance entre les points de passages opposés (au moins 25 blocs,
la piste fait 10 blocs de large).

Chaque section est marquée par `/* ---------- N. ... ---------- */` dans le fichier.
