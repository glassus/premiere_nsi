# 2.3 Dictionnaires

{{initexo(0)}}

![image](data/BO.png){: .center}

# 1. Les dictionnaires : premiers exemples

Une liste est un ensemble d'éléments accessibles par leur **indice**. Cet indice est en quelque sorte la «place» de l'élément dans la liste.
On peut dire que cet indice est **la clé** qui permet d'accéder à l'élément.

Dans un dictionnaire, chaque élément est accessible par une clé qui n'est plus forcément un nombre : une chaine de caractère, un nombre, ou autre chose, peut être une clé.

Imaginons que je fasse l'inventaire de mon dressing :

| habits | quantité |
| :--: | :--: |
| pantalons | 3 |
| pulls | 4 |
| tee-shirts | 8 |


!!! note "Exemple fondateur n°1 :heart:"
    - La création du dictionnaire représentant mon dressing se fera par :
        ```python
        >>> dressing = {"pantalons":3, "pulls":4, "tee-shirts":8}
        ```
    - L'accès à une valeur se fera par :
        ```python
        >>> dressing["pulls"]
          4
        ```
    - On dit que ```"pulls"``` est **la clé** et que 4 est **la valeur** associée à la clé.

    - Un dictionnaire est un ensemble clés / valeurs.  


:warning: **Attention** :warning:  : la clé peut aussi être un nombre :
```python
>>> myst = {9:4, 1:2, 6:3, 7:4} 
>>> myst[1]
2
>>> myst[7]
4 
```



## 2. Définitions et propriétés d'un dictionnaire

### 2.1 Définitions
!!! note "Définition" 
    Un dictionnaire est une donnée composite qui **n'est pas ordonnée** (à la différence des listes !)
    Il fonctionne par un système de `clé:valeur`.  
    Les clés, comme les valeurs, peuvent être de types différents.
    Un dictionnaire est délimité par des accolades. 

_Rappel :_

- crochets `[ ]` -> listes
- parenthèses `( )` -> tuples
- **accolades `{ }` -> dictionnaires**


### 2.2 Méthodes ```.keys()``` et   ```.values()```

!!! note "Exemples fondateurs n°2 :heart:"
    - Pour lister les clés d'un dictionnaire :
        ```python
        >>> dressing.keys()
        dict_keys(['pantalons', 'pulls', 'tee-shirts'])
        ```
    - Pour lister les valeurs d'un dictionnaire :
        ```python
        >>> dressing.values()
        dict_values([3, 4, 8])
        ```


Ces méthodes sont importantes (elles figurent explicitement au programme de NSI) mais sont en pratique peu utilisées. On leur préfèrera très largement la méthode de parcours suivante :

### 2.3 :star: :star: :star: Parcours d'un dictionnaire :star: :star: :star:
!!! note "Exemple fondateur n°3 :heart:"
    ```python
    >>> for habit in dressing:
            print(dressing[habit])
    3
    4
    8
    ```

!!! aide "Observation grâce à PythonTutor"
    <iframe width="800" height="300" frameborder="0" src="https://pythontutor.com/iframe-embed.html#code=dressing%20%3D%20%7B%22pantalons%22%3A3,%20%22pulls%22%3A4,%20%22tee-shirts%22%3A8%7D%0Afor%20habit%20in%20dressing%3A%0A%20%20%20%20print%28dressing%5Bhabit%5D%29&codeDivHeight=400&codeDivWidth=350&cumulative=false&curInstr=0&heapPrimitives=nevernest&origin=opt-frontend.js&py=3&rawInputLstJSON=%5B%5D&textReferences=false"> </iframe>


!!! example "{{ exercice() }}"
    Faire afficher la sortie suivante :
    ```python
    pantalons -> 3
    pulls -> 4
    tee-shirts -> 8
    ```    

    {{
    correction(True,
    """
    ??? success \"Correction\" 
        ```python linenums='1'
        dressing = {'pantalons':3, 'pulls':4, 'tee-shirts':8}

        for habit in dressing:
            print(habit, '->', dressing[habit])       
        ```

    """

    
    )
    }}


### 2.4 Création d'un dictionnaire vide

!!! note "Exemple fondateur n°4 :heart:"
    Deux méthodes existent pour créer un dictionnaire : ```dict()``` et ```{}```  
        ```python
        >>> mondico = dict()
        >>> mondico
        {}
        >>> mondico['john'] = 12
        >>> mondico
        {'john': 12}
        ```
        ```python
        >>> contacts = {}
        >>> contacts['bob'] = '06 12 17 21 32'
        ```



### 2.5 Ajout / Modification d'un élément dans un dictionnaire

