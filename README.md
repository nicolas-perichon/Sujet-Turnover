# Analyse et prédiction de données Turnover
###### Léonie BERTON, Ninon QUESNEL, Paul REVERSAC, Nicolas PERICHON

## Partie I

### Présentation des données

Nous disposons d'un jeu de données concernant les départs des salariés d'une entreprise. Celui-ci est constitué de 10 variables :

* `Satisfaction` : c'est une note sur 1 représentant le taux de satisfaction du salarié dans son métier (son épanouissement).
  * Type : float
* `Deniere_evalutation` : cela correspond à la dernière note attribuée au collaborateur.
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
