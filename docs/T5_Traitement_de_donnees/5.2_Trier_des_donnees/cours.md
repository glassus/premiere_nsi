# 5.2 Trier des données

![image](data/BO.png){: .center}


{{initexo(0)}}
Nous reprenons notre fichier de joueurs de rugby du Top14. : [`top14.csv `](../data/top14.csv)



```python
import csv
f = open('top14.csv', "r", encoding = 'utf-8')
donnees = csv.DictReader(f)
joueurs = []
for ligne in donnees:
    joueurs.append(dict(ligne))
    
f.close()
```

## 1. Créer une fonction filtre

!!! example "{{ question() }}"
    
    Créer une fonction `joueursEquipe` qui renvoie une liste contenant les fiches de tous les joueurs de l'équipe `equipe` passée en paramètre. 


    *Exemple d'utilisation :*

    ```python
    >>> joueursEquipe('Bordeaux')
    [{'Equipe': 'Bordeaux', 'Nom': 'Jefferson POIROT', 'Poste': 'Pilier', 'Date de naissance': '01/11/1992', 'Taille': '181', 'Poids': '117'}, {'Equipe': 'Bordeaux', 'Nom': 'Lasha TABIDZE', 'Poste': 'Pilier', 'Date de naissance': '04/07/1997', 'Taille': '185', 'Poids': '117'}, {'Equipe': 'Bordeaux', 'Nom': 'Laurent DEL.....
    ```

    {{
    correction(False,
    """
    ??? success \"Correction\" 
        ```python
        def joueursEquipe(equipe):      
            return [player for player in joueurs if player['Equipe'] == equipe]
        ```        
    """
    )
    }}

!!! example "{{ question() }}"
    Définir de la même manière une fonction `joueursPoste` qui prend une chaîne de caractères `poste` et qui renvoie la liste des fiches des joueurs jouant à ce poste.

    *Utilisation :*
    ```python
    >>> joueursPoste("Talonneur")
    [{'Equipe': 'Agen', 'Nom': 'Clément MARTINEZ', 'Poste': 'Talonneur', 'Date de naissance': '14/03/1996', 'Taille': '181', 'Poids': '105'}, {'Equipe': 'Agen', 'Nom': 'Marc BARTHOMEUF', 'Poste': 'T...
    ```

    {{
    correction(False,
    """
    ??? success \"Correction\" 
        ```python
        def joueursPoste(poste):      
            return [player for player in joueurs if player['Poste'] == poste]
        ```    
    """
    )
    }}



## 2. Utilisation d'une fonction de tri




### 2.1 Le problème
Comment classer les joueurs suivant leur taille ?
La fonction `sorted(liste)` est efficace sur les listes : elle renvoie une nouvelle liste triée dans l'ordre croissant.


```python
>>> mylist = [4,2,8,6]
>>> mynewlist = sorted(mylist)
>>> print(mynewlist)
  [2, 4, 6, 8]
```

  


Mais comment trier un dictionnaire ? 


```python
>>> test = sorted(joueurs)
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-14-de081d14a3da> in <module>
    ----> 1 test = sorted(joueurs)
    

    TypeError: '<' not supported between instances of 'dict' and 'dict'


Il est normal que cette tentative échoue : un dictionnaire possède plusieurs clés différentes.
Ici, plusieurs clés peuvent être des critères de tri : la taille, le poids.

Nous allons donc utiliser la même stratégie que celle utilisée pour [le problème du sac à dos](../../../T4_Algorithmique/4.6_Algorithmes_gloutons/cours/#31-petite-aide-technique-avant-de-commencer){. target="_blank"}.

### 2.2 Un exemple de tri de dictionnaire


```python
Simpsons = [{"Prenom" : "Bart", "age estimé": "10"},
           {"Prenom" : "Lisa", "age estimé": "8"},
           {"Prenom" : "Maggie", "age estimé": "1"},
           {"Prenom" : "Homer", "age estimé": "38"},
           {"Prenom" : "Marge", "age estimé": "37"}]

def age(personnage):
    return int(personnage["age estimé"])

```


```python
>>> age(Simpsons[0])
   10
```



La création de cette fonction `age` va nous permettre de spécifier une clé de tri, par le paramètre `key` :

!!! note "Tri d'un dictionnaire :heart:"
    ```python
    >>> triSimpsons = sorted(Simpsons, key=age)
    ```


```python
>>> triSimpsons
    [{'Prenom': 'Maggie', 'age estimé': '1'},
     {'Prenom': 'Lisa', 'age estimé': '8'},
     {'Prenom': 'Bart', 'age estimé': '10'},
     {'Prenom': 'Marge', 'age estimé': '37'},
     {'Prenom': 'Homer', 'age estimé': '38'}]