!!! note "Exemple fondateur n°5 :heart:"
    Pas besoin d'une méthode `append()` comme pour les listes, il suffit de rajouter une paire `clé : valeur` :
    ```python
    >>> dressing["chaussettes"] = 12
    ```

    On peut aussi modifier un dictionnaire existant.
    ```python
    >>> dressing["chaussettes"] = 11
    ```


### 2.6 Suppression d'une valeur
!!! note "Exemple fondateur n°6 :heart:"
    On utilise l'instruction `del` (déjà rencontrée pour les listes)
    ```python
    del dressing["chaussettes"]
    ```
    Cette instruction est en pratique peu utilisée.


!!! example "{{ exercice() }}"
    Reprenons notre dictionnaire ```dressing``` :
    ```python
    dressing = {"pantalons":3, "pulls":4, "tee-shirts":8}
    ```
    Créer une fonction `achat` qui prend en paramètre une chaine de caractères ```habit```  augmente de 1 la quantité de l'habit concerné (pantalon, pull ou tee-shirt) de mon dressing.

    Exemple d'utilisation :
    ```python
    >>> dressing["pulls"]
    4
    >>> achat("pulls")
    >>> dressing["pulls"]
    5
    ```
    
    {{
    correction(True,
    """
    ??? success \"Correction\" 
        ```python linenums='1'
        dressing = {'pantalons':3, 'pulls':4, 'tee-shirts':8}

        def achat(habit):
            dressing[habit] += 1
        ```    
    """
    )
    }}


    


**Remarque :**
Petit problème si on essaie d'acheter un vêtement pour la 1ère fois

```python
>>> achat("chemises")
    ---------------------------------------------------------------------------

    KeyError                                  Traceback (most recent call last)

    <ipython-input-28-fd9d1ac5f62d> in <module>
    ----> 1 achat("chemises")
    

    <ipython-input-27-feb173444189> in achat(habit)
          1 def achat(habit):
    ----> 2     dressing[habit] = dressing[habit] + 1
    

    KeyError: 'chemises'
```

Nous allons résoudre ce problème grâce à :



### 2.7 Test d'appartenance à un dictionnaire

!!! note "Exemple fondateur n°7 :heart:"
    Le mot `in` permet de tester l'appartenance d'une clé à un dictionnaire. Un booléen est renvoyé.
    ```python
    >>> "cravates" in dressing
      False
    ```

## 3. Exercices
 
!!! example "{{ exercice() }}"
    Améliorer la fonction `achat` de l'exercice 2 en y incluant un test pour prendre en compte les nouveaux habits.
    
    Exemple d'utilisation :

    ```python
    >>> dressing
    {'pantalons': 3, 'pulls': 4, 'tee-shirts': 8}
    >>> achat('pulls')
    >>> achat('chapeau')
    >>> dressing
    {'pantalons': 3, 'pulls': 5, 'tee-shirts': 8, 'chapeau': 1}
    ```

    {{
    correction(True,
    """
    ??? success \"Correction\" 
        ```python linenums='1'
        def achat(habit):
            if habit in dressing:
                dressing[habit] += 1
            else:
                dressing[habit] = 1
        ```   
    """
    )
    }}


    

