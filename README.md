<div align="center">

# Cloudflare Links Manager

### Tous vos liens. Un seul endroit.

Une application pour créer, organiser et gérer vos redirections depuis votre propre domaine, avec Cloudflare.

<br>

[![Cloudflare](https://img.shields.io/badge/Powered_by-Cloudflare-F38020?style=for-the-badge&logo=cloudflare&logoColor=white)](https://www.cloudflare.com/)
![Workers KV](https://img.shields.io/badge/Storage-Workers_KV-2563EB?style=for-the-badge)
![Language](https://img.shields.io/badge/Interface-Fran%C3%A7aise-16A34A?style=for-the-badge)

<br>

**Une interface centralisée. Des liens personnalisés. Votre infrastructure.**

<br>

[ Télécharger le projet ](#installation) · [ Captures d'écran ](#aperçu) · [ Documentation ](#documentation)

</div>

---

## À propos

Cloudflare Links Manager permet de créer et de gérer facilement des redirections personnalisées depuis une interface d'administration.

Plutôt que de partager des adresses longues et difficiles à retenir, vous pouvez utiliser votre propre domaine pour créer des liens simples.

Par exemple :

| Lien personnalisé | Destination |
|---|---|
| `liens.mondomaine.fr/nextcloud` | Votre espace Nextcloud |
| `liens.mondomaine.fr/docs` | Votre documentation |
| `liens.mondomaine.fr/contact` | Votre page de contact |
| `liens.mondomaine.fr/projet` | Votre site ou application |

Et si une destination change ? Vous modifiez simplement le lien depuis l'administration, sans avoir à diffuser une nouvelle adresse.

Le projet s'appuie sur les services Cloudflare et est distribué sous la forme d'une archive ZIP contenant les fichiers nécessaires au déploiement.

## Aperçu

Voici les emplacements prévus pour présenter l'application en images. Remplacez les chemins des images par les noms de vos propres captures.

### Tableau de bord

*Une vue d'ensemble de l'application.*

<div align="center">

<img width="1698" height="904" alt="image" src="https://github.com/user-attachments/assets/3bd91c19-c6fd-4316-aed6-df47a97b8485" />


![Tableau de bord](screenshots/dashboard.png)

</div>

### Gestion des liens

*Retrouvez vos redirections et gérez vos liens depuis une interface unique.*

<div align="center">

<img width="1691" height="904" alt="image" src="https://github.com/user-attachments/assets/f01f8fb6-eb27-4ea9-b6ad-d20d8cb7b35f" />


![Gestion des liens](screenshots/liens.png)

</div>

### Utilisateurs et permissions

*Gérez les comptes et les accès selon les fonctionnalités disponibles dans votre installation.*

<div align="center">

<img width="1663" height="915" alt="image" src="https://github.com/user-attachments/assets/257daf64-b264-4599-990a-4e8ceda8d69c" />


![Gestion des utilisateurs](screenshots/utilisateurs.png)

</div>

### Personnalisation

*Adaptez l'interface à vos préférences.*

<div align="center">

<!-- Remplacer par une capture des paramètres -->

![Paramètres de l'application](screenshots/parametres.png)

</div>

> **Ajouter les captures :** créez un dossier `screenshots` à la racine de votre dépôt GitHub et placez-y vos images avec les noms indiqués ci-dessus. Vous pouvez aussi modifier les chemins dans ce README pour utiliser vos propres noms de fichiers.

---

## Fonctionnalités

### Liens et redirections

- Création de liens avec des adresses personnalisées.
- Modification et suppression des liens.
- Redirections vers des destinations HTTP ou HTTPS.
- Gestion de dates de début et de fin de disponibilité.
- Protection de certains liens par mot de passe.
- Création de pages contenant un texte court.

### Utilisateurs

- Gestion des comptes.
- Organisation des utilisateurs en groupes et attribution de rôles, selon les fonctions disponibles.
- Activation et désactivation des comptes.
- Gestion des profils et des mots de passe.
- Gestion éventuelle de la date d'expiration des comptes.

### Personnalisation

- Modification du nom du site.
- Personnalisation des textes et du logo.
- Réglages de l'apparence.
- Thèmes clair et sombre.

### Statistiques et fichiers

- Consultation des statistiques disponibles dans l'application.
- Possibilité d'utiliser Cloudflare R2 pour le stockage de fichiers, si cette fonctionnalité est configurée.

Les fonctionnalités réellement disponibles dépendent de la version du code fournie dans l'archive.

---

## Installation

L'application est distribuée sous forme de fichier ZIP. Aucun clonage du dépôt avec Git n'est nécessaire pour récupérer l'archive.

### Prérequis

Avant de commencer, vous aurez besoin de :

- Un compte Cloudflare.
- Un projet Cloudflare Pages configuré pour le mode de déploiement compatible avec le code fourni.
- Un espace de noms Cloudflare Workers KV.
- Le fichier ZIP du projet.

Un nom de domaine personnalisé est recommandé pour utiliser des liens propres, mais vous pouvez commencer par tester le déploiement sur l'adresse Cloudflare attribuée à votre projet.

### 1. Télécharger l'archive

Récupérez le fichier ZIP mis à disposition dans la section de téléchargement du dépôt.

Décompressez-le sur votre ordinateur.

Vous devriez retrouver le fichier `_worker.js` parmi les fichiers fournis.

**Conservez une copie de l'archive originale.** Elle vous sera utile si vous souhaitez repartir d'une version propre.

### 2. Préparer Cloudflare Pages

Dans le tableau de bord Cloudflare :

1. Ouvrez **Workers & Pages**.
2. Créez un projet ou sélectionnez un projet existant.
3. Configurez le mode de déploiement correspondant à la structure de l'archive.
4. Préparez les fichiers nécessaires au déploiement.

La procédure exacte dépend de la structure du ZIP et du mode de déploiement utilisé. Vérifiez que le projet est compatible avec le fichier `_worker.js` fourni avant de publier.

### 3. Configurer Workers KV

L'application utilise Workers KV pour stocker ses données.

1. Ouvrez la section de stockage de Cloudflare.
2. Créez un espace de noms KV.
3. Ouvrez les paramètres de votre projet.
4. Ajoutez une liaison KV pointant vers cet espace de noms.
5. Utilisez le nom de liaison attendu par le code : `LINKS`.

Attention : le nom de l'espace de noms et le nom de la liaison ne sont pas nécessairement identiques.

### 4. Configurer les secrets

Ajoutez les variables et secrets attendus par votre version de l'application.

| Variable | Utilité |
|---|---|
| `ADMIN_PASSWORD` | Mot de passe administrateur initial, si utilisé par le code |
| `SESSION_SECRET` | Secret lié à la gestion des sessions, selon l'implémentation |
| `ADMIN_USER` | Nom d'utilisateur administrateur, si cette variable est prise en charge |

Les noms et les usages doivent correspondre exactement à ceux définis dans le fichier fourni.

Utilisez des valeurs robustes et ne publiez jamais vos secrets dans votre dépôt GitHub.

### 5. Configurer R2 (facultatif)

Si vous souhaitez utiliser le stockage de fichiers :

1. Créez un compartiment Cloudflare R2.
2. Ajoutez la liaison correspondante à votre projet.
3. Utilisez le nom attendu par le code, par exemple `CONTENT_FILES` si votre version le prévoit.

Cette étape est facultative si vous n'avez pas besoin de cette fonctionnalité.

### 6. Déployer et tester

Une fois les paramètres configurés :

1. Enregistrez vos modifications.
2. Déployez ou redéployez le projet.
3. Ouvrez l'application dans votre navigateur.
4. Connectez-vous avec les identifiants configurés.
5. Créez un lien de test.
6. Vérifiez que la redirection fonctionne.

Si une erreur apparaît, consultez les journaux d'exécution Cloudflare et vérifiez les liaisons et les variables de configuration.

---

## Comprendre les limites de Workers KV

Workers KV est pratique pour stocker les données de l'application, mais il est soumis à des quotas.

À titre indicatif, les limites historiquement associées à l'offre gratuite comprennent :

| Opération | Quota journalier indicatif |
|---|---:|
| Lectures | 100 000 |
| Écritures | 1 000 |
| Suppressions | 1 000 |
| Opérations de liste | 1 000 |
| Stockage | 1 Go |

Ces valeurs peuvent évoluer. Consultez les limites applicables à votre compte dans la documentation officielle :

- [Tarification de Workers KV](https://developers.cloudflare.com/kv/platform/pricing/)
- [Limites de Workers KV](https://developers.cloudflare.com/kv/platform/limits/)

Une seule action dans l'interface peut déclencher plusieurs opérations de stockage. Si vous prévoyez un usage important, surveillez donc votre consommation et les éventuelles erreurs de quota.

---

## Sécurité

Quelques précautions permettent de limiter les problèmes :

- Utilisez des mots de passe robustes.
- Gardez vos secrets Cloudflare confidentiels.
- Limitez l'accès à votre tableau de bord Cloudflare.
- Activez HTTPS sur votre domaine.
- Conservez une copie du code et des données importantes.
- Vérifiez les permissions avant de donner accès à d'autres utilisateurs.

La présence d'une fonction de protection par mot de passe ne suffit pas, à elle seule, à garantir la sécurité de l'ensemble de l'application.

---

## Dépannage

| Problème | Vérifications à effectuer |
|---|---|
| L'application ne démarre pas | Consultez les journaux d'exécution et vérifiez le déploiement. |
| Impossible d'enregistrer un lien | Vérifiez la liaison KV `LINKS` et les quotas disponibles. |
| La redirection ne fonctionne pas | Vérifiez le chemin, la destination et les éventuelles dates de disponibilité. |
| La connexion échoue | Vérifiez les identifiants et les variables attendues par le code. |
| Une erreur serveur apparaît | Consultez les journaux Cloudflare et recherchez la cause précise. |

Ne publiez jamais de secrets, de cookies de session ou d'informations personnelles dans un rapport de bug.

---

## Documentation

Pour approfondir la configuration, consultez la documentation officielle :

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
