<div align="center">

# Cloudflare Links Manager

**Un petit gestionnaire de redirections pour centraliser les liens de ses services.**

Une application hébergée sur Cloudflare pour créer des liens courts, gérer les accès et retrouver facilement ses services.

<br>

![Cloudflare Pages](https://img.shields.io/badge/Cloudflare-Pages-orange?logo=cloudflare)
![Workers KV](https://img.shields.io/badge/Cloudflare-Workers%20KV-orange?logo=cloudflare)
![Langue](https://img.shields.io/badge/interface-fran%C3%A7aise-blue)

</div>

---

## Présentation

J'ai créé ce projet pour avoir un endroit unique où gérer mes redirections, sans devoir retenir ou partager les adresses complètes de tous mes services.

Le principe est assez simple : je crée un lien court, je lui associe une destination et je peux ensuite partager ce lien. Tout se gère depuis une interface web, sans avoir à modifier le code à chaque changement de destination.

Par exemple, plutôt que de partager directement l'adresse de mon Nextcloud, je peux utiliser une adresse comme `liens.mondomaine.fr/nextcloud`.

Le projet fonctionne avec Cloudflare Pages, Workers et KV. Il est pensé pour rester relativement léger et peut être utilisé avec l'offre gratuite de Cloudflare, à condition de respecter les quotas.

Au fil du temps, le projet a également intégré d'autres fonctionnalités pour faciliter son utilisation à plusieurs : gestion des comptes, permissions, personnalisation de l'interface et statistiques.

## Ce que propose le projet

### Gestion des liens

- Création de redirections avec un nom personnalisé.
- Modification et suppression des liens.
- Choix d'une destination externe en HTTP ou HTTPS.
- Dates de début et d'expiration pour les liens temporaires.
- Protection par mot de passe pour certains liens.
- Publication de petites pages de texte accessibles par une URL courte.

### Utilisateurs et permissions

L'application peut être utilisée par plusieurs personnes, avec des droits différents selon les besoins.

Elle comprend notamment :

- La création et la gestion des comptes.
- La désactivation des utilisateurs.
- La gestion des permissions.
- Plusieurs groupes de droits prédéfinis.
- La possibilité de créer des groupes personnalisés.
- La gestion du profil et du mot de passe.
- La possibilité de limiter la durée de validité de certains comptes.

L'objectif est de pouvoir partager l'administration sans nécessairement donner tous les droits à tout le monde.

### Personnalisation

L'interface peut être adaptée depuis l'administration, notamment pour le nom du site, les textes de présentation, le logo et l'apparence.

Un thème clair ou sombre est également disponible.

### Statistiques

Un espace d'analyse permet de consulter les informations d'utilisation enregistrées par l'application.

Son accès dépend des permissions attribuées au compte.

### Fichiers

Le code prévoit également une intégration optionnelle avec Cloudflare R2 pour le stockage de fichiers PDF.

Cette partie nécessite une configuration supplémentaire et n'est pas indispensable pour utiliser les redirections classiques.

---

## Quelques exemples

Voici quelques idées d'utilisation :

| Adresse courte | Destination |
|---|---|
| `liens.mondomaine.fr/nextcloud` | Mon Nextcloud |
| `liens.mondomaine.fr/photos` | Ma galerie photo |
| `liens.mondomaine.fr/docs` | Ma documentation |
| `liens.mondomaine.fr/projet` | Un site temporaire |

Ce sont simplement des exemples : chacun peut organiser ses liens comme il le souhaite.

---

## Installation

L'application utilise Cloudflare Pages pour l'hébergement, un Worker pour exécuter le code et KV pour stocker les données.

Il faut disposer d'un compte Cloudflare et avoir accès aux paramètres du projet.

### 1. Déployer le projet

Récupérez le fichier `_worker.js` présent dans le dépôt.

Créez ensuite un projet Cloudflare Pages ou utilisez un projet existant. Le code est prévu pour le mode avancé des Workers pour Pages : il doit être exécuté comme un Worker et non simplement servi comme un fichier statique.

Suivez la documentation officielle si vous découvrez Pages :

[Documentation Cloudflare Pages](https://developers.cloudflare.com/pages/)

### 2. Créer un espace de stockage KV

Dans le tableau de bord Cloudflare :

1. Ouvrez la section Workers & Pages.
2. Accédez à KV.
3. Créez un namespace.

Vous pouvez lui donner le nom que vous voulez. Par exemple : `liens-database`.

### 3. Ajouter le binding

Dans les paramètres de votre projet Pages, ajoutez un binding de type KV namespace.

Configurez-le ainsi :

| Paramètre | Valeur |
|---|---|
| Nom du binding | `LINKS` |
| Namespace associé | Celui créé à l'étape précédente |

Le nom `LINKS` est important : le code s'appuie sur ce nom pour accéder aux données.

### 4. Ajouter les secrets

Dans les paramètres du projet, ouvrez la section des variables et secrets.

Ajoutez les deux secrets suivants :

| Nom | Utilité |
|---|---|
| `ADMIN_PASSWORD` | Mot de passe d'administration |
| `SESSION_SECRET` | Secret utilisé pour signer les sessions |

Choisissez un mot de passe robuste et utilisez une valeur aléatoire suffisamment longue pour `SESSION_SECRET`.

Ces valeurs doivent rester privées. Ne les ajoutez jamais au code source ni au README de votre dépôt.

### 5. Configurer le compte propriétaire

Une variable facultative permet de définir l'identifiant du propriétaire :

`ADMIN_USER`

Si elle n'est pas renseignée, l'application utilise `bertrand` par défaut.

Vous pouvez définir votre propre identifiant dans les paramètres Cloudflare.

### 6. Configurer R2 si nécessaire

Si vous souhaitez utiliser le stockage de fichiers PDF prévu par le projet, créez un bucket Cloudflare R2 et ajoutez un binding nommé `CONTENT_FILES`.

Cette étape est facultative pour les redirections classiques.

[Documentation Cloudflare R2](https://developers.cloudflare.com/r2/)

### 7. Déployer et se connecter

Vérifiez les bindings et les secrets, puis déployez le projet.

Une fois le déploiement terminé, ouvrez votre domaine et accédez à l'administration pour vous connecter et créer vos premières redirections.

Si vous utilisez plusieurs environnements, vérifiez que les bindings et les secrets sont bien configurés dans celui où vous souhaitez exécuter l'application.

---

## Cloudflare KV : ce qu'il faut savoir

Le projet utilise KV pour conserver les redirections, les comptes et différents paramètres.

C'est pratique pour ce type d'application, mais il faut garder en tête que le service possède des quotas.

Sur l'offre gratuite de Workers, les limites documentées sont les suivantes :

| Opération | Quota journalier |
|---|---:|
| Lectures | 100 000 |
| Écritures | 1 000 |
| Suppressions | 1 000 |
| Opérations de liste | 1 000 |
| Stockage | 1 Go |

Les quotas journaliers sont réinitialisés à 00:00 UTC.

Les limites et les tarifs pouvant évoluer, consultez la documentation officielle avant de prendre une décision concernant votre hébergement :

- [Tarification de Workers KV](https://developers.cloudflare.com/kv/platform/pricing/)
- [Limites de Workers KV](https://developers.cloudflare.com/kv/platform/limits/)

### Pourquoi est-ce important ?

Les lectures servent notamment à récupérer des informations stockées dans KV. Les écritures servent à enregistrer ou modifier des données.

Dans le cas de cette application, les créations et modifications de liens, les changements de paramètres ou certaines opérations sur les comptes peuvent consommer des écritures.

Une seule action dans l'interface peut déclencher plusieurs opérations. Il ne faut donc pas considérer qu'un clic correspond systématiquement à une écriture.

Si le quota d'écritures est atteint, les modifications qui nécessitent un enregistrement peuvent échouer jusqu'à la remise à zéro du quota.

Cela peut notamment arriver lorsqu'on effectue beaucoup de modifications pendant les tests ou lors de la configuration initiale.

### Comment limiter la consommation ?

Quelques habitudes peuvent aider :

- Éviter de sauvegarder plusieurs fois les mêmes paramètres.
- Limiter les modifications répétées pendant les tests.
- Consulter les métriques KV dans le tableau de bord Cloudflare.
- Vérifier les logs du Worker lorsqu'une opération échoue.

KV est particulièrement intéressant lorsque les données sont souvent consultées et moins souvent modifiées.

Si votre utilisation nécessite beaucoup d'écritures quotidiennes, il peut être utile d'étudier une autre offre ou une solution de stockage mieux adaptée.

---

## Sécurité

Quelques précautions sont importantes, même pour un petit projet personnel.

- Gardez les secrets Cloudflare privés.
- Utilisez HTTPS pour accéder à l'administration.
- Attribuez uniquement les permissions nécessaires à chaque utilisateur.
- Désactivez les comptes qui ne doivent plus avoir accès à l'application.
- Prévoyez une sauvegarde des données importantes.

Une URL difficile à deviner ne constitue pas une véritable protection. Pour les liens sensibles, utilisez les protections prévues par l'application et évitez d'y partager des informations confidentielles.

---

## Dépannage

### L'application indique que la configuration est incomplète

Vérifiez la présence du binding `LINKS` et des secrets `ADMIN_PASSWORD` et `SESSION_SECRET`.

Vérifiez également qu'ils sont configurés dans le bon environnement Cloudflare.

### Je ne peux pas enregistrer une redirection

Commencez par vérifier le binding KV, les permissions de votre compte et le quota d'écritures.

Si tout semble correct, consultez les logs du Worker pour obtenir le détail de l'erreur.

### J'obtiens une erreur 1101

Cette erreur indique généralement qu'une exception s'est produite pendant l'exécution du Worker.

Un quota KV dépassé peut être à l'origine d'un échec, mais ce n'est pas la seule possibilité. Les logs permettent de distinguer un problème de quota d'une erreur de configuration ou de code.

### Une redirection ne fonctionne pas

Vérifiez que le lien existe, que l'adresse de destination est valide et que les éventuelles dates de disponibilité sont correctes.

Si le lien est protégé par mot de passe, vérifiez également ce paramètre.

### La connexion à l'administration échoue

Vérifiez l'identifiant propriétaire, le mot de passe et la présence de `SESSION_SECRET`.

Si vous venez de modifier les paramètres Cloudflare, vérifiez que le déploiement utilise bien la nouvelle configuration.

---

## Organisation des données

Le code utilise plusieurs préfixes KV pour organiser les informations.

| Préfixe ou clé | Utilisation |
|---|---|
| `l:` | Métadonnées des redirections |
| `t:` | Contenu des pages de texte |
| `u:` | Comptes utilisateurs |
| `g:` | Groupes de permissions |
| `settings:brand` | Personnalisation du site |
| `profile:owner` | Profil du propriétaire |
| `an:` | Événements d'analyse |
| `rl:` | Compteurs temporaires de tentatives de connexion |

Cette liste est indicative. Évitez de modifier ou de supprimer manuellement des clés KV sans connaître leur rôle.

---

## Documentation utile

- [Cloudflare Pages](https://developers.cloudflare.com/pages/)
- [Cloudflare Workers](https://developers.cloudflare.com/workers/)
- [Cloudflare Workers KV](https://developers.cloudflare.com/kv/)
- [Tarification KV](https://developers.cloudflare.com/kv/platform/pricing/)
- [Limites KV](https://developers.cloudflare.com/kv/platform/limits/)
- [Cloudflare R2](https://developers.cloudflare.com/r2/)

---

## Pour finir

Ce projet est avant tout un outil pratique pour centraliser ses redirections et simplifier l'accès à ses services.

Il évolue en fonction des besoins, et l'objectif reste de garder une administration simple à utiliser sans multiplier les services à maintenir.

Si vous l'utilisez ou si vous repérez un problème, n'hésitez pas à ouvrir une issue sur le dépôt.

Merci d'avoir pris le temps de découvrir le projet.

</writing>
