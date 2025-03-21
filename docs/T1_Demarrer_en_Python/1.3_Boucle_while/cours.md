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

Prenons une variable ```a``` égale à 10.
```python
>>> a = 10
>>> a
10
```

Voici différents tests sur cette variable ```a```. Chacun de ces tests va donner un booléen, qui sera égal à ```True``` ou à ```False```. 

La syntaxe de ces tests est à connaître par cœur.

```python
>>> a > 8
True
>>> a > 12
False
>>> a == 10
True
>>> a != 7
True
>>> a != 10
False
>>> a >= 10
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
    Trouver le plus petit nombre entier $n$ tel que $2^n$ soit supérieur à 1 milliard.

    {{
    correction(True,
    """
    ??? success \"Correction\" 
        ```python linenums='1'
        n = 1
        while 2**n < 10**9:
            n = n + 1
        print('trouvé : ',n)
        ```        
    """
    )
    }}

        

        




## 4. Quelques remarques
### 4.1 Lien entre ```while``` et ```for```
![image](data/scooby.png){: .center width=40%}

La boucle bornée ```for``` que nous avons étudiée est très pratique.

Mais nous pourrions nous en passer : toutes les boucles ```for``` peuvent en fait être ré-écrites en utilisant ```while```. (alors que la réciproque est fausse)

!!! example "{{ exercice() }}"

    On considère le code ci-dessous :
    ```python linenums='1'
    for k in range(5):
        print("scooby-doo")
    ``` 
    Ré-écrire ce code en utilisant une boucle ```while```. 

    {{
    correction(True,
    """
    ??? success \"Correction\" 
        ```python linenums='1'
        k = 0
        while k < 5:
            print('scooby-doo')
            k = k + 1
        ```        
    """
    )
    }}
        

        





### 4.2 Les boucles infinies volontaires
![image](data/anakin.jpg){: .center width=40%}

 
La boucle infinie a été présentée comme un danger qu'il faut éviter. 

Pourtant, dans quelques situations, il est d'usage d'enfermer _volontairement_ l'utilisateur dans une boucle infinie.

Observez et exécutez le code suivant :

```python linenums='1'
while True:
    reponse = input("tapez sur la lettre S du clavier pour me sortir de cet enfer : ")
    if reponse == 's':
        break

print("merci, j'étais bloqué dans une boucle infinie")
```

- le début du code : ```while True``` est typique des boucles infinies volontaires. On aurait tout aussi bien pu écrire ```while 3 > 2``` (on rencontre même parfois des ```while 1```)
- vous avez découvert l'expression ```break``` qui comme son nom l'indique permet de casser la boucle (cela marche pour ```while``` comme pour ```for```) et donc d'en sortir. Son emploi est controversé parmi les puristes de la programmation. Nous dirons juste que c'est une instruction bien pratique.


!!! example "{{ exercice() }}"
    Reprendre l'exemple précédent en faisant deviner un mot de passe (préalablement stocké dans une variable).

    {{
    correction(True,
    """
    ??? success \"Correction\" 
        ```python linenums='1'
        mdp = 'supermotdepasse'

        while True:
            rep = input('mot de passe ?')
            if rep == mdp:
                break
        print('accès autorisé')
        ```

        mieux :

        ```python linenums='1'
        import hashlib
        hsh = '696cebb8f23e45f3c3d8e6582bc1a8182abc0119ed3dd89b7de069a9ea8957ab'

        while True:
            rep = input(\"mot de passe \")
            if hashlib.sha256(rep.encode(\"utf-8\")).hexdigest() == hsh:
                break
        print(\"accès autorisé\")
        ```
    """
    )
    }}

{#

code avec haslib :

import hashlib
hsh = '696cebb8f23e45f3c3d8e6582bc1a8182abc0119ed3dd89b7de069a9ea8957ab'

while True:
    rep = input("mot de passe ")
    if hashlib.sha256(rep.encode("utf-8")).hexdigest() == hsh:
        break
print("accès autorisé")

mdp : supermdp


!!! example "{{ exercice() }}"

    Proposer un code qui choisit un nombre aléatoire entre 1 et 100, puis qui propose en boucle à l'utilisateur de le deviner, tant que celui-ci n'a pas trouvé. 

    On donnera à l'utilisateur des instructions "trop grand !" ou "trop petit !" pour le guider.

    Aides :

    - ```int()``` permet de convertir une chaîne de caractères en nombre. 
    - pour avoir un nombre ```a``` pseudo-aléatoire entre 1 et 10 :
    ```python
    from random import randint
    a = randint(1,10)
    ```

    {{
    correction(False,
    """
    ??? success \"Correction\" 
        ```python linenums='1'
        from random import randint

        mystere = randint(1, 100)

        while True:
            reponse = int(input('quel est le nombre mystère ? '))
            if reponse > mystere:
                print('trop grand !')
            elif reponse < mystere:
                print('trop petit !')
            else:
                print('bravo !')
                break
        ```        
    """
    )
    }}

    
        
!!! example "{{ exercice() }}"

    En vous basant sur l'exercice précédent, code un programme d'entraînement aux tables de multiplication de 1 à 10.

    {{
    correction(False,
    """
    ??? success \"Correction\" 
        ```python linenums='1'
        from random import randint

        while True:
            a = randint(1, 10)
            b = randint(1, 10)
            reponse = 0
            while reponse != a*b:
                question = str(a) + '*' + str(b) + ' = '
                reponse = int(input(question))
        ```        
    """
    )
    }}
    
#}