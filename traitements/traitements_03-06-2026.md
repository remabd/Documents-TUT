# Partie mobile

## Voir son profil, ses participations et paniers passés

- Voir les informations importantes (rôle, nom, prénom)
- `Accordéon` pour voir ses précédents panier (liste déroulante)
  - au click sur un panier, `Modale` de détails du panier.
- `Accordéon` pour ses participations (passées et à venir).
  - Bouton annuler (seulement futures et avec conditions).
    - Au click -> `Modale` de confirmation -> Appel au backend -> Contrôle sur les conditions -> BDD
    - Feedback (`Toast`)
- Préférences
  - Menu déroulant
    - visualisation des informations de l'appli (RGPD)
    - `Modale` de choix de thème
    - `Modale` de choix des notifs
    - `Modale`de choix de langue
    - Signaler un problème
      - Formulaire de rédaction -> Appel au backend -> Appel à la base de donnée
    - À propos
      - Page vitrine Top'Coop + RSE
  
   
## Participation

- Information du quota d'heure restant.
- lien vers mes participations (page profil -> `Accordéon` ouvert et les autres fermés).
- Liste des créneaux disponibles (liste déroulante).
  - L'utilisateur peut sélectionner autant de créneaux qu'on veut.
  - Au click sur le bouton "Valider" -> `Modale`de récapitulatif (nom des activités, dates, personnes participantes).
    - À la deuxième validation -> Appel au backend -> contrôle sur la dispo -> Appel à la base de donnée.
      - Feedback de retour(`Toast`).

![Diagramme de séquence](./assets/sequence_participation.png)

## Panier

- Liste déroulante des articles au panier (Indication de quantité et prix).
  - Bouton de changement de quantité
  - Bouton de suppression de l'article du panier.
- Ajouter un article (scan ou catalogue) (boutons).
  - scan -> Ouverture d'un scanner code barre.
    - Au scan réussi, `Modale` de confirmation de scan + son.
  - catalogue (bouton) -> Liste déroulante des articles.
    - Champs de recherche (input text).
    - Indication de la quantité/status restante. 
- Valider son panier (bouton).
  - `Modale` de confirmation.
    - Appel au backend -> Appel à la base de donnée.
    - Feedback (`Toast`).

# Partie web

## Participations

- Système de `Tab`
  - Calendrier: Voir le planning des participations.
    - Au click sur un créneau libre -> `Modale` pour ajouter un créneau.
      - formulaire de saisie du nom, datetime (préremplie), nombre de places, infos supplémentaires.
        - Appel au backend -> Contrôle sur les champs requis (nom, datetime, nombre de places) -> Appel à la base de donnée.
        - Feedback (`Toast`)
    - Au click sur un créneau crée -> `Modale` pour voir et annuler le créneau.
      - Appel au backend -> Contrôle sur la date -> Appel à la base de donnée (Suppression du créneau et désinscription des participants).
        - Feedback (`Toast`)
        - Notifier les adhérents inscrits.
- Liste des adhérents: (liste déroulante).
  - Visibilité sur leurs quota de participations à réaliser.
  - Au click sur un participant -> `Modale` pour voir ses informations et dernières participations.
- Logs: visualisation des logs sous forme de liste déroulante:
  - Inscription, désinscription à un créneau
  - Ajout, modification ou suppression d'un créneau

## Administration

- Sous menu pour accéder aux différentes entités à administrer (liste de boutons).
- CRUD utilisateurs sous forme de table:
  - Ajouter Modifier Supprimer un utilisateur.
    - Appel au backend -> contrôle sur les champs -> Appel à la base de donnée.
    - Feedback (`Toast`)
  - Ajouter ou enlever le mode admin (sauf le sien).
    - Appel au backend -> Appel à la base de donnée.
    - Feedback (`Toast`)
- CRUD du reste des entités (produits, participations, etc.) sous forme de table.
  - Appel au backend -> contrôle sur les champs -> Appel à la base de donnée.
  - Feedback (`Toast`)

## Commande

- Systeme de `Tab`
  - Restock: Liste déroulante des produits consommés (qté max > qté réelle).
    - input pour changer la qté restockée.
    - checkbox pour ajouter ce produit au restock.
  - Champs de recherche pour trouver rapidement un produit à restocker
  - Bouton pour Valider une commande.
      - `Modale` de confirmation.
        - Appel au backend -> Appel à la BDD.
      - Feedback `Toast`
- Catalogue: Liste déroulante des produits (pour les rajouter).
  - Chaque produit a son input pour ajouter quantité et ajouter au restock (déja coché).
  - Bouton d'ajout d'un nouveau produit au catalogue
    - `Modale` comme administration.
