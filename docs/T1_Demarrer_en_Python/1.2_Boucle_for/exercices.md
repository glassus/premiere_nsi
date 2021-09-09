# Exercices sur la boucle `for`

{{ initexo(0) }}

!!! example "{{ exercice() }}"
    === "Énoncé"
        On donne une liste d'acteurs : 
        ```python
        liste_acteurs = ['Tahar', 'Omar', 'Guillaume', 'Swann', 'Alex', 'Roschdy']
        ```

        Utilisez cette liste pour produire la sortie suivante:
        ```python
        Tahar a eu le César du meilleur acteur
        Omar a eu le César du meilleur acteur
        Guillaume a eu le César du meilleur acteur
        Swann a eu le César du meilleur acteur
        Alex a eu le César du meilleur acteur
        Roschdy a eu le César du meilleur acteur
        ```
    === "Correction"
        ```python linenums='1'
        liste_acteurs = ['Tahar', 'Omar', 'Guillaume', 'Swann', 'Alex', 'Roschdy']

        for acteur in liste_acteurs:
            print(acteur, "a eu le César du meilleur acteur")
        ```


!!! example "{{ exercice() }}"
    === "Énoncé"
        1. Fabriquer la chaîne de caractères suivante (qui comporte 80 caractères) :
        ```python
        IIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIII
        ```
        2. Fabriquer la chaîne de caractères suivante :
        ```python
        IIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIIII
        NNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNN
        FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF
        OOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOO
        ```
    === "Correction"
        

!!! example "{{ exercice() }}"
    === "Énoncé"
        Dans l'extrait de code suivant:

        - `chaine` est une variable initialisée avec un `str` vide : `""`;
        - on veut qu'en sortie de programme cette variable contienne la valeur `'aeiouy'`.

        L'idée est d'ajouter une par une les lettres à la variable `chaine`.

        Compléter le code.


        ```python linenums='1'
        chaine = ""
        for ... in ['b', 'r', 'a', 'v', 'o']:
            ...
        ```

        Cette variable `chaine` est appelée un **accumulateur**.
    === "Correction"
       

!!! example "{{ exercice() }}"
    === "Énoncé"
        En Python, la fonction `ord` renvoie le code Unicode d'un caractère et la fonction `chr` le contraire: elle renvoie le caractère correspondant à un code Unicode.

        Par exemple:
        ```python 
        >>> ord('a')
        97
        >>> chr(97)
        'a'
        ```

        Voici une liste contenant les codes Unicode des lettres d'un mot secret...
        À vous d'écrire un programme où en sortie, la variable `mot_secret` contiendra la chaîne de caractères de ce mot.   


        ```python linenums='1'
        mystere = [111, 107, 44, 32, 98, 105, 101, 110, 32, 106, 111, 117, 233]
        mot_secret = ""
        ```

    === "Correction"
      
      
!!! example "{{ exercice() }}"
    === "Énoncé"
        On souhaite calculer la somme des 1000 premiers nombres entiers naturels, c'est-à-dire:

        $1+2+3+4+5+ \dots +999+1000$

        Écrire un programme avec une variable `somme` **accumulateur** (comme à l'exercice 3) qui contiendra la valeur souhaitée en fin de programme.

    === "Correction"
      

!!! example "{{ exercice() }}"
    === "Énoncé"
        Calculer $1\times 2 \times 3 \times \dots 99 \times 100$.
    === "Correction"
      

??? Abstract "Sources et bibliographie"
    - Site de Cédric Gouygou (Angoulême).
