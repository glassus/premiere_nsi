# 5.1 Manipulation de fichiers csv

![image](data/BO.png){: .center}


Les fichiers CSV (pour Comma Separated Values) sont des fichiers-texte (ils ne contiennent aucune mise en forme) utilisés pour stocker des données, séparées par des virgules (ou des points-virgules, ou des espaces...). Il n'y a pas de norme officielle du CSV.  


## 1. Ouverture d'un fichier CSV par des logiciels classiques
- Télécharger le fichier [exemple.csv](../data/exemple.csv)
- Ouvrir avec le Bloc-Notes ce fichier.
- Rajouter une ligne avec une personne supplémentaire, sauvegarder le fichier.
- Ouvrir le fichier avec LibreOffice.

## 2. Exploitation d'un fichier CSV en Python avec le module CSV
L'utilisation d'un tableur peut être délicate lorsque le fichier CSV comporte un très grand nombre de lignes. 
Python permet de lire et d'extraire des informations d'un fichier CSV même très volumineux, grâce à des modules dédiés, comme le bien-nommé `csv` (utilisé ici) ou bien `pandas` (qui sera vu plus tard).

Le logiciel ```Jupyter Notebook``` se prête parfaitement à la consultation et l'exploitation de données structurées, nous l'utiliserons préféremment à ```Thonny```. 

### 2.1 Première méthode
Le script suivant :
```python linenums='1'
import csv                          
f = open('exemple.csv', "r", encoding = 'utf-8') # le "r" signifie "read", le fichier est ouvert en lecture seule
donnees = csv.reader(f)  # donnees est un objet (spécifique au module csv) qui contient des lignes

for ligne in donnees:               
    print(ligne)
    
f.close()    # toujours fermer le fichier !
```

donne :

```python
['Prénom', 'Nom', 'Email', 'SMS']
['John', 'Smith', 'john@example.com', '33123456789']
['Harry', 'Pierce', 'harry@example.com', '33111222222']
['Howard', 'Paige', 'howard@example.com', '33777888898']
```




**Problèmes**

1. Les données ne sont pas structurées : la première ligne est la ligne des «descripteurs» (ou des «champs»), alors que les lignes suivantes sont les valeurs de ces descripteurs.
2. La variable `donnees` n'est pas exploitable en l'état. Ce n'est pas une structure connue.


### 2.2 Améliorations
Au lieu d'utiliser la fonction `csv.reader()`, utilisons `csv.DictReader()`. Comme son nom l'indique, elle renverra une variable contenant des dictionnaires.

Le script suivant :
```python linenums='1'
import csv
f = open('exemple.csv', "r", encoding = 'utf-8')
donnees = csv.DictReader(f)

for ligne in donnees:
    print(dict(ligne))
    
f.close()
```

donne
```python
{'Prénom': 'John', 'Nom': 'Smith', 'Email': 'john@example.com', 'SMS': '33123456789'}
{'Prénom': 'Harry', 'Nom': 'Pierce', 'Email': 'harry@example.com', 'SMS': '33111222222'}
{'Prénom': 'Howard', 'Nom': 'Paige', 'Email': 'howard@example.com', 'SMS': '33777888898'}
```



C'est mieux ! Les données sont maintenant des dictionnaires. Mais nous avons juste énuméré 3 dictionnaires. Comment ré-accéder au premier d'entre eux, celui de John Smith ? Essayons :


```python
>>> donnees[0]

    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-3-9914ab00321e> in <module>
    ----> 1 donnees[0]
    

    TypeError: 'DictReader' object does not support indexing
```



### 2.3 Une liste de dictionnaires

Nous allons donc créer une liste de dictionnaires.


Le script suivant :
```python linenums='1'
import csv
f = open('exemple.csv', "r", encoding = 'utf-8')
donnees = csv.DictReader(f)
amis = []
for ligne in donnees:
    amis.append(dict(ligne))
    
f.close()
```

permet de faire ceci :

```python
>>> amis

    [{'Prénom': 'John',
      'Nom': 'Smith',
      'Email': 'john@example.com',
      'SMS': '33123456789'},
     {'Prénom': 'Harry',
      'Nom': 'Pierce',
      'Email': 'harry@example.com',
      'SMS': '33111222222'},
     {'Prénom': 'Howard',
      'Nom': 'Paige',
      'Email': 'howard@example.com',
      'SMS': '33777888898'}]

>>> print(amis[0]['Email'])
    john@example.com

>>> print(amis[2]['Nom'])
  Paige
```







