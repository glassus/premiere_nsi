# 2.1 Listes

![image](data/BO.png){: .center}



Les listes font partie de ce qu'on appelle les *données composites* (nous verrons plus tard les *tuples* et les *dictionnaires*). Elles permettent de regrouper de manière structurée un **ensemble de valeurs** (et non plus une valeur unique).
On les appelle *listes* en Python, ou bien *tableaux* de manière plus générale.

## 1. Déclaration d'une liste
!!! note "Exemple fondateur n°1 :heart:"
    Une variable de type liste sera délimitée par des **crochets**, et ses éléments séparés par des **virgules** :
    ```python
    >>> maliste = ["riri", "fifi", "loulou"]
    ```

On peut observer le type de la variable ainsi créée :
```python
>>> type(maliste)
<class 'list'>
```

**Remarques :**

- Même si cela n'a ici un grand intérêt, les éléments d'une liste peuvent donc être de types différents : ici, tous les éléments de ma liste sont des chaînes de caractères (`str`), mais la liste `["riri", 5, "fifi", "loulou"]` est aussi une liste valide.

- Une liste **vide** se déclarera avec ```[]```.
```python
>>> copies_corrigees = []
``` 
Nous verrons plus tard qu'il est fréquent dans les exercices de partir d'une liste vide et d'ajouter progressivement des éléments.




## 2. Accès aux éléments d'une liste

!!! note "Exemple fondateur n°2 :heart:"
    On accède à un élément d'une liste en mettant entre crochets l'indice de l'élément (qui commence à **zéro**).
    ```python
    >>> famille = ["Bart", "Lisa", "Maggie"]
    >>> famille[0]
    'Bart'
    >>> famille[1]
    'Lisa'
    >>> famille[2]
    'Maggie'
    >>> famille[3]
    Traceback (most recent call last):
      File "<pyshell>", line 1, in <module>
    IndexError: list index out of range

    ```


**Remarques :**

- Un indice qui dépasse la valeur  `longueur de la liste -1` provoquera donc une erreur `list index out of range`. C'est une erreur **très fréquente** lorsqu'on manipule des listes.
![image](data/errorindex.jpg){: .center width=50%}



- Il est par contre possible d'utiliser des indices **négatifs**. On utilise par exemple très souvent l'indice -1 pour accéder au dernier élément de la liste, sans avoir à connaître la longueur de celle-ci :

```python
>>> famille[-1]
'Maggie'
```

## 3. Longueur d'une liste

!!! note "Exemple fondateur n°3 :heart:"
    La longueur d'une liste sera donnée par la fonction `len()`, qui renvoie donc un nombre entier positif ou nul.
    ```python
    >>> len(famille)
    3
    ```

**Remarques :**

- La liste vide a pour longueur 0 :
```python
>>> len([])
0
```
- Le dernier élément d'une liste ```maliste``` (non vide) sera donc toujours l'élément d'indice ```len(maliste)-1```.
```python
>>> famille[len(famille) - 1]
'Maggie'
```
- Comme indiqué précédemment, ce dernier élément est aussi accessible par l'indice -1.




## 4. Parcours des éléments d'une liste :star: :star: :star:

Il existe deux méthodes pour parcourir séquentiellement tous les éléments d'une liste. Ces deux méthodes sont à maîtriser impérativement.

### 4.1 Parcours «par éléments»

C'est la méthode la plus naturelle, celle déjà vue lors de la présentation de la boucle ```for```. Nous allons simplement *itérer* sur les éléments de la liste.

!!! note "Exemple fondateur n°4 :heart:"
    Le code :
    ```python linenums='1'
    famille = ["Bart", "Lisa", "Maggie"]

    for membre in famille:
        print(membre)
    ```
    renverra :
    ```python
    Bart
    Lisa
    Maggie
    ```

**Remarque :**

- Penser à donner un nom signifiant à la variable qui parcourt la liste. Il aurait par exemple été très maladroit d'écrire 
```python
for k in famille:
    print(k)
```
En effet le nom de variable ```k``` est habituellement utilisé pour les nombres (les indices, les compteurs...).

### 4.2 Parcours «par indice»

Chaque élément étant accessible par son indice (de ```0``` à   ```len(liste) - 1``` ), il suffit de faire parcourir à une variable ```i``` l'ensemble des entiers de ```0``` à   ```len(liste) - 1```, par l'instruction ```range(len(liste))``` :


!!! note "Exemple fondateur n°5 :heart:"
    Le code :
    ```python linenums='1'
    famille = ["Bart", "Lisa", "Maggie"]

    for i in range(len(famille)):
        print(famille[i])
    ```
    renverra :
    ```python
    Bart
    Lisa
    Maggie
    ```

