# Projet : Régie live pour l'animation du mariage

Objectif : deux pages HTML (régie + affichage/conducteur) synchronisées en temps réel via Firebase, pour se coordonner pendant l'animation sans avoir à s'appeler ou se taper sur l'épaule.

---

## Étape 1 — Cadrer le besoin

**À faire :**
- Lister précisément ce qu'il faut synchroniser entre les deux pages. Exemples concrets pour un mariage :
  - l'étape en cours (ex: "Discours", "Ouverture du bal", "Lancer du bouquet")
  - un message libre / note rapide ("micro HS", "retard 10 min", "on décale le gâteau")
  - un minuteur ou horaire cible
- Décider qui a le rôle "régie" (celui qui pilote, écrit les infos) et qui a le rôle "affichage" (celui qui reçoit, en coulisse ou à la sono).
- Se mettre d'accord avec ton père sur cette liste avant de coder — ça évite de refaire la structure de données trois fois.

---

## Étape 2 — Créer le projet Firebase

**À faire :**
- Aller sur console.firebase.google.com, créer un nouveau projet (gratuit, pas de carte bancaire nécessaire pour ce usage).
- Activer **Realtime Database** (plus simple que Firestore pour ce cas d'usage : données très simples, mises à jour fréquentes, pas besoin de requêtes complexes).
- Choisir le mode **test** pour la base de données au démarrage (règles ouvertes), en sachant qu'il faudra les restreindre avant le jour J (voir étape 5).
- Récupérer la configuration du projet (un petit objet JavaScript avec `apiKey`, `databaseURL`, etc.) — Firebase te le donne dans les paramètres du projet.

---

## Étape 3 — Créer le dépôt GitHub

**À faire :**
- Créer un nouveau repo (ex: `mariage-regie`), toi ou ton père en propriétaire, et ajouter l'autre en collaborateur.
- Structure minimale du repo :
  ```
  mariage-regie/
    regie.html       (page de saisie/pilotage)
    affichage.html   (page de lecture)
    firebase-config.js
    README.md
  ```
- Cloner le repo en local (ou éditer directement sur GitHub si vous êtes à l'aise avec l'interface web, pour un petit projet ça suffit).

---

## Étape 4 — Coder la synchro de base

**À faire :**
- Dans chaque page HTML, inclure le SDK Firebase via `<script type="module">` (version CDN, pas besoin d'installer quoi que ce soit).
- Initialiser Firebase avec la config récupérée à l'étape 2.
- Sur la page **régie** : un formulaire simple (champ texte + bouton, ou boutons prédéfinis pour les étapes) qui fait un `set()` ou `update()` dans la Realtime Database à chaque changement.
- Sur la page **affichage** : un `onValue()` qui écoute la base et met à jour le DOM automatiquement dès qu'une donnée change, sans rafraîchissement de page.
- Commencer par une seule info (ex: "étape en cours") pour valider que la synchro marche, avant d'ajouter les autres champs (message, timing).

---

## Étape 5 — Sécuriser un minimum

**À faire :**
- Passer les règles de la Realtime Database du mode "test" (ouvert à tous) à des règles un peu plus restrictives, par exemple limiter l'écriture à un mot de passe simple ou un token partagé, histoire qu'un inconnu ne puisse pas modifier vos données.
- Pour un usage aussi ponctuel (une soirée), une sécurité légère suffit largement — pas besoin d'authentification complexe.

---

## Étape 6 — Héberger avec GitHub Pages

**À faire :**
- Dans les paramètres du repo GitHub, activer **GitHub Pages** sur la branche principale.
- Les deux pages deviennent accessibles via une URL publique (ex: `https://tonpseudo.github.io/mariage-regie/regie.html`).
- Vérifier que ça marche depuis deux appareils différents (ex: ton téléphone et celui de ton père), pas seulement en local.

---

## Étape 7 — Tester en conditions réelles

**À faire :**
- Faire un test grandeur nature quelques jours avant : un de vous deux sur la page régie, l'autre sur la page affichage, dans deux pièces différentes ou avec le wifi coupé sur un des deux (pour tester en 4G).
- Vérifier la latence (normalement quasi instantané), le comportement si la connexion coupe puis revient, et l'ergonomie sur mobile (gros boutons, lisible vite).
- Prévoir un plan B low-tech (ex: message WhatsApp) au cas où le wifi de la salle serait capricieux le jour J.

---

## Étape 8 — Jour J

**À faire :**
- Ouvrir les deux pages en avance, vérifier la connexion internet de la salle.
- Garder les téléphones chargés (ou une batterie externe) puisque tout repose sur la connexion.

---

### Prochaine étape concrète
Si tu veux, je peux te préparer directement un starter fonctionnel (les 2 fichiers HTML + la config Firebase de base, étape 2 à 4 déjà codées) que vous n'aurez plus qu'à adapter aux étapes précises de votre mariage.
