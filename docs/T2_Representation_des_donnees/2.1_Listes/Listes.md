# Définition
Les listes font partie de ce qu'on appelle les *données composites* (nous verrons plus tard les *tuples* et les *dictionnaires*). Elles permettent de regrouper de manière structurée des ensembles de valeurs.
On les appelle *listes* en Python, ou bien *tableaux* de manière plus générale.


**Notation :** dans une liste, les éléments sont séparés par des **virgules**, et l'ensemble est délimité par des **crochets**.


```python
ma_premiere_liste = [1, "ok", True]
```

Même si cela n'a ici un grand intérêt, les éléments d'une liste peuvent donc être de types différents : ici, nous avons successivement un entier (`int`), une chaine de caractères (`str`), et un booléen (`bool`).

 ## Accès aux éléments d'une liste
 On accède à un élément d'une liste en mettant entre crochets l'indice de l'élémént (qui commence à **zéro**).


```python
famille = ["Bart", "Lisa", "Maggie"]
```


```python
famille[0]
```




    'Bart'



Un indice qui dépasse la valeur  `longueur de la liste -1` provoquera une erreur `list index out of range`.


```python
famille[3]
```


    ---------------------------------------------------------------------------

    IndexError                                Traceback (most recent call last)

    <ipython-input-4-6e7a4ba7ec75> in <module>
    ----> 1 famille[3]
    

    IndexError: list index out of range


Il est par contre possible d'utiliser des indices **négatifs** :


```python
famille[-1]
```




    'Maggie'



## Longueur d'une liste
La longueur d'une liste sera donnée par la fonction `len()`


```python
len(famille)
```




    3



Attention : le dernier élément de la liste a donc l'indice `len(liste)-1`

## Parcours des éléments d'une liste


```python
for k in range(len(famille)):
    print(famille[k])
```

    Bart
    Lisa
    Maggie


**Remarque :** nous avons déjà vu une méthode plus directe de parcours d'une liste :


```python
for k in famille :  # <- beaucoup plus efficace !
    print(k)
```

    Bart
    Lisa
    Maggie


## Les éléments d'une liste sont MODIFIABLES.
C'est une différence fondamentale avec une autre structure (les *tuples*) que nous verrons plus tard.


```python
famille[0] = "Milhouse"
```


```python
famille
```




    ['Milhouse', 'Lisa', 'Maggie']



On dit que les listes sont des objets **mutables**.

## Ajout d'un élement à une liste : méthode **append()**


```python
famille.append("Lisa")
```


```python
famille
```




    ['Milhouse', 'Lisa', 'Maggie', 'Lisa']



La méthode `append()` rajoute donc un élément **à la fin** de la liste.

## Liste vide
Très souvent, la méthode `append()` ci-dessus est utilisée à partir d'une liste vide `[]`, à laquelle on rajoute peu à peu des éléments.

####  Exemple
Filtrons la liste m ci-dessous pour n'en garder que les éléments supérieurs à 20.


```python
m = [45, 12, 15, 20, 18, 19, 23, 17, 12, 18]
p = []

for k in m :
    if k > 20:
        p.append(k)
```

## Suppression d'un élément d'une liste ...
### ... par la méthode remove() :


```python
famille.remove("Lisa")
```


```python
famille
```




    ['Milhouse', 'Maggie']



La méthode `remove()` va supprimer le premier élément de la liste (ce qui est problématique s'il y en a plusieurs) qui correspond à l'élément passé en argument.


```python
maliste = [8, 4, 2, 4, 7]
maliste.remove(4)
```


```python
maliste
```




    [8, 2, 4, 7]




```python
maliste.remove(5)
```


    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    <ipython-input-20-a72d2de18dbe> in <module>
    ----> 1 maliste.remove(5)
    

    ValueError: list.remove(x): x not in list


### ...  par la fonction del() :
La fonction `del()` permet de supprimer un élément en donnant son indice.


```python
maliste = [8, 4, 2, 5, 7]
del maliste[3]
```


```python
maliste
```




    [8, 4, 2, 7]




```python

```

## Exercice :
Trouvez le nombre qui est exactement à la même place dans la liste `a` et dans la liste `b` (les deux listes ont la même taille)


```python
a = [8468, 4560, 3941, 3328, 7, 9910, 9208, 8400, 6502, 1076, 5921, 6720, 948, 9561, 7391, 7745, 9007, 9707, 4370, 9636, 5265, 2638, 8919, 7814, 5142, 1060, 6971, 4065, 4629, 4490, 2480, 9180, 5623, 6600, 1764, 9846, 7605, 8271, 4681, 2818, 832, 5280, 3170, 8965, 4332, 3198, 9454, 2025, 2373, 4067]
b = [9093, 2559, 9664, 8075, 4525, 5847, 67, 8932, 5049, 5241, 5886, 1393, 9413, 8872, 2560, 4636, 9004, 7586, 1461, 350, 2627, 2187, 7778, 8933, 351, 7097, 356, 4110, 1393, 4864, 1088, 3904, 5623, 8040, 7273, 1114, 4394, 4108, 7123, 8001, 5715, 7215, 7460, 5829, 9513, 1256, 4052, 1585, 1608, 3941]


for i in range(len(a)):
    if a[i] == b[i]:
        print(a[i], " à l'indice ", i)

```

    5623  à l'indice  32



```python
i
```




    2



## Construction d'une liste d'éléments identiques


```python
p = [0]*12
```


```python
p
```




    [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]



Cette instruction est très utile pour initialiser des listes de taille donnée.

### Exemple
le code ci-dessous compte l'occurence de chaque lettre de l'alphabet dans un texte.


```python
texte = "cet texte est prodigieusement ennuyeux"

def rang(lettre):
    return(ord(lettre)-97)

compt = [0]*26
for k in texte :
    if k != " " :
        compt[rang(k)] += 1
```


```python
compt
```




    [0, 0, 1, 1, 9, 0, 1, 0, 2, 0, 0, 0, 1, 3, 1, 1, 0, 1, 2, 5, 3, 0, 0, 2, 1, 0]



## Construction d'une liste (méthode dite *par compréhension*)


```python
nombres = [k for k in range(10)]
```


```python
nombres
```




    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]



