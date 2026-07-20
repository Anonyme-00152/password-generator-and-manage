# Aetheris Vault

Coffre-fort de mots de passe **100 % local**. Aucune base de données, aucun serveur, aucun compte.
Tout est chiffré et stocké dans le `localStorage` de votre navigateur.

## Ce qui est sûr à publier

Le code de cette app ne contient **aucune** de vos données. Vos identifiants sont
enregistrés uniquement dans le navigateur de votre appareil, chiffrés avec votre
mot de passe maître (AES-GCM 256, clé dérivée en PBKDF2 250 000 itérations).

Publier le site en public = publier une app vide. Chaque visiteur ne voit que ses
propres données, dans son propre navigateur.

## Déployer sur Vercel

1. Renommez `vault.html` en **`index.html`** (Vercel sert `index.html` par défaut).
   Vous pouvez garder `forge.html` (le générateur) à côté.
2. Créez un dépôt GitHub et poussez les fichiers :
   ```bash
   git init
   git add .
   git commit -m "Aetheris Vault"
   git branch -M main
   git remote add origin https://github.com/VOTRE_USER/aetheris-vault.git
   git push -u origin main
   ```
3. Sur [vercel.com](https://vercel.com) : **Add New → Project → Import** votre dépôt.
   Framework preset : **Other**. Aucun build command. Cliquez **Deploy**.
4. Terminé. Votre coffre est en ligne en HTTPS (obligatoire pour le chiffrement Web Crypto).

## À NE JAMAIS committer

- Les fichiers `aetheris-vault-*.json` que vous exportez : **ils ne sont PAS chiffrés**.
  Ils servent de sauvegarde/transfert entre appareils, à garder en privé.
- Le `.gitignore` fourni les exclut déjà par précaution.

## Bon à savoir

- **Pas de récupération** : si vous oubliez le mot de passe maître, les données chiffrées
  sont définitivement illisibles. Notez-le en lieu sûr.
- `localStorage` est **par navigateur et par appareil** — il n'y a pas de synchronisation.
  Utilisez Export/Import JSON pour transférer votre coffre ailleurs.
- Vider le cache/les données du site efface le coffre local. Faites des exports réguliers.
