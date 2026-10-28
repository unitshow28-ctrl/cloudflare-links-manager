# ☁️ Cloudflare Links Manager by Bertrand

<div align="center">

### Tous vos liens. Un seul endroit.

**Créez, gérez et analysez vos redirections depuis votre propre espace d'administration.**

Un projet pensé pour simplifier la gestion de vos liens grâce à une interface centralisée et aux services Cloudflare.

<br>

[![Cloudflare](https://img.shields.io/badge/Powered_by-Cloudflare-F38020?style=for-the-badge\&logo=cloudflare\&logoColor=white)](https://www.cloudflare.com/)
![Workers KV](https://img.shields.io/badge/Storage-Workers_KV-2563EB?style=for-the-badge)
![Interface française](https://img.shields.io/badge/Interface-Fran%C3%A7aise-16A34A?style=for-the-badge)

<br>

[Découvrir les fonctionnalités](#-ce-que-vous-pouvez-faire) · [Voir les captures](#-aperçu-de-lapplication) · [Installer le projet](#-installation) · [Comprendre les coûts](#-est-ce-vraiment-gratuit)

</div>

---

## 📌 Sommaire

* [Le projet](#-le-projet)
* [Aperçu de l'application](#-aperçu-de-lapplication)

  * [Le tableau de bord](#le-tableau-de-bord)
  * [La gestion des liens](#la-gestion-des-liens)
  * [Le centre d'analyse](#le-centre-danalyse)
  * [Les utilisateurs et les groupes de droits](#les-utilisateurs-et-les-groupes-de-droits)
  * [Une interface personnalisable](#une-interface-personnalisable)
* [Ce que vous pouvez faire](#-ce-que-vous-pouvez-faire)
* [Comment ça fonctionne ?](#-comment-ça-fonctionne-)
* [Installation](#-installation)
* [Est-ce vraiment gratuit ?](#-est-ce-vraiment-gratuit-)
* [Quelques conseils de sécurité](#-quelques-conseils-de-sécurité)
* [Un problème pendant l'installation ?](#-un-problème-pendant-linstallation-)
* [Documentation utile](#-documentation-utile)
* [Vous avez trouvé un problème ?](#-vous-avez-trouvé-un-problème-)

---

## 🚀 Le projet

Vous avez des dizaines de liens à gérer ? Des redirections à modifier ? Des utilisateurs à administrer ?

**Cloudflare Links Manager rassemble tout cela au même endroit.**

L'application vous permet de créer des liens personnalisés, de gérer leurs destinations, de consulter les statistiques disponibles et d'organiser les accès à votre espace d'administration.

L'objectif est simple : vous proposer un outil pratique, personnalisable et hébergé sur votre propre infrastructure Cloudflare.

### À quoi ça sert ?

Imaginez que vous souhaitiez partager l'accès à plusieurs services de votre installation.

Au lieu de transmettre des adresses parfois longues ou difficiles à retenir, vous pouvez créer des liens personnalisés :

| Votre lien                      | Destination               |
| ------------------------------- | ------------------------- |
| `liens.mondomaine.fr/nextcloud` | Votre espace Nextcloud    |
| `liens.mondomaine.fr/docs`      | Votre documentation       |
| `liens.mondomaine.fr/contact`   | Votre page de contact     |
| `liens.mondomaine.fr/projet`    | Votre site ou application |

**Et si une adresse change ?**

Vous modifiez simplement la destination dans l'administration. Le lien partagé peut rester le même.

C'est tout l'intérêt d'un gestionnaire de redirections : **vous gardez le contrôle sur vos liens sans devoir tout recommencer à chaque changement.**

---

## 🖥️ Aperçu de l'application

Découvrez les différentes parties de l'interface et les possibilités offertes par Cloudflare Links Manager.

### Le tableau de bord

Retrouvez une vue d'ensemble de votre application dès votre arrivée dans l'espace d'administration.

<div align="center">

<img width="100%" alt="Tableau de bord de Cloudflare Links Manager" src="https://github.com/user-attachments/assets/170d1e16-0387-4467-9919-c84fc9888496" />

*Le tableau de bord principal*

</div>

### La gestion des liens

Créez vos redirections, gérez les destinations et retrouvez vos liens depuis un espace unique.

<div align="center">

<img width="100%" alt="Gestion des liens" src="https://github.com/user-attachments/assets/e65cdff7-a3c7-4c57-b0f8-4b40b17c6d97" />

*La gestion des liens et des redirections*

<br>

<img width="100%" alt="Page de redirection" src="https://github.com/user-attachments/assets/2c3e8cd2-da83-44db-9a28-3ae0fdcf3ffa" />

*Un exemple de page de redirection*

</div>

### Le centre d'analyse

Besoin de comprendre comment vos liens sont utilisés ?

Le centre d'analyse rassemble les statistiques disponibles pour vous aider à suivre l'activité de vos redirections.

<div align="center">

<img width="100%" alt="Centre d'analyse" src="https://github.com/user-attachments/assets/ba196009-4730-4268-94cd-cc0b7f728a39" />

<br>

<img width="100%" alt="Statistiques complémentaires" src="https://github.com/user-attachments/assets/f5150738-3e14-490d-b5b3-b9fefea6baa4" />

*Le centre d'analyse et ses statistiques*

</div>

### Les utilisateurs et les groupes de droits

L'application permet de gérer les comptes et d'organiser les permissions pour adapter les accès aux besoins de votre installation.

<div align="center">

<img width="100%" alt="Gestion des utilisateurs" src="https://github.com/user-attachments/assets/b429c0e0-60d2-4a8a-bcee-57019c32e094" />

*Gestion des utilisateurs*

<br>

<img width="100%" alt="Groupes de droits" src="https://github.com/user-attachments/assets/de9c7532-c53a-409b-a9ee-e61e042d7a71" />

<br>

<img width="55%" alt="Détails des permissions" src="https://github.com/user-attachments/assets/53d002c2-0020-4d91-be56-9adae1aafb2d" />

*Gestion des groupes et des permissions*

</div>

### Une interface personnalisable

Adaptez l'application à vos préférences et à votre environnement.

<div align="center">

<img width="100%" alt="Personnalisation de l'application" src="https://github.com/user-attachments/assets/34545c9a-865d-4780-8c58-da1910f27709" />

<br>

<img width="100%" alt="Options de personnalisation" src="https://github.com/user-attachments/assets/95a88bd7-fe18-4410-bcd3-b6bf96861bad" />

<br>

<img width="100%" alt="Aperçu de l'interface personnalisée" src="https://github.com/user-attachments/assets/c9b62249-abe0-4c94-a1f4-d5403bea29bc" />

*Personnalisation de l'interface*

</div>

---

## ✨ Ce que vous pouvez faire

### 🔗 Gérer vos liens

Tout se passe depuis l'interface d'administration.

* Créer des liens avec des adresses personnalisées.
* Modifier ou supprimer une redirection.
* Rediriger vers des destinations HTTP ou HTTPS.
* Définir des dates de début et de fin de disponibilité.
* Protéger certains liens par mot de passe.
* Créer des pages contenant un court texte.

Plus besoin de modifier manuellement le code à chaque changement de destination.

### 📊 Analyser l'activité

Le centre d'analyse vous permet de consulter les statistiques disponibles dans votre installation.

Vous disposez ainsi d'un espace dédié pour observer l'activité de vos liens et mieux comprendre leur utilisation.

Les indicateurs présentés dépendent des fonctionnalités effectivement disponibles dans la version déployée.

### 👥 Organiser les utilisateurs

Lorsque plusieurs personnes utilisent l'application, il devient important de bien organiser les accès.

Les fonctions disponibles comprennent notamment :

* La gestion des comptes utilisateurs.
* L'organisation en groupes de droits.
* La gestion des permissions selon les rôles disponibles.
* L'activation et la désactivation des comptes.
* La gestion des profils et des mots de passe.
* La gestion éventuelle de l'expiration des comptes.

L'idée est de pouvoir adapter les accès aux responsabilités de chacun, plutôt que de donner systématiquement les mêmes droits à tout le monde.

### 🎨 Personnaliser l'application

L'interface peut être adaptée à vos préférences grâce aux options de personnalisation disponibles.

Vous pouvez notamment retrouver des fonctions liées :

* Au nom du site.
* Au logo et aux textes.
* À l'apparence générale.
* Aux thèmes clair et sombre.

### 📁 Stocker des fichiers avec R2

Une configuration compatible avec Cloudflare R2 peut également permettre de stocker des fichiers, notamment des PDF, lorsque cette fonctionnalité est activée et correctement configurée.

---

## ⚙️ Comment ça fonctionne ?

Le projet s'appuie sur plusieurs services Cloudflare, chacun ayant un rôle précis.

| Service                   | Son rôle                              |
| ------------------------- | ------------------------------------- |
| **Cloudflare Pages**      | Hébergement de l'application          |
| **Cloudflare Workers**    | Exécution du code côté serveur        |
| **Cloudflare Workers KV** | Stockage des données de l'application |
| **Cloudflare R2**         | Stockage de fichiers facultatif       |

Cette architecture permet de faire fonctionner l'application sans administrer un serveur traditionnel.

Les services utilisés restent soumis aux quotas, aux conditions et aux éventuelles limites de votre offre Cloudflare.

---

## 📦 Installation

L'application est distribuée sous la forme d'une **archive ZIP téléchargeable depuis la release GitHub**.

Vous n'avez donc pas besoin de cloner le dépôt pour récupérer les fichiers.

### Avant de commencer

Vous aurez besoin de :

* Un compte Cloudflare.
* L'archive ZIP du projet.
* Un projet configuré pour le mode de déploiement compatible avec le code fourni.
* Un espace de noms Cloudflare Workers KV.

Un domaine personnalisé est recommandé pour obtenir des liens faciles à retenir. Vous pouvez néanmoins commencer par tester votre installation sur l'adresse fournie par Cloudflare.

### Étape 1 — Télécharger le projet

Téléchargez le fichier ZIP joint à la release GitHub.

Gardez une copie de l'archive originale : elle pourra vous servir si vous devez repartir d'une version propre.

### Étape 2 — Préparer Cloudflare Pages

Dans votre tableau de bord Cloudflare :

1. Ouvrez **Workers & Pages**.
2. Créez un projet ou sélectionnez un projet existant.
3. Configurez le mode de déploiement correspondant à la structure des fichiers fournis.
4. Ajoutez le fichier nécessaire au déploiement (glissez simplement le fichier ZIP après avoir choisi votre domaine).

### Étape 3 — Configurer Workers KV

L'application utilise Workers KV pour stocker ses données.

1. Ouvrez la section de stockage de Cloudflare.
2. Créez un espace de noms KV.
3. Ouvrez les paramètres de votre projet.
4. Ajoutez une liaison KV vers cet espace de noms.
5. Utilisez le nom de liaison attendu par le code, notamment `LINKS` si votre version le prévoit.

> **Attention :** le nom de l'espace de noms et celui de la liaison sont deux choses différentes. C'est le nom de la liaison qui doit correspondre à celui attendu par le code.

### Étape 4 — Configurer les secrets

Ajoutez les variables et secrets attendus par votre version de l'application.

| Variable         | Utilité                                                                 |
| ---------------- | ----------------------------------------------------------------------- |
| `ADMIN_PASSWORD` | Mot de passe administrateur initial, si utilisé par le code             |
| `SESSION_SECRET` | Secret lié à la gestion des sessions, selon l'implémentation            |
| `ADMIN_USER`     | Nom d'utilisateur administrateur, si cette variable est prise en charge |

Les noms et les usages doivent correspondre exactement à ceux définis dans `_worker.js`.

Choisissez des valeurs robustes et uniques.

### Étape 5 — Configurer R2 (facultatif)

Vous souhaitez utiliser le stockage de fichiers ?

1. Créez un compartiment Cloudflare R2.
2. Ajoutez la liaison correspondante à votre projet.
3. Utilisez le nom de liaison attendu par le code, par exemple `CONTENT_FILES` si votre version le prévoit.

Si vous n'avez pas besoin de cette fonctionnalité, vous pouvez passer directement à l'étape suivante.

### Étape 6 — Déployer et vérifier

Une fois la configuration terminée :

1. Enregistrez vos paramètres.
2. Déployez ou redéployez le projet.
3. Ouvrez l'application dans votre navigateur.
4. Connectez-vous avec les identifiants configurés.
5. Créez un premier lien de test.
6. Vérifiez que la redirection fonctionne.

En cas de problème, consultez les journaux d'exécution Cloudflare et vérifiez les liaisons et les variables de configuration.

---

## 💰 Est-ce vraiment gratuit ?

**Oui, il est possible d'utiliser le projet avec les offres gratuites de Cloudflare, sous certaines conditions.**

Il faut toutefois distinguer le code de l'application des services qui permettent de l'héberger.

Cloudflare propose des offres gratuites pour plusieurs de ses services, notamment Pages, Workers et Workers KV. Ces offres comportent des limites d'utilisation qui peuvent évoluer.

À titre indicatif, les quotas historiquement associés à l'offre gratuite de Workers KV comprennent :

| Opération           | Quota journalier indicatif |
| ------------------- | -------------------------: |
| Lectures            |                    100 000 |
| Écritures           |                      1 000 |
| Suppressions        |                      1 000 |
| Opérations de liste |                      1 000 |
| Stockage            |                       1 Go |

Ces chiffres sont indicatifs et ne constituent pas une garantie des limites actuellement applicables à votre compte.

Pour consulter les conditions à jour :

* [Tarification de Workers KV](https://developers.cloudflare.com/kv/platform/pricing/)
* [Limites de Workers KV](https://developers.cloudflare.com/kv/platform/limits/)
* [Tarification de Workers](https://developers.cloudflare.com/workers/platform/pricing/)
* [Documentation Cloudflare Pages](https://developers.cloudflare.com/pages/)

### Ce qu'il faut retenir

* Vous pouvez commencer sans payer d'hébergement si votre configuration respecte les conditions des offres gratuites.
* Workers KV est soumis à des quotas journaliers.
* Une seule action dans l'interface peut déclencher plusieurs opérations de stockage.
* Un usage important peut nécessiter une offre payante.
* L'achat d'un nom de domaine peut entraîner des frais supplémentaires.
* Les autres services utilisés, notamment R2, ont leurs propres conditions tarifaires.

**En clair :** vous pouvez mettre en place une installation gratuite dans une configuration adaptée, mais le coût dépend des services choisis et de votre utilisation.

---

## 🔐 Quelques conseils de sécurité

Avant de mettre votre installation à disposition d'autres personnes, prenez le temps de vérifier les points suivants :

* Utilisez des mots de passe robustes.
* Gardez vos secrets Cloudflare confidentiels.
* Limitez l'accès au tableau de bord Cloudflare aux personnes de confiance.
* Utilisez HTTPS sur votre domaine.
* Conservez une copie du code et des données importantes.
* Vérifiez les permissions avant de donner accès à d'autres utilisateurs.

La présence d'une protection par mot de passe ne garantit pas, à elle seule, la sécurité de toute l'application. L'authentification, la gestion des sessions et les permissions dépendent de l'implémentation du code déployé.

---

## 🛠️ Un problème pendant l'installation ?

Voici quelques vérifications utiles avant de chercher plus loin.

| Problème rencontré                | Que vérifier ?                                            |
| --------------------------------- | --------------------------------------------------------- |
| L'application ne démarre pas      | Le déploiement et les journaux d'exécution Cloudflare.    |
| Impossible d'enregistrer un lien  | La liaison KV et les quotas disponibles.                  |
| Une redirection ne fonctionne pas | Le chemin, la destination et les dates de disponibilité.  |
| La connexion échoue               | Les identifiants et les variables attendues par le code.  |
| Une erreur serveur apparaît       | Les journaux Cloudflare pour identifier la cause précise. |

Si vous demandez de l'aide, pensez à préciser les étapes qui ont provoqué le problème et à retirer toute information sensible des journaux partagés.

---

## 📚 Documentation utile

Pour aller plus loin dans la configuration de votre installation, voici les ressources officielles :

* [Cloudflare Pages](https://developers.cloudflare.com/pages/)
* [Cloudflare Workers](https://developers.cloudflare.com/workers/)
* [Cloudflare Workers KV](https://developers.cloudflare.com/kv/)
* [Cloudflare R2](https://developers.cloudflare.com/r2/)

---

## 🐛 Vous avez trouvé un problème ?

Les retours sont utiles pour améliorer le projet.

Si vous rencontrez un bug, indiquez si possible :

* La version de l'archive utilisée.
* Les étapes pour reproduire le problème.
* Le résultat attendu.
* Le résultat obtenu.
* Le message d'erreur, sans informations sensibles.

Un signalement clair permet de comprendre plus facilement ce qui se passe et de trouver une solution.

---

<div align="center">

### ☁️ Cloudflare Links Manager

**Vos liens, votre domaine, votre contrôle.**

Merci de prendre le temps de découvrir le projet.

*Développé par Bertrand.*

</div>
