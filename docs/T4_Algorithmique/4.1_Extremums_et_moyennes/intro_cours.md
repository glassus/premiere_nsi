# Vers les extremums et moyennes


## 1. Algorithme de recherche de maximum

On cherche à coder une fonction `recherche_max` qui prend en paramètre une liste `tab` et qui renvoie le plus grand élément de cette liste. L'usage de la fonction `max` est interdit.

Utilisation :
```python
>>> recherche_max([4, 3, 8, 1])
  8
```

??? note "Code à trous :star: :star: :star: :star:" 
    !!! note "Recherche de maximum "
        ```python
        def recherche_max(tab):
            '''renvoie le maximum de la liste tab'''
        ```

??? note "Code à trous :star: :star: :star: :octicons-star-24: " 
    !!! note "Recherche de maximum "
        ```python
        def recherche_max(tab):
            '''renvoie le maximum de la liste tab'''
            ... = ...                
            for ... in ...:
                if ... > ...:
                    ... = ...
            return ...
        ```

??? note "Code à trous :star: :star: :octicons-star-24: :octicons-star-24:"
    !!! note "Recherche de maximum "
        ```python
        def recherche_max(tab):
            '''renvoie le maximum de la liste tab'''
            maxi = ...           
            for elt in ...:
                if ... > ...:
                    ... = ...
            return ...
        ```



??? note "Code à trous :star: :octicons-star-24: :octicons-star-24: :octicons-star-24:"
    !!! note "Recherche de maximum "
        ```python
        def recherche_max(tab):
            '''renvoie le maximum de la liste tab'''
            maxi = tab[0]           
            for elt in tab:
                if ... > ...:
                    maxi = ...
            return ...
        ```
        



## 2. Algorithme de calcul de moyenne

On cherche à coder une fonction `moyenne` qui prend en paramètre une liste `tab` et qui renvoie la moyenne des éléments de cette liste.

Utilisation :
```python
>>> moyenne([4, 3, 8, 1])
  4.0
```

??? note "Code à trous :star: :star: :star: :star:" 
    !!! note "Recherche de maximum "
        ```python
        def moyenne(tab):
            ''' renvoie la moyenne de tab'''
        ```

??? note "Code à trous :star: :star: :star: :octicons-star-24: " 
    !!! note "Recherche de maximum "
        ```python
        def moyenne(tab):
            ''' renvoie la moyenne de tab'''
            ... = ...
            for ... in ...:
                ... += ...
            return ... / ...
        ```

??? note "Code à trous :star: :star: :octicons-star-24: :octicons-star-24:"
    !!! note "Recherche de maximum "
        ```python
        def moyenne(tab):
            ''' renvoie la moyenne de tab'''
            somme = 0
            for elt in ...:
                ... += ...
            return ... / ...
        ```


??? note "Code à trous :star: :octicons-star-24: :octicons-star-24: :octicons-star-24:"
    !!! note "Recherche de maximum "
        ```python
        def moyenne(tab):
            ''' renvoie la moyenne de tab'''
            somme = 0
            for elt in tab:
                somme += ...
            return ... / ...
        ```
    


## 3. Algorithme de recherche d'occurrence

On cherche à coder une fonction `recherche_occurrence` qui prend en paramètre un élement ```elt``` et une liste `tab` et qui renvoie la liste (éventuellement vide) des indices de ```elt``` dans ```tab```.

Utilisation :
```python
>>> recherche_occurrence(3, [1, 6, 3, 8, 3, 2])
[2, 4]
>>> recherche_occurrence(7, [1, 6, 3, 8, 3, 2])
[]

```

??? note "Code à trous :star: :star: :star: :star:" 
    !!! note "Recherche d'occurrence "
        ```python
        def recherche_occurrence(elt, tab):
            ''' renvoie la liste (éventuellement vide)
            des indices de elt dans tab'''
        ```


??? note "Code à trous :star: :star: :star: :octicons-star-24: " 
    !!! note "Recherche d'occurrence "
        ```python
        def recherche_occurrence(elt, tab):
            ''' renvoie la liste (éventuellement vide)
            des indices de elt dans tab'''
            ... = ...
            for ... in range(...):
                if ... == ...:
                    ...
            return ...
        ```



??? note "Code à trous :star: :star: :octicons-star-24: :octicons-star-24:"
    !!! note "Recherche d'occurrence "
        ```python
        def recherche_occurrence(elt, tab):
            ''' renvoie la liste (éventuellement vide)
            des indices de elt dans tab'''
            liste_indices = ...
            for i in range(...):
                if ... == ...:
                    ....append(i)
            return ...
        ```


??? note "Code à trous :star: :octicons-star-24: :octicons-star-24: :octicons-star-24:"
    !!! note "Recherche d'occurrence "
        ```python
        def recherche_occurrence(elt, tab):
            ''' renvoie la liste (éventuellement vide)
            des indices de elt dans tab'''
            liste_indices = []
            for i in range(len(tab)):
                if tab[i] == ...:
                    ....append(i)
            return ...
        ```


