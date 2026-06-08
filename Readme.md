# Projet TP2 : Régression Linéaire et Descente de Gradient

## 📝 Description du projet
Ce projet a pour objectif d'implémenter et de comprendre le fonctionnement de modèles de prédiction de valeurs continues basés sur la régression linéaire[cite: 799]. Le projet est divisé en deux parties :
1. **Régression univariée** : Prédiction de la taille d'un enfant en fonction de son âge[cite: 802, 804].
2. **Régression multivariée** : Estimation du prix de biens immobiliers (à Portland) en fonction de plusieurs caractéristiques (superficie et nombre de pièces)[cite: 996, 998, 999].

## 🧠 Méthode d'Apprentissage Automatique
Le modèle prédictif est construit de zéro ("from scratch") sans utiliser de solveurs de haut niveau pour la phase d'apprentissage :
- **Descente de gradient** : Implémentation mathématique de l'algorithme d'optimisation itératif pour minimiser la fonction de coût[cite: 848, 850].
- **Calcul matriciel** : Vectorisation des opérations pour traiter efficacement la régression linéaire à variables multiples[cite: 996].
- **Recherche d'hyperparamètres** : Automatisation de la recherche du meilleur taux d'apprentissage ($\alpha$) en observant la convergence de la fonction de coût sur plusieurs itérations[cite: 1051, 1053, 1054].
- **Standardisation** : Utilisation de `StandardScaler` pour mettre à l'échelle les données immobilières avant l'entraînement[cite: 1007, 1008]. Une fois le modèle entraîné, il est utilisé pour prédire le prix d'un nouveau logement[cite: 1056].

# Projet TP3 : Régression Polynomiale et Sur-apprentissage

## 📝 Description du projet
Ce projet explore la modélisation de jeux de données présentant des relations non linéaires[cite: 431]. L'objectif est d'ajuster une fonction polynomiale de degré 5 sur un jeu de données à une dimension[cite: 477, 481]. La problématique centrale est la gestion du sur-apprentissage (over-fitting) inhérent à l'utilisation de polynômes de haut degré sur un faible nombre de points[cite: 481].

## 🧠 Méthode d'Apprentissage Automatique
- **Régression Polynomiale** : Transformation des caractéristiques (features) d'entrée pour intégrer des puissances supérieures (de $x$ à $x^5$) afin de complexifier le modèle linéaire[cite: 478, 479].
- **Régularisation Ridge** : Ajout d'une pénalité (paramètre $\lambda$) à la fonction de coût pour contraindre la magnitude des poids du modèle et éviter le sur-apprentissage[cite: 482, 483, 486].
- **Analyse du Compromis Biais-Variance** : Étude expérimentale de l'impact du paramètre de régularisation sur l'erreur du modèle. Des graphiques sont générés pour visualiser l'évolution du biais et de la variance en fonction des différentes valeurs de $\lambda$ afin de trouver le modèle optimal[cite: 604, 606].
- **Comparaison avec Scikit-Learn** : Le modèle mathématique codé manuellement (par descente de gradient) est ensuite comparé aux outils de production fournis par la librairie Scikit-Learn (`PolynomialFeatures`, `Ridge` dans un pipeline)[cite: 717, 718, 719, 720].

# Projet TP4 : Filtre Anti-Spam par Classification Naïve Bayésienne

## 📝 Description du projet
Ce projet applique des techniques de traitement du langage naturel (NLP) pour créer un classifieur de courriels[cite: 179]. En utilisant un jeu de données réel issu de Ling-spam comprenant 960 emails prétraités (700 pour l'entraînement, 260 pour le test), le but est de catégoriser automatiquement les messages en "spam" ou "non-spam"[cite: 180, 181, 185]. Les textes sont représentés sous la forme d'un dictionnaire de 2500 mots (matrice creuse)[cite: 194, 195, 196].

## 🧠 Méthode d'Apprentissage Automatique
- **Modèle Bayésien Naïf (Naive Bayes)** : Implémentation basée sur le théorème de Bayes, supposant une indépendance forte entre l'apparition des différents mots dans un document[cite: 211, 212, 230].
- **Log-Vraisemblance** : Transformation des calculs de probabilités par l'application du logarithme népérien afin d'éviter les erreurs d'arrondi ou de sous-dépassement (underflow) lors de la multiplication de très petites probabilités[cite: 246, 247, 248].
- **Modélisation de Bernoulli** : Analyse basée sur la présence (1) ou l'absence (0) d'un mot plutôt que sur sa fréquence absolue d'apparition[cite: 270, 293].
- **Évaluation des performances** : Construction d'une matrice de confusion et calcul des métriques de classification (précision, rappel, F1-score)[cite: 260, 262].
- Les résultats obtenus par le classifieur codé à la main sont ensuite confrontés à ceux obtenus par la classe `GaussianNB` de Scikit-Learn[cite: 399, 411].

# Projet TP5 : Compression d'Images par K-Means

## 📝 Description du projet
Ce projet illustre une application pratique de l'apprentissage non supervisé pour le traitement d'images[cite: 38]. L'objectif est de compresser une image haute résolution ($538 \times 538$ pixels) encodée en 24-bits (soit 16 millions de couleurs possibles) en réduisant drastiquement sa palette de couleurs[cite: 41, 42, 43]. Le programme trouve et applique les 16 couleurs optimales pour reconstituer l'image tout en réduisant son poids[cite: 44].

## 🧠 Méthode d'Apprentissage Automatique
- **Clustering / Algorithme K-Means (Centres mobiles)** : Regroupement (clustering) des pixels de l'image en fonction de leur proximité chromatique dans l'espace colorimétrique RGB[cite: 38, 45, 68].
- **Entraînement sur données réduites** : Pour optimiser considérablement les temps de calcul, l'algorithme K-Means est d'abord exécuté sur une version miniature de l'image ($128 \times 128$ pixels)[cite: 47].
- **Processus Itératif** : L'algorithme initialise 16 centroïdes aléatoires, assigne chaque pixel au centroïde de couleur le plus proche (calcul de distance euclidienne), puis met à jour la position des centroïdes (calcul du barycentre) jusqu'à convergence[cite: 66, 67, 68, 69].
- **Inférence** : Une fois les 16 centroïdes de couleurs trouvés, cette palette est projetée sur la grande image : chaque pixel est remplacé par la couleur du cluster auquel il appartient, réalisant ainsi la compression[cite: 48, 77, 78].