Il est bien sûr possible d'agir sur le paramètre :


```python
carres_parfaits = [k**2 for k in range(10)]
```


```python
carres_parfaits
```




    [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]



Plus subtil, on peut filtrer "à la volée" les éléments pour n'en garder que certains.


```python
c = [n for n in carres_parfaits if n % 3 == 0]
```


```python
c
```




    [0, 9, 36, 81]



### Exercice
En une ligne, créez la liste `p` qui contient tous les éléments positifs de `m`.


```python
m = [-3, -6, 4, 7, -2, 1, -3, 5]
p = [k for k in m if k > 0]
```


```python
p
```




    [4, 7, 1, 5]



## Un phénomène inquiétant : la copie de liste


```python
a = 3
b = a
a = 5
```


```python
id(a)
```




    1527898960




```python
id(b)
```




    1527898928




```python
b
```




    3




```python
a = [4, 5, 7]
b = a
a[0] = 12
```

Selon toute vraisemblance, la liste `a` est maintenant égale à `[12, 5, 7]`. 
Vérifions-le :


```python
id(a)
```




    81446152




```python
id(b)
```




    81446152




```python
a
```




    [12, 5, 7]



Tout est donc normal. Mais :


```python
b
```




    [12, 5, 7]



`b` est lui **aussi** devenu égal à `[12, 5, 7]`, alors que la modification sur l'élément `a[0]` n'a été faite qu'**après** l'affectation `b = a`.  
Les listes `a` et `b` sont en fait strictement et définitivement identiques, elles sont simplement deux dénominations différentes d'un même objet. 
On peut le vérifier en regardant l'emplacement-mémoire vers lequel pointent la variable `a` et la variable `b` :


```python
id(a)
```


```python
id(b)
```

## Comment copier le contenu d'une liste vers une autre
Parmi plusieurs solutions, celle-ci est simple et efficace : la méthode `copy()`


```python
a = [3, 4, 9]
b = a.copy()
a[0] = 12
```


```python
a
```




    [12, 4, 9]




```python
b
```




    [3, 4, 9]



On pourrait aussi écrire `b = list(a)` mais la méthode `copy()` a l'avantage d'exister aussi pour les *dictionnaires*, que nous verrons plus tard.

# Tableaux à plusieurs dimensions : listes de listes


```python
a = [[3, 5, 2],
     [7, 1, 4], 
     [8, 6, 9]]
```

La liste `a` est composée de 3 éléments qui sont eux-même des listes de 3 éléments.


```python
a[0]
```




    [3, 5, 2]




```python
a[0][1]
```




    5




```python
a[2][2]
```




    9



## Exercice
Résolvez ce [pydéfi](https://callicode.fr/pydefis/AlgoMat/txt)

Solution possible :


```python
M=[[36, 19, 27, 36, 7, 10], [2, 18, 3, 33, 2, 21], [26, 27, 4, 22, 30, 31], [29, 36, 7, 20, 6, 30], [30, 6, 14, 23, 15, 13], [22, 10, 10, 35, 15, 22]]

def modif(k):
    return ( 11*k + 4 ) % 37

for k in range(23): #pour répéter 23 fois
    for i in range(6) :
        for j in range(6):
            M[i][j] = modif(M[i][j]) 
            # ou bien M[i][j] = ( 11*M[i][j] + 4 ) % 37

s = 0
for i in range(6) :
    for j in range(6):
        s = s + M[i][j] 
```


```python
s
```




    575



### Pydéfi :  Le sanglier d'Erymanthe
https://callicode.fr/pydefis/Herculito04Sanglier/txt


```python
M = [0, 50, 40, 100, 70, 90, 0]
s = 0
for k in range(7-1):
    if M[k] > M[k+1]:
        pierreLancees = (M[k]-M[k+1])//10+1
        s += pierreLancees
print(s)

# penser à faire le total des pierres lancées depuis le début
```

    16


*En une ligne (aucun intérêt à part pour épater la galerie...) :*


```python
M = [0, 50, 40, 100, 70, 90, 0]
k = sum([(M[i]-M[i+1])//10+1 for i in range(len(M)-1) if M[i]>M[i+1]])
```


```python
k
```




    16


