# Vers la recherche dichotomique




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
            ... = (... + ...) // 2     
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
        



