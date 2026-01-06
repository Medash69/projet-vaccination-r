# 🔬 Analyse des Campagnes de Vaccination Animale

## 📋 Description du Projet

Ce projet constitue une **analyse statistique complète** des campagnes de vaccination animale menées dans le **Gouvernorat de Sousse (2017-2020)** en Tunisie.

### 🎯 Objectifs Principaux

1. **Analyser l'évolution temporelle** des campagnes de vaccination (2017-2020)
2. **Mesurer les taux de couverture vaccinale** par espèce et campagne
3. **Évaluer l'écart** entre objectifs et réalisations
4. **Classer les campagnes** par efficacité
5. **Identifier les points d'amélioration** et recommandations stratégiques
6. **Modéliser les relations** entre variables (régression linéaire)

### 📊 Données Utilisées

- **Source** : Catalogue Open Data Tunisie (CRDA Sousse)
- **Période** : 2017-2020 (4 ans)
- **Observations** : 44 enregistrements
- **Variables** : 7 colonnes
- **Maladies couvertes** : Rage, Fièvre Aphteuse, Clavelée, Blue Tongue
- **Espèces** : Bovins, Ovins, Caprins, Chats, Chiens

---

## 🛠️ Technologies Utilisées

### Langage et Frameworks

| Technologie | Description | Version |
|:---|:---|:---|
| **R** | Langage de programmation statistique | 4.3.1 |
| **Quarto** | Format de rapport dynamique (Markdown + Code) | - |
| **RMarkdown** | Documentation interactive | - |

### Bibliothèques R Principales

```r
library(tidyverse)    # Manipulation et visualisation de données
library(ggplot2)      # Graphiques avancés
library(ggthemes)     # Thèmes personnalisés
library(scales)       # Formatage des échelles
library(knitr)        # Rapports dynamiques
library(kableExtra)   # Tables améliorées
library(readxl)       # Lecture fichiers Excel
```

### Analyses Statistiques

- ✅ Statistiques descriptives (moyenne, écart-type, quartiles)
- ✅ Analyse de variance (ANOVA)
- ✅ Test post-hoc de Tukey
- ✅ Régression linéaire
- ✅ Visualisations avancées (heatmaps, graphiques temporels)

---

## 🚀 Quarto : Format de Rapport Dynamique

### Qu'est-ce que Quarto ?

**Quarto** est un système de publication scientifique et technique qui combine :
- 📝 **Markdown** pour le texte et la mise en forme
- 💻 **Code R** (ou Python, Julia, Observable) pour les analyses
- 📊 **Résultats** générés automatiquement

### Configuration du Projet Quarto

Le projet utilise le fichier `presentationProjetR.qmd` avec la configuration suivante :

```yaml
---
title: "Analyse des Campagnes de Vaccination Animale"
subtitle: "Gouvernorat de Sousse (2017-2020)"
author: "Meddeb Acharf"
date: "2025-12-29"
format:
  html:
    theme: flatly
    code-fold: true
    code-tools: true
    toc: true
    toc-depth: 2
    number-sections: true
    highlight-style: github
    self-contained: true
    fig-width: 12
    fig-height: 8
---
```

### Avantages de Quarto

| Avantage | Description |
|:---|:---|
| 🔄 **Reproductibilité** | Code et résultats intégrés dans un seul document |
| 📱 **Format flexible** | Export en HTML, PDF, DOCX, Revealjs (présentations) |
| 🎨 **Styling avancé** | Thèmes personnalisés et CSS customisé |
| 🔐 **Traçabilité** | Version contrôle du code et de l'analyse |
| 🚀 **Automatisation** | Génération de rapports automatisée |

### Commandes Quarto Essentielles

```bash
# Installer Quarto
# https://quarto.org/docs/get-started/

# Rendre le document (générer HTML/PDF)
quarto render presentationProjetR.qmd

# Visualiser le résultat en temps réel
quarto preview presentationProjetR.qmd

# Créer un nouveau projet Quarto
quarto create-project mon-projet
```

---

## 📁 Structure du Projet

```
projetR/
├── README.md                                  # Ce fichier
├── presentationProjetR.qmd                    # Rapport Quarto
├── presentationProjetR.html                   # HTML généré
├── indexProjetR.html                         # Page d'accueil
├── index.html                                 # Alternative accueil
├── Data/
│   └── campagnes-de-vaccination-2017-2020.xlsx  # Données brutes
├── _quarto.yml                               # Configuration Quarto
└── .gitignore                                # Fichiers à ignorer
```

---

## 🌐 Déploiement sur GitHub Pages

### Configuration GitHub Pages

Le projet est déployé automatiquement sur GitHub Pages à l'adresse :
🔗 **https://medash69.github.io/projet-vaccination-r/**

### Étapes de Configuration

#### 1️⃣ Initialiser le dépôt Git

```bash
cd projetR
git init
git add .
git commit -m "Initial commit: Projet de vaccination animale"
```

#### 2️⃣ Créer un dépôt GitHub

```bash
# Via GitHub CLI
gh repo create projet-vaccination-r --public --source=. --remote=origin

# Ou créer manuellement sur https://github.com/new
```

#### 3️⃣ Pousser vers GitHub

```bash
git branch -M main
git push -u origin main
```

#### 4️⃣ Activer GitHub Pages

