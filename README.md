<div align="center">

# Cloudflare Links Manager by Bertrand

### Tous vos liens. Un seul endroit.

Une application pour créer, organiser et gérer vos redirections depuis votre propre domaine, avec Cloudflare.

<br>

[![Cloudflare](https://img.shields.io/badge/Powered_by-Cloudflare-F38020?style=for-the-badge&logo=cloudflare&logoColor=white)](https://www.cloudflare.com/)
![Workers KV](https://img.shields.io/badge/Storage-Workers_KV-2563EB?style=for-the-badge)
![Interface](https://img.shields.io/badge/Interface-Fran%C3%A7aise-16A34A?style=for-the-badge)

<br>

**Une interface centralisée. Des liens personnalisés. Votre infrastructure.**

<br>

[Installation](#installation) · [Captures d'écran](#aperçu) · [Fonctionnalités](#fonctionnalités) · [Documentation](#documentation)

</div>

---

## À propos

Cloudflare Links Manager permet de créer et de gérer facilement des redirections personnalisées depuis une interface d'administration.

Plutôt que de partager des adresses longues et difficiles à retenir, utilisez votre propre domaine pour créer des liens simples, pratiques et faciles à mémoriser.

| Lien personnalisé | Destination |
|---|---|
| `liens.mondomaine.fr/nextcloud` | Votre espace Nextcloud |
| `liens.mondomaine.fr/docs` | Votre documentation |
| `liens.mondomaine.fr/contact` | Votre page de contact |
| `liens.mondomaine.fr/projet` | Votre site ou application |

Si une destination change, modifiez simplement la redirection depuis l'administration. Pas besoin de communiquer une nouvelle adresse à tout le monde.

Le projet s'appuie sur les services Cloudflare et est distribué sous la forme d'une archive ZIP.

## Aperçu

Les captures d'écran suivantes permettront de découvrir l'interface avant l'installation.

### Tableau de bord

Une vue d'ensemble de votre espace d'administration.

<div align="center">

![Tableau de bord](screenshots/dashboard.png)
<img width="1670" height="998" alt="image" src="https://github.com/user-attachments/assets/170d1e16-0387-4467-9919-c84fc9888496" />

*Tableau de bord principal*

</div>

### Gestion des liens

Créez, modifiez et organisez vos redirections depuis une interface centralisée.

<div align="center">

![Gestion des liens](screenshots/liens.png)
<img width="1663" height="1027" alt="image" src="https://github.com/user-attachments/assets/e65cdff7-a3c7-4c57-b0f8-4b40b17c6d97" />
*Gestion des liens et des redirections*

<img width="1710" height="555" alt="image" src="https://github.com/user-attachments/assets/2c3e8cd2-da83-44db-9a28-3ae0fdcf3ffa" />
*Page de redirection*
</div>

### Centre d'analyse

Consultez les statistiques disponibles pour mieux comprendre l'utilisation de vos liens.

<div align="center">

![Centre d'analyse](screenshots/analyses.png)
<img width="1696" height="1006" alt="image" src="https://github.com/user-attachments/assets/ba196009-4730-4268-94cd-cc0b7f728a39" />
<img width="1681" height="700" alt="image" src="https://github.com/user-attachments/assets/f5150738-3e14-490d-b5b3-b9fefea6baa4" />
*Centre d'analyse et statistiques*

</div>




### Utilisateurs et groupes de droits

Gérez les comptes et organisez les autorisations selon les besoins de votre installation.

<div align="center">

![Gestion des utilisateurs](screenshots/utilisateurs.png)
<img width="1663" height="915" alt="image" src="https://github.com/user-attachments/assets/b429c0e0-60d2-4a8a-bcee-57019c32e094" />
*Gestion des utilisateurs*



![Groupes de droits](screenshots/groupes-droits.png)
<img width="1644" height="904" alt="image" src="https://github.com/user-attachments/assets/de9c7532-c53a-409b-a9ee-e61e042d7a71" />
<img width="675" height="1055" alt="image" src="https://github.com/user-attachments/assets/53d002c2-0020-4d91-be56-9adae1aafb2d" />

*Groupes et permissions*

</div>

### Personnalisation

Adaptez l'apparence de l'application à vos préférences.

<div align="center">

![Personnalisation](screenshots/personnalisation.png)
<img width="1657" height="1046" alt="image" src="https://github.com/user-attachments/assets/34545c9a-865d-4780-8c58-da1910f27709" />
<img width="1713" height="894" alt="image" src="https://github.com/user-attachments/assets/95a88bd7-fe18-4410-bcd3-b6bf96861bad" />
<img width="1676" height="803" alt="image" src="https://github.com/user-attachments/assets/c9b62249-abe0-4c94-a1f4-d5403bea29bc" />

*Personnalisation de l'interface*

</div>

---

## Fonctionnalités

### Gestion des liens

Créez et gérez vos redirections sans devoir modifier le code à chaque changement.

- Création de liens avec des adresses personnalisées.
- Modification et suppression des liens.
- Prise en charge des destinations HTTP et HTTPS.
- Gestion des dates de début et de fin de disponibilité.
- Protection de certains liens par mot de passe.
- Création de pages contenant un court texte.

### Centre d'analyse

Le centre d'analyse permet de consulter les statistiques disponibles dans l'application et de suivre l'utilisation de vos liens.

Il offre un point central pour observer l'activité et mieux comprendre comment vos redirections sont utilisées.

Les données et indicateurs affichés dépendent des fonctionnalités implémentées dans la version installée.

### Utilisateurs et groupes de droits

L'application propose des outils pour organiser les accès à l'administration.

- Gestion des comptes utilisateurs.
- Organisation des utilisateurs en groupes de droits.
- Gestion des permissions selon les rôles disponibles.
- Activation et désactivation des comptes.
- Gestion des profils et des mots de passe.
- Gestion éventuelle de l'expiration des comptes.

Ces fonctions permettent d'adapter l'accès à l'application en fonction des responsabilités de chaque utilisateur.

### Personnalisation

Adaptez l'interface à votre environnement.

- Modification du nom du site.
- Personnalisation du logo et des textes.
- Réglages de l'apparence.
- Thèmes clair et sombre.

### Stockage de fichiers

Une configuration compatible avec Cloudflare R2 peut être utilisée pour stocker des fichiers, notamment des PDF, si cette fonctionnalité est activée dans votre version.

---

## Architecture

Le projet repose sur les services suivants :

| Service | Utilité |
|---|---|
| **Cloudflare Pages** | Hébergement de l'application |
| **Cloudflare Workers** | Exécution du code côté serveur |
| **Cloudflare Workers KV** | Stockage des données |
| **Cloudflare R2** | Stockage de fichiers optionnel |

Cette architecture permet de faire fonctionner l'application sans administrer un serveur traditionnel.

Les services utilisés restent soumis aux quotas et aux conditions de Cloudflare.

---

## Installation

L'application est distribuée sous la forme d'un fichier ZIP. Il n'est pas nécessaire de cloner le dépôt GitHub pour récupérer l'archive.

### Prérequis

Avant de commencer, vous aurez besoin de :

- Un compte Cloudflare.
- Un projet Cloudflare Pages compatible avec le code fourni.
- Un espace de noms Workers KV.
- L'archive ZIP du projet.

Un domaine personnalisé est recommandé pour profiter de liens faciles à retenir. Vous pouvez néanmoins commencer par tester le déploiement sur l'adresse fournie par Cloudflare.

### 1. Télécharger le ZIP

Téléchargez l'archive jointe à la release GitHub.

Décompressez-la sur votre ordinateur et repérez le fichier `_worker.js`.

Conservez une copie de l'archive originale afin de pouvoir repartir d'une version propre en cas de problème.

### 2. Préparer Cloudflare Pages

Dans le tableau de bord Cloudflare :

1. Ouvrez **Workers & Pages**.
2. Créez un projet ou sélectionnez un projet existant.
3. Configurez le mode de déploiement correspondant à la structure du projet fourni.
4. Ajoutez les fichiers nécessaires au déploiement.

La procédure exacte dépend du format de l'archive et du mode de déploiement utilisé. Assurez-vous que la configuration choisie prend en charge le fichier `_worker.js` fourni.

### 3. Configurer Workers KV

L'application utilise Workers KV pour stocker ses données.

1. Ouvrez la section de stockage de Cloudflare.
2. Créez un espace de noms KV.
3. Ouvrez les paramètres du projet.
4. Ajoutez une liaison KV pointant vers cet espace de noms.
5. Nommez cette liaison `LINKS`, si c'est bien le nom attendu par votre version du code.

**Attention :** le nom de l'espace de noms et celui de la liaison sont deux éléments distincts. C'est le nom de la liaison qui doit correspondre à celui attendu par le code.

### 4. Configurer les secrets

Ajoutez les variables et secrets attendus par votre version de l'application.

| Variable | Utilité |
|---|---|
| `ADMIN_PASSWORD` | Mot de passe administrateur initial, si utilisé par le code |
| `SESSION_SECRET` | Secret lié à la gestion des sessions, selon l'implémentation |
| `ADMIN_USER` | Nom d'utilisateur administrateur, si cette variable est prise en charge |

Les noms et les usages doivent correspondre exactement à ceux définis dans `_worker.js`.

Utilisez un mot de passe robuste et un secret unique. Ne publiez jamais leurs valeurs dans votre dépôt GitHub.

### 5. Configurer R2 (facultatif)

Si vous souhaitez utiliser le stockage de fichiers :

1. Créez un compartiment Cloudflare R2.
2. Ajoutez la liaison correspondante au projet.
3. Utilisez le nom attendu par le code, par exemple `CONTENT_FILES` si votre version le prévoit.

Vous pouvez ignorer cette étape si vous n'avez pas besoin de cette fonctionnalité.

### 6. Déployer et tester

Une fois la configuration terminée :

1. Enregistrez vos paramètres.
2. Déployez ou redéployez le projet.
3. Ouvrez l'application dans votre navigateur.
4. Connectez-vous avec les identifiants configurés.
5. Créez un lien de test.
6. Vérifiez que la redirection fonctionne.

Si une erreur apparaît, consultez les journaux d'exécution Cloudflare et vérifiez les liaisons et les variables de configuration.

---

## Gratuité et limites de Cloudflare

**Cloudflare Links Manager peut être hébergé gratuitement dans certaines configurations.** Il faut toutefois distinguer le logiciel lui-même des services utilisés pour le faire fonctionner.

Cloudflare propose des offres gratuites pour plusieurs de ses services, notamment Pages, Workers et Workers KV. Elles comportent des limites d'utilisation.

À titre indicatif, les quotas historiquement associés à l'offre gratuite de Workers KV comprennent :

| Opération | Quota journalier indicatif |
|---|---:|
| Lectures | 100 000 |
| Écritures | 1 000 |
| Suppressions | 1 000 |
| Opérations de liste | 1 000 |
| Stockage | 1 Go |

Ces chiffres sont indicatifs : les limites applicables peuvent évoluer et doivent être vérifiées dans la documentation officielle.

- [Tarification de Workers KV](https://developers.cloudflare.com/kv/platform/pricing/)
- [Limites de Workers KV](https://developers.cloudflare.com/kv/platform/limits/)
- [Tarification de Workers](https://developers.cloudflare.com/workers/platform/pricing/)
- [Documentation Cloudflare Pages](https://developers.cloudflare.com/pages/)

### Que faut-il retenir ?

- Vous pouvez commencer avec les offres gratuites de Cloudflare si votre configuration respecte leurs conditions.
- Les opérations de stockage sont soumises à des quotas.
- Une seule action dans l'interface peut déclencher plusieurs opérations KV.
- Un usage plus important peut nécessiter une offre payante.
- Un nom de domaine acheté séparément peut également entraîner des frais.
- Les fonctionnalités utilisant d'autres services, comme R2, peuvent avoir leurs propres conditions tarifaires.

**En résumé :** l'application peut fonctionner sans abonnement payant dans une configuration adaptée, mais il serait incorrect de garantir que toutes les installations et tous les usages seront toujours entièrement gratuits.

---

## Sécurité

Quelques précautions permettent de limiter les risques :

- Utilisez des mots de passe robustes.
- Gardez vos secrets Cloudflare confidentiels.
- Limitez l'accès au tableau de bord Cloudflare aux personnes de confiance.
- Utilisez HTTPS sur votre domaine.
- Conservez une copie du code et des données importantes.
- Vérifiez les permissions avant d'accorder l'accès à d'autres utilisateurs.

La présence d'une protection par mot de passe ne suffit pas, à elle seule, à garantir la sécurité de l'ensemble de l'application. L'authentification, la gestion des sessions et les permissions dépendent de l'implémentation du code déployé.

---

## Dépannage

| Problème | Vérifications |
|---|---|
| L'application ne démarre pas | Consultez les journaux d'exécution et vérifiez le déploiement. |
| Impossible d'enregistrer un lien | Vérifiez la liaison KV et les quotas disponibles. |
| Une redirection ne fonctionne pas | Vérifiez le chemin, la destination et les dates de disponibilité. |
| La connexion échoue | Vérifiez les identifiants et les variables attendues par le code. |
| Une erreur serveur apparaît | Consultez les journaux Cloudflare pour identifier la cause. |

Ne publiez jamais de secrets, de cookies de session ou d'informations personnelles dans un rapport de bug.

---

## Documentation officielle

- [Cloudflare Pages](https://developers.cloudflare.com/pages/)
- [Cloudflare Workers](https://developers.cloudflare.com/workers/)
- [Cloudflare Workers KV](https://developers.cloudflare.com/kv/)
- [Cloudflare R2](https://developers.cloudflare.com/r2/)

---

## Signaler un problème

Si vous rencontrez un bug, indiquez si possible :

- La version de l'archive utilisée.
- Les étapes permettant de reproduire le problème.
- Le résultat attendu.
- Le résultat obtenu.
- Le message d'erreur, en retirant toute information sensible.

Les retours permettent de rendre le projet plus fiable et plus simple à utiliser.

---

<div align="center">

**Cloudflare Links Manager**

*Vos redirections, votre domaine, votre contrôle.*

</div>
