# Algorithmes de tri (2) : tri par sélection

## Principe
- le travail sur le fait essentiellement sur les **indices**.
- on part de l'indice du premier élément, on considère que cet élément est l'élément minimum.
- on parcourt les éléments suivants, et si on repère un élémént plus petit que notre mininum on garde en mémoire l'indice de ce nouvel élément minimum.
- une fois le parcours fini, on échange l'élément de travail avec l'élément minimum qui a été trouvé.
- on avance d'un élément, et on recommence, jusqu'à l'avant-dernier.


## Animation
Considérons la liste `[5, 4, 2, 1]`  
Voici le fonctionnement de l'algorithme :  
![](data/selection.gif)

## Codage de l'algorithme

Complétez l'algorithme ci-dessous


```python
def tri(l) :
    for k in range(0, len(l)-1):
        indice_du_minimum = k
        for i in range(k+1,len(l)) :
            if l[i] < l[indice_du_minimum]:
                indice_du_minimum = i
        l[k], l[indice_du_minimum] = l[indice_du_minimum], l[k]
```

*Vérification :*


```python
a = [7, 5, 2, 8, 1, 4]
tri(a)
print(a)
```

    [1, 2, 4, 5, 7, 8]


## Complexité de l'algorithme

Pour pouvoir utiliser la fonction `%timeit`, nous allons modifier légèrement notre algorithme de tri : comme la fonction `%timeit` effectue un grand nombre d'appel à la fonction `tri()`, la liste serait triée dès le premier appel et les autres appels essaieraient donc de tri une liste *déjà triée*. 


```python
def tri(L) :
    l = list(L) # pour ne pas modifier la liste passée en argument.
    for k in range(0, len(l)-1):
        indice_du_minimum = k
        for i in range(k+1,len(l)) :
            if l[i] < l[indice_du_minimum]:
                indice_du_minimum = i
        l[k], l[indice_du_minimum] = l[indice_du_minimum], l[k]
```


```python
a = [k for k in range(100,0,-1)] #on se place dans le pire des cas : une liste triée dans l'ordre décroissant
```


```python
b = [k for k in range(200,0,-1)] #on se place dans le pire des cas : une liste triée dans l'ordre décroissant
```


```python
%timeit tri(a)
```

    632 µs ± 14.3 µs per loop (mean ± std. dev. of 7 runs, 1000 loops each)



```python
%timeit tri(b)
```

    2.35 ms ± 35.9 µs per loop (mean ± std. dev. of 7 runs, 100 loops each)


En comparant les temps de tri des listes `a` et `b`, que pouvez-vous supposer sur la complexité du tri par sélection ?

Une liste à trier 2 fois plus longue prend 4 fois plus de temps : l'algorithme semble de complexité **quadratique**.


```python

```

## Calcul du nombre d'opérations
Dénombrons le nombre d'opérations, pour une liste de taille $n$.
- boucle for : elle s'exécute $n-1$ fois.
- deuxième boucle for imbriquée : elle exécute d'abord 1 opération, puis 2, puis 3... jusqu'à $n-1$. Or 
$$1+2+3+\dots+n-1=\dfrac{n \times (n-1)}{2}$$

## Vérification expérimentale

Insérez un compteur `c` dans votre algorithme pour vérifier le calcul précédent. On pourra renvoyer cette valeur en fin d'algorithme par un `return c`.


```python

```

## Preuve de la terminaison de l'algorithme



Est-on sûr que notre algorithme va s'arrêter ?  
À l'observation du programme, constitué de deux boucles `for` imbriquées, il n'y a pas d'ambiguïté : on ne peut pas rentrer dans une boucle infinie. Le programme s'arrête forcément au bout de d'un nombre fixe d'opérations. 
D'après nos calculs sur la complexité, ce nombre de tours de boucles est égal à $$\dfrac{n \times (n-1)}{2}$$ 

Ceci prouve que l'algorithme se terminera.


## Preuve de la correction de l'algorithme
Les preuves de correction sont des preuves théoriques. La preuve ici s'appuie sur le concept mathématique de **récurrence**. 
Principe du raisonnement par récurrence : 
une propriété $P(n)$ est vraie si :
- $P(0)$ (par exemple) est vraie
- Pour tout entier naturel $n$, si $P(n)$ est vraie alors $P(n+1)$ est vraie.

Ici, la propriété serait : « Quand $k$ varie entre 0 et `longueur(liste) -1`, la sous-liste de longueur $k$ est triée dans l'ordre croissant.» On appelle cette propriété un **invariant de boucle** (sous-entendu : elle est vraie pour chaque boucle)

- quand $k$ vaut 0, on place le minimum de la liste en l[0], la sous-liste l[0] est donc triée.
-  si la sous-liste de $k$ éléments est triée, l'algorithme rajoute en dernière position de la liste le minimum de la sous-liste restante, dont tous les éléments sont supérieurs au maximum de la sous-liste de $k$ éléments. La sous-liste de $k+1$ éléments est donc aussi triée.



```python

```
