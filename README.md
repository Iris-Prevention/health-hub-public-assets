# health-hub-public-assets

Actifs publics de la plateforme Iris Prévention, servis par GitHub Pages :

- `terms/` — documents de CGU (plateforme et entreprises), consultés par les patients à l'enrôlement ;
- `email/` — actifs référencés par les e-mails transactionnels.

## Politique de publication — `terms/`

**Un fichier publié sous `terms/` est immuable** : une adresse sert un contenu unique et définitif, sans
modification, suppression ni renommage possible après publication. Les captures de consentement de
health-hub référencent ces fichiers par URL : écraser un PDF créerait une divergence silencieuse entre le
document consulté par les patients et la preuve de consentement stockée ; le supprimer casserait le chemin
consulté à l'enrôlement (404 → 503).

Pour faire évoluer des CGU :

1. publier le nouveau document sous un **nouveau nom de fichier** (ex. `platform-terms-fr-v2.pdf`) ;
2. mettre à jour le paramétrage côté health-hub (CGU de la plateforme, ou de l'entreprise concernée) pour
   pointer vers la nouvelle adresse — l'entrée en vigueur est immédiate pour les nouvelles inscriptions.

Le workflow [`terms-immutability`](./.github/workflows/terms-immutability.yml) fait respecter cette règle :
tout commit ou PR qui modifie, supprime ou renomme un fichier existant sous `terms/` échoue. Seuls les
ajouts sont autorisés. Le fichier `terms/immutability-canary.txt` sert de cible de test au garde-fou — comme
le reste du dossier, il ne se modifie pas.

Contexte : spec `F79-consent-document-cache` de health-hub (incident INC-2026-002).
