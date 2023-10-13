# Projet DDD

## Problématique

_XYZ Hôtel_ est une entreprise d'hôtellerie implantée dans le business depuis une centaine d'années. Jusque là,
elle a réussi à être performante avec un système de réservations sur papier. Mais, rattrapée par le temps et victime de sa
renommée, l'entreprise souhaiterait se moderniser en
informatisant son système de gestion de réservations.

## Fonctionnalités

#### Créer son compte

Afin de prétendre à réserver son séjour au sein de l'hôtel, un client doit pouvoir créer un compte dans le système en
renseignant comme informations:
- son nom complet
- son adresse mail (unique au sein du système)
- son numéro de téléphone

En réponse, le système renverra un identifiant généré aléatoirement, et qu'il devra renseigner pour utiliser
les services de l'hôtel via le système.

#### Alimenter son portefeuille

Une spécifité de _XYZ Hôtel_ est que le paiement se fait exclusivement via un portefeuille électronique. Chaque client
dispose d'un portefeuille qu'il peut alimenter. Bien que l'entreprise soit implantée en France, les devises suivantes
sont acceptées:
- Euro
- Dollar
- Livre Sterling
- Yen
- Franc Suisse

Le solde du portefeuille sera en euros, une conversion sera donc appliquée si nécessaire.

#### Voir les infos des chambres

Le client peut voir les infos des chambres avant de faire sa réservation. Il aura un affichage avec ces infos:

- chambre standard: 50€ par nuit
    - Lit 1 place
    - Wifi
    - TV
- chambre supérieure: 100€ par nuit
    - Lit 2 places
    - Wifi
    - TV écran plat
    - Minibar
    - Climatiseur
- suite: 200€ par nuit
    - Lit 2 places
    - Wifi
    - TV écran plat
    - Minibar
    - Climatiseur
    - Baignoire
    - Terrasse

#### Effectuer une réservation

Le client peut effectuer une réservation en choisissant la date du check-in, le nombre de nuits et le/les chambres souhaitées

En réponse, la réservation du client est enregistrée dans le système, et le client est débité de 50%
de la somme totale. L'autre moitié sera payée le jour même. 

NB: On considère que chaque chambre est pour 1 personne, on ne tient donc pas en compte
la notion de capacité des chambres

NB: On ne prend pas en compte le stock des chambres

#### Confirmer une réservation

Le client doit payer l'autre moitié de la réservation pour la confirmer. 

NB: On ne considère pas la date de check-in ici, ce n'est pas grave si la confirmation est faite après la date de
check-in

# Rendu

### Design stratégique [5 pts]

- `Ubiquitous language`: lister des concepts métiers et leurs définitions
- `Bounded contexts`: créer un schéma représentant l'ensemble des contextes du métier
- `Context maps`: compléter le schéma des contextes bornés avec les relations entre les contextes
- `Core/Supporting/Generic domains`: identifier les domaine cœur, secondaires et generiques de votre système

### Design tactique [15 pts]

- `Entities`: lister les entités de votre système
- `Value Objects`: lister les "value objects" de votre système
- Implémenter le domaine dans sa totalité, en respectant ces règles:
  - la partie métier du système DOIT refléter la compréhension de l'expert métier, et donc pouvoir être compréhensible
  par celui-ci
  - le système ne DOIT PAS représenter d'états invalides
  - les signatures de fonctions (et des constructeurs de classes) ne doivent pas mentir. Elles doivent être explicites
  notamment sur les cas d'erreurs potentielles
- Implémenter la partie database, avec la base de données de votre choix entre:
  - un fichier texte
  - une base de données en mémoire H2
  - une base de données dans un container Docker (PostgreSQL, MySQL, MongoDB...)
- Implémenter la partie infrastructure, qui sera au choix soit:
  - un programme en ligne de commande
  - une API HTTP

# Conseils

- Commencer par coder le domaine, puis la base de données, puis l'interface.
C'est la partie domaine qui est la plus importante dans ce module.
- Dans le domaine lui-même, d'abord se focaliser sur le "core domain", avant d'attaquer le reste