### 4.3 Avantages et inconvénients de chaque méthode

#### 4.3.1 Parcours par élément 

```python
    for membre in famille:
        print(membre)
```

**Les avantages** :+1:

- la simplicité : un code plus facile à écrire, avec un nom de variable explicite.
- la sécurité  : pas de risque d'```index out of range``` !

**Les inconvénients** :-1:

- méthode rudimentaire : lorsqu'on est «positionné» sur un élément, il n'est pas possible d'accéder au précédent ou au suivant. (et c'est parfois utile).

#### 4.3.2 Parcours par indice 

```python
    for i in range(len(famille)):
        print(famille[i])
```

**Les avantages**  :+1:

- le contrôle : en parcourant par indice, on peut s'arrêter où on veut, on peut accéder au suivant/précédent...
- pour les tableaux à deux dimensions, on retrouve la désignation classique d'un élément par numéro de ligne / numéro de colonne.

**Les inconvénients** :-1:

- la complexité : il faut connaître le nombre d'éléments de la liste (ou le récupérer par la fonction ```len()``` )
- le risque d'erreur : encore et toujours le ```index out of range```...


{{initexo(0)}}
!!! example "{{ exercice() }}"
    === "Énoncé"
        On donne la liste :
        ```python
        lst = [3, 1, 4, 1, 5, 9]
        ```
        Afficher les éléments de cette liste dans l'ordre inverse (en commençant par 9)

    === "Correction"
        {{ correction(False,
        "
        ```python linenums='1'
        lst = [3, 1, 4, 1, 5, 9]

        for i in range(len(lst)-1, -1, -1):
            print(lst[i])


        ```
        "
        ) }}

!!! example "{{ exercice() }}"
    === "Énoncé"
        Trouvez le nombre qui est **exactement à la même place** dans la liste `list1` et dans la liste `list2`, sachant que :

        - les deux listes ont la même taille
        - vous n'avez droit qu'à une seule boucle ```for```. 

        ```python
        list1 = [8468, 4560, 3941, 3328, 7, 9910, 9208, 8400, 6502, 1076, 5921, 6720, 948, 9561, 7391, 7745, 9007, 9707, 4370, 9636, 5265, 2638, 8919, 7814, 5142, 1060, 6971, 4065, 4629, 4490, 2480, 9180, 5623, 6600, 1764, 9846, 7605, 8271, 4681, 2818, 832, 5280, 3170, 8965, 4332, 3198, 9454, 2025, 2373, 4067]
        list2 = [9093, 2559, 9664, 8075, 4525, 5847, 67, 8932, 5049, 5241, 5886, 1393, 9413, 8872, 2560, 4636, 9004, 7586, 1461, 350, 2627, 2187, 7778, 8933, 351, 7097, 356, 4110, 1393, 4864, 1088, 3904, 5623, 8040, 7273, 1114, 4394, 4108, 7123, 8001, 5715, 7215, 7460, 5829, 9513, 1256, 4052, 1585, 1608, 3941]
        ```
        
    === "Correction"
        {{ correction(False,
        "
        ```python linenums='1'
        list1 = [8468, 4560, 3941, 3328, 7, 9910, 9208, 8400, 6502, 1076, 5921, 6720, 948, 9561, 7391, 7745, 9007, 9707, 4370, 9636, 5265, 2638, 8919, 7814, 5142, 1060, 6971, 4065, 4629, 4490, 2480, 9180, 5623, 6600, 1764, 9846, 7605, 8271, 4681, 2818, 832, 5280, 3170, 8965, 4332, 3198, 9454, 2025, 2373, 4067]
        list2 = [9093, 2559, 9664, 8075, 4525, 5847, 67, 8932, 5049, 5241, 5886, 1393, 9413, 8872, 2560, 4636, 9004, 7586, 1461, 350, 2627, 2187, 7778, 8933, 351, 7097, 356, 4110, 1393, 4864, 1088, 3904, 5623, 8040, 7273, 1114, 4394, 4108, 7123, 8001, 5715, 7215, 7460, 5829, 9513, 1256, 4052, 1585, 1608, 3941]

        for i in range(len(list1)):
            if list1[i] == list2[i]:
                print(list1[i])
        ```
        "
        ) }}





## 5. Modification d'une liste

En Python, les objets de type ```List``` sont modifiables (on emploie le mot *mutables*). Et c'est souvent une bonne chose, car des listes peuvent évoluer après leur création.
Lorsqu'on souhaitera **figer** le contenu d'une liste (pour des raisons de sécurité du code essentiellement), on utilisera alors le type ```Tuple```, qui sera vu ultérieurement.

### 5.1 Modification d'un élément existant
Il suffit d'écraser la valeur actuelle avec une nouvelle valeur

