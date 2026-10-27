<div align="center">

# Cloudflare Links Manager

### Vos liens. Votre domaine. Votre infrastructure.

Une application de gestion de liens et de redirections hébergée sur Cloudflare, conçue pour centraliser vos URL, simplifier leur gestion et garder le contrôle sur votre propre infrastructure.

<br>

![Cloudflare Pages](https://img.shields.io/badge/Cloudflare-Pages-F38020?style=for-the-badge&logo=cloudflare&logoColor=white)
![Workers KV](https://img.shields.io/badge/Storage-Workers_KV-2563EB?style=for-the-badge)
![Interface](https://img.shields.io/badge/Interface-Fran%C3%A7aise-16A34A?style=for-the-badge)

**Simple à déployer · Agréable à utiliser · Pensé pour durer**

</div>

---

## Présentation

Cloudflare Links Manager permet de créer et de gérer ses propres liens courts et redirections depuis une interface d'administration.

L'idée est simple : au lieu de partager des URL interminables, vous utilisez votre domaine pour créer des adresses courtes, personnalisées et faciles à retenir.

Par exemple :

| Votre lien | Destination |
|---|---|
| `liens.mondomaine.fr/nextcloud` | `cloud.mondomaine.fr` |
| `liens.mondomaine.fr/docs` | Une documentation en ligne |
| `liens.mondomaine.fr/contact` | Une page de contact |
| `liens.mondomaine.fr/mon-projet` | Le site de votre projet |

Vous gardez la maîtrise de vos liens. Si une destination change, il suffit de modifier la redirection dans l'administration : pas besoin de communiquer une nouvelle adresse à tout le monde.

Le projet s'appuie sur les services Cloudflare pour fonctionner sans avoir à gérer un serveur traditionnel.

## Fonctionnalités

### Gestion des liens

Créez des redirections adaptées à vos besoins et gérez-les depuis une interface centralisée.

- Création de liens personnalisés.
- Modification et suppression des redirections.
- Prise en charge des destinations HTTP et HTTPS.
- Gestion de dates de début et de fin de disponibilité.
- Protection de certains liens par mot de passe.
- Création de pages contenant un court texte.

### Utilisateurs et permissions

L'application propose des fonctions d'administration pour organiser l'accès à votre espace.

- Gestion des comptes utilisateurs.
- Attribution de rôles et organisation en groupes.
- Activation et désactivation des comptes.
- Gestion des profils et des mots de passe.
- Possibilité de définir une date d'expiration pour certains comptes.

### Personnalisation

Adaptez l'interface à votre environnement plutôt que l'inverse.

- Personnalisation du nom du site.
- Modification des textes et du logo.
- Réglages d'apparence.
- Prise en charge des thèmes clair et sombre.

### Statistiques

Consultez les informations de fréquentation disponibles dans l'application pour mieux comprendre l'utilisation de vos liens.

### Stockage de fichiers avec R2

Une configuration compatible avec Cloudflare R2 peut également être utilisée pour le stockage de fichiers, notamment des PDF, si cette fonctionnalité est activée et correctement configurée.

---

## Architecture

Le projet repose sur les services suivants :

| Service | Rôle |
|---|---|
| **Cloudflare Pages** | Hébergement et déploiement de l'application |
| **Cloudflare Workers** | Exécution du code côté serveur |
| **Cloudflare Workers KV** | Stockage des données de l'application |
| **Cloudflare R2** | Stockage de fichiers optionnel |

L'objectif est de disposer d'une application accessible depuis votre domaine, sans devoir administrer un serveur Linux ni maintenir une base de données traditionnelle.

Les quotas et conditions d'utilisation dépendent de votre offre Cloudflare.

---

## Installation

Cette partie s'adresse aux personnes qui souhaitent installer leur propre instance.

Quelques notions de base sur Cloudflare sont utiles, mais les étapes ci-dessous permettent de suivre la configuration sans partir de zéro.

### 1. Préparer le projet

Récupérez le fichier `_worker.js` fourni avec le projet.

Il contient le code de l'application. Conservez une copie du fichier original afin de pouvoir revenir à la version initiale en cas de problème.

### 2. Créer le projet Cloudflare Pages

Dans votre tableau de bord Cloudflare :

1. Ouvrez **Workers & Pages**.
2. Créez un projet Pages ou ouvrez celui que vous souhaitez utiliser.
3. Configurez le déploiement correspondant au format du projet fourni.
4. Déployez le code selon la méthode compatible avec votre version de Cloudflare Pages.

Les intitulés exacts des menus peuvent varier selon l'interface Cloudflare et la méthode de déploiement utilisée.

### 3. Créer l'espace de stockage KV

L'application utilise Cloudflare Workers KV pour conserver ses données.

1. Ouvrez la section **Storage & Databases** de Cloudflare.
2. Créez un espace de noms KV.
3. Donnez-lui un nom explicite, par exemple `links-manager`.
4. Ouvrez les paramètres du projet Pages.
5. Ajoutez cet espace de noms comme liaison KV.

**Nom de la liaison attendu par l'application :**

`LINKS`

Attention : le nom de l'espace de noms et celui de la liaison sont deux choses différentes. C'est le nom de la liaison qui doit correspondre à celui attendu par le code.

### 4. Configurer les variables d'environnement

Dans les paramètres de votre projet, ajoutez les secrets nécessaires à l'application.

| Variable | Rôle |
|---|---|
| `ADMIN_PASSWORD` | Mot de passe administrateur initial, si prévu par la version utilisée |
| `SESSION_SECRET` | Secret utilisé pour les mécanismes de session, selon l'implémentation |

Si votre version utilise également une variable `ADMIN_USER`, configurez-la conformément au code. Une valeur par défaut peut exister, mais vérifiez-la avant la première mise en service.

**Important :** utilisez un mot de passe robuste et un secret suffisamment long, aléatoire et unique. Ne publiez jamais leurs valeurs dans votre dépôt GitHub.

Les noms des variables doivent correspondre exactement à ceux utilisés dans le fichier `_worker.js`.

### 5. Configurer R2 (facultatif)

Si vous souhaitez utiliser les fonctions de stockage de fichiers :

1. Créez un compartiment Cloudflare R2.
2. Ajoutez-le au projet en tant que liaison.
3. Utilisez le nom de liaison attendu par le code, par exemple `CONTENT_FILES` si votre version le prévoit.

Cette étape peut être ignorée si vous n'avez pas besoin du stockage de fichiers.

### 6. Déployer et vérifier

Une fois la configuration terminée :

1. Enregistrez vos paramètres.
2. Redéployez l'application.
3. Ouvrez l'adresse de votre site.
4. Connectez-vous avec les identifiants configurés.
5. Créez un premier lien de test.
6. Vérifiez que la redirection fonctionne.

Si quelque chose ne fonctionne pas, consultez la section de dépannage avant de modifier le code.

---

## Comprendre les limites de Workers KV

Cloudflare Workers KV est un stockage distribué. Il est pratique pour ce type d'application, mais il est soumis à des quotas.

Les limites exactes dépendent de l'offre et des conditions en vigueur. À titre indicatif, l'offre gratuite a notamment été associée aux quotas journaliers suivants :

| Type d'opération | Quota journalier indicatif |
|---|---:|
| Lectures | 100 000 |
| Écritures | 1 000 |
| Suppressions | 1 000 |
| Opérations de liste | 1 000 |
| Stockage | 1 Go |

Ces chiffres sont donnés à titre indicatif et **ne constituent pas une garantie des quotas applicables à votre compte en octobre 2026**. Vérifiez les valeurs actuelles dans la documentation officielle avant de dimensionner votre installation.

- [Tarification de Workers KV](https://developers.cloudflare.com/kv/platform/pricing/)
- [Limites de Workers KV](https://developers.cloudflare.com/kv/platform/limits/)

### Qu'est-ce que cela signifie concrètement ?

Les opérations de lecture servent notamment à récupérer des données. Les écritures et suppressions sont utilisées lorsque des données sont créées, modifiées ou supprimées. Les opérations de liste permettent de parcourir les clés stockées.

Une application peut donc fonctionner parfaitement avec un usage modéré, puis rencontrer des limites si le volume d'activité augmente fortement.

Il faut également tenir compte du fait qu'une seule action dans l'interface peut déclencher plusieurs opérations KV.

**Notre conseil :** surveillez l'utilisation de votre compte Cloudflare, surtout si vous ouvrez l'accès à plusieurs utilisateurs ou si vos liens reçoivent beaucoup de trafic.

---

## Sécurité

Comme pour toute application accessible depuis Internet, quelques précautions sont indispensables.

- Choisissez des identifiants robustes.
- Ne partagez jamais vos secrets Cloudflare.
- Limitez les accès au tableau de bord Cloudflare aux personnes de confiance.
- Utilisez HTTPS sur votre domaine.
- Vérifiez régulièrement les paramètres et les autorisations de votre projet.
- Testez les changements avant de les mettre en production.
- Conservez une copie du code et des données importantes.

La présence d'une option de protection par mot de passe ne remplace pas une vérification complète de la sécurité de l'application. Les mécanismes d'authentification, de session et de contrôle des permissions dépendent de l'implémentation exacte du code déployé.

---

## Dépannage

### L'application ne démarre pas

Vérifiez que le dernier déploiement s'est terminé correctement et consultez les journaux d'exécution Cloudflare.

### Impossible d'enregistrer un lien

Vérifiez que la liaison KV est présente et qu'elle porte exactement le nom attendu par le code.

Si le quota d'écritures est atteint, certaines opérations peuvent également échouer jusqu'au rétablissement de la capacité disponible.

### La redirection ne fonctionne pas

Vérifiez le chemin du lien, la destination enregistrée, les éventuelles restrictions de disponibilité et la configuration du domaine.

### La connexion échoue

Vérifiez les variables de configuration, les identifiants utilisés et les éventuels changements récents apportés au déploiement.

### Une erreur serveur apparaît

Consultez les journaux Cloudflare pour identifier l'erreur précise. Évitez de publier des journaux contenant des secrets, des cookies de session ou des informations personnelles.

---

## Documentation officielle

Pour aller plus loin, les ressources suivantes sont utiles :

- [Cloudflare Pages](https://developers.cloudflare.com/pages/)
- [Cloudflare Workers](https://developers.cloudflare.com/workers/)
- [Cloudflare Workers KV](https://developers.cloudflare.com/kv/)
- [Cloudflare R2](https://developers.cloudflare.com/r2/)

---

## Contribuer

Les suggestions, les signalements de bugs et les améliorations sont les bienvenus.

Avant de proposer une modification, vérifiez qu'elle ne compromet pas les redirections existantes, les données stockées ou les mécanismes d'authentification.

Pour signaler un problème, indiquez autant que possible :

- Le comportement attendu.
- Le comportement observé.
- Les étapes permettant de reproduire le problème.
- Le message d'erreur obtenu, en retirant toute information sensible.

---

## Licence

Ajoutez ici la licence choisie pour le projet si vous souhaitez autoriser sa réutilisation.

En l'absence de licence explicite, ne partez pas du principe que le code peut être librement copié, modifié ou redistribué.

---

<div align="center">

**Cloudflare Links Manager**

*Un seul endroit pour gérer vos liens, avec votre propre infrastructure.*

</div>
