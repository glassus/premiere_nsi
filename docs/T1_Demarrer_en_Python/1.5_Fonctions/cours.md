# 1.5 Fonctions

![image](data/meme.jpg){: .center width=40%}


La notion de fonction est essentielle en programmation.  
Elle permet de construire des codes modulaires, plus faciles à lire et à modifier.  
En Python, une fonction se crée avec le mot-clé `def`.

## 1. Fonctions sans paramètre, sans valeur renvoyée

![image](data/f1.png){: .center }

!!! note "Exemple fondateur n°1 :heart:"
    ```python linenums='1'
    def accueil():
        print("bonjour")
        print("comment allez-vous ?")
    ```


Lorsque l'interpréteur Python parcourt cette fonction, **rien** ne s'affiche : la fonction est maintenant prête à être appelée, mais n'est pas exécutée tant que l'utilisateur ne le demande pas explicitement.

Ce sera le cas pour toutes les fonctions : elles doivent être **appelées** pour s'exécuter.


```python
>>> accueil()
bonjour
comment allez-vous ?
```

Dans ce cas d'utilisation, la fonction ```accueil``` n'est qu'un raccourci, une factorisation d'un ensemble d'instructions.



## 2. Fonction avec paramètre(s), sans valeur renvoyée

![image](data/f2.png){: .center}

### 2.1 Paramètre simple

!!! note "Exemple fondateur n°2 :heart:"
    ```python linenums='1'
    def chat_penible(n):
        for k in range(n):
            print("meoww")
    ```

```python
>>> chat_penible(3)
meoww
meoww
meoww
```

!!! voc "Vocabulaire :heart:"
    - La valeur `n` est appelée **paramètre** de la fonction `chat_penible`.
    - On dit qu'on **passe** le paramètre `n` à la fonction `chat_penible`.
    - Dans l'exemple ci-dessus, on dit qu'on a appelé la fonction `chat_penible` avec **l'argument** 3.


**Remarques :**

- là encore, notre fonction ne renvoie rien : on peut encore la considérer comme un ensemble d'instructions factorisé dans un même bloc. À la différence de la fonction sans paramètre, ces instructions ne sont pas toujours les mêmes, grâce à l'utilisation du paramètre demandé à l'utilisateur.
- la fonction bien connue  `print()` est une fonction à paramètre, qui affiche dans la console le contenu du paramètre.

### 2.2 Paramètres multiples

Une fonction peut avoir de multiples paramètres :

!!! note "Exemple fondateur n°2 :heart:"
    ```python linenums='1'
    def repete(mot, k) :
        for i in range(k):
            print(mot)
    ```
    
```python
>>> repete("NSI", 3)
NSI
NSI
NSI
```

L'ordre des paramètres passés est alors important ! Le code ci-dessous est incorrect.


```python
>>> repete(3, "test")
---------------------------------------------------------------------------

TypeError                                 Traceback (most recent call last)

<ipython-input-9-a84914f8a6c6> in <module>()
----> 1 repete(3, "test")


<ipython-input-8-7dc8032e3f17> in repete(mot, k)
        1 def repete(mot, k) :
----> 2     for i in range(k):
        3         print(mot)
        4 
        5 repete("NSI", 5)


TypeError: 'str' object cannot be interpreted as an integer
```





## 3. Fonction avec paramètre(s) et avec valeur renvoyée

![image](data/f3.png){: .center}


On retrouve ici la notion classique de fonction rencontrée en mathématiques : un procédé qui prend un nombre et en renvoie un autre. En informatique, l'objet renvoyé ne sera pas forcément un nombre (cela pourra être aussi une liste, un tableau, une image...).
Le renvoi d'une valeur se fait grâce au mot-clé `return`.



!!! note "Exemple fondateur n°3 :heart:"
    La fonction mathématique $f : x \longmapsto 2x+3$ se codera par :
    ```python linenums='1'
    def f(x):
        return 2*x + 3
    ```

```python
>>> f(10)
23
```

## 4. Autour du ```return``` 

### 4.1 La force du ```return``` 

!!! danger "Différence fondamentale entre ```return``` et ```print``` :star: :star: :star:"
    Le mot-clé ```return``` de l'exemple précédent fait que l'expression ```f(10)``` est **égale** à 23.
    On peut d'ailleurs écrire en console :
    ```python
    >>> f(10) + 5
    28
    ```
    Imaginons (avant de l'oublier très vite) le code **affreux** ci-dessous :
    ```python linenums='1'
    def g(x):
        print(2*x + 3)
    ```
    On pourrait avoir *l'illusion* que la fonction ```g``` fait correctement son travail :
    ```python
    >>> g(10)
    23
    ```
    Mais ```g``` se contente **d'afficher** sa valeur calculée, et non pas de la renvoyer. En effet :
    ```python
    >>> g(10) + 5
    23
    Traceback (most recent call last):
    File "<pyshell>", line 1, in <module>
    TypeError: unsupported operand type(s) for +: 'NoneType' and 'int'
    ```
    En résumé :
    ![image](data/yoda.png){: .center width=40%}
    

### 4.2 Le ```return``` est un siège éjectable 

Le mot-clé `return` provoque une *éjection* du code : tout ce qui est situé **après** le  `return` **ne sera pas exécuté**.  
Observez la différence entre les fonctions $g$ et $h$.



```python linenums='1'
def g(x):
    print("ce texte sera bien affiché")
    return 2*x+3
```


```python
>>> g(4)
ce texte sera bien affiché
11
```



```python linenums='1'
def h(x):
    return 2*x+3
    print("ceci ne sera jamais affiché")
```


```python
>>> h(4)
11
```

### 4.3 Les fonctions sans ```return``` sont-elles des fonctions ?

- Pour les puristes, une fonction sans valeur renvoyée sera plutôt appelée *procédure*. Le mot *fonction* est alors réservé aux fonctions qui ont effectivement un `return`.

- On peut doter artificiellement à toutes les fonctions d'un ```return```, en renvoyant la valeur ```None``` :
```python linenums='1'
def chat_penible(n):
    for k in range(n):
        print("meoww")
    return None
```


## 5. Variables locales, variables globales

## 6. Documenter une fonction

## 7. Jeux de tests pour une fonction