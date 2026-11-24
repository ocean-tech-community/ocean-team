# AGENTS.md

## Projet

Ocean Team est l’application de la communauté Ocean Tech, qui rassemble des profils tech et produit au Pays basque et dans le sud des Landes autour des Apéros, Soirées et Labs. L’application doit aider l’équipe à gérer les profils et les membres à se retrouver et à prolonger leurs échanges après les événements.

## Priorités proposées

- Commencer par un annuaire accessible sur invitation. Un membre peut renseigner son nom affiché, sa ville, ses sujets tech ou produit et un lien de contact facultatif. Il peut choisir d’apparaître dans l’annuaire, mettre son profil à jour et l’en retirer.
- Tester ensuite un fil lié à un Lab ou à une Soirée. Pour un Lab, le fil peut servir à proposer un sujet, à retrouver un binôme ou à partager des ressources. Prévoir quand c’est nécessaire une action de modération pour l’équipe.
- Faire valider avant implémentation les choix qui changent le périmètre, comme la gestion de contacts sans compte, l’import Luma, la messagerie privée et le rôle d’un éventuel frontend Next.js.

## Profil, compte et visibilité

- Distinguer le compte de connexion, le profil du membre, le contact de billetterie Luma et l’abonné à la newsletter. Une même personne peut relever de plusieurs de ces situations.
- Pour l’annuaire, proposer une visibilité réservée aux membres connectés et activée par le titulaire du profil. Garder l’e-mail de connexion privé. Définir les champs exposés explicitement.
- Vérifier côté serveur les droits d’accès au profil, sa modification par son titulaire et les actions réservées à l’équipe. Couvrir notamment le cas d’un profil masqué et celui d’une tentative de modification du profil d’un autre membre.
- Utiliser des données fictives dans les tests et exemples. Ne jamais committer de secrets, notamment les fichiers `.env`, les clés API et les identifiants.

## Stack et structure

- Le dépôt contient un backend NestJS 12 et TypeScript en mode strict. Le point d’entrée est `src/main.ts` et le module racine est `src/app.module.ts`.
- Le projet utilise les modules ESM. Les imports relatifs TypeScript utilisent l’extension `.js`, comme dans le code existant.
- Organiser les nouvelles fonctionnalités en modules métier NestJS. Livrer les parcours en petits incréments de bout en bout et réutiliser les conventions du dépôt.
- Placer les tests unitaires Vitest à côté du code et les tests HTTP Vitest et Supertest dans `test/`. Utiliser Oxlint et Prettier.

## Commandes et vérifications

Utiliser npm 11 ou plus. Sur la branche Node 22, le lockfile actuel contient des dépendances qui exigent au moins la 22.22.3.

```bash
npm ci
npm run start:dev
npm run build
npm test
npm run test:e2e
npm run lint
npm run format
```

Pour un changement de code, lancer les vérifications pertinentes parmi la compilation, le lint et les tests. Ajouter ou mettre à jour des tests ciblés lorsque le comportement change. Pour la documentation seule, vérifier les commandes, chemins et liens cités. Dans la PR, indiquer les contrôles exécutés et les éventuels blocages.

## Conventions de contribution

- Rédiger la documentation, les issues et les PR en français. Utiliser l’anglais pour les noms dans le code et les fichiers source.
- Créer des branches courtes à partir de `main` avec un préfixe `feat/`, `fix/`, `docs/` ou `chore/`.
- Suivre Conventional Commits, par exemple `docs: précise les conventions de contribution`.
- Ouvrir des PR petites et ciblées. Expliquer ce qui motive le changement et comment l’équipe peut le vérifier.
