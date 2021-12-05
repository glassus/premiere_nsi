# Algorithmes de tri (1) : tri par insertion
<img src="data/color_bars.svg" width='30%' />

## Préambule
Pourquoi étudier des algorithmes de tri ?  
Autant ne pas le cacher, ces algorithmes sont déjà implémentés (quelque soit le langage) dans des fonctions très performantes.  

En Python, on utilise la fonction `sort()`



```python
tab = [4, 8, 1, 2, 6]
tab.sort()
```


```python
tab
```

Le meilleur de nos futurs algorithmes de tri sera moins efficace que celui de cette fonction `sort()`...  
Malgré cela, il est essentiel de se confronter à l'élaboration manuelle d'un algorithme de tri.  
Le tri par insertion est le premier des deux algorithmes de tri que nous allons étudier (nous étudierons aussi le tri par sélection).  
Ces deux algorithmes ont pour particularité de :
- ne pas nécessiter la création d'une nouvelle liste. Ils modifient la liste à trier sur place.
- ne pas faire intervenir de fonctions complexes (comme la recherche d'un minimum par exemple)


## Tri par insertion (version la plus intuitive)
Considérons la liste `[7, 5, 2, 8, 1, 4]`  
Voici le fonctionnement de l'algorithme :  
![](data/insertion1.gif)

**Explications :**
- on traite successivement toutes les valeurs à trier, en commençant par celle en deuxième position.
- Traitement : tant que la valeur à traiter est inférieure à celle située à sa gauche, on échange ces deux valeurs.

## Codage de l'algorithme

**algorithme :** 

Pour toutes les valeurs, en commençant par la deuxième :
- tant qu'on trouve à gauche une valeur supérieure et qu'on n'est pas revenu à la première valeur, on échange ces deux valeurs.


```python
def tri(lst):
    '''trie la liste lst donnée en paramètre'''
    for i in range(1, len(lst)):
        k = i
        while  k > 0 and lst[k-1] > lst[k] :
            lst[k], lst[k-1] = lst[k-1], lst[k] 
            k = k -1
```

*Vérification :*


```python
a = [7, 5, 2, 8, 1, 4]
tri(a)
print(a)
```

## Tri par insertion (version optimisée)
Observez l'animation ci-dessous et comparer avec la version initiale.  
![](data/insertion2.gif)

## Codage de l'algorithme

Voici l'algorithme optimisé :


```python
def tri(lst) :
    for k in range(1,len(lst)):
        cle = lst[k]
        i = k-1
        while  i>=0 and lst[i] > cle :
            lst[i+1] = lst[i]
            i = i -1
        lst[i+1] = cle
```

*Vérification :*


```python
a = [7, 5, 2, 8, 1, 4]
tri(a)
print(a)
```

## Complexité de l'algorithme

Pour pouvoir utiliser la fonction `%timeit`, nous allons modifier légèrement notre algorithme de tri : comme la fonction `%timeit` effectue un grand nombre d'appel à la fonction `tri()`, la liste serait triée dès le premier appel et les autres appels essaieraient donc de tri une liste *déjà triée*. 


```python
def tri(L) :
    l = list(L) # pour ne pas modifier la liste passée en argument.
    for k ...
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


```python
%timeit tri(b)
```

En comparant les temps de tri des listes `a` et `b`, que pouvez-vous supposer sur la complexité du tri par insertion ?

Une liste à trier 2 fois plus longue prend 4 fois plus de temps : l'algorithme semble de complexité **quadratique**.

## Démonstration
Dénombrons le nombre d'opérations dans le pire des cas, pour une liste de taille $n$.
- boucle for : elle s'exécute $n-1$ fois.
- boucle while : dans le pire des cas, elle exécute d'abord 1 opération, puis 2, puis 3... jusqu'à $n-1$. Or 
$$1+2+3+\dots+n-1=\dfrac{n \times (n-1)}{2}$$

Si la liste est déjà triée, on ne rentre jamais dans la boucle `while` : le nombre d'opérations est dans ce cas égal à $n-1$, ce qui caractérise une complexité linéaire.

## Résumé de la complexité 
- dans le meilleur des cas (liste déjà triée) : complexité **linéaire**
- dans le pire des cas (liste triée dans l'ordre décroissant) : complexité **quadratique**

## Preuve de la terminaison de l'algorithme



Est-on sûr que notre algorithme va s'arrêter ?  
Le programme est constitué d'une boucle `while` imbriquée dans une boucle `for`. Seule la boucle `while` peut provoquer une non-terminaison de l'algorithme. Observons donc ses conditions de sortie : 

```  while  i>=0 and l[i] > cle : ```

La condition `l[i] > cle` ne peut pas être rendue fausse avec certitude. 
Par contre, la condition `i>=0` sera fausse dès que la variable `i` deviendra négative. Or la ligne 
`i = i - 1` nous assure que la variable `i` diminuera à chaque tour de boucle. La condition  `i>=0` deviendra alors forcément fausse au bout d'un certain temps.

Nous avonc donc prouvé la **terminaison** de l'algorithme.

On appelle la valeur `i` un **variant de boucle**. C'est une notion théorique (ici illustrée de manière simple par `i` qui permet de prouver la bonne sortie d'une boucle et donc la terminaison d'un algorithme.


## Preuve de la correction de l'algorithme
Les preuves de correction sont des preuves théoriques. La preuve ici s'appuie sur le concept mathématique de **récurrence**. 
Principe du raisonnement par récurrence : 
une propriété $P(n)$ est vraie si :
- $P(0)$ (par exemple) est vraie
- Pour tout entier naturel $n$, si $P(n)$ est vraie alors $P(n+1)$ est vraie.

Ici, la propriété serait : « Quand $k$ varie entre 0 et `longueur(liste) -1`, la sous-liste de longueur $k$ est triée dans l'ordre croissant.» On appelle cette propriété un **invariant de boucle** (sous-entendu : elle est vraie pour chaque boucle)

- quand $k$ vaut 0, on place le minimum de la liste en l[0], la sous-liste l[0] est donc triée.
-  si la sous-liste de $k$ éléments est triée, l'algorithme rajoute en dernière position de la liste le minimum de la sous-liste restante, dont tous les éléments sont supérieurs au maximum de la sous-liste de $k$ éléments. La sous-liste de $k+1$ éléments est donc aussi triée.




---
## Bibliographie
- Wikipedia, https://en.wikipedia.org/wiki/Sorting_algorithm



---

![](../../../ccbysa.png "image") G.Lassus, Lycée François Mauriac --  Bordeaux  



```python

```
