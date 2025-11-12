# 📦 StockManager - Système de Gestion de Stock

## 📋 Table des matières
1. [Vue d'ensemble](#vue-densemble)
2. [Structure du projet](#structure-du-projet)
3. [Architecture HTML](#architecture-html)
4. [Styles CSS](#styles-css)
6. [Pages et sections](#pages-et-sections)
7. [Composants](#composants)
8. [Guide d'utilisation](#guide-dutilisation)

---

## 🎯 Vue d'ensemble

**StockManager** est une application web de gestion de stock pour produits électroniques. C'est une **Single Page Application (SPA)** qui permet de naviguer entre différentes sections sans rechargement de page.

### Fonctionnalités principales :
- ✅ Tableau de bord avec statistiques
- 📊 Analytics et rapports
- 🛒 Gestion des commandes
- ⚙️ Paramètres système
- 📄 Génération de rapports
- 🔔 Centre de notifications
- 👤 Profil utilisateur

---

## 📁 Structure du projet
```
StockManager/
│
├── index.html          # Fichier principal (tout-en-un)
└── README.md          # Documentation
```

Le projet est conçu en **un seul fichier HTML** contenant :
- Le HTML (structure)
- Le CSS (styles)
- Le JavaScript (interactivité)

---

## 🏗️ Architecture HTML

### 1. **Structure de base**
```html
<!DOCTYPE html>
<html lang="fr">
<head>
    <!-- Meta tags, titre, Font Awesome, styles -->
</head>
<body>
    <!-- Sidebar -->
    <!-- Modal Profil -->
    <!-- Main Content -->
    <!-- JavaScript -->
</body>
</html>
```

### 2. **Composants principaux**

#### A. Sidebar (Barre latérale)
```html
<aside class="sidebar">
    <div class="sidebar-header">       <!-- Logo + titre -->
    <nav class="sidebar-nav">          <!-- Navigation -->
    <div class="sidebar-footer">       <!-- Profil utilisateur -->
</aside>
```

**Explication :**
- `sidebar-header` : Affiche le logo et le titre "Dashboard"
- `sidebar-nav` : Contient tous les liens de navigation (Tableau de Bord, Analytics, etc.)
- `sidebar-footer` : Affiche l'avatar de l'utilisateur et les boutons "Mon Profil" et "Déconnexion"

#### B. Modal Profil
```html
<div class="modal-overlay" id="modalProfil">
    <div class="modal-content">
        <!-- Bouton fermeture -->
        <!-- Avatar -->
        <!-- Formulaire -->
    </div>
</div>
```

**Explication :**
- `modal-overlay` : Fond sombre semi-transparent qui couvre toute la page
- `modal-content` : Fenêtre popup blanche contenant le formulaire de profil
- Apparaît quand on clique sur "Mon Profil"

#### C. Main Content (Contenu principal)
```html
<main class="main-content">
    <header class="header">            <!-- En-tête avec titre -->
    
    <div id="tableau" class="page-section active">     <!-- Page 1 -->
    <div id="analytics" class="page-section">          <!-- Page 2 -->
    <div id="commandes" class="page-section">          <!-- Page 3 -->
    <!-- etc. -->
</main>
```

**Explication :**
- `header` : En-tête fixe avec titre, notifications et profil
- `page-section` : Chaque section est une "page" différente
- `.active` : Seule la page avec cette classe est visible

---

## 🎨 Styles CSS

### 1. **Reset et base**
```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
```
**Explication :** Réinitialise tous les styles par défaut du navigateur

### 2. **Layout principal**
```css
body {
    display: flex;              /* Layout flexbox */
    min-height: 100vh;          /* Hauteur minimale = 100% de la fenêtre */
    background: #f5f7fa;        /* Couleur de fond grise */
}
```

### 3. **Sidebar (260px fixe)**
```css
.sidebar {
    width: 260px;
    position: fixed;            /* Reste fixe lors du scroll */
    height: 100vh;              /* Hauteur = 100% de la fenêtre */
    background: #2c3e50;        /* Bleu foncé */
}
```

**Points clés :**
- `position: fixed` : La sidebar ne bouge pas quand on scrolle
- `width: 260px` : Largeur fixe de la sidebar
- `z-index: 100` : Au-dessus des autres éléments

### 4. **Navigation active**
```css
.nav-item.active {
    background: #3498db;        /* Fond bleu */
    border-left: 3px solid #2980b9;  /* Bordure gauche */
}
```

**Explication :** L'élément de navigation actif est surligné en bleu

### 5. **Cartes statistiques**
```css
.stat-card {
    display: flex;
    align-items: center;        /* Centre verticalement */
    gap: 20px;                  /* Espace entre l'icône et le texte */
    transition: transform 0.3s; /* Animation fluide */
}

.stat-card:hover {
    transform: translateY(-5px); /* Monte de 5px au survol */
}
```

**Couleurs des icônes :**
- `.blue` : #3498db (bleu)
- `.orange` : #f39c12 (orange)
- `.green` : #27ae60 (vert)
- `.gray` : #6c7a89 (gris)
- `.purple` : #9b59b6 (violet)
- `.red` : #e74c3c (rouge)

### 6. **Modal Profil**
```css
.modal-overlay {
    display: none;              /* Caché par défaut */
    position: fixed;            /* Couvre toute la page */
    background: rgba(0,0,0,0.5);/* Fond noir semi-transparent */
    z-index: 1000;              /* Au-dessus de tout */
}

.modal-overlay.active {
    display: flex;              /* Visible avec classe active */
}
```

**Animation d'ouverture :**
```css
@keyframes modalSlideIn {
    from {
        transform: translateY(-50px);  /* Part de 50px plus haut */
        opacity: 0;                     /* Invisible */
    }
    to {
        transform: translateY(0);       /* Position finale */
        opacity: 1;                     /* Visible */
    }
}
```

### 7. **Toggle Switch (Interrupteur)**
```css
.toggle-switch input:checked + .slider {
    background-color: #3498db;  /* Bleu quand activé */
}

.toggle-switch input:checked + .slider:before {
    transform: translateX(24px); /* Déplace le cercle vers la droite */
}
```

**Explication :** Crée un interrupteur animé comme sur iOS/Android

### 8. **Responsive Design**
```css
@media (max-width: 768px) {
    .sidebar {
        transform: translateX(-100%);  /* Cache la sidebar sur mobile */
    }
    
    .main-content {
        margin-left: 0;                /* Contenu en pleine largeur */
    }
    
    .stats-grid {
        grid-template-columns: 1fr;    /* Une colonne sur mobile */
    }
}
```

---



**Comment ça marche :**
1. Sélectionne tous les liens de navigation
2. Écoute le clic sur chaque lien
3. Change la classe `active` pour afficher/cacher les sections
4. Utilise l'attribut `data-page` pour savoir quelle page afficher

**Exemple :**
```html
<a class="nav-item" data-page="analytics">  <!-- data-page = ID de la page -->
```


## 📊 Pages et sections

### 1. **Tableau de Bord** (`#tableau`)
- 4 cartes statistiques (Produits, Stock Faible, Valeur, Commandes)
- Barre de recherche
- Tableau des produits avec actions (éditer/supprimer)

### 2. **Analytics** (`#analytics`)
- Statistiques avec évolution (+12.5%, -2.1%, etc.)
- Graphique en barres (évolution des ventes)
- Répartition par catégorie avec barres de progression

### 3. **Commandes** (`#commandes`)
- 4 cartes de statut (En attente, En cours, Expédiées, Livrées)
- Filtres (Statut, Période, Recherche)
- Liste des commandes détaillées

### 4. **Paramètres** (`#parametres`)
- Paramètres généraux avec toggle switches
- Sélecteurs (langue, devise, format date)
- Paramètres de sécurité

### 5. **Rapports** (`#rapports`)
- Générateur de rapports (Type, Période, Format)
- Statistiques détaillées
- Historique des rapports téléchargeables

### 6. **Notifications** (`#notifications`)
- 4 types de notifications (Non lues, Urgentes, Aujourd'hui, Total)
- Filtres multiples
- Liste de notifications avec actions

---

## 🧩 Composants

### 1. **Cartes statistiques**
```html
<div class="stat-card blue">
    <div class="stat-icon">
        <i class="fas fa-box"></i>         <!-- Icône Font Awesome -->
    </div>
    <div class="stat-info">
        <h3>1,234</h3>                     <!-- Chiffre -->
        <p>Produits en Stock</p>           <!-- Description -->
    </div>
</div>
```

**Classes de couleur disponibles :**
- `blue`, `orange`, `green`, `gray`, `purple`, `red`

### 2. **Badges**
```html
<!-- Badge de catégorie -->
<span class="badge-category laptop">LAPTOP</span>

<!-- Badge de stock -->
<span class="stock-badge stock-good">15</span>
<span class="stock-badge stock-low">8</span>

<!-- Badge de statut -->
<span class="status-badge active">Actif</span>
```

### 3. **Boutons**
```html
<!-- Bouton principal -->
<button class="btn-primary">
    <i class="fas fa-plus"></i> Ajouter
</button>

<!-- Bouton secondaire -->
<button class="btn-secondary">
    <i class="fas fa-download"></i> Exporter
</button>

<!-- Bouton icône -->
<button class="btn-icon edit">
    <i class="fas fa-edit"></i>
</button>
```

### 4. **Toggle Switch**
```html
<label class="toggle-switch">
    <input type="checkbox" checked>
    <span class="slider"></span>
</label>
```

**États :**
- `checked` : Activé (bleu)
- Non coché : Désactivé (gris)

### 5. **Barres de progression**
```html
<div class="progress-bar">
    <div class="progress-fill" style="width: 35%; background: #3498db;"></div>
</div>
```

**Personnalisation :**
- `width` : Pourcentage de remplissage
- `background` : Couleur de la barre

---

## 📖 Guide d'utilisation

### Démarrage

1. **Ouvrir le fichier**
```
   Ouvrez index.html dans votre navigateur
```

2. **Navigation**
   - Cliquez sur les éléments de la sidebar pour changer de page
   - La page active est surlignée en bleu

### Fonctionnalités

#### 1. **Voir son profil**
```
Sidebar → Mon Profil → Modal s'ouvre
```

#### 2. **Modifier son profil**
```
1. Modifier les champs (Nom, Prénom, Email, Téléphone)
2. Cliquer sur "Sauvegarder"
3. Message de confirmation
```

#### 3. **Fermer le modal**
```
3 méthodes :
- Cliquer sur le X (en haut à droite)
- Cliquer sur "Fermer"
- Cliquer en dehors du modal
```

#### 4. **Naviguer entre les pages**
```
Cliquer sur :
- Tableau de Bord
- Analytics
- Commandes
- Paramètres
- Rapports
- Notifications
```

---

## 🎨 Personnalisation

### Changer les couleurs
```css
/* Couleur principale */
.stat-card.blue .stat-icon { 
    background: #3498db;  /* Modifier ici */
}

/* Couleur de la sidebar */
.sidebar {
    background: #2c3e50;  /* Modifier ici */
}

/* Couleur des boutons */
.btn-primary {
    background: #3498db;  /* Modifier ici */
}
```

### Ajouter une nouvelle page

1. **Ajouter le lien dans la sidebar**
```html
<a class="nav-item" data-page="mapage">
    <i class="fas fa-star"></i>
    <span>Ma Page</span>
</a>
```

2. **Créer la section**
```html
<div id="mapage" class="page-section">
    <div class="dashboard-content">
        <!-- Votre contenu ici -->
    </div>
</div>
```

### Modifier les données du profil
```html
<!-- Dans le modal -->
<input type="text" value="Votre Nom">        <!-- Nom par défaut -->
<input type="email" value="votre@email.com"> <!-- Email par défaut -->
```

---




## 📱 Responsive Design

### Points de rupture
```css
@media (max-width: 1024px) {
    /* Tablettes */
}

@media (max-width: 768px) {
    /* Mobiles */
    .sidebar {
        transform: translateX(-100%);  /* Cache la sidebar */
    }
}
```

### Comportement mobile

- **Sidebar** : Cachée par défaut
- **Grilles** : Passent en une seule colonne
- **Modal** : S'adapte à la largeur de l'écran
- **Tableaux** : Scroll horizontal

---



## 📚 Technologies utilisées

- **HTML5** : Structure sémantique
- **CSS3** : 
  - Flexbox pour les layouts
  - Grid pour les grilles
  - Transitions et animations
  - Media queries pour le responsive
  - Gestion des classes CSS
- **Font Awesome 6.4.0** : Icônes

---

## 💡 Concepts clés

### 1. Single Page Application (SPA)
Une seule page HTML qui change dynamiquement son contenu sans recharger la page.

### 2. Responsive Design
L'interface s'adapte automatiquement à la taille de l'écran (desktop, tablette, mobile).

### 3. Modal / Popup
Fenêtre qui s'affiche par-dessus le contenu principal.

### 4. Toggle Switch
Interrupteur on/off animé.

### 5. Grid System
Système de grilles CSS pour organiser les éléments en colonnes.

---


```css
/* Vérifier que les classes existent */
.stat-card { ... }        /* OK */
.stat-card .blue { ... }  /* ERREUR : devrait être .stat-card.blue */
```

---

## ✅ Checklist de vérification

- [ ] Font Awesome se charge correctement
- [ ] La sidebar est visible et fixe
- [ ] La navigation change les pages
- [ ] Le modal profil s'ouvre au clic
- [ ] Le modal se ferme (3 méthodes)
- [ ] Les formulaires ne rechargent pas la page
- [ ] Les hover effects fonctionnent
- [ ] Responsive sur mobile (sidebar cachée)
- [ ] Toutes les icônes s'affichent
- [ ] Les couleurs sont correctes

---

## 📞 Support

Pour toute question ou problème :
1. Vérifier ce README
2. Inspecter la console du navigateur (F12)
3. Vérifier que Font Awesome est chargé
4. Tester sur un navigateur récent (Chrome, Firefox, Edge)

---

**Créé avec courage est ambition pour la gestion de stock efficace**

Version : 1.0.0  
Dernière mise à jour : Novembre 2024