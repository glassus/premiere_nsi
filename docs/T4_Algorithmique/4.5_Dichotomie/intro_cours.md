# Vers la recherche dichotomique

Écrire une fonction ```recherche_dichotomique``` qui prend pour argument une liste ```lst``` **triée** et qui recherche une valeur ```val``` dans cette liste.

Si la valeur est trouvée, l'indice de la valeur est renvoyé. Sinon, on renvoie ```None```.


**Exemple d'utilisation**

```python
>>> mylist = [2, 3, 6, 7, 11, 14, 18, 19, 24]
>>> recherche_dichotomique(mylist, 14)
5
>>> recherche_dichotomique(mylist, 2)
0
>>> recherche_dichotomique(mylist, 24)
8
>>> recherche_dichotomique(mylist, 1789)
>>> 
```

??? note "Code à trous :star: :star: :star: :star:"
    ```python linenums='1'
    def recherche_dichotomique(lst, val) :
                           
    ``` 



??? note "Code à trous :star: :star: :star: :octicons-star-24: " 
    ```python linenums='1'
    def recherche_dichotomique(lst, val) :
        indice_debut = ...
        indice_fin = ...
        while ... <= ... :
            ... = (... + ...) // ...    
            ... = lst[...]            
            if ... == ... :          
                return ...
            if valeur_centrale < ... :             
                ... = ... + ...
            else :
                ... = ... - ...
        return None                               
    ``` 

??? note "Code à trous :star: :star: :octicons-star-24: :octicons-star-24:"
    ```python linenums='1'
    def recherche_dichotomique(lst, val) :
        indice_debut = ...
        indice_fin = ...
        while ... <= ... :
            indice_centre = (... + ...) // 2     
            ... = lst[...]            
            if valeur_centrale == ... :          
                return ...
            if valeur_centrale < ... :             
                ... = ... + 1
            else :
                ... = ... - 1
        return None                              
    ``` 



??? note "Code à trous :star: :octicons-star-24: :octicons-star-24: :octicons-star-24:"
    ```python linenums='1'
    def recherche_dichotomique(lst, val) :
        indice_debut = ...
        indice_fin = ...
        while indice_debut <= ... :
            indice_centre = (... + ...) // 2     
            valeur_centrale = lst[...]            
            if valeur_centrale == ... :          
                return indice_centre
            if valeur_centrale < ... :             
                indice_debut = ... + 1
            else :
                indice_fin = ... - 1
        return None
                        
    ``` 
        



