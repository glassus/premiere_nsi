
{{initexo(0)}}

!!! example "{{ exercice() }}"

    ![image](data/sanglier.jpg){: .center width=60%}
    Résolvez le **Pydéfi** proposé à [cette adresse](https://pydefis.callicode.fr/defis/Herculito04Sanglier/txt){. target="_blank"}.

    Vous pouvez vous créer un compte pour valider vos résultats, ce site (géré par l'Académie de Poitiers) est **remarquable**. 
    
    {{
    correction(True,
    """
    ??? success \"Correction\" 
        ```python linenums='1'
        lst = [0, 50, 40, 100, 70, 90, 0]

        total = 0
        for i in range(len(lst)-1):
            if lst[i] > lst[i+1]:
                nb_pierres = (lst[i]-lst[i+1])//10 + 1
                total += nb_pierres

        print(total)
        ```

        (à faire avec les valeurs de test)         
    """
    )
    }}




!!! example "{{ exercice() }}"


    On donne la liste ```jours``` suivante :
    ```python
    jours = ["lundi", "mardi", "mercredi", "jeudi", "vendredi", "samedi", "dimanche"]
    ```  

    On rappelle que la fonction ```len``` permet d'obtenir le nombre de caractères d'une chaine de caractères :

    ```python
    >>> len("test")
    4
    ```

    **Q1.** Créer **en compréhension** une liste ```lst1``` contenant uniquement les jours comportant 5 lettres.
    {{
    correction(True,
    """
    ??? success \"Correction\" 
        ```python
        lst1 = [day for day in jours if len(day) == 5]
        ```            
    """
    )
    }}

    **Q2.** Créer **en compréhension** une liste ```lst2``` contenant uniquement les jours comportant la lettre ```a``` dans leur nom.
    {{
    correction(True,
    """
    ??? success \"Correction\" 
        ```python
        lst2 = [day for day in jours if 'a' in day]
        ```        
    """
    )
    }}

    **Q3a.** Créer une fonction ```compte_e``` qui prend en paramètre une chaine de caractères et qui renvoie le nombre de ```e``` que contient cette chaine de caractères.
    {{
    correction(True,
    """
    ??? success \"Correction\" 
        ```python linenums='1'
        def compte_e(mot):
            compteur = 0
            for lettre in mot:
                if lettre == 'e':
                    compteur += 1
            return compteur
        ```    
    """
    )
    }}

    **Q3b.**  Créer **en compréhension** une liste ```lst3``` contenant uniquement les jours comportant deux fois la lettre ```e``` dans leur nom.

    {{
    correction(True,
    """
    ??? success \"Correction\" 
        ```python
        lst3 = [day for day in jours if compte_e(day) == 2]
        ```    
    """
    )
    }}










!!! example "{{ exercice() }}"

    On donne le tableau ```m``` suivant :
    ```python linenums='1'
    m = [[17, 71, 75, 89, 45, 10, 54, 26, 59, 47, 57, 64, 44], \
        [67, 25, 47, 49, 28, 40, 10, 17, 77, 35, 87, 15, 68], \
        [66, 89, 28, 43, 16, 14, 12, 21, 68, 22, 14, 18, 59], \
        [60, 35, 30, 23, 22, 37, 49, 89, 82, 80, 85, 28, 17], \
        [61, 42, 39, 46, 29, 38, 85, 72, 44, 60, 47, 35, 52], \
        [44, 28, 24, 40, 71, 71, 46, 25, 78, 54, 66, 84, 52], \
        [29, 71, 7, 38, 71, 60, 71, 60, 16, 82, 35, 39, 23], \
        [18, 61, 38, 7, 8, 32, 67, 43, 23, 28, 29, 16, 30], \
        [45, 30, 74, 9, 84, 78, 11, 80, 42, 64, 9, 39, 26], \
        [78, 57, 54, 66, 57, 63, 10, 42, 61, 19, 26, 25, 53], \
        [38, 87, 10, 64, 75, 26, 14, 68, 19, 33, 75, 50, 18], \
        [52, 81, 24, 67, 37, 78, 17, 19, 61, 82, 57, 24, 54]]

    ```
    Afficher successivement chaque ligne du tableau en respectant les règles suivantes :

    - si le nombre est divisible par 7, afficher ```*```, sinon afficher une espace ``` ```
    - sur une même ligne, on affichera tous les symboles côte à côte, en rajoutant le paramètre ```end = ''``` à la fonction ```print```. (*exemple :* ```print('*', end = '')``` )
    - on ira à la ligne à la fin de chaque ligne, par l'instruction ```print()```   


    {{
    correction(True,
    """
    ??? success \"Correction\" 
        ```python linenums='1'
        m = [[17, 71, 75, 89, 45, 10, 54, 26, 59, 47, 57, 64, 44], \\
            [67, 25, 47, 49, 28, 40, 10, 17, 77, 35, 87, 15, 68], \\
            [66, 89, 28, 43, 16, 14, 12, 21, 68, 22, 14, 18, 59], \\
            [60, 35, 30, 23, 22, 37, 49, 89, 82, 80, 85, 28, 17], \\
            [61, 42, 39, 46, 29, 38, 85, 72, 44, 60, 47, 35, 52], \\
            [44, 28, 24, 40, 71, 71, 46, 25, 78, 54, 66, 84, 52], \\
            [29, 71, 7, 38, 71, 60, 71, 60, 16, 82, 35, 39, 23], \\
            [18, 61, 38, 7, 8, 32, 67, 43, 23, 28, 29, 16, 30], \\
            [45, 30, 74, 9, 84, 78, 11, 80, 42, 64, 9, 39, 26], \\
            [78, 57, 54, 66, 57, 63, 10, 42, 61, 19, 26, 25, 53], \\
            [38, 87, 10, 64, 75, 26, 14, 68, 19, 33, 75, 50, 18], \\
            [52, 81, 24, 67, 37, 78, 17, 19, 61, 82, 57, 24, 54]]

        for ligne in m:
            for elt in ligne:
                if elt % 7 == 0:
                    print('*', end = '')
                else:
                    print(' ', end = '')
            print('')
        ```        
    """
    )
    }}


!!! example "{{ exercice() }}"

    Pydéfi **Insaisissable matrice** (version originale à [cette adresse](https://pydefis.callicode.fr/defis/AlgoMat/txt){. target="_blank"})

    On considère la matrice suivante :

    ```python
    -------------------------------
    | 17 | 3  | 4  | 14 | 5  | 17 |
    -------------------------------
    | 8  | 16 | 3  | 17 | 14 | 12 |
    -------------------------------
    | 13 | 5  | 15 | 4  | 16 | 3  |
    -------------------------------
    | 14 | 7  | 3  | 16 | 3  | 2  |
    -------------------------------
    | 6  | 1  | 16 | 10 | 5  | 13 |
    -------------------------------
    | 11 | 1  | 9  | 11 | 18 | 8  |
    -------------------------------
    ``` 
    
    ```python
    M = [[17, 3, 4, 14, 5, 17], [8, 16, 3, 17, 14, 12], [13, 5, 15, 4, 16, 3], [14, 7, 3, 16, 3, 2], [6, 1, 16, 10, 5, 13], [11, 1, 9, 11, 18, 8]]
    ```

    Cette matrice va évoluer au cours du temps, et le contenu `k` d'une case est transformé, à chaque étape en `(9*k + 3) % 19`.

    Rappelons que  `a % b` donne le reste de la division entière de `a` par `b`.

    À chaque étape de calcul, tous les nombres de la matrice sont simultanément modifiés. L'entrée du problème est le nombre d'étapes à appliquer (ici : **39**). Vous devez répondre en donnant la somme des valeurs contenues dans la matrice après application de toutes les étapes.

    {{
    correction(True,
    """
    ??? success \"Correction\" 
        ```python linenums='1'
        M = [[17, 3, 4, 14, 5, 17], [8, 16, 3, 17, 14, 12], [13, 5, 15, 4, 16, 3], [14, 7, 3, 16, 3, 2], [6, 1, 16, 10, 5, 13], [11, 1, 9, 11, 18, 8]]

        def f(k):
            return (9*k + 3) % 19

        def tour():
            for i in range(6):
                for j in range(6):
                    M[i][j] = f(M[i][j])

        for _ in range(39):
            tour()

        somme = 0
        for i in range(6):
            for j in range(6):
                somme += M[i][j]

        print(somme)

        ```        
    """
    )
    }}



!!! example "{{ exercice() }}"

    **D'après Advent Of Code 2021, day02**

    ![image](data/aoc.png){: .center}
    

    Un sous-marin peut se déplacer horizontalement (toujours vers la droite) grâce à l'instruction ```forward``` suivie d'un nombre.

    Il peut aussi monter ou descendre, grâce aux instructions ```up``` ou ```down```, elles aussi suivies d'un nombre.

    Un grand nombre d'instructions successives sont données. Le but de l'exercice est de trouver le produit final de l'abscisse du sous-marin et de sa profondeur.

    Exemple :

    ```
    forward 5
    down 5
    forward 8
    up 3
    down 8
    forward 2
    ``` 

    Après ces déplacements, le sous-marin se trouve à l'abscisse 15 et à la profondeur 10. La réponse à l'énigme serait donc 150.

    - [énoncé orginal](https://adventofcode.com/2021/day/2){. target="_blank"}

    
    - Téléchargez le fichier [input.txt](data/input.txt). Votre fichier ```.py``` de travail doit se situer dans le même répertoire que le fichier ```input.txt```.

    :arrow_right: **Parsing des données**

    *Parser* des données consiste à les récupérer et les rendre exploitables. C'est quelque chose de souvent pénible (dans les énigmes de code ET dans la vraie vie). Pourtant de la qualité du parsing (et surtout de la structure de stockage choisie) va dépendre la difficulté (ou non) de l'exploitation des données.

    Proposition de parsing :

    ```python linenums='1'
    data_raw = open('input.txt').read().splitlines()
    lst_raw = [d.split(' ') for d in data_raw]
    lst = [[l[0], int(l[1])] for l in lst_raw]

    ```

    Exécutez ce code et observez ce que contient la liste ```lst```.

    :arrow_right: **Résolution de l'énigme**
    
    À la fin de toutes ses manœuvres, quel est le produit de l'abscisse du sous-marin et de sa profondeur ?
    

    {{
    correction(False,
    """
    ??? success \"Correction\" 
        ```python linenums='1'
        data_raw = open('input.txt').read().splitlines()
        lst_raw = [d.split(' ') for d in data_raw]
        lst = [[l[0], int(l[1])] for l in lst_raw]

        x = 0
        y = 0

        for couple in lst:
            direction = couple[0]
            valeur = couple[1]
            if direction == 'forward':
                x += valeur
            if direction == 'down':
                y += valeur
            if direction == 'up':
                y -= valeur

        print(x*y)
        ```

        La réponse est donc 1746616.        
    """
    )
    }}
