
{{initexo(0)}}

!!! example "{{ exercice() }}"
    === "Énoncé"
        Définissez une fonction `maxi(n1, n2)` qui renvoie le plus grand élément entre `n1` et `n2`.

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
        Définissez une fonction `nb_voyelles(mot)` qui renvoie le nombre de voyelles de `mot`.

    === "Tester sa fonction"
        Vous pouvez utiliser la fonction de tests ci-dessous :
        ```python linenums='1'
        def test_nb_voyelles():
            assert nb_voyelles("bonjour") == 3
            assert nb_voyelles("fdjgdhk") == 0
            assert nb_voyelles("au") == 2
            print("tests ok")
        ```

    === "Correction"
        {{ correction(True,
        "
        ```python linenums='1'
        def nb_voyelles(mot):
            voyelles = 'aeiouy'
            nb = 0
            for lettre in mot:
                if lettre in voyelles:
                    nb += 1
            return nb
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
            phrase_decalee = ''
            for lettre in p:
                if lettre == ' ':
                    phrase_decalee += ' '
                else:
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
        def decale(lettre, n):
            rang_ancienne_lettre = ord(lettre) - 65
            rang_nouvelle_lettre = (rang_ancienne_lettre + n) % 26 + 65  

            return chr(rang_nouvelle_lettre)

        def decale_phrase(p, n):
            phrase_decalee = ''
            for lettre in p:
                if lettre == ' ':
                    phrase_decalee += ' '
                else:
                    nouvelle_lettre = decale(lettre, n)
                    phrase_decalee += nouvelle_lettre
            return phrase_decalee


        def decrypt(msg_secret):
            for decalage in range(25):
                    print(decale_phrase(msg_secret, decalage))

        msg = 'RT BTHHPVT CT RDCIXTCI GXTC S XCITGTHHPCI'

        decrypt(msg)

        # cette méthode impose de tout lire pour y chercher une phrase ayant du sens.
        # Si on sait que la phrase sera en français, on peut chercher des mots du
        # dictionnaire. Si par exemple on sait que la phrase contiendra le mot 'MESSAGE',
        # le code peut devenir :


        def decrypt2(msg_secret):
            for decalage in range(25):
                phrase_clair = decale_phrase(msg_secret, decalage)
                if 'MESSAGE' in phrase_clair:
                    print(phrase_clair)

        msg = 'RT BTHHPVT CT RDCIXTCI GXTC S XCITGTHHPCI'

        decrypt2(msg)


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

!!! example "{{ exercice() }}"
    === "Énoncé"
        1. Écrire une fonction ```temps_de_vol(n)``` qui renvoie le nombre d'étapes pour arriver à 1, en partant de ```n```
        2. Écrire une fonction ```temps_max(nmax)``` qui affiche le plus grand temps de vol pour un nombre entre 1 et ```nmax```.
        3. Modifier cette fonction pour afficher aussi le nombre de départ donnant ce plus grand temps de vol.

    === "Correction"
        {{ correction(True,
        "
        1.
        ```python linenums='1'
        def temps_de_vol(n):
            compteur = 1
            while n != 1:
                compteur += 1
                n = suivant(n)
            return compteur

        ```
        2.
        ```python linenums='1'
        def temps_max(nmax):
            maximum = 0
            for k in range(1, nmax + 1):
                duree = temps_de_vol(k)
                if duree > maximum:
                    maximum = duree
            print('le plus grand temps de vol vaut :', maximum)
        ``` 
        "
        ) }}        
       