```


On peut aussi inverser l'ordre de tri :


```python
>>> triSimpsons = sorted(Simpsons, key=age, reverse=True)
>>> triSimpsons
    [{'Prenom': 'Homer', 'age estimé': '38'},
     {'Prenom': 'Marge', 'age estimé': '37'},
     {'Prenom': 'Bart', 'age estimé': '10'},
     {'Prenom': 'Lisa', 'age estimé': '8'},
     {'Prenom': 'Maggie', 'age estimé': '1'}]

```

!!! example "{{ question() }}"
    Trier les joueurs du Top14 par taille.
    {{
    correction(False,
    """
    ??? success \"Correction\" 
        ```python
        def taillePlayer(player) :
            return int(player['Taille'])

        joueurs_taille_croissant = sorted(joueurs, key=taillePlayer)
        ```        
    """
    )
    }}


    
!!! example "{{ question() }}"
    Trier les joueurs du Top14 par poids.

    {{
    correction(False,
    """
    ??? success \"Correction\" 
        ```python
        def poidsPlayer(player) :
            return int(player['Poids'])

        joueurs_poids_croissant = sorted(joueurs, key=poidsPlayer)
        ```        
    """
    )
    }}


!!! example "{{ question() }}"
    Trier les joueurs de Bordeaux suivant leur Indice de Masse Corporelle ([IMC](https://fr.wikipedia.org/wiki/Indice_de_masse_corporelle){. target="_blank"} )    


    {{
    correction(False,
    """
    ??? success \"Correction\" 
        ```python
        def IMC(player):
            masse = int(player['Poids'])
            taille_m = int(player['Taille']) / 100
            return masse / taille_m**2

        joueursUBB = [player for player in joueurs if player['Equipe'] == 'Bordeaux']
        joueursUBB_tri = sorted(joueursUBB, key=IMC)
        ```        
    """
    )
    }}



## 3. Recherche des joueurs de profil physique similaire

### 3.1 Distance entre deux joueurs

!!! example "{{ question() }}"
    
    Construire une fonction `distance` qui renvoie la somme des carrés des différences de tailles et de poids entre deux joueurs `joueur1` et `joueur2`, passés en paramètres. 

    $$d = (p_1-p_2)^2 + (t_1-t_2)^2$$

    Cette fonction nous permettra d'estimer la différence morphologique entre deux joueurs.

    *Exemple d'utilisation :*
    ```python
    >>> distance(joueurs[23], joueurs[31])
    244
    ```

    *Vérification :*
    ```python
    >>> joueurs[23]
    {'Equipe': 'Agen', 'Nom': 'Alban CONDUCHÉ', 'Poste': 'Centre', 'Date de naissance': '29/10/1996', 'Taille': '190', 'Poids': '102'}
    >>> joueurs[31]
    {'Equipe': 'Agen', 'Nom': 'JJ TAULAGI', 'Poste': 'Arrière', 'Date de naissance': '18/06/1993', 'Taille': '180', 'Poids': '90'}
    ```

    $(102-90)^2+(190-180)^2=244$

    {{
    correction(False,
    """
    ??? success \"Correction\" 
        ```python
        def distance(joueur1,joueur2):
            p1 = int(joueur1['Poids'])
            p2 = int(joueur2['Poids'])
            t1 = int(joueur1['Taille'])
            t2 = int(joueur2['Taille'])
            return (p1-p2)**2+(t1-t2)**2
        ```        
    """
    )
    }}




### 3.2 Distance des joueurs avec Baptiste Serin

Retrouvons d'abord le numéro de Baptiste Serin dans notre classement de joueurs :


```python
>>>  for k in range(len(joueurs)) :
        if joueurs[k]['Nom'] == 'Baptiste SERIN' :
            print(k)
530
```





```python
>>> joueurs[530]
    {'Equipe': 'Toulon',
     'Nom': 'Baptiste SERIN',
     'Poste': 'Mêlée',
     'Date de naissance': '20/06/1994',
     'Taille': '180',
     'Poids': '79'}
```


Baptiste SERIN est donc le joueur numéro 530.

!!! example "{{ question() }}"
    
    Créer une fonction ```distanceSerin``` qui prend en paramètre un joueur et qui renvoie sa différence avec Baptiste Serin.

    *Exemple d'utilisation :*

    ```python
    >>> distanceSerin(joueurs[18])
    745
    ```

    {{
    correction(False,
    """
    ??? success \"Correction\" 
        ```python
        def distanceSerin(joueur):
            return distance(joueurs[530], joueur)
        ```        
    """
    )
    }}


!!! example "{{ question() }}"
    Classer l'ensemble des joueurs du Top14 suivant leur différence morphologique avec Baptiste Serin (du plus proche au plus éloigné).
    Afficher le nom des 10 premiers joueurs.

    {{
    correction(False,
    """
    ??? success \"Correction\" 
        ```python linenums='1'
        joueurs_VS_Serin = sorted(joueurs, key=distanceSerin)
        for i in range(10):
            joueur = joueurs_VS_Serin[i]
            print(joueur['Nom'])
        ```
    """
    )
    }}



