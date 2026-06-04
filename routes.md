liste des routes HTTP:

# Admin 

- CRUD admin sur toutes les entitées




# Utilisateur

- Ajouter une participation 
  - controle sur nb de place (>0), date (> aujd)
- Enelever sa participation
  - controle sur date (>72h avant)
- voir ses participations
  - Controle id
- voir tous les créneaux
- voir ses paniers
  - Controle id
- Créer un panier

- Créneaux
  - GET/
  - GET/:id
  - POST/ (admin) -> {nb_places > 0, date_debut > aujd, date_fin > aujd, status = pending, created_at = aujd}
  - PATCH/ (admin) -> {...}
