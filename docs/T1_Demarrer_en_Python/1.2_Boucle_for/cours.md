# 1.2 Boucle For

![image](data/meme.png){: .center width=30%}



## 1. Les énumérables

En mathématiques, on dit qu'un ensemble est *dénombrable* lorsqu'on peut associer à chaque élément de l'ensemble un nombre (traditionnellement 1, 2, 3...)

- les fraises Tagada d'un paquet sont dénombrables.
- les voitures qui roulent sur l'autoroute sont dénombrables.
- l'eau qui coule d'un robinet n'est pas dénombrable.

En informatique, il existe un concept similaire qui va désigner les objets que l'on peut **énumérer**, c'est-à-dire les décomposer en une succession ordonnée d'éléments. On les appelle les **énumérables** ou les **itérables** (Python utilise le mot anglais ```iterable```).

- la variable ```NSI``` (qui est de type ```String```) est énumérable : on peut la décomposer en  ```N```,  ```S```, ```I```.
- la variable ```[4, 3, 17]```  (qui est de type ```List```) est énumérable : on peut la décomposer en  ```4```,  ```3```, ```17```.
- la variable ```5```  (qui est de type ```Int```) n'est PAS énumérable : on ne peut pas la décomposer. 





## 2. Itérer sur les itérables : la boucle `for`

La principale caractéristique d'un ordinateur est d'exceller dans les opérations répétitives.

