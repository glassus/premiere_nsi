# 4.4 Tri par sélection

![image](data/BO.png){: .center}


## 1. Animation
Considérons la liste `[5, 4, 2, 1]`  
Voici le fonctionnement de l'algorithme :  
![](data/selection.gif){: .center}

## 2. Principe

!!! note "description de l'algorithme"
    Le travail se fait essentiellement sur les **indices**.
    
    - du premier élément jusqu'à l'avant-dernier :
        - on considère que cet élément est l'élément minimum, on stocke donc son indice dans une variable *indice du minimum*.
        - on parcourt les éléments suivants, et si on repère un élémént plus petit que notre mininum on met à jour notre *indice du minimum*.
        - une fois le parcours fini, on échange l'élément de travail avec l'élément minimum qui a été trouvé.
 




## 3. Implémentation de l'algorithme

!!! abstract "Tri par sélection :heart: "
    ```python
    def tri_selection(lst) :
        for k in range(len(lst)-1):
            indice_min = k
            for i in range(k+1, len(lst)) :
                if lst[i] < lst[indice_min]:
                    indice_min = i
            lst[k], lst[indice_min] = lst[indice_min], lst[k]
    ```

*Vérification :*

```python
>>> ma_liste = [7, 5, 2, 8, 1, 4]
>>> tri_selection(ma_liste)
>>> ma_liste
[1, 2, 4, 5, 7, 8]
```

    


## 4. Complexité de l'algorithme


### 4.1 Mesure du temps d'exécution

Nous allons fabriquer deux listes de taille 100 et 200 :



```python
lst_a = [k for k in range(100,0,-1)] #on se place dans le pire des cas : une liste triée dans l'ordre décroissant

lst_b = [k for k in range(200,0,-1)] #on se place dans le pire des cas : une liste triée dans l'ordre décroissant
```


La mesure du temps moyen de tri pour ces deux listes donne le résultat ci-dessous (avec le module ```timeit``` sous Jupyter Notebook)

```python
%timeit tri_selection(lst_a)

    632 µs ± 14.3 µs per loop (mean ± std. dev. of 7 runs, 1000 loops each)
```


```python
%timeit tri_selection(lst_b)

    2.35 ms ± 35.9 µs per loop (mean ± std. dev. of 7 runs, 100 loops each)
```

En comparant les temps de tri des listes `lst_a` et `lst_b`, que pouvez-vous supposer sur la complexité du tri par sélection ?

<!--
Une liste à trier 2 fois plus longue prend 4 fois plus de temps : l'algorithme semble de complexité **quadratique**.
-->


### 4.2. Calcul du nombre d'opérations
Dénombrons le nombre d'opérations, pour une liste de taille $n$.

- boucle `for` : elle s'exécute $n-1$ fois.
- deuxième boucle `for` imbriquée : elle exécute d'abord 1 opération, puis 2, puis 3... jusqu'à $n-1$. 

Or 
$1+2+3+\dots+n-1=\dfrac{n \times (n-1)}{2}$

Ceci est bien un polynôme du second degré, ce qui confirme que la complexité de ce tri est quadratique.

**Vérification expérimentale**

Insérez un compteur `c` dans votre algorithme pour vérifier le calcul précédent. On pourra renvoyer cette valeur en fin d'algorithme par un `return c`.



## 5. Preuve de la terminaison de l'algorithme

**Est-on sûr que notre algorithme va s'arrêter ?**

À l'observation du programme, constitué de deux boucles `for` imbriquées, il n'y a pas d'ambiguïté : on ne peut pas rentrer dans une boucle infinie. Le programme s'arrête forcément au bout de d'un nombre fixe d'opérations. 
D'après nos calculs sur la complexité, ce nombre de tours de boucles est égal à $\dfrac{n \times (n-1)}{2}$.

Ceci prouve que l'algorithme se terminera.


## 6. Preuve de la correction de l'algorithme

**Est-on sûr que notre algorithme va bien trier notre liste ?**

Les preuves de correction sont des preuves théoriques. La preuve ici s'appuie sur le concept mathématique de **récurrence**. 
Principe du raisonnement par récurrence : 
une propriété $P(n)$ est vraie si :

- $P(0)$ (par exemple) est vraie
- Pour tout entier naturel $n$, si $P(n)$ est vraie alors $P(n+1)$ est vraie.

Ici, la propriété serait : « Quand $k$ varie entre 0 et `longueur(liste) -1`, la sous-liste de longueur $k$ est triée dans l'ordre croissant.» On appelle cette propriété un **invariant de boucle** (sous-entendu : elle est vraie pour chaque boucle)

- quand $k$ vaut 0, on place le minimum de la liste en l[0], la sous-liste l[0] est donc triée.
-  si la sous-liste de $k$ éléments est triée, l'algorithme rajoute en dernière position de la liste le minimum de la sous-liste restante, dont tous les éléments sont supérieurs au maximum de la sous-liste de $k$ éléments. La sous-liste de $k+1$ éléments est donc aussi triée.

## 7. Bonus : comparaison des algorithmes de tri 


Une jolie animation permettant de comparer les tris :

![image](data/comparaisons.gif){: .center}

Issue de ce [site](https://www.toptal.com/developers/sorting-algorithms).

