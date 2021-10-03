# 1.4 Instruction conditionnelle if

![image](data/meme.jpg){: .center width=50%}



L'instruction conditionnelle `if` permet de soumettre l'exécution d'instructions à une condition donnée.
Cette condition sera une expression booléenne, comme pour la boucle `while`.

## 1. Premiers exemples

Testez les codes suivants (plusieurs fois en variant les valeurs) dans un IDE:

!!! note "`if`"
    ```python  linenums="1"
    n = int(input("Donne moi un nombre: "))
    if n == 42:
        print("C'est le sens de la vie")
    ```
    
!!! note "`if else`"
    ```python linenums="1"
    age = int(input("Quel âge avez-vous?"))
    if age < 12:
        print("pas besoin de pass sanitaire")
    else:
        print("merci de présenter votre pass sanitaire")
    ```

!!! note "imbriquer les `if`"
    ```python linenums="1"
    for i in range(13):
        if i == 0:
            print("rien")
        else:
            if i < 3:
                print("pas beaucoup")
            else:
                if i < 8:
                    print("moyen")
                else:
                    print("beaucoup")
    ```
    
## 2. La syntaxe

!!! abstract "L'instruction `if`"

    **Syntaxe générale:**
    ```python linenums="1"
    if expression:
        *instructions à effectuer si expression est vraie*
    else:
        *instructions à effectuer sinon, c'est-à-dire si expression est fausse*
    ```
    
    **Remarques:**

    - `expression` doit renvoyer une valeur **booléenne** : une égalité, comparaison, appartenance, etc. ;
    - il faut terminer la ligne commençant par `if` et `else` par `:` ;
    - les instructions à effectuer selon l'évaluation d'`expression` doivent être indentées;
    - le `else` est facultatif (comme au premier exemple);
    - en cas d'emploi du `else`, aucune expression n'est attendue.

## 3. `elif` et les cas multiples

Dans les situations où l'on veut effectuer des instrucitons différentes selon les différentes valeurs prises par une variable, comme dans le troisième exemple, on peut imbriquer les instructions `if` ... `else`.

Mais cela est vite long et peu lisible, et les différents niveaux d'indentation sont parfois piégeux.

Il existe alors une instruction qui contracte `else` et `if` : `elif` (sinon si).

Le code du troisième exemple devient alors:

```python linenums="1"
for i in range(13):
    if i == 0:
        print("rien")
    elif i < 3:
        print("pas beaucoup")
    elif i < 8:
        print("moyen")
    else:
        print("beaucoup")
```


## 4. Exercices

{{ initexo(0) }}

!!! example "{{ exercice() }}"
    === "Énoncé" 
        Écrire un programme qui demande deux nombres et qui affiche le plus grand des deux.
    === "Solution" 


!!! example "{{ exercice() }}"
    === "Énoncé" 
        On calcule l'IMC (Indice de Masse Corporelle) par la formule $I = M / T^2$ où M est la masse (en kg) d'une personne et T sa taille (en m).
        Selon la classification de l'OMS, une personne est en état de maigreur si son IMC est inférieur à 18 et en surpoids si son IMC est supérieur à 25. 

        1. Écrire un programme qui demande la masse et la taille d'une personne, calcule son IMC et annonce si la personne est en état de maigreur.
        2. Modifier ensuite le programme pour qu'il annonce si la personne est en état de maigreur, en surpoids ou bien si son IMC est normal.
    === "Solution" 

!!! example "{{ exercice() }}"
    === "Énoncé" 
        Mölkky
    === "Solution" 

!!! example "{{ exercice() }}"
    === "Énoncé" 
        Années bissextiles
    === "Solution" 

!!! example "{{ exercice() }}"
    === "Énoncé" 
        Fizzbuzz
    === "Solution" 