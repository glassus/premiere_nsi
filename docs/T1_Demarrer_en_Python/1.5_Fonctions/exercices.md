
{{initexo(0)}}

!!! example "{{ exercice() }}"
    === "Énoncé"
        Définissez une fonction `maxi(n1,n2)` qui renvoie le plus grand élément entre `n1` et `n2`.

    === "Tester sa fonction"
        Vous pouvez utiliser la fonction de tests ci-dessous :
        ```python linenums='1'
        def test_maxi():
            assert maxi(3,4) == 4
            assert maxi(5,2) == 5
            assert maxi(7,7) == 7
            print("tests ok")
        ```

    === "Correction"
        {{ correction(True,
        "
        ```python linenums='1'
        def maxi(n1, n2):
            if n1 < n2 :
                return n2
            else :
                return n1
        ```
        "
        ) }}


!!! example "{{ exercice() }}"
    === "Énoncé"
        Définissez une **fonction** `decale(lettre)` qui décale de 3 rangs dans l'alphabet la lettre `lettre` passée en argument (après Z, on recommencera à A..)


    === "Tester sa fonction"
        Vous pouvez utiliser la fonction de tests ci-dessous :
        ```python linenums='1'
        def test_decale():
            assert decale('A') == 'D'
            assert decale('Z') == 'C'
            print('tests ok !')
        ```


    === "Correction"
        {{ correction(True,
        "
        ```python linenums='1'
        def decale(lettre):
            rang_ancienne_lettre = ord(lettre) - 65
            rang_nouvelle_lettre = (rang_ancienne_lettre + 3) % 26 + 65  
            
            return chr(rang_nouvelle_lettre)
        ```
        "
        ) }}


!!! example "{{ exercice() }}"
    === "Énoncé"
        Rajoutez un paramètre `n` à la fonction précédente pour pouvoir décaler la lettre de `n` rangs.

    === "Tester sa fonction"
        Vous pouvez utiliser la fonction de tests ci-dessous :
        ```python linenums='1'
        def test_decale():
            assert decale('A', 3) == 'D'
            assert decale('A', 5) == 'F'
            assert decale('Z', 1) == 'A'
            print('tests ok !')
        ```


    === "Correction"
        {{ correction(True,
        "
        ```python linenums='1'
        def decale(lettre, n):
            rang_ancienne_lettre = ord(lettre) - 65
            rang_nouvelle_lettre = (rang_ancienne_lettre + n) % 26 + 65  
            
            return chr(rang_nouvelle_lettre)

        ```
        "
        ) }}



### Exercice 3


### Exercice 4
Utilisez la fonction précédente pour créer la fonction `decale_phrase(p, n)` qui décale toutes les lettres d'une phrase `p` de `n` rangs.

## Exercice 5
Décodez la phrase `PRZRFFNTRARPBAGVRAGEVRAQVAGRERFFNAG`
