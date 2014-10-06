Conseils et directives pour une rédaction CSS de haut niveau
=============


##1- Largeur des colonnes##

il est fortement recommandé qu'une ligne dans un fichier CSS ne dépasse pas les 80 caractères, et cela pour les raisons suivantes:

- Avoir une meilleur visibilité et lisibilité du code
- Ne pas scroller pour lire la valeur d'une propriété 
- Assurer la possibilité d'ouvrir deux fichiers côte à côte
- Assurer la possiblité d'écrire des commentaires sur la même ligne
- Avoir la possibilité d'afficher la CSS sur des sites comme GitHub et bitbucket

Il y aura des exceptions inévitables à cette règle, comme les URL, dans ce cas nous pouvon igonrer cette régle


##2- Diviser la CSS en plusieurs fichiers##

Pour eviter d'avoir un fichier CSS contenant plus de 1000 ligne, il est bien de diviser vos fichiers de styles en plusieurs fichiers.
Cette pratique nous permet de séparer le code CSS selon un choix prédefini (CSS par page / CSS par module), et assurer la maintenabilité de nos travaux.
Pour faire des appels à des fichier des styles nous pouvons utilser La règle **@import**


##3- Syntaxe et formatage

Dans une équipe, il faut avoir un standard de rédaction de code dans le but de faciliter la maintenance et laisser la possibilité aux cooéquipier de travailler sur nos codes en les gardant toujours propres.

Pour cela nous aimons voir:

- 4 espaces au lieux d'une tabulation
- Une propriété par ligne
- Bien utiliser les espaces


##4- Titrage 

Le titrage est une notion très important lorsqu'on écrit un fichier de style. C'est un moyen de définir une section ou un module.

Un titre doit être précédé par un dièse (#), pour le but de faciliter les recherche via les commandes **grep** ou autres.

Si nous travaillons sur un projet où chaque section a son propre fichier, ce titre devrait apparaître en haut de chacun. Si nous travaillons sur un projet avec plusieurs sections par fichier, chaque titre doit être précédé par cinq retours chariot. Cet espace peut rendre plus facile de repérer les titres lorsque vous faites défiler les fichiers volumineux
```
/*------------------------------------*\
    #SECTION
\*------------------------------------*/

.selector {}





/*------------------------------------*\
    #ANOTHER-SECTION
\*------------------------------------*/
```
