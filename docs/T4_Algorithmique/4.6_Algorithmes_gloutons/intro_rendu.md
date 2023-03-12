# Vers l'algorithme de rendu de monnaie

On veut coder la fonction ```rendu``` qui prend pour paramètre un entier positif ```somme_a_rendre``` et qui renvoie la liste des pièces à donner.

Les pieces disponibles (en quantité illimitée) sont stockées dans une variable ```pieces = [200, 100, 50, 20, 10, 5, 2, 1]```.



**Utilisation** : `rendu(13)` doit renvoyer `[10, 2, 1]`


```python
>>> rendu(13)
    [10, 2, 1]
>>> rendu(58)
    [50, 5, 2, 1]
```



??? note "Code à trous :star: :star: :star: :star:"
    ```python linenums='1'
    def rendu(somme_a_rendre):
        pieces = [200, 100, 50, 20, 10, 5, 2, 1]
        solution = []
        ...
        ...
        ...
        ...
        ...
        ...
        ...  
        return solution                   
    ``` 



??? note "Code à trous :star: :star: :star: :octicons-star-24: " 
    ```python linenums='1'
    def rendu(somme_a_rendre):
        pieces = [200, 100, 50, 20, 10, 5, 2, 1]
        solution = []
        i =  ...     
        while ... > ...:
            if ... <= ... : 
                ....append(...)     
                ... = ... - ... 
            else :
                ... += ...     
        return solution                                
    ``` 

??? note "Code à trous :star: :star: :octicons-star-24: :octicons-star-24:"
    ```python linenums='1'
    def rendu(somme_a_rendre):
        pieces = [200, 100, 50, 20, 10, 5, 2, 1]
        solution = []
        i =  0     
        while ... > ...:
            if pieces[i] <= ... : 
                solution.append(...)     
                somme_a_rendre = ... - ... 
            else :
                ... += ...     
        return solution                              
    ``` 



??? note "Code à trous :star: :octicons-star-24: :octicons-star-24: :octicons-star-24:"
    ```python linenums='1'
    def rendu(somme_a_rendre):
        pieces = [200, 100, 50, 20, 10, 5, 2, 1]
        solution = []
        i =  0     
        while somme_a_rendre > ...:
            if pieces[i] <= somme_a_rendre : 
                solution.append(...)     
                somme_a_rendre = ... - ... 
            else :
                i += 1     
        return solution
                           
    ``` 
        