## 3. Un fichier un peu plus intéressant : les joueurs de rugby du TOP14

Le fichier [`top14.csv `](../data/top14.csv)  contient tous les joueurs du Top14 de rugby, saison 2019-2020, avec leur date de naissance, leur poste, et leurs mensurations. 

_Ce fichier a été généré par Rémi Deniaud, de l'académie de Bordeaux._


**Q1.** Stocker dans  une variable `joueurs`  les renseignements de tous les joueurs présents dans ce fichier csv.


??? tip "réponse"
    ```python linenums='1'
    import csv
    f = open('data/top14.csv', "r", encoding = 'utf-8')
    donnees = csv.DictReader(f)
    joueurs = []
    for ligne in donnees:
        joueurs.append(dict(ligne))
        
    f.close()
    ```

### 3.1 Première analyse

**Q2.** Combien de joueurs sont présents dans ce fichier ?

??? tip "réponse"
    ```python
    >>> len(joueurs)
     595
    ```



**Q3.** Quel est le prénom du joueur n°486 ?

??? tip "réponse"
    ```python
    >>> joueurs[486]['Nom']
      'Wenceslas LAURET'
    ```




  



### 3.2 Extraction de données particulières


**Q4.**  Où joue Baptiste SERIN ?  

La méthode la plus naturelle est de parcourir toute la liste jusqu'à trouver le bon joueur, puis d'afficher son équipe.


??? tip "réponse"
    ```python
    >>> for joueur in joueurs :
            if joueur['Nom'] == 'Baptiste SERIN' :
                print(joueur['Equipe'])
    ```


Une méthode plus efficace est d'utiliser une liste par compréhension incluant un test. 

??? tip "réponse"
    ```python
    >>> clubSerin = [joueur['Equipe'] for joueur in joueurs if joueur['Nom'] == 'Baptiste SERIN']
    >>> clubSerin
    ```



**Q5.**  Qui sont les joueurs de plus de 140 kg ?

Attention à bien convertir en entier la chaine de caractère renvoyée par la clé ```Poids``` 

??? tip "réponse"
    ```python
    >>> lourds = [(joueur['Nom'], joueur['Poids']) for joueur in joueurs if int(joueur['Poids']) > 140]
    >>> lourds
    ```


### 4. Exploitation graphique
Nous allons utiliser le module Matplotlib pour illustrer les données de notre fichier csv.

### 4.1 Exemple 


```python linenums='1'
%matplotlib inline
import matplotlib.pyplot as plt
X = [0,1,3,6]
Y = [12,10,7,15]
plt.plot(X,Y,'ro') # r pour red, o pour un cercle. voir https://matplotlib.org/api/markers_api.html
plt.show()
```


![png](01_Manipulation_csv_files/01_Manipulation_csv_34_0.png){: .center}


### 4.2 Application

**Q1.** Afficher sur un graphique tous les joueurs de rugby du top14, en mettant le poids en abscisse et la taille en ordonnée.

??? tip "réponse"

    ```python linenums='1'
    %matplotlib inline
    X = [int(joueur['Poids']) for joueur in joueurs]
    Y = [int(joueur['Taille']) for joueur in joueurs]
    plt.plot(X,Y,'ro') # r pour red, o pour un cercle. voir https://matplotlib.org/api/markers_api.html
    plt.show()
    ```


    ![png](01_Manipulation_csv_files/01_Manipulation_csv_37_0.png){: .center}


**Q2.** Faire apparaître ensuite les joueurs évoluant au poste de Centre en bleu, et les 2ème lignes en vert.

??? tip "réponse"
    ```python linenums='1'
    %matplotlib inline
    #tous les joueurs
    X = [int(joueur['Poids']) for joueur in joueurs]
    Y = [int(joueur['Taille']) for joueur in joueurs]
    plt.plot(X,Y,'ro') 

    #on recolorie les Centres en bleu
    X = [int(joueur['Poids']) for joueur in joueurs if joueur['Poste'] == 'Centre']
    Y = [int(joueur['Taille']) for joueur in joueurs if joueur['Poste'] == 'Centre']
    plt.plot(X,Y,'bo')

    #on recolorie les 2ème ligne en vert
    X = [int(joueur['Poids']) for joueur in joueurs if joueur['Poste'] == '2ème ligne']
    Y = [int(joueur['Taille']) for joueur in joueurs if joueur['Poste'] == '2ème ligne']
    plt.plot(X,Y,'go')


    plt.show()
    ```


    ![png](01_Manipulation_csv_files/01_Manipulation_csv_38_0.png){: .center}


