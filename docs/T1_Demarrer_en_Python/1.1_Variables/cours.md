# 1.1 Variables

## A. Pourquoi des variables ?

### A.1 Introduction
Imaginons à l'oral l'expression *«nous allons stocker le prix du spectacle dans une variable  ```a```, qui vaudra donc au départ 32.»*

Il y a plusieurs commentaires à faire sur une telle annonce :

- Dans le problème que l'on cherche à modéliser, le prix du spectacle est une donnée importante, qui va peut-être évoluer (ou pas !).
- Pour la manipuler plus simplement, on va la désigner par un nom, le **nom de la variable** (ici, le nom ```a``` est particulièrement mal choisi, voir D. Bonnes pratiques de nommage)
- Comme en mathématiques, le nom de cette variable va désigner une valeur qui peut changer (*varier*) au cours du temps (encore une fois : ou pas).
- Cette valeur est fixée *au départ* à 32. On dira en informatique qu'elle est *initialisée* à 32.
- Si cette valeur ne change pas, on dira qu'elle est constante. Cela peut paraître inutile de donner un nom à quelque chose qui ne change pas, mais cela est très utile de définir les constantes au début d'un programme. 

### A.2 On code !
La phrase précédente donnera donc lieu à la ligne Python suivante :

```python
a = 32
```
!!! warning "Attention"
    Le symbole ```=``` ici utilisé n'a **rien à voir** avec le symbole = utilisé en mathématique. On dit qu'on a **affecté** à ```a``` la valeur 32, et il faut se représenter mentalement cette action par l'écriture ```a ← 32```.

!!! note "Comparaison de la syntaxe dans différents langages"

    === "Python"

        ```python
        a = 32
        ```

    === "C"

        ```c
        int a = 32;
        ```

    === "PHP"

        ```PHP
        $a = 32;
        ```


    === "Java"

        ```java
        int a = 32;
        ```

    === "Javascript"

        ```javascript
        var a = 32;
        ```
    === "Rust"

        ```rust
        let a = 32;
        ```
    === "Go"

        ```go
        a := 32
        ```
 
Une fois la valeur 32 stockée dans la variable ```a```, on peut alors utiliser cette variable :

```python
>>> a
32
>>> a + 5
37
>>> b
Traceback (most recent call last):
  File "<pyshell>", line 1, in <module>
NameError: name 'b' is not defined
```

Notez l'erreur de la ligne 5 : on a fait appel à une variable ```b``` qui n'avait jamais été définie, comme le dit explicitement le message ```NameError: name 'b' is not defined``` 

## B. Le fonctionnement interne
### B.1 Explication simplifiée
En première intention, il est possible d'expliquer le fonctionnement interne de l'affectation des variables par la *métaphore des tiroirs* :


Écrire  l'instruction :
```python
a = 2
```

va provoquer chez l'ordinateur le comportement suivant :

- Est-ce que je possède **déjà** un tiroir appelé ```a``` ? 
    - si oui, je me positionne devant.
    - si non, je crée un tiroir appelé ```a```.
    - J'ouvre le tiroir et j'y dépose la valeur numérique 2. Si le tiroir contenait déjà une valeur, celle-ci disparaît (on dit qu'elle est **écrasée**).

![image](data/tiroirs.png){: .center}

Cette explication est suffisante pour aborder la notion de variable : c'est un mot (ou une lettre) qui va désigner une valeur. 

Mais cette métaphore du tiroir est malheureusement un peu trop simplificatrice.

### B.2 Une réalité bien plus complexe...
#### B.2.1 La commande ```id()``` : l'adresse du tiroir ?
Python possède une fonction qui renvoie l'adresse mémoire de la variable donnée en argument. 

```python
>>> b = 7
>>> id(b)
9788800
```

Faites le test avec votre propre IDE Python (vous n'obtiendrez pas forcément la même valeur d'adresse mémoire)

#### B.2.2 Cela se complique.
Sans refermer notre IDE, écrasons la valeur de ```b``` avec une nouvelle valeur :
```python
>>> b = 12
```
et redemandons l'adresse de ```b``` :
```python
>>> id(b)
9788960
```

Très mauvaise nouvelle : l'adresse de la variable ```b``` a changé. Ceci invalide notre métaphore du «tiroir», une place unique qui serait réservée pour y stocker les valeurs successives d'une variable. 

La modification de la valeur de ```b``` ne s'est pas faite «en place», la variable ```b``` s'est déplacée : que s'est-il passé ?

#### B.2.3 Tentative d'explication

L'affectation 
```python
>>> b = 9
```
ne provoque pas la réservation définitive d'un espace-mémoire pour la variable ```b```, mais la création d'un lien vers un espace-mémoire qui contient la valeur 9. Ce lien consiste en l'adresse-mémoire de cette valeur 9. 

Cette adresse-mémoire vaut (sur ma configuration personnelle) ```978864```.
```python
>>> id(b)
978864
```

![image](data/mem1.png){: .center}





Comme le présente le ruban ci-dessus, Python pré-positionne les entiers (de -5 à 256) sur des petites adresses-mémoires, car il considère que ces entiers servent souvent, et doivent donc être rapidement accessibles.

Si on créé une nouvelle variable ```tokyo``` aussi égale à 9, elle va aussi *pointer* vers la même adresse-mémoire :


```python
>>> tokyo = 9
>>> id(tokyo)
9788864
```
Les variables ```tokyo``` et ```b``` renvoient vers la même adresse-mémoire.

Affectons maintenant à ```tokyo``` la valeur 2020 et observons son adresse-mémoire :

```python
>>> tokyo = 2020
>>> id(tokyo)
139762979309936
```

L'adresse-mémoire est (bien) plus grande : elle a été choisie sur le moment par Python pour y stocker 2020 (car 2020 > 256). 

De manière plus surprenante, si on créé une nouvelle variable ```jo``` qui vaut *aussi* 2020, Python va ouvrir une *autre* adresse-mémoire pour y stocker 2020, alors qu'il l'a déjà stockée ailleurs :

```python
>>> jo = 2020
>>> id(jo)
139762979310064
```
#### B.2.4 En conclusion




### B.3 Une histoire en 2 temps : évaluation, affectation

Observons l'instruction
```python
>>> a = 2 + 3
```

#### B.3.1 Étape 1 : **l'évaluation**

Python va prendre la partie à droite du signe égal et va l'évaluer, ce qui signifie qu'il va essayer de lui donner une valeur. Dans nos exemples, cette valeur sera numérique, mais elle peut être d'un autre type (voir plus loin)


Ici, Python effectue le calcul 2 + 3 et l'évalue à la valeur 5.

#### B.3.2 Étape 2 : **l'affectation**
Une fois évaluée l'expression à droite du signe =, il ne reste plus qu'à l'affecter à la variable (déjà existante ou pas) située à gauche du signe =.

Comme expliqué précédemment, un «lien» est fait entre le nom de la variable et l'adresse-mémoire qui contient la valeur évaluée.
```a``` sera donc lié à la valeur 5. Plus simplement, on dira que «```a``` vaut 5» 

#### B.3.2 L'incrémentation d'une variable.

#### B.3.3 L'échange de variables

## C. Différents types de variables

## D. Bonnes pratiques de nommage