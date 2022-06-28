# Les dictionnaires : premiers exemples


```python
dressing = {"pantalons":3, "pulls":4, "tee-shirts":8}
```


```python
dressing["pulls"]
```




    4




```python
FR_to_EN = {"navigateur":"browser", "précédent":"back", "suivant":"forward"}
```


```python
FR_to_EN["suivant"]
```




    'forward'




```python
AlanTuring = {"naissance":(23,6,1912),"décès":(12,6,1954),"lieu naissance":"Londres", "lieu décès":"Wilmslow"}
```


```python
AlanTuring["décès"]
```




    (12, 6, 1954)



# Définition d'un dictionnaire
Un dictionnaire est une donnée composite qui **n'est pas ordonnée**.  
Il fonctionne par un système de `clé:valeur`.  
Les clés, comme les valeurs, peuvent être de types différents.
Un dictionnaire est délimité par des accolades. 

_Rappel :_
- crochets [ ] -> listes
- parenthèses ( ) -> tuples
- accolades { } -> dictionnaires



```python
FR_to_EN
```




    {'navigateur': 'browser', 'précédent': 'back', 'suivant': 'forward'}




```python
type(FR_to_EN)
```




    dict



Il est possible d'obtenir la liste des clés et des valeurs avec la méthode `keys()` et la méthode `values`.


```python
dressing.keys()
```




    dict_keys(['pantalons', 'pulls', 'tee-shirts'])




```python
FR_to_EN.values()
```




    dict_values(['browser', 'back', 'forward'])



## Création d'un dictionnaire vide
On crée un dictionnaire vide par l'instruction :


```python
monDico = dict()
```


```python
type(monDico)
```




    dict



ou plus simplement de cette manière :


```python
unAutreDico = {}
```


```python
type(unAutreDico)
```




    dict



## Ajout / Modification d'un élément dans un dictionnaire
Pas besoin d'une méthode `append()`, il suffit de rajouter une paire `clé : valeur`


```python
dressing["chaussettes"] = 12
```


```python
dressing
```




    {'pantalons': 3, 'pulls': 4, 'tee-shirts': 8, 'chaussettes': 12}



On peut modifier un dictionnaire existant.


```python
dressing["chaussettes"] = 11
```


```python
dressing
```




    {'pantalons': 3, 'pulls': 4, 'tee-shirts': 8, 'chaussettes': 11}



## Suppression d'une valeur
On utilise l'instruction `del` (déjà rencontrée pour les listes)


```python
del dressing["chaussettes"]
```


```python
dressing
```

## Exercice 1:

Reprenons notre dictionnaire ```dressing``` :


```python
dressing = {"pantalons":3, "pulls":4, "tee-shirts":8}
```

Créer une fonction `achat(habit)` qui augmente de 1 le nombre d'habits (pantalon, pull ou tee-shirt) de mon dressing.


```python
def achat(habit):
    dressing[habit] = dressing[habit] + 1

```

Utilisation :


```python
print(dressing)
achat("pantalons")
print(dressing)
```

    {'pantalons': 3, 'pulls': 4, 'tee-shirts': 8}
    {'pantalons': 4, 'pulls': 4, 'tee-shirts': 8}


Petit problème si on essaie d'acheter un vêtement pour la 1ère fois :


```python
achat("chemises")
```


    ---------------------------------------------------------------------------

    KeyError                                  Traceback (most recent call last)

    <ipython-input-28-fd9d1ac5f62d> in <module>
    ----> 1 achat("chemises")
    

    <ipython-input-27-feb173444189> in achat(habit)
          1 def achat(habit):
    ----> 2     dressing[habit] = dressing[habit] + 1
    

    KeyError: 'chemises'


##  Test d'appartenance à un dictionnaire
Le mot `in` permet de tester l'appartenance d'une clé à un dictionnaire. Un booléen est renvoyé.


```python
"cravates" in dressing
```




    False




```python
"pulls" in dressing
```




    True



## Exercice 2:
Améliorer la fonction `achat(habit)` en y incluant un test pour prendre en compte les nouveaux habits.


```python
dressing = {"pantalons":3, "pulls":4, "tee-shirts":8}
```


```python
def achat(habit):
    if habit in dressing :
        dressing[habit] = dressing[habit] + 1
    else :
        dressing[habit] = 1
```


```python
achat("gants")
```


```python
dressing
```




    {'pantalons': 4, 'pulls': 4, 'tee-shirts': 8, 'gants': 1}



---------

## Annexe : utilisation de `in` pour d'autres types construits (listes, tuples, chaines de caractères...)


```python
voyelles = ("a", "e", "i", "o", "u", "y")
```


```python
"y" in voyelles
```


```python
"z" in voyelles
```


```python
mot = "vacances"
"k" in mot
```


```python

```
