# Vers le tri par sélection




??? note "Code à trous :star: :star: :star: :star:" 
    ```python
    def tri_selection(lst) :
        for i in range(len(lst)-1):
            indice_min = i
            for k in range(i+1, len(lst)) :
                if lst[k] < lst[indice_min]:
                    indice_min = k
            lst[i], lst[indice_min] = lst[indice_min], lst[i]
    ```


??? note "Code à trous :star: :star: :star: :octicons-star-24: " 
    ```python
    def tri_selection(lst) :
        for i in range(len(lst)-1):
            indice_min = i
            for k in range(i+1, len(lst)) :
                if lst[k] < lst[indice_min]:
                    indice_min = k
            lst[i], lst[indice_min] = lst[indice_min], lst[i]
    ```

??? note "Code à trous :star: :star: :octicons-star-24: :octicons-star-24:"
    ```python
    def tri_selection(lst) :
        for i in range(len(lst)-1):
            indice_min = i
            for k in range(i+1, len(lst)) :
                if lst[k] < lst[indice_min]:
                    indice_min = k
            lst[i], lst[indice_min] = lst[indice_min], lst[i]
    ```



??? note "Code à trous :star: :octicons-star-24: :octicons-star-24: :octicons-star-24:"
    ```python
    def tri_selection(lst) :
        for i in range(len(lst)-1):
            indice_min = i
            for k in range(i+1, len(lst)) :
                if lst[k] < lst[indice_min]:
                    indice_min = k
            lst[i], lst[indice_min] = lst[indice_min], lst[i]
    ```
        



