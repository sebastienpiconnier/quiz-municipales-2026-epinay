# Quiz de compatibilité LIPE : Municipales 2026 à Épinay-sur-Orge

![Aperçu du quiz](og-image.png)

Quiz web interactif réalisé pendant la campagne des élections municipales des 15 et 22 mars 2026 à Épinay-sur-Orge (Essonne), pour la liste **LIPE (Libres et Indépendants pour Épinay)** menée par Arnaud Collot.

Le principe : répondre à 12 questions tirées au sort parmi 25 pour mesurer la proximité de ses priorités avec le programme LIPE, puis découvrir son « profil citoyen ».

> Projet archivé : la campagne est terminée, ce dépôt conserve le code tel qu'il a été mis en ligne sur `quizz.arnaudcollot.com`.

## Fonctionnalités

- **Banque de 25 questions** réparties sur 14 thèmes (sécurité, urbanisme, finances, écoles, jeunesse, solidarité, santé, cadre de vie, démocratie locale, commerce, mobilité, sport et culture, petite enfance, inclusion).
- **Tirage équilibré** : une question piochée dans chaque thème, puis mélange et sélection de 12 questions.
- **Trois types de questions** : choix unique, choix multiple et curseur (slider).
- **Retour immédiat** après chaque réponse, avec mise en évidence de la position LIPE et un encart « Ce que LIPE fera ».
- **Score global de 0 à 100 %** (moyenne des scores par question, chacun borné entre 0 et 1) et détail par thème.
- **6 profils citoyens** selon le score obtenu.
- **Partage** : Facebook (message pré-rédigé copié dans le presse-papier), X, WhatsApp et e-mail.
- **Mise en avant de la réunion publique** du 11 mars 2026.
- Optimisé mobile, installable comme web app sur iOS, balises Open Graph / Twitter Card et données structurées Schema.org.

## Stack technique

Un seul fichier `index.html` autonome : HTML, CSS et JavaScript natifs, sans framework ni étape de build. Seules dépendances externes : Google Fonts (Syne, DM Sans) et Google Analytics.

## Structure

```
.
├── index.html             # Quiz complet (contenu, styles, logique)
├── og-image.png           # Image de partage réseaux sociaux (1200×630)
├── apple-touch-icon.png   # Icône web app iOS
└── README.md
```

## Lancer en local

Ouvrir `index.html` dans un navigateur, ou servir le dossier :

```bash
python3 -m http.server 8000
# puis http://localhost:8000
```

## Logique de scoring

| Type de question | Calcul du score (0 à 1) |
|---|---|
| Choix unique | score attribué à la réponse choisie |
| Choix multiple | moyenne des scores des réponses cochées |
| Curseur | `1 - écart / (amplitude / 2)`, borné ; option `nopenalty` pour ne pas pénaliser un dépassement de l'objectif |

Le pourcentage final est la moyenne arithmétique des 12 scores, arrondie à l'entier.

## Crédits

- Conception et développement : Sébastien Piconnier
- Contenu programmatique : liste LIPE, Épinay-sur-Orge
