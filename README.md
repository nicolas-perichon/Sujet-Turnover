# Analyse et prédiction de données Turnover
###### Léonie BERTON, Ninon QUESNEL, Paul REVERSAC, Nicolas PERICHON

## Présentation des données

Nous disposons d'un jeu de données concernant les départs des salariés d'une entreprise. Celui-ci est constitué de 10 variables :

* `Satisfaction` : c'est une note sur 1 représentant le taux de satisfaction du salarié dans son métier (son épanouissement).
  * Type : float
* `Derniere_evaluation` : cela correspond à la dernière note attribuée au collaborateur.
  * Type : float
* `Nombre_de_projets` : nombre de missions sur lesquelles le salarié travaille.
  * Type : int
* `Nombre_heures_mensuelles_moyenne` : nombre d'heures travaillées en moyenne par mois pour un employé.
  * Type : int
* `Temps_passe_dans_entreprise` : nombre d'années passées dans l'entreprise par le salarié.
  * Type : int
* `Accident_du travail` : l’employé a déjà eu un accident du travail ou non.
  * Type : int
* `Depart` : l’employé a-t-il quitté l’entreprise ? → 1 OUI, 0 → NON.
  * Type : int
* `Promotion_5_dernieres_annees` : le salarié a-t-il eu une promotion ces 5 dernières années ? 1 : Oui / 0 : Non.
  * Type : int
* `Service` : service dans lequel l’employé travaille.
  * Type : object
* `Niveau_salaire` : Niveau de salaire de l’employé (low,medium,high).
  * Type : object

Notre variable cible sera celle du `depart`, être capable de déterminer à partir des autres variables (features) si le salarié part ou non.

## Méthodologie

### Architecture du projet

* On crée un répertoire `DataBaseTrain` dans lequel se situe le fichier *csv*. Il sera utilisé pour l'entraînement de nos modèles.
* On crée un répertoire `DataBaseTest` dans lequel nous situons un fichier "externe" (reprenant le schéma de la base de données de *train*) pour tester nos modèles.
* On crée un fichier *jupyter notebook* sur lequel nous réaliserons notre développement (code) à la racine du projet GIT.

### Plan de développement

* On place en haut de page tous les imports nécessaires au fonctionnement de notre code.
* On place en premier notre fonction d'affichage qui nous permettra de retourner la valeur (ici le départ ou non de l'employé) pour un enregistrement (= un salarié) donné (test).
* On importe ensuite les données à partir du fichier csv donné. On affiche les différents types des variables puisqu'il sera nécessaire de n'avoir que des nombres pour la suite. Cela permet donc d'identifier les variables à traiter.
* On affiche différentes informations concernant la base de données, notamment à l'aide de la fonction .describe(). Elle permettra d'afficher, pour nos 10 variables, le nombre de fois qu'elles sont présentes, leur moyenne respective, leur minimum ... Cela permet notamment de savoir sur combien est évaluée la satisfaction ou bien la dernière évaluation ...
* On réalise ensuite différents graphiques pour constater la proportion de départ ou non par rapport à différentes variables.
* On réalise également une matrice de corrélation pour remarquer quelles variables sont plus importantes que d'autres pour la suite. Cela permet d'avoir un premier aperçu.
* Le VCramer sera intéressant pour comparer les variables qu'il choisit automatiquement (corrélées) avec les résultats de la matrice précédente. Cela nous donne deux analyses pour confirmer notre choix ou non.
* On crée une matrice de corrélation sur les scores précédents.
* On entraîne ensuite notre jeu de données sur 4 modèles : Random Forest / Logistic Regression / KNN / SVM
* On compare les taux de fiabilité et on affiche les matrices de confusion qui permettent de voir les faux positifs et les faux négatifs.
* On en conclut le meilleur modèle.
* On réitère ensuite en réalisant une feature engineering.
* On crée 3 nouvelles variables en fonction des autres :
  * `heures_totales` : c'est la multiplication du `Nombre_heures_mensuelles_moyenne` par 12 (une année) et par le `Temps_passe_dans_entreprise` (en années).
  * `projets_par_années` : c'est le `Nombre_de_projets` par rapport au `Temps_passe_dans_entreprise`.
  * `satisf_eval` : c'est la `Satisfaction` divisée par `Deniere_evalutation`.
* On refait une matrice de corrélation suivi d'un VCramer.
* On recrée la matrice associée et on constate que nos 3 nouvelles variables sont bien parmis les plus corrélées.
* On réalise cette fois un ou des modèles précédents sur les meilleures features.
* On compare les résultats et on conlut.
