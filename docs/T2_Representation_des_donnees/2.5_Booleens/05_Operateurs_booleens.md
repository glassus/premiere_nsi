# Les opérateurs booléens


### Repères historiques

![](data/portrait_boole.jpg)

En 1847, le  britannique  *George BOOLE*  inventa un formalisme permettant d'écrire des raisonnements logiques : l'algèbre de Boole. La notion même d'informatique n'existait pas à l'époque, même si les calculs étaient déjà automatisés (penser à la Pascaline de 1642).

Bien plus tard, en  1938, les travaux de l'américain *Claude  SHANNON*  prouva  que des  circuits  électriques
peuvent  résoudre tous  les  problèmes  que l'algèbre  de  Boole peut  elle-même résoudre.  Pendant la deuxième guerre mondiale, les travaux  d'*Alan  TURING*  puis de *John VON NEUMANN* poseront définitivement les bases de l'informatique moderne.

# Algèbre de Boole

L'algèbre de Boole définit des opérations dans un ensemble
qui ne contient que **deux éléments** notés **0 et 1**, ou bien **FAUX et VRAI** ,ou encore **False** et **True** (en Python)

Les opérations fondamentales sont :
- la *conjonction* ("ET") 
- la *disjonction* ("OU") 
- la *négation* ("NON").

Dans  toute la  suite,  `x` et  `y` désigneront  des  *Booléens* (éléments  d'une
algèbre de Boole) quelconques, `F` désignera FAUX et `V` désignera VRAI.

____________

## Conjonction (AND)
- symbole usuel : & (appelé _esperluette_ en français et _ampersand_ en anglais)
- français : ET
- anglais (et Python) : `and`
- notation logique : $\wedge$
- notation mathématique :  `.`

C'est l'opération définie par:

* `x & F = F`
* `x & V = x`

Puisque l'algèbre de  Boole ne contient que deux éléments,  on peut étudier tous
les cas possibles et les regrouper dans un tableau appelé **table de vérité**:


|`x`| `y` | `x & y`|
|:--:|:-:|:--:|
|F|F|F|
|F|V|F|
|V|F|F|
|V|V|V|


On représente souvent les opérateurs booléens à l'aide de portes logiques:
![](data/porte_et.png)

Notation usuelle en électronique : $Q=A \wedge B$
![](data/and.png)


### Exemples en Python


```python
n = 20
```


```python
(n % 10 == 0) and (n % 7 == 0)
```




    False




```python
(n % 4 == 0) and (n % 5 == 0)
```




    True



#### L'évaluation paresseuse
Pouvez-vous prévoir le résultat du code ci-dessous ?


```python
(n % 4 == 0) and (n % 0 == 0)
```


    ---------------------------------------------------------------------------

    ZeroDivisionError                         Traceback (most recent call last)

    <ipython-input-3-d8a98dcba9be> in <module>
    ----> 1 (n % 4 == 0) and (n % 0 == 0)
    

    ZeroDivisionError: integer division or modulo by zero


Évidemment, la division par 0 provoque une erreur.  
Mais observez maintenant ce code :


```python
(n % 7 == 0) and (n % 0 == 0)
```




    False



On appelle **évaluation paresseuse** le fait que l'interpréteur Python s'arrête dès que sa décision est prise : comme le premier booléen vaut False et que la conjonction `and` est appelée, il n'est pas nécessaire d'évaluer le deuxième booléen. 

____________

## Disjonction (OR)

- symbole usuel : | appelé _pipe_ en anglais
- français : OU
- anglais (et Python) : `or`
- notation logique : $\vee$
- notation mathématique :  $+$

C'est l'opération définie par:


C'est l'opération définie par:

* `x | V = V`
* `x | F = x`

On en déduit la table suivante:



|`x`| `y` | `x or y`|
|:--:|:----:|:--:|
|F|F| F|
|F|V|V|
|V|F|V|
|V|V|V|



![](data/porte_ou.png)

Notation usuelle en électronique : $Q=A \vee B$

![](data/or.png)


### Exemples en Python


```python
n = 20
```


```python
(n % 10 == 0) or (n % 7 == 0)
```




    True




```python
(n % 4 == 0) or (n % 5 == 0)
```




    True




```python
(n % 7 == 0) or (n % 3 == 0)
```




    False



#### L'évaluation paresseuse (retour)
Pouvez-vous prévoir le résultat du code ci-dessous ?


```python
(n % 5 == 0) or (n % 0 == 0)
```

## Négation (NOT)

- symbole usuel : ~
- français : NON
- anglais (et Python) : `not`
- notation logique :  $\neg$
- notation mathématique :  $\overline{x}$

C'est l'opération définie par:

* `~V = F`
* `~F = V`

On en déduit la table suivante:


|`x`| `~x` |
|:--:|:----:|
|F|V|
|V|F|

![](data/porte_non.png)

Notation usuelle en électronique : $Q=\neg A$

