<div align="center">

# 🔗 Cloudflare Links Manager

### ✨ Toutes tes redirections au même endroit.

<p>
  Un gestionnaire de liens léger, personnalisable et hébergé sur Cloudflare.
  <br>
  Crée des URL courtes, gère les accès et partage tes services facilement.
</p>

<p>
  <img src="https://img.shields.io/badge/Cloudflare-Pages-orange?logo=cloudflare" alt="Cloudflare Pages">
  <img src="https://img.shields.io/badge/Cloudflare-Workers%20KV-orange?logo=cloudflare" alt="Cloudflare Workers KV">
  <img src="https://img.shields.io/badge/Interface-Fran%C3%A7ais-blue" alt="Interface française">
  <img src="https://img.shields.io/badge/Co%C3%BBt-Plan%20gratuit%20possible-brightgreen" alt="Plan gratuit possible">
</p>

</div>

---

## 📖 Sommaire

- [👋 Présentation](#-présentation)
- [✨ Fonctionnalités](#-fonctionnalités)
- [🖥️ Exemples d'utilisation](#️-exemples-dutilisation)
- [⚙️ Prérequis](#️-prérequis)
- [🚀 Installation pas à pas](#-installation-pas-à-pas)
- [🔐 Configuration et sécurité](#-configuration-et-sécurité)
- [📊 Limites de Cloudflare KV](#-limites-de-cloudflare-kv)
- [🧯 Dépannage](#-dépannage)
- [🗂️ Organisation des données](#️-organisation-des-données)
- [💡 Conseils](#-conseils)
- [📚 Documentation officielle](#-documentation-officielle)

---

## 👋 Présentation

**Cloudflare Links Manager** est une application web conçue pour centraliser la gestion de redirections URL.

Tu héberges plusieurs services, tu as des liens difficiles à retenir ou tu souhaites partager des adresses sans dévoiler leurs URL complètes ? Cette application te permet de créer des liens courts, faciles à utiliser et administrables depuis une interface web.

Par exemple, au lieu de partager une longue adresse, tu peux utiliser :

| Lien court | Destination |
|---|---|
| `liens.mondomaine.fr/nextcloud` | Ton instance Nextcloud |
| `liens.mondomaine.fr/photos` | Ta galerie photo |
| `liens.mondomaine.fr/docs` | Tes documents |
| `liens.mondomaine.fr/projet` | Un site ou projet particulier |

Les exemples ci-dessus sont fictifs : les destinations dépendent de ta propre configuration.

L'application s'appuie sur les services Cloudflare pour exécuter le code et stocker les informations nécessaires.

### 🎯 L'objectif

- Une interface centralisée pour gérer tes liens.
- Une administration avec plusieurs utilisateurs et différents niveaux de droits.
- Des redirections configurables.
- Des options de personnalisation.
- Des statistiques pour suivre l'utilisation des liens.
- Une infrastructure pouvant fonctionner dans les limites du forfait gratuit de Cloudflare.

> 💡 **Important :** le forfait gratuit n'est pas illimité. Les quotas de stockage et d'exécution doivent être pris en compte, notamment lorsque tu modifies souvent tes redirections ou tes paramètres.

---

## ✨ Fonctionnalités

### 🔗 Gestion des redirections

L'application permet de créer et de gérer des liens courts.

Selon les options disponibles dans l'interface, tu peux notamment :

- Définir un nom personnalisé pour chaque lien.
- Choisir une destination externe.
- Modifier une redirection existante.
- Supprimer une redirection.
- Configurer une période de disponibilité.
- Définir une date de début et une date d'expiration.
- Protéger certains liens par un mot de passe.
- Copier rapidement une adresse pour la partager.

### 📝 Pages de texte

Le projet comprend également une fonctionnalité de publication de contenu texte enrichi.

Elle permet de créer une petite page accessible depuis une URL courte, sans devoir héberger un site séparé.

### 👥 Gestion des utilisateurs

L'administration prend en charge plusieurs comptes.

Les fonctionnalités comprennent notamment :

- La création et la modification des utilisateurs.
- La désactivation de comptes.
- La gestion des droits d'accès.
- La limitation de la période de validité de certains comptes.
- La gestion du profil.
- Le changement de mot de passe.
- La demande de changement de mot de passe à la première connexion.

### 🛡️ Permissions et groupes

Les droits permettent de contrôler les actions accessibles à chaque utilisateur.

Les groupes prédéfinis comprennent :

- **Super-Admin** : administration complète.
- **Utilisateur Standard** : utilisation courante selon les permissions attribuées.
- **Lecteur** : consultation des éléments autorisés.
- **Utilisateur Restreint** : accès limité.
- **Personnalisé** : groupe adapté à des besoins particuliers.

Les permissions peuvent notamment contrôler la consultation, la création, la modification et la suppression des liens, ainsi que la gestion des utilisateurs et l'accès aux statistiques.

### 📊 Statistiques

Le centre d'analyse permet de consulter les informations d'utilisation enregistrées par l'application.

L'accès dépend des permissions du compte.

### 🎨 Personnalisation

L'interface propose des options de personnalisation, notamment :

- Le nom du site.
- Les textes de présentation.
- Le logo.
- L'apparence.
- Le thème clair ou sombre.
- Certaines préférences individuelles.

### 📄 Stockage de fichiers

Le code prévoit également un binding R2 optionnel nommé `CONTENT_FILES`, destiné aux anciens fichiers PDF hébergés.

Cette fonctionnalité nécessite une configuration R2 appropriée et n'est pas indispensable au fonctionnement des redirections externes.

---

## 🖥️ Exemples d'utilisation

Voici quelques idées pour exploiter le gestionnaire :

| Usage | Exemple de lien |
|---|---|
| Cloud personnel | `liens.mondomaine.fr/cloud` |
| Galerie photo | `liens.mondomaine.fr/photos` |
| Documentation | `liens.mondomaine.fr/docs` |
| Projet temporaire | `liens.mondomaine.fr/projet` |
| Page d'information | `liens.mondomaine.fr/infos` |

Tu peux utiliser ton propre domaine ou un sous-domaine associé à Cloudflare Pages.

Les liens sont des exemples : ils ne seront accessibles qu'une fois le domaine configuré et les redirections créées.

---

## ⚙️ Prérequis

Avant de commencer, assure-toi de disposer des éléments suivants :

- Un compte Cloudflare.
- Un projet Cloudflare Pages configuré pour exécuter le Worker fourni.
- Un namespace Cloudflare Workers KV.
- Un navigateur web récent.
- Un mot de passe d'administration.
- Un secret de session aléatoire.

Un nom de domaine personnalisé est facultatif, mais recommandé pour obtenir des liens faciles à retenir.

### 🧰 Les services utilisés

| Service | Rôle |
|---|---|
| Cloudflare Pages | Hébergement du projet |
| Cloudflare Workers | Exécution du code côté serveur |
| Cloudflare Workers KV | Stockage des redirections et des paramètres |
| Cloudflare R2 | Stockage de fichiers optionnel |

---

## 🚀 Installation pas à pas

Pas besoin d'être développeur pour suivre ce guide. Il suffit de prendre le temps de vérifier chaque réglage.

### Étape 1 — Récupérer le projet

Télécharge le fichier `_worker.js` fourni dans le dépôt.

Il contient le code de l'application.

Le projet utilise le mode avancé des Workers pour Pages : il ne suffit donc pas de déposer le fichier comme une simple page HTML statique.

### Étape 2 — Créer un projet Cloudflare Pages

1. Connecte-toi au [tableau de bord Cloudflare](https://dash.cloudflare.com/).
2. Ouvre **Workers & Pages**.
3. Crée un projet Pages ou sélectionne un projet existant.
4. Configure le déploiement pour utiliser le Worker fourni.
5. Déploie le projet selon le mode de déploiement choisi.

Tu peux commencer avec le domaine attribué par Cloudflare, puis configurer un domaine personnalisé ultérieurement.

📚 Documentation : [Cloudflare Pages](https://developers.cloudflare.com/pages/)

### Étape 3 — Créer le stockage KV

Cloudflare KV sert à conserver les informations de l'application.

1. Dans le tableau de bord, ouvre la section **Workers & Pages**, puis **KV**.
2. Crée un namespace.
3. Donne-lui un nom explicite, par exemple `liens-database`.
4. Enregistre le namespace.

Le nom du namespace est libre. C'est le nom du **binding** qui doit respecter exactement la configuration attendue par le code.

### Étape 4 — Ajouter le binding `LINKS`

Retourne dans les paramètres de ton projet.

1. Ouvre les paramètres du projet.
2. Accède à la section des bindings.
3. Ajoute un binding de type **KV namespace**.
4. Renseigne le nom de variable suivant :

`LINKS`

5. Sélectionne le namespace créé à l'étape précédente.
6. Enregistre.

⚠️ Attention : `LINKS` doit être écrit exactement ainsi, en majuscules.

Si tu nommes le binding `links`, `KV` ou `DATABASE`, le code ne trouvera pas le stockage attendu.

📚 Documentation : [Configurer un binding KV](https://developers.cloudflare.com/kv/get-started/)

### Étape 5 — Configurer les secrets

Le projet utilise deux secrets obligatoires.

Dans les paramètres de ton projet, ouvre la section **Variables and Secrets**.

Ajoute les valeurs suivantes :

| Nom | Type | Rôle |
|---|---|---|
| `ADMIN_PASSWORD` | Secret | Mot de passe d'administration |
| `SESSION_SECRET` | Secret | Signature des sessions |

#### `ADMIN_PASSWORD`

Choisis un mot de passe long et difficile à deviner.

Évite les mots de passe déjà utilisés sur d'autres sites.

#### `SESSION_SECRET`

Ce secret est utilisé pour sécuriser les sessions d'administration.

Il doit être aléatoire, suffisamment long et différent du mot de passe.

Ne publie jamais ces deux valeurs dans ton dépôt GitHub.

### Étape 6 — Configurer l'identifiant administrateur

Le projet prend en charge une variable facultative :

`ADMIN_USER`

Elle définit l'identifiant du compte propriétaire.

Si cette variable n'est pas définie, le code utilise par défaut :

`bertrand`

Tu peux donc définir ton propre identifiant si tu préfères ne pas conserver cette valeur par défaut.

Respecte le format accepté par l'application : lettres minuscules, chiffres, tirets et tirets bas, en commençant par une lettre ou un chiffre.

### Étape 7 — Ajouter R2 si nécessaire

Cette étape est facultative.

Si tu souhaites utiliser la fonctionnalité de stockage de fichiers PDF prévue par le projet :

1. Crée un bucket Cloudflare R2.
2. Retourne dans les paramètres de ton projet.
3. Ajoute un binding R2.
4. Nomme-le exactement `CONTENT_FILES`.
5. Sélectionne le bucket correspondant.

Pour les redirections externes classiques, cette configuration n'est pas nécessaire.

📚 Documentation : [Cloudflare R2](https://developers.cloudflare.com/r2/)

### Étape 8 — Déployer le projet

Une fois les bindings et les secrets configurés :

1. Vérifie que tous les noms sont corrects.
2. Enregistre les paramètres.
3. Lance un nouveau déploiement si nécessaire.
4. Attends que Cloudflare indique que le déploiement est terminé.
5. Ouvre le domaine de ton application.

Si tu utilises des environnements Production et Preview, vérifie que les bindings et secrets sont configurés dans l'environnement que tu souhaites utiliser.

### Étape 9 — Se connecter à l'administration

Ouvre l'adresse de ton application, puis accède à la page d'administration.

Connecte-toi avec l'identifiant propriétaire et le mot de passe configuré.

Tu pourras ensuite créer tes premières redirections et gérer les utilisateurs selon les permissions disponibles.

🎉 **Félicitations !** Ton gestionnaire est prêt à être configuré.

---

## 🔐 Configuration et sécurité

Quelques règles simples permettent d'éviter les mauvaises surprises.

### Protéger les secrets

Ne partage jamais publiquement :

- `ADMIN_PASSWORD`
- `SESSION_SECRET`

Ne les écris pas dans le README, dans le code source ou dans une capture d'écran publique.

### Utiliser HTTPS

Utilise HTTPS pour accéder à l'administration et partager les liens.

Si tu relies un domaine personnalisé à Cloudflare, vérifie sa configuration DNS et son certificat TLS.

### Limiter les permissions

N'accorde pas les droits d'administration à tous les utilisateurs.

Attribue uniquement les permissions nécessaires à chaque compte.

### Comprendre les liens protégés

Un lien protégé par mot de passe ajoute une barrière d'accès, mais ne remplace pas un système d'authentification complet pour des données sensibles.

Évite de partager publiquement des informations confidentielles.

### Sauvegarder les données

Les informations sont conservées dans KV. Pour les données importantes, prévois une stratégie de sauvegarde adaptée.

Ne supprime pas manuellement des clés KV sans comprendre leur rôle.

---

## 📊 Limites de Cloudflare KV

Cloudflare Workers KV est pratique pour ce type d'application, mais il possède des quotas.

Sur l'offre gratuite Workers, les limites documentées sont les suivantes :

| Opération | Quota gratuit |
|---|---:|
| Lectures | 100 000 par jour |
| Écritures | 1 000 par jour |
| Suppressions | 1 000 par jour |
| Opérations de liste | 1 000 par jour |
| Stockage | 1 Go |

Ces quotas sont réinitialisés chaque jour à **00:00 UTC**. Si un quota est dépassé, les opérations correspondantes peuvent échouer jusqu'à sa réinitialisation.

📚 Références officielles :
- [Tarification de Workers KV](https://developers.cloudflare.com/kv/platform/pricing/)
- [Limites de Workers KV](https://developers.cloudflare.com/kv/platform/limits/)

### 🧠 Qu'est-ce qu'une lecture ?

Une lecture correspond à une opération qui récupère une valeur depuis KV.

Par exemple, l'application peut devoir lire les informations d'une redirection ou les paramètres d'un compte.

Les consultations du site peuvent donc contribuer au quota de lectures, selon le fonctionnement du code.

### ✏️ Qu'est-ce qu'une écriture ?

Une écriture correspond à l'enregistrement d'une valeur dans KV.

Par exemple :

- Créer une redirection.
- Modifier une redirection.
- Enregistrer certains paramètres.
- Modifier des informations de compte.
- Enregistrer des données de suivi.

Une action dans l'interface peut entraîner plusieurs opérations KV. Il ne faut donc pas supposer qu'un clic correspond toujours à une seule écriture.

### 🗑️ Qu'est-ce qu'une suppression ?

Une suppression est une opération qui retire une clé de KV.

La suppression d'un lien ou d'une autre donnée peut consommer ce quota.

### 📋 Qu'est-ce qu'une opération de liste ?

Une opération de liste sert à parcourir les clés d'un namespace.

Elle peut être utilisée pour rechercher les données présentes dans le stockage.

### ⚠️ Que se passe-t-il si le quota est dépassé ?

Si tu dépasses le quota d'écritures, les modifications qui nécessitent une écriture peuvent échouer.

Tu peux alors constater :

- Une redirection qui ne se sauvegarde pas.
- Une modification de compte qui échoue.
- Une erreur renvoyée par le Worker.
- Une erreur Cloudflare 1101 si une exception n'est pas correctement gérée par le code.

Une erreur 1101 n'indique pas systématiquement un quota dépassé. Il faut consulter les logs du Worker pour confirmer la cause.

### 🕛 Quand les quotas sont-ils réinitialisés ?

Les quotas gratuits sont réinitialisés à minuit UTC, et non nécessairement à minuit selon ton heure locale.

Après la réinitialisation, les opérations peuvent de nouveau fonctionner si le quota concerné était la cause du problème.

### 💳 Et avec une offre payante ?

L'offre payante utilise une tarification différente, avec des allocations mensuelles et des coûts supplémentaires selon l'utilisation.

Les prix et allocations peuvent évoluer. Consulte toujours la [tarification officielle de Workers KV](https://developers.cloudflare.com/kv/platform/pricing/) avant de changer d'offre.

### 💡 Comment éviter de consommer trop d
