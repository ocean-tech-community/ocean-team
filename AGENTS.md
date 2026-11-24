# AGENTS.md

## Contexte

Ocean Team est une application en démarrage pour gérer les profils de la communauté Ocean Tech. Les champs des profils, les rôles et les parcours restent à définir. Pour chaque tâche, partir du comportement demandé et rendre explicite toute hypothèse métier qui affecte le résultat.

## Se repérer dans le dépôt

- Vérifier la stack et les scripts du périmètre modifié dans son `package.json` et ses fichiers de configuration. Suivre les conventions du framework installé et de sa version.
- Le projet à la racine utilise NestJS 12, TypeScript strict et les modules ESM. Dans ce périmètre, les imports relatifs TypeScript utilisent l’extension `.js`.
- `src/main.ts` démarre l’application et `src/app.module.ts` assemble ses modules. Les tests unitaires Vitest sont à côté du code. Les tests HTTP Vitest et Supertest sont dans `test/`.
- Suivre les instructions locales et les exemples pertinents du dépôt. Pour une convention de framework sans exemple local, consulter la documentation de la version installée.

## Faire évoluer le code

- Livrer un petit incrément qui fonctionne par son point d’entrée normal. Réutiliser le code existant et ajouter les abstractions quand un besoin concret le justifie.
- Dans NestJS, garder les contrôleurs centrés sur HTTP. Placer le comportement métier dans du code testable indépendamment du transport lorsque ce comportement apparaît. Regrouper le code qui change ensemble.
- Faire les choix locaux et réversibles au fil de l’implémentation. Si la tâche demande une décision structurante, comme le choix d’une base de données, d’un mécanisme d’authentification ou d’un découpage en applications, présenter la décision et son impact à l’équipe avant de l’inscrire dans le code.
- Pour les fonctionnalités de profil, valider les entrées à la frontière, appliquer côté serveur les droits définis pour le parcours et exposer explicitement les champs retournés. Utiliser des données fictives dans les exemples et tests. Garder les secrets hors du dépôt.

## Vérifier et contribuer

- Utiliser npm 11 ou plus et une version de Node compatible avec le lockfile. Sur la branche Node 22, les dépendances verrouillées exigent au moins la 22.22.3.
- Installer les dépendances avec `npm ci` et démarrer en local avec `npm run start:dev`.
- Pour une modification de code, lancer `npm run build`, `npm run lint` et `npm test`. Lancer `npm run test:e2e` quand le parcours HTTP ou son assemblage change. Pour un changement de comportement, couvrir le cas utile au niveau de test le plus simple.
- Utiliser `npm run format` pour le formatage du code. Dans la PR, indiquer les vérifications exécutées et les éventuels blocages.
- Rédiger la documentation, les issues et les PR en français. Utiliser l’anglais pour les noms dans le code et les fichiers source.
- Créer des branches ciblées depuis `main` avec un préfixe `feat/`, `fix/`, `docs/` ou `chore/`. Suivre Conventional Commits et expliquer dans la PR pourquoi le changement est nécessaire et comment le vérifier.