!!! example "{{ exercice() }}"
    On considère la liste suivante :
    ```python
    lst = ['Yanis', 'Fortuné', 'Fortuné', 'Andgel', 'Morgan', 'Lenny', 'Raphaël', 'Aya', 'Eliott', 'Aya', 'Sohel', 'Elma', 'Normann', 'Cyril', 'Lana', 'Fortuné', 'Lenny', 'Tom', 'Nina', 'Andgel', 'Lenny', 'Raphaël', 'Eliott', 'Gift', 'Cyril', 'Nina', 'Tom', 'Aya', 'Cyril', 'Raphaël', 'Justine', 'Nina', 'Lana', 'Elma', 'Mariam', 'Elma', 'Normann', 'Gift', 'Eliott', 'Aya', 'Robin', 'Fortuné', 'Nina', 'Saule', 'Aya', 'Elma', 'Andgel', 'Aya', 'Lenny', 'Misha', 'Fortuné', 'Yanis', 'Fortuné', 'Justine', 'Andgel', 'Sohel', 'Andgel', 'Gift', 'Morgan', 'Elma', 'Saule', 'Nina', 'Morgan', 'Andgel', 'Cyril', 'Raphaël', 'Misha', 'Fortuné', 'Saule', 'Justine', 'Saule', 'Nina', 'Eliott', 'Normann', 'Robin', 'Cyril', 'Misha', 'Misha', 'Cyril', 'Normann', 'Vitor', 'Yanis', 'Andgel', 'Normann', 'Vitor', 'Cyril', 'Normann', 'Sohel', 'Vitor', 'Andgel', 'Saule', 'Justine', 'Morgan', 'Lana', 'Raphaël', 'Sohel', 'Justine', 'Fortuné', 'Normann', 'Cyril', 'Nina', 'Lenny', 'Mariam', 'Tom', 'Morgan', 'Cyril', 'Cyril', 'Andgel', 'Lenny', 'Andgel', 'Sohel', 'Aya', 'Fortuné', 'Fortuné', 'Misha', 'Aya', 'Nina', 'Lenny', 'Raphaël', 'Aya', 'Lana', 'Raphaël', 'Cyril', 'Elma', 'Vitor', 'Andgel', 'Aya', 'Eliott', 'Tom', 'Vitor', 'Cyril', 'Normann', 'Fortuné', 'Mariam', 'Morgan', 'Sohel', 'Aya', 'Vitor', 'Robin', 'Fortuné', 'Sohel', 'Lenny', 'Mariam', 'Tom', 'Normann', 'Misha', 'Andgel', 'Eliott', 'Cyril', 'Mariam', 'Normann', 'Justine', 'Saule', 'Saule', 'Gift', 'Tom', 'Eliott', 'Fortuné', 'Normann', 'Eliott', 'Saule', 'Sohel', 'Justine', 'Nina', 'Eliott', 'Robin', 'Gift', 'Andgel', 'Andgel', 'Nina', 'Morgan', 'Robin', 'Morgan', 'Yanis', 'Justine', 'Raphaël', 'Aya', 'Normann', 'Saule', 'Yanis', 'Robin', 'Tom', 'Fortuné', 'Mariam', 'Sohel', 'Aya', 'Tom', 'Lenny', 'Eliott', 'Morgan', 'Morgan', 'Normann', 'Saule', 'Aya', 'Cyril', 'Saule', 'Lenny', 'Raphaël', 'Justine', 'Andgel']
    ```
    

    Créer un dictionnaire qui associera à chaque prénom son nombre d'occurrences dans la liste.

    {{
    correction(True,
    """
    ??? success \"Correction\" 
        ```python linenums='1'
        occurrence = {}

        for prenom in lst:
            if prenom in occurrence:
                occurrence[prenom] += 1
            else:
                occurrence[prenom] = 1
        ```         
    """
    )
    }}
       


    

!!! example "{{ exercice() }}"
    On considère la liste suivante :
    ```lst = ['5717', '1133', '5545', '4031', '6398', '2734', '3070', '1346', '7849', '7288', '7587', '6217', '8240', '5733', '6466', '7972', '7341', '6616', '5061', '2441', '2571', '4496', '4831', '5395', '8584', '3033', '6266', '2452', '6909', '3021', '5404', '3799', '5053', '8096', '2488', '8519', '6896', '7300', '5914', '7464', '5068', '1386', '9898', '8313', '1072', '1441', '7333', '5691', '6987', '5255']``` 

    Quel est le **chiffre** qui revient le plus fréquemment dans cette liste ?

     
    {{
    correction(True,
    """
    ??? success \"Correction\" 
        ```python linenums='1'
        lst = ['5717', '1133', '5545', '4031', '6398', '2734', '3070', '1346', '7849', '7288', '7587', '6217', '8240', '5733', '6466', '7972', '7341', '6616', '5061', '2441', '2571', '4496', '4831', '5395', '8584', '3033', '6266', '2452', '6909', '3021', '5404', '3799', '5053', '8096', '2488', '8519', '6896', '7300', '5914', '7464', '5068', '1386', '9898', '8313', '1072', '1441', '7333', '5691', '6987', '5255']

        occ = {}
        maxi = 0
        for nombre in lst:
            for chiffre in nombre:
                if chiffre in occ:
                    occ[chiffre] += 1
                else:
                    occ[chiffre] = 1
                if occ[chiffre] > maxi:
                    maxi = occ[chiffre]
                    chiffre_max = chiffre

        print(chiffre_max, 'est le chiffre le plus fréquent')
        print('il apparait', maxi, 'fois')

        ```        
    """
    )
    }}