![](data/no.png)

### Exemples en Python


```python
n = 20
```


```python
not(n % 10 == 0)
```




    False



## Exercice 1

Comprendre [ce mème](https://www.reddit.com/r/engineeringmemes/comments/897mu2/logic_gates_drake_version/).


## Exercice 2
1. Ouvrir le [simulateur de circuits](http://dept-info.labri.fr/ENSEIGNEMENT/archi/circuits/blank-teacher.html) et créer pour chaque opération AND, OR, NOT un circuit électrique illustrant ses propriétés.

Exemple (inintéressant) de circuit :
![](data/ex_circuit.png)

2. Utiliser successivement les circuits XOR, NAND et NOR et établir pour chacun leur table de vérité.

# Fonctions composées

## Disjonction exclusive XOR
(en français OU EXCLUSIF)

`x ^ y = (x & ~y) | (~x & y)`


|`x`| `y` | `x ^ y`|
|:--:|:----:|:--:|
|F|F| F|
|F|V|V|
|V|F|V|
|V|V|F|



![](data/porte_xor.png)

![](data/xor.png)

Le XOR joue un rôle fondamental en cryptographie car il possède une propriété très intéressante : 
$(x\wedge y)\wedge y=x$

Si $x$ est un message et $y$ une clé de chiffrage, alors $x\wedge y$ est le message chiffré. 
Mais en refaisant un XOR du message chiffré avec la clé $y$, on retrouve donc le message $x$ initial.

##  Fonction Non Et (NAND)

`x ↑ y = ~(x & y)`


|`x`| `y` | `x ↑ y`|
|:--:|:----:|:--:|
|F|F| V|
|F|V|V|
|V|F|V|
|V|V|F|



![](data/porte_nand.png)

## Non Ou (NOR)


`x ↓ y = ~(x & y)`


|`x`| `y` | `x ↓ y`|
|:--:|:----:|:--:|
|F|F| V|
|F|V|F|
|V|F|F|
|V|V|F|



![](data/porte_nor.png)

Il est temps de se reposer un peu et d'admirer cette vidéo :
![](data/watergates.gif)

## Remarque :
Les fonctions NAND ET NOR sont dites **universelles** : chacune d'entre elles peut générer l'intégralité des autres portes logiques. Il est donc possible de coder toutes les opérations uniquement avec des NAND (ou uniquement avec des NOR).
Voir [Wikipedia](https://fr.wikipedia.org/wiki/Fonction_NON-ET)

## Exercice 4
Calculer les opérations suivantes.


```python
   1011011
&  1010101
----------
   

   1011011
|  1010101
----------
   

   1011011
^  1010101
----------
   
```

*solution*


```python
   1011011
&  1010101
----------
   1010001
   
   1011011
|  1010101
----------
   1011111
   
   1011011
^  1010101
----------
   0001110
```

### Calculs en Python
les opérateurs `&`, `|` et `^` sont utilisables directement en Python


```python
# calcul A
12 & 7
```




    4




```python
# calcul B
12 | 7
```




    15




```python
# calcul C
12 ^ 5
```




    9



Pour comprendre ces résultats, il faut travailler en binaire. Voici les mêmes calculs :


```python
# calcul A
bin(0b1100 & 0b111)
```




    '0b100'




```python
# calcul B
bin(0b1100 | 0b111)
```




    '0b1111'




```python
# calcul C
bin(0b1100 ^ 0b111)
```




    '0b1011'



### Exercice 5 : préparation du pydéfi
Objectif : chiffrer (= crypter) le mot "BONJOUR" avec la clé (de même taille) "MAURIAC".  

Protocole de chiffrage : XOR entre le code ASCII des lettres de même position.



```python
msg = "BONJOUR"
cle = "MAURIAC"

def crypte_lettre(lm, lc):
    a = ord(lm)
    b = ord(lc)
    c = a^b
    lettre = chr(c)

    return lettre

def crypte_mot(mot1, mot2):
    mot3 = ""
    for i in range(len(mot1)):
        car = crypte_lettre(mot1[i],mot2[i])
        mot3 = mot3 + car
    return mot3

crypte_mot(msg, cle)
```




    '\x0f\x0e\x1b\x18\x06\x14\x11'



### Exercice 6 :
Résolvez le pydéfi [la clé endommagée](https://callicode.fr/pydefis/MasqueJetable/txt)

*solution :*

[lien](https://gist.github.com/glassus/7aef2c4cbed5097e1857ecc851b7b740)


```python

```

# Complément : propriétés des opérateurs logiques

Les propriétés suivantes sont facilement démontrables à l'aide de tables de vérités: *(source : G.Connan)*

![](data/lois.png)

Toutes ces lois sont aisément compréhensibles si on les transpose en mathématiques : 
- & équivaut à $\times$
- $|$ équivaut à $+$
- $\neg$ équivaut à $-$
