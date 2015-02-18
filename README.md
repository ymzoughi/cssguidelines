Conseils et directives pour une rédaction CSS de haut niveau
=============


*Ce document n'est pas le guidelines, mais plutôt un guidelines* 

##1- Largeur des colonnes##

il est fortement recommandé qu'une ligne dans un fichier CSS ne dépasse pas les 80 caractères, et cela pour les raisons suivantes:

- Avoir une meilleur visibilité et lisibilité du code
- Ne pas scroller pour lire la valeur d'une propriété 
- Assurer la possibilité d'ouvrir deux fichiers côte à côte
- Assurer la possiblité d'écrire des commentaires sur la même ligne
- Avoir la possibilité d'afficher le code CSS sur des sites comme GitHub et bitbucket

Il y aura des exceptions inévitables à cette règle, comme les URL, dans ce cas nous pouvons igonrer ce point


##2- Diviser la CSS en plusieurs fichiers##

Pour eviter d'avoir un fichier CSS contenant plus de 1000 lignes, il est bien de diviser vos fichiers de styles en plusieurs fichiers.
Cette pratique nous permet de séparer le code CSS selon un choix prédefini (CSS par page / CSS par module), et assurer la maintenabilité de nos travaux.
Pour faire des appels à des fichiers des styles nous pouvons utilser la règle **@import**


##3- Syntaxe et formatage

Dans une équipe, il faut avoir un standard de rédaction de code dans le but de faciliter sa maintenance.
Il permet aussi aux coéquipiers de travailler sur le même code en le gardant toujours propres.

Pour cela nous aimons voir:

- 4 espaces au lieux d'une tabulation (ou bien paramétrer la tabulation dans son IDE à 4 espaces)
- Une propriété par ligne
- Bien utiliser les espaces


##4- Titrage 

Le titrage est une notion très importante lorsqu'on écrit un fichier de style. C'est un moyen de définir une section ou un module.

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

##5- Régles d'écriture

Il est fortement recommandé d'écrire le code CSS en respectant les régles suivantes: 

- sélecteurs connexes sur la même ligne
- sélecteurs indépendants sur de nouvelles lignes
- un espace avant notre accolade ouvrante ({) 
- propriétés et les valeurs sur la même ligne
- un espace après notre propriété-valeur délimitant deux points (:)
- chaque déclaration dans sa propre nouvelle ligne
- l'accolade d'ouverture ({) sur la même ligne que notre dernière sélection 
- notre accolade fermante (}) sur sa propre nouvelle ligne; 
- un point-virgule de fuite (;) lors de notre dernière déclaration.

```
.foo, .foo--bar,
.baz {
    display: block;
    background-color: green;
    color: red;
}
```

##6- Indentation, alignement et espaces

###Indentation

Exemple: 

```
.foo {}

    .foo__bar {}

        .foo__baz {}
```

Cette methode d'indentation de code permet aux developpeurs d'avoir une visibilité sur la structure HTML

###Alignement

Exemple:

```
.foo {
    -webkit-border-radius: 3px;
       -moz-border-radius: 3px;
            border-radius: 3px;
}

.bar {
    position: absolute;
    top:    0;
    right:  0;
    bottom: 0;
    left:   0;
    margin-right: -10px;
    margin-left:  -10px;
    padding-right: 10px;
    padding-left:  10px;
}
```

###Espaces

Exemples: 

```
/*------------------------------------*\
    #FOO
\*------------------------------------*/

.foo {}

    .foo__bar {}


.foo--baz {}





/*------------------------------------*\
    #BAR
\*------------------------------------*/

.bar {}

    .bar__baz {}

    .bar__foo {}
```

Les espaces entres les lignes nous permettent d'avoir un très bonne visibilité sur nos régles et sections :

- Une ligne vide entre les ensembles de règles étroitement liés
- Deux lignes vides entre les ensembles de règles vaguement liés
- Cinq lignes vides entre deux sections.

##7- Conventions de nommage

Les conventions de nommage en CSS sont extrêmement utiles pour rendre votre code plus strict, plus transparent et plus informatif.

Toutes les chaînes dans les classes sont délimitées par un trait d'union (-).

En CSS il ne faut pas utiliser les CamelCase

Utiliser des noms de classe explicites et de préférence en anglais (pour éviter les caractères accentués) 

Exemples: 

    .bloc-newsletter, .section-blog, .article-news... 


##8- Utilisation des langages dynamiques de génération de feuilles de style (Less, SASS ..)
Dans certains projets, nous sommes parfois obligés de réécrire le même code css pour plusieurs selecteurs, ce qui rend la feuille de style non maintenable et compliquée à lire, d'ou l'utilsation des langages dynamiques
### A) LESS
LESS, comme l'indique son nom, c'est ecrire moins. C'est un Préprocesseur CSS basé sur le langage JavaScript.
LESS permet d'ajouter des notions manquantes à la CSS telque:
- La déclaration des variables
- Les opérations de calculs dynamiques
- La factorisation de parties de code
- Les imbrications de sélecteurs

**Installation**
```
$ npm install -g less
```
**Command-line**
```
$ lessc styles.less
```
Ou pour définir le fichier de sortie (ajouter -x en option pour génerer le fichier minimisé)
```
$ lessc styles.less > styles.css
```
**Usage Client-side**

**Usage en developpement**

### A) SASS
SASS tout comme LESS, est un préprocesseur css basé sur le langage Ruby.
L'extension des fichiers SASS est .scss
SASS s'occupera de générer les fichiers .scss en .css

**Installation**
Il faut d'abord installer Ruby sous windows/Linux. Sous mac Ruby il est pré-installé.
Ensuite il faut taper les commande :
```
$ gem install sass
```

**Code Impriqué**
Cette methode ne nous aide pas à comprendre les relations unissant les éléments HTML auxquels nous appliquons un style. 
Avec l’imbrication, nous pouvons écrire un code SCSS qui est à la fois non redondant et plus facile à suivre :

Exemple :
 
```
body.home { 
    .media-unit {
        border: 1px solid #ccc; 
        background-color: #fff; 
        .right {
            border-left: 1px solid #ccc;
            h1 {
                font-size: 24px;
            }
        }
    }
}

Code css généré :

body.home .media-unit {
    border: 1px solid #ccc; 
    background-color: #fff; 
}

body.home .media-unit .right {
    border-left: 1px solid #ccc;
}

body.home .media-unit .right h1 {
    font-size: 24px;
}

```

**Les variables**
Les variables Sass sont très utiles pour 2 raisons :
- elles permettent de modifier le code plus facilement en réduisant les duplications. 
- elles permettent de nommer la valeur d’une propriété, la couleur par exemple, ce qui permet de comprendre l’intention derrière un style donné.

Exemple :
 
```
$color-green: "#99cc00"; 
$site-link-color: $color-green;

a {
    color: $site-link-color;
}

.main-menu {
    color: $site-link-color;
}

Code css généré :

a {
    color: #99cc00;
}

.main-menu {
    color: #99cc00;
}

```

**Les mixins**
Les Mixins sont des ensembles de propriétés ou de règles que vous pouvez inclure, ou “mixer”, dans d’autres règles. 
Vous les définissez en utilisant le mot clé @mixin et vous les intégrez en utilisant le mot clé @include.

Exemple :
 
```

@mixin border-radius($radius) {
    -webkit-border-radius: $radius;
       -moz-border-radius: $radius;
            border-radius: $radius;
}

.button {
    @include border-radius('2px'); 
}

Code css généré :

.button {
    -webkit-border-radius: 2px;
       -moz-border-radius: 2px;
            border-radius: 2px;
}

```