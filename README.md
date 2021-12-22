# Analyse des décès covid par statut vaccinal 


## Résumé

Cette feuille de calcul [Jupyter](https://jupyter.org/) analyse les données de décès de la DREES, par statut vaccinal et par âge, et tente d'évaluer les décès évités par la vaccination, et ceux qui auraient pu l'être avec une couverture vaccinale complète.


## Données

Les données proviennent du site de la DREES. Elle comportent les décès depuis juin 2021, par statut vaccinal, dat et tranche d'âge

https://data.drees.solidarites-sante.gouv.fr/explore/dataset/covid-19-resultats-par-age-issus-des-appariements-entre-si-vic-si-dep-et-vac-si/information/

## Méthodologie 

Pour chaque tranche d'âge, chaque statut vaccinal et chaque date, la DREES fournit les effectifs du groupe correspondant (age et statut vaccinal), à date. Ceci permet de calculer une mortalité journalière pour chaque sous groupe.

Il est alors possible de simuler des scénarios de couverture vaccinale (0% et 100%) appliquant la mortalité d'un sous groupe à l'autre, pour une même tranche d'âge.

## Limitations

Ces calculs reposent sur l'hypothèse que la différence de mortalité des groupes vaccinés et non-vaccinés dépend essentiellement de leur statut vaccinal. Le facteur de confusion "âge" est pris en compte par la strafification par âge déjà appliquée par la DREES. 

D'autres facteurs de confusion peuvent néamoins subsister:

* **Comorbidités** : Chez les plus jeunes surtout (0-19 ans), les individus présentant des comorbidités ont été vaccinés en priorité. L'ignorance de cette corrélation tend à sous estimer l'impact positif de la vaccination.

* **Classes sociales** : Les classes populaires sont à la fois moins plus vulnérables et moins vaccinées que le reste de la population. [1](https://www.cdc.gov/mmwr/volumes/70/wr/mm7022e1.htm) [2](https://www.huffingtonpost.fr/entry/vaccination-la-richesse-ou-les-diplomes-insuffisants-pour-expliquer-le-choix-de-ceux-qui-decident-de-ne-pas-le-faire_fr_61166e34e4b07c1403142492). L'ignorance de cette corrélation tend à surestimer l'impact positif de la vaccination.

* **Transmission** : Cette étude ne considère pas l'effet de la vaccination sur la transmission ([évalué à 40% environ](https://www.france24.com/en/live-news/20211124-vaccines-reduce-covid-transmission-by-40-who)). L'ignorance de cet tend à sous estimer l'impact positif de la vaccination.

# Résultats 

Au total, la vaccination a permis d'éviter plus de 27000 décès depuis juin 2021. 
Sur les 8400 décès répertoriés par la DREES sur cette période, plus de la moitié (4800) auraient pu etre évités par une couverture vaccinale complète. 


## Graphes

### Décès par tranche d'âge et statut vaccinal

![](res/deces.png)

### Décès par tranche d'âge et statut vaccinal, normalisés pour 1 million d'individus

![](res/deces_ratios.png)

### Scenarios

![](res/scenarios.png)

## Tableau

| age       | décès non-vax  | décès vax  | décès si 0% vax | décès si 100% vax | décès évités | décès évitables |
|-----------|----------------|------------|-----------------|-------------------|--------------|-----------------|
| [0,19]    | 11             | 2          | 13              | 10                | 0            | 2               |
| [20,39]   | 85             | 22         | 277             | 32                | 169          | 75              |
| [40,59]   | 563            | 163        | 2524            | 239               | 1797         | 487             |
| [60,79]   | 2249           | 1112       | 15881           | 1300              | 12520        | 2061            |
| [80;+]    | 2483           | 1774       | 17574           | 2057              | 13316        | 2199            |
| **Total** | 5391           | 3073       | 36269           | 3638              | **27802**    | **4824**        |


# Code 

Le code est disponible sur Github :
https://github.com/raphaeljolivet/drees-deces


# Auteur

Raphaël Jolivet : https://mamot.fr/@RaphJ


# Licence

Cette feuille de calcul est distribuée sous [licence CC-By](https://creativecommons.org/licenses/by/4.0/)


