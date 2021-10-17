
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
        Définissez une **fonction** `decale(lettre)` qui décale de 3 rangs dans l'alphabet la lettre majuscule `lettre` passée en argument (après Z, on recommencera à A..)

        Aide : 
        ```python
        >>> ord('A')
        65
        >>> chr(65)
        'A'
        ```


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



!!! example "{{ exercice() }}"
    === "Énoncé"
        Utilisez la fonction précédente pour créer la fonction `decale_phrase(p, n)` qui décale toutes les lettres d'une phrase `p` de `n` rangs.

    === "Correction"
        {{ correction(True,
        "
        ```python linenums='1'
        def decale_phrase(p, n):
            phrase_decalee = ""
            for lettre in p:
                nouvelle_lettre = decale(lettre, n)
                phrase_decalee += nouvelle_lettre
            return phrase_decalee
        ```
        "
        ) }}



!!! example "{{ exercice() }}"
    === "Énoncé"
        Décodez la phrase `RT BTHHPVT CT RDCIXTCI GXTC S XCITGTHHPCI`.

    === "Correction"
        {{ correction(True,
        "
        ```python linenums='1'
        ```
        "
        ) }}




!!! example "{{ exercice() }}"
    === "Énoncé"
        La [conjecture de Syracuse](https://fr.wikipedia.org/wiki/Conjecture_de_Syracuse) (ou de Collatz) postule ceci :  

        *Prenons un nombre $n$ : si $n$ est pair, on le divise par 2, sinon on le multiplie par 3 puis on ajoute 1. On recommence cette opération tant que possible. Au bout d'un certain temps, on finira toujours par tomber sur le nombre 1.*

        1. Écrire une fonction ```suivant(n)``` qui renvoie le successeur du nombre ```n```, suivant les règles énoncées ci-dessus.
        2. Écrire une fonction ```syracuse(n)``` qui affiche tous les termes de la suite de Syracuse jusqu'à (on l'espère !) 1.  

    === "Correction"
        {{ correction(True,
        "
        1.
        ```python linenums='1'
        def suivant(n):
            if n % 2 == 0:
                return n // 2
            else:
                return 3*n + 1
        ```
        2.
        ```python linenums='1'
        def syracuse(n):
            print(n)
            while n != 1:
                n = suivant(n)
                print(n)
        ``` 
        "
        ) }}        