!!! note "Exemple fondateur n°6 :heart:"
    ```python 
    >>> famille = ["Bart", "Lisa", "Maggie"]
    >>> famille[0] = "Bartholomew" # oui, c'est son vrai nom
    >>> famille
    ['Bartholomew', 'Lisa', 'Maggie']   
    
    ```


### 5.2 Ajout d'un élement à la fin d'une liste : la méthode **append()** :star: 


!!! note "Exemple fondateur n°7 :heart:"
    ```python 
    >>> famille = ["Bart", "Lisa", "Maggie"]
    >>> famille.append("Milhouse")
    >>> famille
    ['Bart', 'Lisa', 'Maggie', 'Milhouse']  
    ```

**Remarques :**

- La méthode `append()` rajoute donc un élément **à la fin** de la liste.
- *(HP)* Il est possible d'insérer un élément à la position ```i``` avec la méthode ```insert``` :
```python
>>> famille = ["Bart", "Lisa", "Maggie"]
>>> famille.insert(1, "Nelson") # on insère à la position 1
>>> famille
['Bart', 'Nelson', 'Lisa', 'Maggie']
```


!!! example "{{ exercice() }}"
    === "Énoncé"
        Construire une liste contenant tous les nombres inférieurs à 100 qui sont divisibles par 7.
    === "Correction"
        {{ correction(True,
        "
        ```python linenums='1'
        lst = []
        for n in range(1, 101):
            if n % 7 == 0:
                lst.append(n)
        ```
        "
        ) }}

### 5.3 Suppression d'un élément d'une liste ...
#### 5.3.1 ... par la méthode remove() 

!!! note "Exemple fondateur n°7 :heart:"
    ```python 
    >>> famille = ['Bart', 'Nelson', 'Lisa', 'Maggie']
    >>> famille.remove("Nelson")
    >>> famille
    ['Bart', 'Lisa', 'Maggie']
    ```

**Remarques :**

- Attention, ```remove``` n'enlève que la *première occurrence* de l'élément désigné. S'il y en a d'autres après, elles resteront dans la liste :
```python
>>> lst = [3, 1, 4, 5, 1, 9]
>>> lst.remove(1)
>>> lst
[3, 4, 5, 1, 9]
```
- Si l'élément à supprimer n'est pas trouvé, un message d'erreur est renvoyé :
```python
>>> lst = [3, 1, 4, 5, 1, 9]
>>> lst.remove(6)
Traceback (most recent call last):
  File "<pyshell>", line 1, in <module>
ValueError: list.remove(x): x not in list
```


### 5.3.2 ... par l'instruction ```del```
L'instruction `del`  (qui n'est pas une fonction) permet de supprimer un élément en donnant son indice.


```python
>>> maliste = [8, 4, 2, 5, 7]
>>> del maliste[3]
>>> maliste
[8, 4, 2, 7]
```





## 6. Construction d'une liste d'éléments identiques
Il est souvent pratique d'initialiser une liste de taille donnée, souvent en la remplissant de 0.

Imaginons par exemple que nous souhaitions une liste de taille 26 remplie de 0.
Il est possible de faire comme ceci :

```python linenums='1'
lst = []
for k in range(26):
    lst.append(0)
```

mais on préfèrera ce code :

!!! note "Exemple fondateur n°8 :heart:"
    ```python 
    >>> lst = [0]*26
    ```
qui produira la liste ```[0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]``` 


!!! example "{{ exercice() }}"
    === "Énoncé"
        Que fait le code ci-dessous ?
        ```python
        texte = "cet texte est prodigieusement ennuyeux"

        def rang(lettre):
            return(ord(lettre) - 97)

        compt = [0]*26
        for lettre in texte :
            if lettre != " " :
                compt[rang(lettre)] += 1
        ```

    === "Correction"
        {{ correction(True,
        "
        À l'issue de ce code la variable ```compt``` contient ```[0, 0, 1, 1, 9, 0, 1, 0, 2, 0, 0, 0, 1, 3, 1, 1, 0, 1, 2, 5, 3, 0, 0, 2, 1, 0]```, qui correspond au nombre d'occurences de chaque lettre : 0 fois la lettre 'a', 0 fois la lettre 'b', 1 fois la lettre 'c', etc.

        Ce genre de comptage se fera de manière beaucoup plus efficace et élégante avec la structure de dictionnaire.
        "
        ) }}


## 7. Construction d'une liste *par compréhension* :star: :star: :star:


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



## 8. Un phénomène inquiétant : la copie de liste


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

### Comment copier le contenu d'une liste vers une autre
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

## 9. Tableaux à plusieurs dimensions : listes de listes


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


