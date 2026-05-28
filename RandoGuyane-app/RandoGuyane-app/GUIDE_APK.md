# 📱 RandoGuyane — Guide de génération de l'APK

Ce projet transforme l'application web **RandoGuyane** en une vraie application Android (`.apk`) installable, grâce à **Capacitor** et **GitHub Actions**.

Tu n'as **rien à installer** sur ton ordinateur : GitHub compile l'APK pour toi, en ligne.

---

## 🗂️ Contenu du projet

```
RandoGuyane-app/
├── www/
│   └── index.html              ← l'application (carte, 32 sentiers, 8 cascades)
├── resources/
│   ├── icon.svg / icon.png     ← icône de l'app
│   └── splash.png              ← écran de démarrage
├── .github/workflows/
│   └── build-apk.yml           ← recette de compilation automatique
├── capacitor.config.json       ← configuration de l'app
├── package.json                ← dépendances
└── .gitignore
```

---

## 🚀 Étapes pour obtenir ton APK

### 1. Créer un dépôt GitHub

1. Va sur [github.com](https://github.com) et connecte-toi.
2. Clique sur le **+** en haut à droite → **New repository**.
3. Donne-lui un nom, par exemple `randoguyane`.
4. Laisse-le en **Public** (gratuit pour GitHub Actions).
5. **Ne coche rien** (pas de README, pas de .gitignore — on les a déjà).
6. Clique **Create repository**.

### 2. Envoyer le projet sur GitHub

**Option A — Glisser-déposer (le plus simple, sans logiciel)**

1. Sur la page de ton dépôt vide, clique sur le lien **« uploading an existing file »**.
2. Glisse-dépose **tout le contenu** du dossier `RandoGuyane-app` (pas le dossier lui-même, son contenu).
   - ⚠️ GitHub n'accepte pas les dossiers vides par glisser-déposer. Si le dossier `.github/workflows` ne monte pas, voir la note plus bas.
3. Écris un message (ex. « Premier import ») et clique **Commit changes**.

**Option B — En ligne de commande (si tu as Git installé)**

```bash
cd RandoGuyane-app
git init
git add .
git commit -m "Premier import RandoGuyane"
git branch -M main
git remote add origin https://github.com/TON-PSEUDO/randoguyane.git
git push -u origin main
```

> 📌 **Note importante sur le dossier `.github`** : par glisser-déposer, GitHub peut ignorer les dossiers commençant par un point. Si c'est le cas :
> - Crée le fichier manuellement : sur GitHub, clique **Add file → Create new file**, tape `.github/workflows/build-apk.yml` comme nom (les `/` créent les dossiers), puis colle le contenu du fichier `build-apk.yml`.

### 3. Lancer la compilation

Dès que les fichiers sont sur GitHub (notamment `.github/workflows/build-apk.yml`), la compilation **démarre automatiquement**.

Pour la suivre ou la relancer :

1. Va dans l'onglet **Actions** de ton dépôt.
2. Tu verras un workflow **« Build Android APK »** en cours (rond orange) puis terminé (coche verte ✅).
3. La première compilation prend **5 à 10 minutes** (GitHub télécharge Android SDK, etc.).

Pour la lancer manuellement : onglet **Actions** → clique sur **Build Android APK** → bouton **Run workflow**.

### 4. Télécharger l'APK

1. Quand le workflow affiche ✅, clique dessus.
2. En bas de la page, section **Artifacts**, tu trouveras **RandoGuyane-APK**.
3. Clique pour télécharger le `.zip`, décompresse-le → tu as `RandoGuyane.apk`.

> 💡 Si tu lances le workflow manuellement (**Run workflow**), une **Release** est aussi créée automatiquement avec l'APK attaché, dans l'onglet **Releases** de ton dépôt — plus pratique à partager.

### 5. Installer l'APK sur ton téléphone Android

1. Transfère `RandoGuyane.apk` sur ton téléphone (câble USB, email, Google Drive…).
2. Ouvre le fichier sur le téléphone.
3. Android va demander d'autoriser **« Installer des applications inconnues »** → accepte (c'est normal pour une app hors Play Store).
4. L'app **RandoGuyane** apparaît dans ton tiroir d'applications. 🎉

---

## 🔄 Modifier l'application plus tard

Pour changer le contenu (ajouter un sentier, corriger un texte…) :

1. Modifie `www/index.html` directement sur GitHub (crayon ✏️) ou en local.
2. Valide (**Commit**).
3. La compilation se relance toute seule → nouvel APK dans **Actions**.

---

## ❓ Questions fréquentes

**L'APK est-il signé pour le Google Play Store ?**
Non, c'est un APK *debug*, parfait pour installer directement sur des téléphones. Pour le publier sur le Play Store, il faudra une signature *release* (étape ultérieure si tu le souhaites).

**Faut-il internet pour utiliser l'app ?**
L'app et ses illustrations fonctionnent **hors-ligne**. Seul le **fond de carte OpenStreetMap** se télécharge à la demande (donc nécessite internet pour s'afficher la première fois).

**Combien ça coûte ?**
0 € — GitHub Actions est gratuit pour les dépôts publics.

---

*Application développée pour les sentiers et chutes du Parc naturel régional de Guyane.*