!!! example "{{ exercice() }}"
    *Exercice extrait de la [BNS 2025](https://glassus.github.io/terminale_nsi/T6_6_Epreuve_pratique/BNS_2025/){. target="_blank"}*

    Le nombre d’occurrences d’un caractère dans une chaîne de caractère est le nombre
    d’apparitions de ce caractère dans la chaîne.

    Exemples :

    - le nombre d’occurrences du caractère `‘o’` dans `‘bonjour’` est 2 ;
    - le nombre d’occurrences du caractère `‘b’` dans `‘Bébé’` est 1 ;
    - le nombre d’occurrences du caractère `‘B’` dans `‘Bébé’` est 1 ;
    - le nombre d’occurrences du caractère `‘ ‘` dans `‘Hello world !’` est 2.

    On cherche les occurrences des caractères dans une phrase. On souhaite stocker ces
    occurrences dans un dictionnaire dont les clefs seraient les caractères de la phrase et
    les valeurs le nombre d’occurrences de ces caractères.


    Par exemple : avec la phrase `'Hello world !'` le dictionnaire est le suivant :

    `{'H': 1,'e': 1,'l': 3,'o': 2,' ': 2,'w': 1,'r': 1,'d': 1,'!': 1}`

    *L’ordre des clefs n’a pas d’importance.*

    Écrire une fonction `nbr_occurrences` prenant comme paramètre une chaîne de
    caractères `chaine` et renvoyant le dictionnaire des nombres d’occurrences des
    caractères de cette chaîne.


    {{
    correction(True,
    """
    ??? success \"Correction\" 
        ```python linenums='1'
        def nbr_occurrences(chaine):
            nb_occ = {}
            for caractere in chaine:
                if caractere in nb_occ:
                    nb_occ[caractere] += 1
                else:
                    nb_occ[caractere] = 1
            return nb_occ
        ```
    """
    )
    }}


!!! example "{{ exercice() }}"
    *Exercice extrait de la [BNS 2025](https://glassus.github.io/terminale_nsi/T6_6_Epreuve_pratique/BNS_2025/){. target="_blank"}*

    Écrire une fonction `enumere` qui prend en paramètre un tableau `tab` (type `list`) et renvoie
    un dictionnaire `d` dont les clés sont les éléments de `tab` avec pour valeur associée la liste
    des indices de l’élément dans le tableau `tab`.

    Exemple :

    ```python
    >>> enumere([])
    {}
    >>> enumere([1, 2, 3])
    {1: [0], 2: [1], 3: [2]}
    >>> enumere([1, 1, 2, 3, 2, 1])
    {1: [0, 1, 5], 2: [2, 4], 3: [3]}
    ```

    {{
    correction(True,
    """
    ??? success \"Correction\" 
        ```python linenums='1'
        def enumere(tab):
            d = {}
            for i in range(len(tab)):
                if tab[i] in d:
                    d[tab[i]].append(i)
                else:
                    d[tab[i]] = [i]
            return d
        ```
    """
    )
    }}


!!! example "{{ exercice() }}"
    Exercice 2 du sujet [Centres Etrangers J1 2021](https://glassus.github.io/terminale_nsi/T6_Annales/data/2021/21_Centres_Etrangers_1.pdf){. target="_blank"}

    {{
    correction(True,
    """
    ??? success \"Correction Q1.a. \" 
        ```flotte[26]``` renvoie  ```{'type' : 'classique', 'etat' : 1, 'station' : 'Coliseum'}```
    """
    )
    }}

    {{
    correction(True,
    """
    ??? success \"Correction Q1.b. \" 
        ```flotte[80]['etat']``` renvoie la valeur ```0```. 
    """
    )
    }}

    {{
    correction(True,
    """
    ??? success \"Correction Q1.c. \" 
        ```flotte[99]['etat']``` renverra une erreur car la clé 99 n'existe pas. 
    """
    )
    }}


    {{
    correction(True,
    """
    ??? success \"Correction Q2.a. \" 
        Les valeurs possibles pour ```choix``` sont ```electrique``` ou ```classique```. 
    """
    )
    }}

    {{
    correction(True,
    """
    ??? success \"Correction Q2.b. \" 
        En fonction du choix (```electrique``` ou ```classique```), cette fonction va renvoyer le nom de la première station où un vélo est disponible (à l'```etat``` 1).  
        Seule la première station sera renvoyée, à cause du ```return```. Si aucun vélo n'est disponible, la fonction ne renverra rien. 
    """
    )
    }}

    {{
    correction(True,
    """
    ??? success \"Correction Q3.a. \" 
        ```python linenums='1'
        for id_velo in flotte:
            if flotte[id_velo]['station'] == 'Citadelle' and flotte[id_velo]['etat'] == 1:
                print(id_velo)
        ``` 
    """
    )
    }}


    {{
    correction(True,
    """
    ??? success \"Correction Q3.b. \" 
        ```python linenums='1'
        for id_velo in flotte:
            if flotte[id_velo]['type'] == 'electrique' and flotte[id_velo]['etat'] != -1:
                print(id_velo, flotte[id_velo]['station'])
        ``` 
    """
    )
    }}

    {{
    correction(True,
    """
    ??? success \"Correction Q4. \" 
        ```python linenums='1'
        def velo_finder(coordonnees):
            velo_dispo = []
            for id_velo in flotte:
                d = distance(coordonnees, stations[flotte[id_velo]['station']])
                if d < 800 and flotte[id_velo]['etat'] == 1:
                    velo_dispo.append((flotte[id_velo]['station'], d, id_velo))
            return velo_dispo
        ```        
    """
    )
    }}