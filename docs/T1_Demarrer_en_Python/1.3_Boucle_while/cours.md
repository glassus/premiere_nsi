# 1.3 Boucle While

## 1. Premiers exemples

À la différence essentielle des boucles `for`, dont on peut savoir à l'avance combien de fois elles vont être exécutées, les boucles `while` sont des boucles dont on ne sort que lorsqu'une condition n'est plus satisfaite. 

Avec donc le risque de rester infiniment bloqué à l'intérieur !  

![image](data/danger.jpg){: .center width=40%}

!!! note "Exemple fondateur n°1 :heart:"
    Le programme suivant :
    ```python linenums='1'
    a = 0
    while a < 3:
        print("ok")
        a = a + 1
    print("fini")
    ```
    va donner ceci :
    ```python
    ok
    ok
    ok
    fini

    ```
!!! aide "Analyse grâce à PythonTutor"
    <iframe width="800" height="300" frameborder="0" src="https://pythontutor.com/iframe-embed.html#code=a%20%3D%200%0Awhile%20a%20%3C%203%3A%0A%20%20%20%20print%28%22ok%22%29%0A%20%20%20%20a%20%3D%20a%20%2B%201%0Aprint%28%22fini%22%29&codeDivHeight=400&codeDivWidth=350&cumulative=false&curInstr=0&heapPrimitives=nevernest&origin=opt-frontend.js&py=3&rawInputLstJSON=%5B%5D&textReferences=false"> </iframe>


!!! question
    le code ci-dessous va-t-il donner un résultat différent ?
    ```python linenums='1'
    a = 0
    while a < 3:
        a = a + 1
        print("ok")
    print("fini")
    ```

??? info "Résultat du programme ⏬"
    ```python
    ok
    ok
    ok
    fini
    ```



**Conclusion** : l'évaluation de la condition ne se fait pas à chaque ligne mais bien au début de chaque tour de boucle. Si la variable qui déclenchera la sortie de boucle atteint sa valeur de sortie au milieu des instructions, les lignes restantes sont quand même exécutées.


## 2. Syntaxe générale

!!! abstract "Écriture d'une boucle ```while```"
    ```python
    while condition:
        instruction1
        instruction2
            ...
        instructionN
    ```

### 2.1 La condition

La ```condition``` est un booléen, c'est-à-dire une expression que Python évaluera à ```True``` ou à ```False```.

Exemple de booléens résultant d'une évaluation :
```python
>>> 1 < 3
True
>>> 5 > 7
False
>>> a = 10
>>> a > 8
True
```

Un cours sur les booléens aura lieu [ici](../../../T2_Representation_des_donnees/2.5_Booleens/cours/).

### 2.2 Les instructions

Les instructions ```instruction1``` jusqu'à ```instructionN``` sont exécutées dans cet ordre à chaque tour de boucle. 

:warning: **Attention :** ces instructions doivent obligatoirement avoir un impact sur la ```condition``` évaluée après le ```while```(dans le cours sur la [dichotomie](../../../T4_Algorithmique/4.5_Dichotomie/cours/), nous évoquerons la notion de _variant de boucle_).

Voir le piège n°1 ...

## 3. Les pièges ...

### 3.1 piège n°1 : ne JAMAIS SORTIR de la boucle


!!! bug "Exemple fondateur n°2 :heart:"
    Le programme suivant :
    ```python linenums='1'
    a = 0
    while a < 3:
        print("ok")
        a = a + 1
        a = a * 0
    print("ce texte ne s'écrira jamais")
    ```
    va écrire une suite infinie de ```ok``` et ne **jamais s'arrêter**


### 3.2 piège n°2 : ne JAMAIS ENTRER dans la boucle

!!! bug "Exemple fondateur n°3 :heart:"
    Le programme suivant :
    ```python linenums='1'
    a = 0
    while a > 10:
        print("ce texte non plus ne s'écrira jamais")
        a = a + 1
        
    print("fini") 
    ```

    va écrire ```fini``` et s'arrêter.

{{ initexo(0) }}
!!! example "{{ exercice() }}"
    === "Énoncé"
        Trouver le plus petit nombre entier $n$ tel que $2^n$ soit supérieur à 1 milliard.
    === "Correction"
        ```python linenums='1'
        n = 1
        while 2**n < 10**9:
            n = n + 1
            print("trop petit")
        print("trouvé : ",n)
        ```




## 4. Quelques remarques
### 4.1 Lien entre ```while``` et ```for```
![image](data/scooby.png){: .center width=40%}

La boucle bornée ```for``` que nous avons étudiée est très pratique.

Mais nous pourrions nous en passer : toutes les boucles ```for``` peuvent en fait être ré-écrites en utilisant ```while```. (alors que la réciproque est fausse)

!!! example "{{ exercice() }}"
    === "Énoncé"
        On considère le code ci-dessous :
        ```python linenums='1'
        for k in range(5):
            print("scooby-doo")
        ``` 
        Ré-écrire ce code en utilisant une boucle ```while```. 
    === "Correction"
        ```python linenums='1'
        k = 0
        while k < 5:
            print("scooby-doo")
            k = k + 1
        ```





### 4.2 Les boucles infinies volontaires
![image](data/anakin.jpg){: .center width=40%}

 
La boucle infinie a été présentée comme un danger qu'il faut éviter. 

Pourtant, dans quelques situations, il est d'usage d'enfermer _volontairement_ l'utilisateur dans une boucle infinie.

C'est notamment le cas des codes Processing (ou p5) où la fonction ```draw()``` est une boucle infinie dont on ne sort que lorsqu'un évènement est intercepté (par exemple, le clic sur la fermeture de la fenêtre d'affichage).

Observez et exécutez le code suivant :

```python linenums='1'
while True :
    reponse = input("tapez sur la lettre S du clavier pour me sortir de cet enfer : ")
    if reponse == 'S' or reponse == 's':
        break

print("merci, j'étais bloqué dans une boucle infinie")
```

- le début du code : ```while True``` est typique des boucles infinies volontaires. On aurait tout aussi bien pu écrire ```while 3 > 2``` (on rencontre même parfois des ```while 1```)
- vous avez découvert l'expression ```break``` qui comme son nom l'indique permet de casser la boucle (cela marche pour ```while``` comme pour ```for```) et donc d'en sortir. Son emploi est controversé parmi les puristes de la programmation. Nous dirons juste que c'est une instruction bien pratique.

!!! example "{{ exercice() }}"
    === "Énoncé"
        Proposer un code qui choisit un nombre aléatoire entre 1 et 10, puis qui propose en boucle à l'utilisateur de le deviner, tant que celui-ci n'a pas trouvé.

        Aides :

        - ```int()``` permet de convertir une chaîne de caractères en nombre. 
        - pour avoir un nombre ```a``` pseudo-aléatoire :
        ```python
        from random import randint
        a = randint(1,10)
        ```
    === "Correction"
        {{ correction(True,
        "
        ```python linenums='1'
        from random import randint

        mystere = randint(1, 10)

        while True:
            reponse = int(input('quel est le nombre mystère ? '))
            if reponse == mystere:
                break
        print('bravo !')
        ```
        "
        ) }}
        