- Aller dans **Settings** → **Pages**
- Sélectionner **Deploy from a branch**
- Choisir la branche **main** et le dossier **/root**
- Cliquer sur **Save**

#### 5️⃣ Workflow Automatique (Optional)

Créer `.github/workflows/publish.yml` pour automatiser le rendu Quarto :

```yaml
name: Publish to GitHub Pages

on:
  push:
    branches: [ main ]

jobs:
  build-deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      
      - name: Install Quarto
        uses: quarto-dev/quarto-actions/setup@v2
      
      - name: Set up R
        uses: r-lib/actions/setup-r@v2
        with:
          r-version: '4.3.1'
      
      - name: Install R dependencies
        run: |
          install.packages(c('tidyverse', 'ggplot2', 'ggthemes', 'scales', 
                            'readxl', 'knitr', 'kableExtra'))
        shell: Rscript {0}
      
      - name: Render Quarto
        run: quarto render presentationProjetR.qmd
      
      - name: Deploy to GitHub Pages
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./
```

### Lien Direct

🔗 **Accéder au projet** : [https://medash69.github.io/projet-vaccination-r/](https://medash69.github.io/projet-vaccination-r/)

---

## 📊 Résultats Clés

### Performance Globale

- 📈 **Taux moyen de couverture** : 80.5%
- 🏆 **Meilleure année** : 2018 (85.3%)
- 📉 **Impact COVID-19** : Baisse en 2020 (72.1%)
- 🎯 **Campagne la plus efficace** : Rage (88.2%)

### Efficacité par Espèce

| Espèce | Taux Moyen | Efficacité |
|:---|:---:|:---|
| Bovins | 82% | ✅ Bonne |
| Ovins | 79% | ✅ Bonne |
| Caprins | 75% | ✅ Bonne |
| Chats | 89% | ✅ Excellente |
| Chiens | 76% | ✅ Bonne |

### Recommandations

1. 🔍 Cibler les espèces à faible taux de couverture
2. 📅 Optimiser la planification des campagnes
3. 📊 Renforcer le monitoring en temps réel
4. 🤝 Améliorer la coordination inter-année
5. 🎯 Établir des objectifs réalistes et mesurables

---

## 📖 Guide d'Utilisation

### Générer le Rapport HTML

```bash
# Windows
Rscript -e "quarto::quarto_render('presentationProjetR.qmd')"

# Linux/Mac
quarto render presentationProjetR.qmd
```

### Visualiser Localement

```bash
# Ouvrir le fichier HTML généré
# Windows
start presentationProjetR.html

# Linux
xdg-open presentationProjetR.html

# Mac
open presentationProjetR.html
```

### Modifier le Rapport

1. Ouvrir `presentationProjetR.qmd` dans un éditeur (VS Code, RStudio, etc.)
2. Modifier le contenu Markdown et/ou le code R
3. Exécuter `quarto render` pour générer la nouvelle version
4. Pousser les modifications vers GitHub : `git push`

---

## 👨‍💼 Auteur

**Meddeb Acharf**
- 📧 Email : [votre-email]
- 🔗 GitHub : [medash69](https://github.com/medash69)
- 📍 Localisation : Sousse, Tunisie

---

## 📄 Licence

Ce projet est sous licence **MIT**. Voir le fichier [LICENSE](LICENSE) pour plus de détails.

---

## 🔗 Ressources Utiles

### Documentation Quarto
- 📚 [Guide Officiel Quarto](https://quarto.org/docs/)
- 📚 [Quarto HTML Format](https://quarto.org/docs/output-formats/html-basics.html)
- 📚 [Quarto with R](https://quarto.org/docs/computations/r.html)

### GitHub Pages
- 📚 [GitHub Pages Documentation](https://docs.github.com/en/pages)
- 📚 [Jekyll & GitHub Pages](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll)

### R et Statistiques
- 📚 [R Project](https://www.r-project.org/)
- 📚 [tidyverse](https://www.tidyverse.org/)
- 📚 [ggplot2](https://ggplot2.tidyverse.org/)

---

## 🐛 Dépannage

### Erreur : "Quarto not found"
```bash
# Installer Quarto depuis https://quarto.org/docs/get-started/
# Puis ajouter au PATH système
```

### Erreur : "Package not found in R"
```r
# Installer les dépendances manquantes
install.packages(c("tidyverse", "ggplot2", "readxl", "kableExtra"))
```

### Erreur de déploiement GitHub Pages
- Vérifier que les fichiers `.html` sont dans le dépôt
- S'assurer que la branche `main` est correctement configurée
- Vérifier les paramètres GitHub Pages dans Settings



---

## ✨ Points Forts du Projet

- ✅ Analyse statistique complète et rigoureuse
- ✅ Visualisations modernes et informatives
- ✅ Documentation intégrée avec Quarto
- ✅ Reproductibilité garantie (code + données)
- ✅ Déploiement automatisé sur GitHub Pages
- ✅ Styles professionnels et modernes
- ✅ Accessible depuis n'importe quel navigateur

---

<div align="center">

### 🚀 Le projet est prêt pour le déploiement !

**Consultez le rapport complet** : [https://medash69.github.io/projet-vaccination-r/](https://medash69.github.io/projet-vaccination-r/)

---

*Projet réalisé avec ❤️ en R et Quarto | 2025*

</div>