(Je vous laisse faire la recherche Google «Gérard Berry l'ordinateur est...»)

Il existe donc une instruction permettant de faire une (ou plusieurs) action(s) à chaque itération sur un élément énumérable.

!!! abstract "Un exemple fondateur :heart:"
    Le programme suivant :
    ```python linenums='1'
    for k in 'NSI':
        print(k)
    ```
    va donner ceci :
    ```python
    >>> %Run example.py
    N
    S
    I
    ```

Étudions, grâce à PythonTutor, le détail de cette exécution.

Cliquez sur Next et observez bien l'évolution de la variable ```k```. 
<iframe width="800" height="500" frameborder="0" src="https://pythontutor.com/iframe-embed.html#code=for%20k%20in%20'NSI'%3A%0A%20%20%20%20print%28k%29&codeDivHeight=400&codeDivWidth=350&cumulative=false&curInstr=0&heapPrimitives=nevernest&origin=opt-frontend.js&py=3&rawInputLstJSON=%5B%5D&textReferences=false"> </iframe>



## 1. Le principe
<!-- «Une cuillère pour ... maman», «Une cuillère pour ... Papa», «Une cuillère pour ... Tatie Jacqueline», etc. -->

Imaginons - nous sommes en 2074 - une maman (ou un papa) qui souhaite faire manger à son enfant les 10 dernières cuillères de soupe... en programmant son robot domestique pour qu'il annonce ces phrases à sa place.

On pourrait imaginer un code qui ressemble à ça:

```python
print("Une cuillère pour maman")
print("Une cuillère pour papa")
print("Une cuillère pour mamie Françoise")
print("Une cuillère pour papy Jacques")
print("Une cuillère pour mémé Paulette")
print("Une cuillère pour tata Jacqueline")
print("Une cuillère pour tonton Michel")
print("Une cuillère pour le cousin Maurice")
print("Une cuillère pour la cousine Gertrude")
print("Une cuillère pour Médor")
```

C'est très répétitif. Et heureusement qu'il n'y a que 10 cuillères...

D'autant que chaque instruction est quasiment identique, seul le nom du membre de la famille change.

En français, on serait tenté de résumer en 
> «annonce une cuillère pour chacun des 10 membres de la famille»

Heureusement, dans tous les langages de programmation, il existe une instruction qui permet de répeter une instruction (ou plusieurs instructions) **pour chaque élément d'un ensemble de valeurs donné**: la boucle[^1] `for`.

[^1]: en programmation, on parle de **boucle** pour toute instruction qui permet de répéter des instructions.

## 2. La syntaxe
!!! abstract "La boucle `for`"
    Pour mettre en place cette boucle, on a besoin d'identifier:

    - les instructions à répéter;
    - pour quelles valeurs *différentes* on doit les répéter: on a donc besoin d'une variable et d'un ensemble de valeurs;
    - identifier dans les instructions ce qui dépend de cette variable de boucle.

    Ici, seul le nom change, on a donc besoin d'une variable de boucle qui va prendre successivement tous les noms des membres de la famille (nommons-la de façon très originale `nom`), et on va répéter l'instruction pour chacune des valeurs `"maman", "papa", "mamie Françoise", "papy Jacques", "mémé Paulette", "tata Jacqueline", "tonton Michel", "le cousin Maurice", "la cousine Gertrude", "Médor"`.

    Cela donne en Python:
    ```python
    liste_noms = ["maman", "papa", "mamie Françoise", "papy Jacques", "mémé Paulette", "tata Jacqueline", "tonton Michel", "le cousin Maurice", "la cousine Gertrude", "Médor"]

    for nom in liste_noms:
        print("Une cuillère pour", nom)
    ```
    
    Syntaxe générale:
    ```python
    for var in ensemble:
        *instructions à répéter*
    ```
    où `var` est un nom de variable (non précédemment déclarée dans le programme), `ensemble` un ensemble de valeurs défini à l'avance.

    On dit que `var` *parcourt* l'ensemble `ensemble`.


!!! warning "Syntaxe"
    Il faut absolument un caractère `:` à la fin de la ligne du `for` !

!!! warning "Indentation"
    C'est le **décalage par rapport à la marge** - qu'on appelle **indentation** - qui détermine quelles sont les instructions à répéter !

!!! note "Exemple"
    Tester les différents codes suivants dans votre IDE ou dans la console ci-dessous:

    === "Code 1"
        ```python
        for k in ["toto", "tata", "tutu"]:
        print("Bonjour", end=" ")
        print(k)
        ```
    === "Code 2"
        ```python
        for k in ["toto", "tata", "tutu"]:
            print("Bonjour", end=" ")
            print(k)
        ```
    === "Code 3"
        ```python
        for k in ["toto", "tata", "tutu"]:
            print("Bonjour", end=" ")
        print(k)
        ```
    
    {{ IDEv() }}
    

## 3. Les ensembles de valeurs

!!! abstract "Iterables"
    Dans une boucle `for`, l'ensemble des valeurs que la variable de boucle va parcourir doit être **itérable**, c'est-à-dire un objet dont on peut énumérer les éléments un par un.

    Par exemple:

    - une liste : c'est un type construit, que nous étudierons au thème 2, qui s'écrit entre crochets, ses éléments étant séparés par une virgule (comme dans l'exemple du **2.**). On peut donc parcourir ses éléments.
    - une chaîne de caractères. On peut parcourir chacun des caractères;
    - un objet de type `range`: c'est un objet qui produit une plage de nombres entiers. On peut parcourir chacun des nombres un à un.

!!! note "Exemples à tester"
    === "avec une chaîne de caractères"
        ```python
        for l in "Angoulême":
            print(l)
        ```
        
    === "avec une liste"
        ```python
        for a in [1, 2, 3, 4]:
            b = 2 * a
            print("le double de", a, "est", b)
        ```
    
    === "sans appel à la variable de boucle"
        ```python
        for a in [1, 2, 3, 4, 5, 6]:
            print("miaou")
        ```
    === "avec un `range`"
        ```python
        for k in range(10):
            print(k, "x 5 =", k*5)
        ```
    
    {{ IDEv() }}
    
    
        
## 4. À propos du `range`

Il arrive très fréquemment que la variable soit tout simplement un entier, qui doit parcourir un ensemble de nombres entiers consécutifs.

Par exemple, imaginons que votre professur.e d'EPS, à court d'idées d'activités à cause des conditions sanitaires, décide de vous faire faire 20 tours de stade et vous demande d'annoncer à chaque passagesur la ligne de départ à quel tour vous en êtes...

Vous allez donc annoncer successivement «Tour 1!», «Tour 2!», «Tour 3!», etc. jusqu'à «Tour 20!».

Pour représenter cette situation, on peut donc imaginer un code ressemblant à:
```python
for k in [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16 ,17 ,18 ,19 ,20]:
    print("Tour",k)
```
Mais la liste est très pénible à écrire.

Heureusement, comme vous avez dû le comprendre dans le dernier exemple du **3.**, l'objet de type `range` permet de générer ce genre d'ensemble de nombres entiers consécutifs.

!!! abstract "Générer une plage de nombres entiers"
    L'objet `range(start, stop, step)`:
    
    - il renvoie une séquence de nombres entiers en partant de `start` (**inclus**) jusqu'à `stop` (**exclus**), en incrémentant de `step`;

    - `start` est facultatif et vaut 0 par défaut;

    - `step` est facultatif et vaut 1 par défaut. Mais si on veut préciser `step`, alors il faut donner aussi `start`, même si sa valeur est 0.


??? warning "Attention"
    Un objet `range` **n'est pas** de type `list`. Mais on peut le convertir en liste avec la fonction `list`.
    
    ```python
    >>> range(10)
    range(0, 10)
    >>> list(range(10))
    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
    >>> 
    ```

??? question "Question"
    === "Énoncé"
        Comment générer les nombres entiers de 1 à 20 (comme dans l'exemple des tours de terrain) avec un `range`?


        {{ terminal() }}

    === "Indication"
        Il ne faut pas commencer à 0... et le `stop` n'est pas inclus dans la séquence !
    
    === "Solution"
        Il faut utiliser `range(1, 21)` .
        

## 5. Pour conclure

!!! done "À retenir"
    - La boucle `for` s'utilise lorsqu'on connaît à l'avance le nombre de répétitions à effectuer: soit un nombre entier, soit un ensemble de valeurs contenus dans un *iterable*. On parle de boucle **bornée**.
    - Les instructions répétées peuvent - mais ce n'est pas obligatoire - faire appel à la variable de boucle, mais il ne faut pas que ces instructions la modifient.

    - Ne pas oublier les `:` et l'indentation !
    - `range(n)` génère une séquence de `n` nombres entiers: on s'en servira dès qu'on aura besoin de répéter `n` fois des instructions.


## 6. Exercices

### Série 1: «Python pur»

Téléchargez le notebook d'exercices : [T6.1_Exercices2.ipynb](./data/T6.1_Exercices2.ipynb){:target="_blank"} 


### Série 2: avec Processing

???+ example "{{ exercice() }}"
    L'objectif est d'obtenir un dégradé de gris:

    ![](./data/6_1_2_ex1.png){: .center} 

    Pour rappel, un niveau de gris est un couleur RGB dont les trois composantes (entre 0 et 255) rouge, verte et bleue sont identiques.

    On prendra une taille de 256x100 pixels.

??? example "{{ exercice() }}"
    Écrire un programme qui dessine une ligne de 20 carrés de taille 50x50, dont la couleur sera aléatoire.

    ![](./data/6_1_2_ex2.png){: .center} 

??? example "{{ exercice() }}"
    Animer le programme de l'exercice précédent.

??? example "{{ exercice() }}"
    Reprendre l'exercice2, mais cette fois avec un carré de carrés... (penser à réduire la taille de moitié).

    ![](./data/6_1_2_ex4.png){: .center} 

??? example "{{ exercice() }}"
    === "Figure à reproduire"
        ![](./data/6_1_2_ex5.png){: .center} 
    === "Indications"
        - la composante bleue est toujours 0;
        - faire varier les composantes rouge et verte;
        - pas d'animation
    