# Vers le tri par insertion

!!! tip "Principe de l'algorithme"
    Pour toutes les valeurs, en commençant par la deuxième :

    - Tant qu'on trouve à gauche une valeur supérieure et qu'on n'est pas revenu à la première valeur, on échange ces deux valeurs.


Pour tester son code :
```python
>>> maliste = [7, 5, 2, 8, 1, 4]
>>> tri_insertion(maliste)
>>> maliste
[1, 2, 4, 5, 7, 8]
```

??? note "Code à trous :star: :star: :star: :star:"
    ```python linenums='1'
    def tri_insertion(lst):
        '''trie en place la liste lst donnée en paramètre'''
                           
    ``` 


??? note "Code à trous :star: :star: :star: :octicons-star-24: " 
    ```python linenums='1'
    def tri_insertion(lst):
        '''trie en place la liste lst donnée en paramètre'''
        for i in range(..., ...):                 
            ... = ...                                    
            while ... > ... and ... > ... :      
                ..., ... = ..., ...      
                ... = ...                              
    ``` 

??? note "Code à trous :star: :star: :octicons-star-24: :octicons-star-24:"
    ```python linenums='1'
    def tri_insertion(lst):
        '''trie en place la liste lst donnée en paramètre'''
        for i in range(..., len(lst)):                 
            k = ...                                    
            while k > ... and lst[...] > lst[...] :      
                lst[...], lst[...] = lst[...], lst[...]      
                k = ...                               
    ``` 



??? note "Code à trous :star: :octicons-star-24: :octicons-star-24: :octicons-star-24:"
    ```python linenums='1'
    def tri_insertion(lst):
        '''trie en place la liste lst donnée en paramètre'''
        for i in range(1, len(lst)):                 
            k = ...                                    
            while k > ... and lst[k-1] > lst[k] :      
                lst[k], lst[k-1] = lst[...], lst[...]      
                k = ...                               
    ``` 
        



