# Exercices sur la boucle `while`

{{ initexo(0) }}

!!! example "{{ exercice() }}"
    
    Pour chaque code, écrire ce qui va s'afficher en console.

    **Code A**
    ```python linenums='1'
    c = 0
    while c <= 3:
        print("ok")
        c += 1
    ```
    {{
    correction(True,
    """
    ??? success \"Correction\" 
        ```
        ok
        ok
        ok
        ok
        ```        
    """
    )
    }}
        
    **Code B**
    ```python linenums='1'
    k = 0
    while k > 3:
        print("ok")
        k += 1
    print("fini")

    ```
    {{
    correction(True,
    """
    ??? success \"Correction\" 
        ```
        fini
        ```        
    """
    )
    }}

    **Code C**
    ```python linenums='1'
    n = 0
    while n < 4:
        print("ok")
        n += 2
    ```
    {{
    correction(True,
    """
    ??? success \"Correction\" 
        ```
        ok
        ok
        ```        
    """
    )
    }}
 

!!! example "{{ exercice() }}"
    Que va afficher le code ci-dessous ?

    ```python linenums='1'
    c = 0
    mot = 'a'
    while mot != 'aaaa':
        mot += 'a'
        c += 1
    print(c)

    ```

    {{
    correction(False,
    """
    ??? success \"Correction\" 
        Il va afficher 4.
    """
    )
    }}

!!! example "{{ exercice() }}"
    
    Un capital de 10 000 € est placé au taux annuel de 4 %. 

    Écrire le code permettant d'afficher au bout de combien d'années le capital va dépasser 14 000 €.

    On rappelle qu'une augmentation de 4 % correspond à une multiplication par 1,04.

    {{
    correction(False,
    """
    ??? success \"Correction\" 
        ```python linenums='1'
        capital = 10000
        annee = 0
        while capital < 14000:
            annee += 1
            capital = capital * 1.04 #(1)
        print(annee)
        ```

        1. ou ```#!python capital *= 1.04```         
    """
    )
    }}
    