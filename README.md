# 🚜 Pickup Minecraft — Prairie Meuh Meuh & Prairie des Cloches

Deux versions d'un jeu 3D style Minecraft, en HTML + JavaScript avec Three.js, faites pour un enfant de 9 ans.

## 🌾 Prairie des Cloches (nouveau) — `prairie.html`

Nouvelle version selon le cahier des charges « Prairie des Cloches » : un circuit **100 % voxel** (uniquement des cubes axis-alignés ; seule exception autorisée : les ailes tournantes du moulin).

- **Circuit fermé ~1000 m** en dalles de terre ocres (3 teintes, ornières en filets discontinus) : 8 sections, virages, montées en marches de 0,25 m, largeur variable par section.
- **Prairie 220×220 m** en blocs d'herbe + brins en colonnes de cubes ; l'herbe ralentit le kart (plafond 13,4 m/s contre 32 m/s sur la terre).
- **Clôtures en poteaux/lisses cubes** : contact = ralentissement + repousse, jamais bloquant.
- **8 vaches en cubes** (corps, tête, cloche...) : au tour 1 elles paissent sur l'herbe ; aux tours 2-3 elles traversent la piste. Choc sur la terre = toupie 180°, sur l'herbe = simple poussée.
- **4 galeries** : tas de cubes puis tête qui surgit (cycle 6,3 s) — les effets n'existent que quand les cubes sont visibles.
- **Rampe bleue** en 9 marches (saut + boost ×1,35 à l'atterrissage) et **rampe orange** sur la colline H1 (boost ×1,8).
- **Décor** : ferme, silo carré crénelé, grange, chariot à lait, moulin, rivière + pont, 26 arbres, bottes de foin, panneau « PRAIRIE », bannière au-dessus de la ligne de départ.
- **3 tours** comptés à la ligne de départ (sens +Z, anti-rebond 2 s), chrono, écran de fin. Touche **R** = retour au centre de la piste.

## 🎮 Prairie Meuh Meuh (version originale) — `index.html`

La voiture roule sur un vrai **circuit fermé avec des virages**, inspiré de la Prairie Meuh Meuh de Mario Kart Wii !

## ▶️ Jouer

Ouvre simplement le fichier `index.html` (ou `prairie.html` pour la version Prairie des Cloches) dans un navigateur.
Three.js est chargé via CDN : il faut juste une connexion internet.

## ⌨️ Commandes

| Touche | Action |
|--------|--------|
| ⬆️ | Avancer |
| ⬇️ | Freiner / reculer |
| ⬅️ ➡️ | Tourner (vrai virage : la voiture change de direction) |
| Espace | Klaxon (canard) 🦆 (`index.html` uniquement) |
| R | Retour au centre de la piste le plus proche (`prairie.html`) |

## 🏁 Le jeu (`index.html`)

- Le circuit est une **boucle fermée** : grandes courbes, virages en S, retour en épingle douce.
- **Ligne de départ/arrivée en damier** : chaque passage = un tour de plus (compteur en haut).
- Si tu sors de la piste, l'herbe **ralentit** le pickup — reviens sur l'asphalte !
- Décor de prairie : **vaches 🐄**, arbres et maisons tout autour de la piste.

## 🛠️ Modifier le jeu

`index.html` : tout le code est dans un seul fichier, découpé en sections commentées :

1. Scène, caméra, lumières
2. Le circuit (la boucle fermée + la ligne de damier)
3. Le décor (arbres, maisons, vaches)
4. La voiture (pickup + creeper en armure d'or)
5. La conduite (position, cap, sortie de piste)
6. Le compteur de tours et le chrono
7. Le klaxon canard

`prairie.html` : même principe, sections numérotées 1 à 11 (configuration physique, outil voxel
`V()` + InstancedMesh, points de contrôle du circuit, sol, clôtures, décor, acteurs, voiture,
conduite, boucle de jeu). Pour changer le tracé de la Prairie des Cloches, édite les listes
`POINTS` et `LARGEURS` en section 4.

### Créer un nouveau circuit 🗺️ (`index.html`)

Le tracé est défini par la liste `POINTS_CIRCUIT` (des points `[x, z]` reliés
en douceur). Change ces points et le circuit change ! Astuce : garde une
bonne distance entre les points de passages opposés (au moins 25 blocs,
la piste fait 10 blocs de large). `ECHELLE_CIRCUIT` (2 par défaut)
agrandit tout le tracé proportionnellement.

`CONFIG.largeurRoute` (20 par défaut) règle la largeur de la route :
accotements, lignes blanches, poteaux et ligne de damier suivent
automatiquement (tout est calculé à partir de cette valeur).

Chaque section est marquée par `/* ---------- N. ... ---------- */` dans le fichier.
