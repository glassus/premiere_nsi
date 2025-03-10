{{initexo(0)}}

# Micro:bit

## 0. Présentation de la carte BBC micro:bit

**BBC micro:bit** est une carte à [microcontrôleur](https://fr.wikipedia.org/wiki/Microcontr%C3%B4leur){. target="_blank"} conçue en 2015 au Royaume-Uni pour développer l'apprentissage de l'algorithmique et de la programmation.

![](data/microbit1.png){: .center}


La carte micro:bit dispose des [spécificités techniques](https://microbit.org/fr/guide/features/){. target="_blank"}  suivantes :

- 25 LEDs programmables individuellement
- 2 boutons programmables
- Broches de connexion
- Capteurs de lumière et de température
- Capteurs de mouvements (accéléromètre et boussole)
- Communication sans fil, via Radio et Bluetooth
- Interface USB

## 1. "Hello world !", virtuellement ou IRL...

### 1.1 À distance ? Pas de micro:bit ? le simulateur est là !

Rendez-vous sur la page [https://python.microbit.org/v/3](https://python.microbit.org/v/3){. target="_blank"}

Effacez le code existant et collez-le code ci-dessous :


```python
from microbit import *

while True:
    display.scroll('Hello, World!')
    display.show(Image.HEART)
    sleep(2000)
```


Cliquez sur le bouton Play de la micro:bit virtuelle. C'est parti !
![](data/create.png)

Pour éviter des erreurs, fermez la fenêtre de droite (le simulateur) à chaque fois que vous modifiez votre code de la partie gauche.

### 1.2 Avec une micro:bit réelle

La manipulation suivante ne marche que sur le navigateur Google Chrome.

1. Branchez la carte sur un port USB. Un lecteur MICROBIT apparait dans les périphériques USB.
2. Rendez-vous sur l'adresse [https://python.microbit.org/v/3](https://python.microbit.org/v/3){. target="_blank"}
3. Modifiez le code présent puis cliquez sur le bouton Play de la micro:bit virtuelle.
4. Cliquer sur le bouton violet «Send to micro:bit». 


Cette procédure est à répéter à chaque nouveau code.

## 2. Découverte des fonctionnalités

###  2.1 Commandes de base de l'afficheur, matrice de 5x5 LEDs
[voir vidéo explicative (en anglais)](https://youtu.be/qqBmvHD5bCw){. target="_blank"}

LED signifie Light Emitting Diode, Diode électroluminescente. La carte micro:bit en dispose de 25, toutes programmables individuellement, ce qui permet d'afficher du texte, des nombres et des images.

#### 2.1.1 Afficher un texte "défilant" `display.scroll(string, delay=400)`



```python
from microbit import *
display.scroll("NSI")
```


La première ligne de ce programme importe la bibliothèque de fonctions micro:bit. La deuxième ligne fait défiler un message à l’écran. Cela n'arrive qu'une seule fois.


La vitesse de défilement peut être ralentie ou accélérée à l'aide du paramètre `delay`. L'unité est la milliseconde.


```python
from microbit import *
display.scroll("mauriac", delay=20)
```

#### 2.1.2 Afficher une "image" `display.show(image)`
Exécuter le programme suivant:


```python
from microbit import *
display.show(Image.SAD)
```

??? note "Liste des images disponibles"
    ```
    Image.HEART
    Image.HEART_SMALL
    Image.HAPPY
    Image.SMILE
    Image.SAD
    Image.CONFUSED
    Image.ANGRY
    Image.ASLEEP
    Image.SURPRISED
    Image.SILLY
    Image.FABULOUS
    Image.MEH
    Image.YES
    Image.NO
    Image.CLOCK12
    Image.CLOCK11
    Image.CLOCK10
    Image.CLOCK9
    Image.CLOCK8
    Image.CLOCK7
    Image.CLOCK6
    Image.CLOCK5
    Image.CLOCK4
    Image.CLOCK3
    Image.CLOCK2
    Image.CLOCK1
    Image.ARROW_N
    Image.ARROW_NE
    Image.ARROW_E
    Image.ARROW_SE
    Image.ARROW_S
    Image.ARROW_SW
    Image.ARROW_W
    Image.ARROW_NW
    Image.TRIANGLE
    Image.TRIANGLE_LEFT
    Image.CHESSBOARD
    Image.DIAMOND
    Image.DIAMOND_SMALL
    Image.SQUARE
    Image.SQUARE_SMALL
    Image.RABBIT
    Image.COW
    Image.MUSIC_CROTCHET
    Image.MUSIC_QUAVER
    Image.MUSIC_QUAVERS
    Image.PITCHFORK
    Image.XMAS
    Image.PACMAN
    Image.TARGET
    Image.TSHIRT
    Image.ROLLERSKATE
    Image.DUCK
    Image.HOUSE
    Image.TORTOISE
    Image.BUTTERFLY
    Image.STICKFIGURE
    Image.GHOST
    Image.SWORD
    Image.GIRAFFE
    Image.SKULL
    Image.UMBRELLA
    Image.SNAKE
    ``` 

!!! example "{{ exercice() }}"
    Créer un code qui permet d'afficher la totalité des images, pendant une demi-seconde chacune (grâce à l'instruction ```sleep(500)``` ).
    On utilisera la liste
    ```python
    lst = [Image.HEART, Image.HEART_SMALL, Image.HAPPY, Image.SMILE,
        Image.SAD, Image.CONFUSED, Image.ANGRY, Image.ASLEEP, Image.SURPRISED, Image.SILLY,
        Image.FABULOUS, Image.MEH, Image.YES, Image.NO, Image.CLOCK12,
        Image.CLOCK11, Image.CLOCK10, Image.CLOCK9, Image.CLOCK8, Image.CLOCK7,
        Image.CLOCK6, Image.CLOCK5, Image.CLOCK4, Image.CLOCK3, Image.CLOCK2,
        Image.CLOCK1, Image.ARROW_N, Image.ARROW_NE, Image.ARROW_E, Image.ARROW_SE,
        Image.ARROW_S, Image.ARROW_SW, Image.ARROW_W, Image.ARROW_NW, Image.TRIANGLE,
        Image.TRIANGLE_LEFT, Image.CHESSBOARD, Image.DIAMOND, Image.DIAMOND_SMALL, Image.SQUARE,
        Image.SQUARE_SMALL, Image.RABBIT, Image.COW, Image.MUSIC_CROTCHET, Image.MUSIC_QUAVER,
        Image.MUSIC_QUAVERS, Image.PITCHFORK, Image.XMAS, Image.PACMAN, Image.TARGET, Image.TSHIRT,
        Image.ROLLERSKATE, Image.DUCK, Image.HOUSE, Image.TORTOISE, Image.BUTTERFLY, Image.STICKFIGURE,
        Image.GHOST, Image.SWORD, Image.GIRAFFE, Image.SKULL, Image.UMBRELLA, Image.SNAKE]
    ```

    {{
    correction(False,
    """
    ??? success \"Correction\" 
        ```python linenums='1'
        from microbit import *

        lst = [Image.HEART, Image.HEART_SMALL, Image.HAPPY, Image.SMILE,
            Image.SAD, Image.CONFUSED, Image.ANGRY, Image.ASLEEP, Image.SURPRISED, Image.SILLY,
            Image.FABULOUS, Image.MEH, Image.YES, Image.NO, Image.CLOCK12,
            Image.CLOCK11, Image.CLOCK10, Image.CLOCK9, Image.CLOCK8, Image.CLOCK7,
            Image.CLOCK6, Image.CLOCK5, Image.CLOCK4, Image.CLOCK3, Image.CLOCK2,
            Image.CLOCK1, Image.ARROW_N, Image.ARROW_NE, Image.ARROW_E, Image.ARROW_SE,
            Image.ARROW_S, Image.ARROW_SW, Image.ARROW_W, Image.ARROW_NW, Image.TRIANGLE,
            Image.TRIANGLE_LEFT, Image.CHESSBOARD, Image.DIAMOND, Image.DIAMOND_SMALL, Image.SQUARE,
            Image.SQUARE_SMALL, Image.RABBIT, Image.COW, Image.MUSIC_CROTCHET, Image.MUSIC_QUAVER,
            Image.MUSIC_QUAVERS, Image.PITCHFORK, Image.XMAS, Image.PACMAN, Image.TARGET, Image.TSHIRT,
            Image.ROLLERSKATE, Image.DUCK, Image.HOUSE, Image.TORTOISE, Image.BUTTERFLY, Image.STICKFIGURE,
            Image.GHOST, Image.SWORD, Image.GIRAFFE, Image.SKULL, Image.UMBRELLA, Image.SNAKE]

        for img in lst:
            display.show(img)
            sleep(500)
        ```
    """
    )
    }}



#### Créer sa propre image
Chaque pixel LED sur l’affichage physique peut prendre une parmi dix valeurs. Si un pixel prend la valeur 0 c’est qu’il est éteint. Littéralement, il a une luminosité de zéro. En revanche, s’il prend la valeur 9 il est à la luminosité maximale. Les valeurs de 1 à 8 représentent des niveaux de luminosité entre éteint (0) et « au maximum » (9).


```python
from microbit import *

bateau = Image("05050:"
               "05050:"
               "05050:"
               "99999:"
               "09990")

display.show(bateau)
```



### 2.1.3 Les pixels (`display.set_pixel(x, y, val)`)
Vous pouvez régler la luminosité des pixels de l'affichage individuellement de 0 (désactivé) à 9 (luminosité maximale). Pour des informations sur les coordonnées de l'affichage, voir le [guide pour matrice à LED](https://microbit.org/guide/hardware/leds/){. target="_blank"}.

Exécuter le programme suivant:


```python
from microbit import *
display.set_pixel(1, 4, 9)
```

!!! example "{{ exercice() }}"
    
    Faire clignoter le pixel central.

    {{
    correction(True,
    """
    ??? success \"Correction\" 
        ```python linenums='1'
        from microbit import *

        while True:
            display.set_pixel(2, 2, 9)
            sleep(200)
            display.set_pixel(2, 2, 0)
            sleep(200)
        ```
    """
    )
    }}


!!! example "{{ exercice() }}"
    Faire afficher en boucle un pixel aléatoire pendant 200 ms.

    Pour obtenir un entier pseudo-aléatoire, on utilisera la fonction `randint` du module `random`.
    Par exemple, l'instruction ```randint(2, 8)``` va renvoyer un nombre (pseudo-)aléatoire entre 2 et 8 inclus.

    On pourra aussi utiliser l'instruction `display.clear()` pour éteindre tout l'affichage.

    {{
    correction(False,
    """
    ??? success \"Correction\" 
        ```python linenums='1'
        from microbit import *
        from random import randint

        while True:
            x = randint(0,4)
            y = randint(0,4)
            display.set_pixel(x, y, 9)
            sleep(200)
            display.clear()
        ```
    """
    )
    }}




### 2.4 Les entrées boutons A, B et A+B - programmation événementielle [(vidéo explicative)](https://youtu.be/t_Qujjd_38o){. target="_blank"}

![image](data/mb_AB.png){: .center width=30%}


 Il y a deux boutons sur la face avant du micro:bit (étiquetés A et B). On peut détecter quand ces boutons sont pressés, ce qui permet de déclencher des instructions sur l'appareil.

Exemples avec le boutton A:

- `button_a.is_pressed()`: renvoie *True* si le bouton spécifié est actuellement enfoncé et *False* sinon.
- `button_a.was_pressed()`: renvoie *True* ou *False* pour indiquer si le bouton a été appuyé depuis le démarrage de l'appareil ou la dernière fois que cette méthode a été appelée.

**Exemple :** Essayer le programme suivant qui fait défiler le texte "NSI" indéfiniment. Dès qu'un bouton est pressé, on sort de la boucle `break` et le programme s'achève.


```python
from microbit import *
while True:
    display.scroll("NSI")
    sleep(200)
    if button_a.was_pressed():
        break
display.clear()
display.show(Image.SAD)
```

!!! example "{{ exercice() }}"
    Créer le code permettant de basculer d'un visage triste à un visage heureux suivant qu'on appuie sur A ou sur B. 

    ![](data/exo1.webp){: .center}   


    {{
    correction(False,
    """
    ??? success \"Correction\" 
        ```python
        from microbit import *
        while True:
            if button_a.was_pressed():
                display.show(Image.SAD)
            if button_b.was_pressed():
                display.show(Image.HAPPY)
        ``` 
    """
    )
    }}

       

!!! example "{{ exercice() }}"
    
    Créer le code permettant de déplacer un point vers la gauche ou vers la droite en appuyant sur A ou sur B.

    ![](data/exo2.webp){: .center}

    {{
    correction(False,
    """
    ??? success \"Correction\" 
        ```python linenums='1'
        from microbit import *
        x = 2
        while True:
            display.clear()
            display.set_pixel(x, 2, 9)
            if button_a.was_pressed():
                x = x - 1
            if button_b.was_pressed():
                x = x + 1
        ```        
    """
    )
    }}



!!! example "{{ exercice() }}"
    
    Même énoncé que l'exercice précédent, mais en faisant parcourir tout l'écran au pixel :

    - si on sort à droite, on se décale d'une ligne vers le bas et on revient tout à gauche.
    - si on sort à gauche, on se décale d'une ligne vers le haut et on revient tout à droite.
    - arrivé tout en bas à droite, on réapparaît en haut à gauche (et réciproquement).

    
    {{
    correction(False,
    """
    ??? success \"Correction\" 
        ```python linenums='1'
        from microbit import *
        x = 2
        y = 2
        while True:
            display.clear()
            display.set_pixel(x, y, 9)
            if button_a.was_pressed():
                x = x - 1
            if button_b.was_pressed():
                x = x + 1
            if x == 5:
                x = 0
                y = y + 1
            if x == -1:
                x = 4
                y = y - 1
            if y == 5:
                x = 0
                y = 0
            if y == -1:
                x = 4
                y = 4       
        ```        
    """
    )
    }}

!!! example "{{ exercice() }}"
    
    On veut créer le jeu suivant :
    
    - au démarrage, un pixel aléatoire est placé sur l'écran.
    - il faut ensuite se déplacer un point vers la gauche ou vers la droite en appuyant sur A ou sur B.
    - lorsque qu'on a rejoint le point aléatoire, un emoji HAPPY apparait.

    ![](data/poursuite.gif){: .center}

    
 
    {{
    correction(False,
    """
    ??? success \"Correction\" 
        ```python linenums='1'
        from microbit import *
        from random import randint

        n = randint(0,4)
        p = randint(0,4)

        x = 2
        y = 2

        while True:
            display.clear()
            display.set_pixel(n, p, 9)
            display.set_pixel(x, y, 9)

            if button_a.was_pressed():
                x = x - 1

            if button_b.was_pressed():
                x = x + 1

            if x == 5:
                x = 0
                y = y + 1

            if x == -1:
                x = 4
                y = y - 1

            if y == 5:
                y = 0

            if y == -1:
                y = 4

            if x == n and y == p:
              display.show(Image.HAPPY)  
              break

        
        ```        
    """
    )
    }}

    

!!! example "{{ exercice() }}"
    **Rajout d'un temps limité**

    La fonction ```tick_ms``` du module ```utime``` renvoie le nombre de millisecondes écoulées depuis le démarrage de la carte. Pour mesurer le temps écoulé dans un programme, on fixe le temps du début du programme dans une variable ```t0```. Il suffit d'observer ensuite la valeur de ```tick_ms() - t0``` pour savoir combien de temps (en millisecondes) s'est écoulé depuis le début du programme.

    Exemple (à exécuter pour comprendre !) :
    ```python linenums='1'
    from microbit import *
    from utime import *

    display.show(Image.HAPPY)
    t0 = ticks_ms()

    while True:
        if ticks_ms() - t0 > 5000:
            display.show(Image.SAD)
            break
    ```

    :arrow_right: Reprendre l'exercice précédent en rajoutant une difficulté supplémentaire avec un temps limité.

    {{
    correction(False,
    """
    ??? success \"Correction\" 
        ```python linenums='1'
        from microbit import *
        from random import randint
        from utime import *

        n = randint(0,4)
        p = randint(0,4)

        x = 2
        y = 2

        t0 = ticks_ms()

        while True:
            if ticks_ms() - t0 > 5000:
            display.show(Image.SAD)
            break

            display.clear()
            display.set_pixel(n, p, 9)
            display.set_pixel(x, y, 9)

            if button_a.was_pressed():
                x = x - 1

            if button_b.was_pressed():
                x = x + 1

            if x == 5:
                x = 0
                y = y + 1

            if x == -1:
                x = 4
                y = y - 1

            if y == 5:
                y = 0

            if y == -1:
                y = 4

            if x == n and y == p:
            display.show(Image.HAPPY)
            break
        ```             
    """
    )
    }}
    


!!! example "{{ exercice() }}"
    Créer un jeu de Pierre-Feuille-Ciseaux qui se déclenchera lorsqu'on secoue la Microbit. (Vous pouvez créer vos propres images de pierre, de feuille et de ciseaux)

    ![](data/PFC.gif){: .center}

    La détection du "secouage" de la carte se fera avec l'instruction suivante :
    ```python
    if accelerometer.was_gesture('shake'):
        ...
    ```

    {{
    correction(False,
    """
    ??? success \"Correction\" 
        ```python linenums='1'
        from microbit import *
        from random import randint

        pierre = Image('09990:'
                       '09009:'
                       '09990:'
                       '09000:'
                       '09000')

        feuille = Image('09999:'
                       '09000:'
                       '09990:'
                       '09000:'
                       '09000')

        ciseaux = Image('00999:'
                       '09000:'
                       '09000:'
                       '09000:'
                       '00999')


        while True:
            if accelerometer.was_gesture('shake'):
                v = randint(1,3)
                if v == 1:
                    display.show(pierre)
                if v == 2:
                    display.show(feuille)
                if v == 3:
                    display.show(ciseaux)
        ```        
    """
    )
    }}


!!! example "{{ exercice() }}"
    En utilisant les fonctions ```accelerometer.get_x()``` et ```accelerometer.get_y()``` de l'[accéléromètre](https://microbit-micropython.readthedocs.io/fr/latest/accelerometer.html){. target="_blank"}, créer un code qui allumera la LED du centre lorsque la carte est à l'horizontale, puis qui fera bouger cette LED en fonction de l'inclinaison de la carte.


    ```python linenums='1'
    from microbit import *

    def move(x, y):
        incx = accelerometer.get_x()
        if incx > 500:
            x += 1
            x = min(..., ...)
        if incx < -500:
            x -= 1
            x = max(..., ...)
        incy = accelerometer.get_y()
        if incy > 500:
            y += 1
            y = min(..., ...)
        if incy < -500:
            y -= 1
            y = max(..., ...)
        return x, y

    x = 2
    y = 2
    while True:
        display.clear()
        ..., ...  = move(..., ...)
        display.set_pixel(..., ..., 9)
        sleep(200)    
    ```

    {{
    correction(False,
    """
    ??? success \"Correction\" 
        ```python linenums='1'
        from microbit import *

        def move(x, y):
            incx = accelerometer.get_x()
            if incx > 500:
                x += 1
                x = min(x,4)
            if incx < -500:
                x -= 1
                x = max(0,x)
            incy = accelerometer.get_y()
            if incy > 500:
                y += 1
                y = min(y,4)
            if incy < -500:
                y -= 1
                y = max(0,y)
            return x, y

        x = 2
        y = 2
        while True:
            display.clear()
            x, y  = move(x, y)
            display.set_pixel(x,y,9)
            sleep(200)  
        ``` 
    """
    )
    }}

!!! example "{{ exercice() }}"
    **Communication radio**

    Voici un code proposant une communication radio entre deux cartes. Inspirez-vous de ce code pour (par exemple) faire un «vrai» Pierre-Feuille-Ciseaux entre deux cartes.

    ```python linenums='1'
    from microbit import *
    import radio
    
    radio.on()
    radio.config(channel=12)
    radio.config(power=7)

    while True:
        message = radio.receive()
        if message:
            if message == 'yes':
                display.show(Image.YES)
                sleep(500)
                display.clear()
            elif message == 'no':
                display.show(Image.NO)
                sleep(500)
                display.clear()
        if button_a.was_pressed():
            radio.send('yes')
            display.show(Image.YES)
            sleep(500)
            display.clear()
        if button_b.was_pressed():
            radio.send('no')
            display.show(Image.NO)
            sleep(500)
            display.clear()
    ```

    Plus de renseignements [ici](https://nsirennes.fr/os-archi/bbc-microbit/){. target="_blank"}




!!! example "{{ exercice() }}"
    En utilisant l'exercice 10 et la communication radio, faire «passer» une led d'une carte à l'autre en inclinant la carte.

    ??? tip "video"
         
        <iframe width="463" height="823" src="https://www.youtube.com/embed/uaG4TuBxN-w" title="" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

    {{
    correction(False,
    """
    ??? success \"Correction\" 
        Carte 1

        ```python linenums='1'
        from microbit import *
        import radio

        radio.on()
        radio.config(channel=12)
        radio.config(power=7)
        hasBall = True
        x = 2
        y = 2

        def move(x, y):
            incx = accelerometer.get_x()
            if incx > 500:
                x += 1
                x = min(x,5)
            if incx <-500:
                x -= 1
                x = max(0,x)
            incy = accelerometer.get_y()
            if incy > 500:
                y += 1
                y = min(y,4)
            if incy <-500:
                y -= 1
                y = max(0,y)
            return x, y

        while True:
            if not hasBall:
                message = radio.receive()
                if message: 
                    y = int(message)
                    x = 4
                    hasBall = True
            if hasBall:
                x, y = move(x, y)
                if x <= 4:
                    display.clear()
                    display.set_pixel(x, y, 9)
                if x == 5:
                    radio.send(str(y))
                    display.clear()
                    hasBall = False         
        
            sleep(100)
        ```

        Carte 2

        ```python linenums='1'
        from microbit import *
        import radio

        radio.on()
        radio.config(channel=12)
        radio.config(power=7)
        hasBall = False
        x = 2
        y = 2

        def move(x, y):
            incx = accelerometer.get_x()
            if incx > 500:
                x += 1
                x = min(x,4)
            if incx <-500:
                x -= 1
                x = max(-1,x)
            incy = accelerometer.get_y()
            if incy > 500:
                y += 1
                y = min(y,4)
            if incy <-500:
                y -= 1
                y = max(0,y)
            return x, y

        while True:
            if not hasBall:
                message = radio.receive()
                if message:     
                    y = int(message)
                    x = 0
                    hasBall = True
            if hasBall:
                x, y = move(x, y)
                if x >= 0 :
                    display.clear()
                    display.set_pixel(x, y, 9)
                if x == -1:
                    radio.send(str(y))
                    display.clear()
                    hasBall = False         
        
            sleep(100)
        ```
    """
    )
    }}




















{#

### 2.5 Capteur de lumière [(vidéo)](https://youtu.be/TKhCr-dQMBY){. target="_blank"}

En inversant les LEDs d'un écran pour devenir un point d'entrée, l'écran LED devient un capteur de lumière basique, permettant de détecter la luminosité ambiante.

La commande `display.read_light_level()` retourne un entier compris entre 0 et 255 représentant le niveau de lumière.

**Exercice :** Compléter le programme ci-dessous qui affiche une image de lune si on baisse la luminosité (en recouvrant la carte avec sa main par exemple) et un soleil sinon.


```python

from microbit import *

soleil = Image("90909:"
               "09990:"
               "99999:"
               "09990:"
               "90909:")

lune = Image("00999:"
             "09990:"
             "09900:"
             "09990:"
             "00999:")

while True:
    if display.read_light_level()> ... : #trouver la bonne valeur (entre 0 et 255)
        display.show(soleil)
    else:
        display.show(...) #trouver la bonne variable
    sleep(10)
```

**Prolongement:** créer un programme qui affiche le niveau de luminosité et le tester avec la LED d'un téléphone portable ou une lampe-torche par exemple. Plus la luminosité sera élevée, plus il y aura de LEDs affichées sur la matrice.

### 2.6 Capteur de température [(vidéo)](https://youtu.be/_T4N8O9xsMA){. target="_blank"}


Le micro:bit n’a pas un capteur de température dédié. Au lieu de cela, la température fournie est en fait la température de la puce de silicium du processeur principal. Comme le processeur chauffe peu en fonctionnement (c'est un processeur ARM à grande efficacité), sa température est une bonne approximation de la température ambiante.
L'instruction `temperature()` renvoie la température de la carte micro:bit en degrés Celsius.

**Exercice :** Ecrire un programme qui affiche la température (aide: on pourra utiliser l'instruction `display.scroll()`; revoir le point 2.1.1).

### 2.7 Accéléromètre [(vidéo)](https://youtu.be/byngcwjO51U){. target="_blank"}

Un accéléromètre mesure l'accélération de la carte micro:bit, ce composant détecte quand la micro:bit est en mouvement. Il peut aussi détecter d'autres actions (gestes), par exemple quand elle est secouée, inclinée ou qu'elle tombe.



La carte micro:bit est munie d’un accéléromètre. Il mesure le mouvement selon trois axes :

- X - l’inclinaison de gauche à droite.
- Y - l’inclinaison d’avant en arrière.
- Z - le mouvement haut et bas.

Dans l'exemple suivant à essayer, l'instruction `accelerometer.get_x()` permet de détecter un mouvement de gauche à droite en renvoyant un nombre compris entre -1023 et 1023; 0 étant la position "d'équilibre"


```python
#Exemple
from microbit import *

while True:
    abscisse = accelerometer.get_x()
    if abscisse > 500:
        display.show(Image.ARROW_E)
    elif abscisse < -500:
        display.show(Image.ARROW_W)
    else:
        display.show("-")
```

**Prolongement (*secouer les dés!*):**
!!! example "Exercice 4"
    === "Énoncé"
        Écrire un programme qui simule un dé en affichant une face au hasard lorsque la micro:bit est secouée. On pourra utiliser l'instruction `accelerometer.is_gesture(shake)` qui teste si la carte est secouée. Plus d'informations sur les gestes [ici](https://microbit-micropython.readthedocs.io/fr/latest/tutorials/gestures.html){target = "_blank"}.



### 2.8 Boussole

La boussole détecte le champ magnétique de la Terre, nous permettant de savoir quelle direction la micro:bit indique. La boussole doit être étalonnée avant de pouvoir être utilisée. Pour cela, on utilise `compass.calibrate()` qui exécute un petit jeu: au départ, micro:bit fait défiler "Tilt to fill screen". Ensuite, incliner micro:bit pour déplacer le point au centre de l’écran autour jusqu'à ce que vous ayez rempli la totalité de l’écran.

La fonction `compass.heading()` donne le cap de la boussole sous la forme d'un entier compris entre 0 et 360, représentant l'angle en degrés, dans le sens des aiguilles d'une montre, avec le nord égal à 0.

**Exercice :** Compléter le programme suivant qui indique le Nord.


```python

from microbit import *

compass.calibrate()

while True:
    if compass.heading() < "remplir ici" or compass.heading() > "remplir ici":
        display.show(Image.ARROW_N)
    else:
        display.show(Image.DIAMOND_SMALL)
```

**Prolongement:** Améliorer le programme pour que le micro:bit indique "N", "S", "E" et "O" en fonction de l'orientation de la boussole.

**Autre prolongement:** fabriquer une station météo qui détermine la direction du vent.

**Autre prolongement:** étudier l'intensité du champ magnétique autour du périphérique (en utilisant la fonction `compass.get_field_strength()`). Plus d'informations sur les fonctions "boussole" [ici](https://microbit-micropython.readthedocs.io/en/latest/compass.html).


*document basé sur le travail de Thomas Basso, académie de Polynésie*


#}