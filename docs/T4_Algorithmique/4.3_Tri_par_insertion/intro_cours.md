# Vers le tri par insertion




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
        



