# Douce Garde — Baby-sitting avec Léa

Site vitrine et de réservation de baby-sitting, déployé sur GitHub Pages :
**https://amsolutions-pro.github.io/douce-garde-babysitting/**

## Fonctionnalités

- **Réservation par quarts d'heure** : grille tactile de créneaux de 15 min
  (matin 7h–9h, fin de journée 16h–19h) sur 14 jours, estimation du prix en direct
  (8 €/h, +2 €/h après 20h, minimum 1 h).
- **Demande par WhatsApp** : le formulaire génère un message pré-rempli envoyé
  au numéro de Léa — aucun backend, aucune donnée stockée en ligne.
- **Connexion Google** (optionnelle) : pré-remplit prénom/nom et mémorise le
  profil sur l'appareil. Les autres infos (téléphone, adresse, enfants) sont
  mémorisées en `localStorage` à chaque envoi.
- **Mode pro (admin)** : accessible via `#pro` à la fin de l'adresse, ou
  automatiquement quand un compte Google listé dans `EMAILS_ADMIN` se connecte.
  Permet de bloquer/libérer des créneaux et d'enregistrer `disponibilites.json`
  via l'API GitHub (jeton personnel requis) ou par copier-coller.

## Structure

| Fichier | Rôle |
|---|---|
| `index.html` | Tout le site (HTML + CSS + JS inline) |
| `disponibilites.json` | Créneaux occupés, lus au chargement |
| `404.html` | Redirection vers l'accueil |

## Configuration (constantes en tête du script dans `index.html`)

- `NUMERO_WHATSAPP` — numéro qui reçoit les demandes
- `FENETRES`, `NB_JOURS_AFFICHES` — créneaux proposés
- `TARIF_HORAIRE`, `MAJORATION_SOIREE`, `MINIMUM_FACTURE` — tarification
- `GOOGLE_CLIENT_ID` — ID client OAuth (console.cloud.google.com) ; le bloc
  Google reste masqué tant qu'il n'est pas renseigné
- `EMAILS_ADMIN` — comptes Google ayant le mode pro automatique

## Développement local

```bash
python -m http.server 8123
# puis ouvrir http://localhost:8123
```

Le déploiement se fait en fusionnant dans `main` (GitHub Pages).
