# Exercices

{{ initexo(0) }}

!!! example "{{ exercice() }}"
    === "Énoncé"
        Écrire un programme qui demande deux nombres et qui affiche le plus grand des deux.
    === "Correction"
        {{ correction(True,
        "
        
        "
        ) }}


!!! example "{{ exercice() }}"
    === "Énoncé"
        On calcule l'IMC (Indice de Masse Corporelle) par la formule $I = M / T^2$ où M est la masse (en kg) d'une personne et T sa taille (en m).
        Selon la classification de l'OMS, une personne est en état de maigreur si son IMC est inférieur à 18 et en surpoids si son IMC est supérieur à 25. 

        1. Écrire un programme qui demande la masse et la taille d'une personne, calcule son IMC et annonce si la personne est en état de maigreur.
        2. Modifier ensuite le programme pour qu'il annonce si la personne est en état de maigreur, en surpoids ou bien si son IMC est normal.
    === "Correction"
        {{ correction(True,
        "
        
        "
        ) }}

!!! example "{{ exercice() }}"
    === "Énoncé"
        Le jeu du FizzBuzz : il s'agit de compter à partir de 1 en remplaçant certains nombres par Fizz, Buzz ou Fizzbuzz :

        - si le nombre est divisible par 3, on ne le dit pas et on le remplace par Fizz.
        - si le nombre est divisible par 5, on ne le dit pas et on le remplace par Buzz.
        - si le nombre est divisible par 3 et par 5, on ne le dit pas et on le remplace par FizzBuzz.

        Écrire un code qui joue au FizzBuzz jusqu'à 50.

    === "Correction"
        {{ correction(False,
        "
        ```python linenums='1'
        for k in range(1,20):
            if k % 3 == 0 and k % 5 == 0:
                print('fizzbuzz')
            elif k % 3 == 0:
                print('fizz')
            elif k % 5 == 0:
                print('buzz')
            else:
                print(k)
        ```
        "
        ) }}


!!! example "{{ exercice() }}"
    === "Énoncé"
        Une année est déclarée bissextile (et compte donc 366 jours au lieu de 365) si :

        - elle est divisible par 4.
        - elle est divisible par 400 mais n'est pas divisible par 100.

        Écrire un code qui détermine si une année est bissextile ou non.

    === "Correction"
        {{ correction(True,
        "
        
        "
        ) }}