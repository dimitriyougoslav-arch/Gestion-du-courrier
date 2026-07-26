# Gestion des Courriers — Arrivés / Départs

Application 100 % hors-ligne : interface web moderne + **base de données SQL (SQLite)** stockée en permanence sur cet ordinateur.

## Installation

1. Placez **gestion_courriers.html** dans un dossier permanent (ex : `Documents\GestionCourriers\`).
2. Double-cliquez dessus : il s'ouvre dans votre navigateur, sans connexion internet requise.
3. Créez un raccourci sur le Bureau pour un accès rapide.

Ce mode fonctionne toujours et reste le plus simple : aucun serveur requis, aucune installation logicielle.

## Où sont stockées mes données ?

Cette application utilise **deux niveaux de stockage sur le disque dur**, expliqués dans l'onglet **Administration** :

1. **Stockage interne (toujours actif, automatique)** — la base SQL est enregistrée dans le stockage sécurisé du navigateur, physiquement sur le disque de cet ordinateur, à chaque ajout/modification/suppression et toutes les 30 secondes. C'est fiable et ne demande aucune action.
2. **Fichier .sqlite visible sur le disque (optionnel)** — depuis l'onglet **Administration → Stockage des données**, vous pouvez cliquer sur **« Créer un nouveau fichier sur le disque »** pour choisir un emplacement (ex : vos Documents). Un vrai fichier `.sqlite`, ouvrable avec n'importe quel outil compatible SQLite (DB Browser for SQLite, etc.), sera alors mis à jour automatiquement à chaque enregistrement, en plus du stockage interne. Vous pouvez aussi connecter un fichier `.sqlite` déjà existant. Cette option nécessite Chrome ou Edge (technologie File System Access) ; les autres navigateurs continuent d'utiliser uniquement le stockage interne, qui fonctionne normalement.

## Mot de passe oublié / récupération / changement

- **Sur l'écran de connexion** : un lien **« Mot de passe oublié ? »** permet, si une question secrète a été configurée pour le profil, de la vérifier puis de définir un nouveau mot de passe soi-même, sans aide extérieure.
- **Une fois connecté** : cliquez sur votre nom (en haut à droite) pour ouvrir **« Mon profil »**, où vous pouvez changer votre mot de passe (avec vérification de l'ancien) et définir/modifier votre question secrète à tout moment.
- **Réinitialisation par un administrateur** : dans l'onglet **Administration**, tout compte de fonction « Administrateur » peut cliquer sur l'icône 🔑 en face d'un profil pour lui définir directement un nouveau mot de passe — utile si l'utilisateur n'avait pas configuré de question secrète.

La question secrète est fortement recommandée dès la création du tout premier compte administrateur, car c'est le seul moyen de récupération tant qu'aucun autre administrateur n'existe.

## Premier démarrage

Création d'un compte administrateur (nom, identifiant, mot de passe, question secrète recommandée). La case « Rester connecté sur cet ordinateur » recharge automatiquement votre profil aux ouvertures suivantes.

## Structure des Courriers Arrivés

| Champ | Description |
|---|---|
| Réf. Courrier | Généré automatiquement (premier champ affiché) |
| Nature | Liste évolutive |
| Date de réception / Heure | |
| Origine | Secrétariat Général / DGFP / Cabinet du Ministre / Autre |
| Objet | |
| Provenance | Liste évolutive |
| Instructions (Oui/Non) | Précision si Oui |
| Deadline (Oui/Non) | Date limite suggérée à J+2, modifiable |
| Traitement à faire | |
| Service concerné | Liste évolutive |
| Statut | Liste extensible |
| Observations | |

## Structure des Courriers Départs

| Champ | Description |
|---|---|
| Réf. Courrier | Généré automatiquement (premier champ affiché) |
| Nature | Liste évolutive |
| Objet du courrier | |
| Date de réception / Date de rédaction / Date d'envoi | |
| Délai de traitement | Calculé automatiquement (Date d'envoi − Date de réception) |
| Heure d'envoi | |
| Id. du déposant | Liste évolutive |
| Statut du courrier | Liste extensible |

## Profils utilisateurs et fonctions

Administrateur, Directeur, Chef de Service, Vérificateur, Générateur, Agent, ou toute fonction personnalisée ajoutée à la volée lors de la création d'un profil.

## Partage sur un réseau ou entre postes

1. Onglet **Administration** → **Exporter la base (.sqlite)**.
2. Transférez le fichier vers l'autre poste (réseau partagé, clé USB, email…).
3. Sur l'autre poste : **Administration** → **Importer une base (.sqlite)**.

⚠️ L'import remplace intégralement les données locales du poste de destination.

## Installation en tant qu'application de bureau (PWA, optionnel)

Si le fichier est hébergé via un serveur local, un intranet ou un site web (adresse `http://` ou `https://`), un bouton **« Installer l'application »** apparaît dans l'onglet Administration pour créer une icône de bureau et ouvrir l'application dans sa propre fenêtre. Non disponible en ouverture directe du fichier (restriction de sécurité des navigateurs).

## Export CSV

Chaque registre dispose d'un bouton « Exporter CSV » pour un tableur (Excel, LibreOffice).
