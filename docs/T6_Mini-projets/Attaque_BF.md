# Attaque d'un mot de passe par force brute


![image](data/hackerman.png){: .center width=40%}


!!! tip ":warning: attention :warning:"
    L'activité ci-dessous n'est pas réalisable sous Capytale, qui n'autorise pas l'utilisation du module ```requests```.
    Vous devez donc la réaliser sur (par exemple) Thonny.  
    Si vous n'avez pas (encore) Thonny sur votre ordinateur personnel, téléchargez-le [ici](https://thonny.org/){. target="_blank"}

    Par contre, les réponses aux questions posées doivent être données sur l'activité Capytale [https://capytale2.ac-paris.fr/web/c/7371-1140429](https://capytale2.ac-paris.fr/web/c/7371-1140429){. target="_blank"}


Votre objectif est de trouver le mot de passe demandé sur la page [http://glassus1.free.fr/exoBF.html](http://glassus1.free.fr/exoBF.html){. target="_blank"}


Vous allez vous appuyer sur un leak (fuite) très célèbre de mots de passe , qui est le leak du site Rockyou. Dans la base de données de ce site, 32 millions de mots de passe étaient stockés en clair.

Lorsque le site a été piraté (par une injection SQL, voir le cours de Terminale), ces 32 millions de mots de passe se sont retrouvés dans la nature. Ils sont aujourd'hui téléchargeables librement, et constituent un dictionnaire de 14 341 564 mots de passe différents (car parmi les 32 millions d'utilisateurs, beaucoup utilisaient des mots de passe identiques). 

Nous allons utiliser un fichier beaucoup plus léger ne contenant que les 1000 premiers mots de passe. Ce fichier est nommé `extraitrockyou.txt`.


## 1. Lire les mots d'un fichier

### 1.1 Téléchargement du fichier `extraitrockyou.txt`

Téléchargez le fichier [extraitrockyou.txt](data/extraitrockyou.txt){. target="_blank"}.  
Attention, ce fichier doit être impérativement situé dans le même répertoire que le fichier du code Python que vous allez écrire.


### 1.2 Récupérer les éléments du fichier

Ouvrir un nouveau code dans Thonny et enregistrez-le **à côté du fichier `extraitrockyou.txt`**.  

La ligne suivante va stocker dans une liste `liste_mdp` les 1000 mots de passe présents dans le fichier `extraitrockyou.txt`.

```python
liste_mdp = open("extraitrockyou.txt").read().splitlines()
```

:warning: Si vous avez l'erreur : 
```python
FileNotFoundError: [Errno 2] No such file or directory: 'extraitrockyou.txt'
```

c'est que votre code et le fichier `extraitrockyou.txt` ne sont pas dans le même répertoire.

!!! abstract "Question 1"
    Écrire un code qui affiche les 1000 mots de passe contenus dans ```liste_mdp```.


(rappel : vous devez aller écrire vos réponses sur l'activité Capytale [https://capytale2.ac-paris.fr/web/c/7371-1140429](https://capytale2.ac-paris.fr/web/c/7371-1140429){. target="_blank"})

## 2. Utilisation du module `requests`
Le module `requests` de Python permet de récupérer le contenu d'une page web dont on aura donné l'adresse en paramètre.

Souvenez-vous par exemple de cette superbe page : [http://glassus1.free.fr/interesting.html](http://glassus1.free.fr/interesting.html){. target="_blank"}

Excécutez le code ci-dessous :

```python linenums='1'
import requests
p = requests.get("http://glassus1.free.fr/interesting.html")
print(p.text)
```

!!! abstract "Question 2"
    Écrire ce qui s'affiche en console lors de l'exécution du code :
    ```python linenums='1'
    import requests
    p = requests.get("http://glassus1.free.fr/interesting.html")
    print(p.text)
    ```
    
:warning: Si vous avez l'erreur : 
```python
ModuleNotFoundError: No module named 'requests'
```

c'est que le module ```requests``` n'est pas installé. Dans Thonny, aller dans Outils / Gérer les paquets et installer ```requests```.


## 3. Proposer un mot de passe

Un des 1000 mots de passe du fichier `extraitrockyou.txt` est le bon. Mais comment savoir lequel ?

### 3.1 Observation «à la main»

!!! abstract "Question 3"
    Rendez-vous sur la page [http://glassus1.free.fr/exoBF.html](http://glassus1.free.fr/exoBF.html){. target="_blank"} et proposer le mot de passe ```mauriac```.  
    Quelle url s'affiche alors dans la barre d'adresse ?


### 3.2 Automatisation d'un proposition

!!! abstract "Question 4"
    Écrire un code qui va proposer le mot de passe ```vacances``` et afficher le texte de la page obtenue. 


## 4. Résolution du problème

### 4.1 Petite aide sur les chaines de caractères

Pour rappel la concaténation des chaines de caractères permet de faire ceci :

```python
base = "je vous souhaite de bonnes"
suite = "vacances"
phrase = base + suite
```

!!! abstract "Question 5"
    Écrire un code qui va afficher les 1000 urls différentes qui serviront à tester tous les mots de passe du fichier `extraitrockyou.txt`. 

### 4.2 Quel est le bon mot de passe ?

!!! abstract "Question 6"
    Écrire un code qui détermine le mot de passe de la page [http://glassus1.free.fr/exoBF.html](http://glassus1.free.fr/exoBF.html). 


         

