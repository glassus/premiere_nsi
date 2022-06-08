# Trier des données


Nous reprenons notre fichier de joueurs de rugby du Top14. 



```python
import csv
f = open('data/top14.csv', "r", encoding = 'utf-8')
donnees = csv.DictReader(f)
joueurs = []
for ligne in donnees:
    joueurs.append(dict(ligne))
    
f.close()
```

### Créer une fonction filtre
L'objectif est de créer une fonction `joueursEquipe(equipe)` qui renvoie une liste contentant tous les joueurs de l'équipe `equipe`. 
Le paramètre `equipe` sera donnée sous forme de chaîne de caractères. 
La valeur renvoyée sera de type liste.


```python
def joueursEquipe(equipe):
    ret = []
    
    for k in joueurs :
        if k['Equipe'] == equipe :
            ret.append(k)
    
    return ret

```

Exemple d'utilisation :


```python
len(joueursEquipe("Bordeaux"))
```




    37



Définir de la même manière une fonction `joueursPoste(poste)`.


```python

```

## Utilisation d'une fonction de tri

Comment classer les joueurs suivant leur taille ?
La fonction `sorted(liste)` est efficace sur les listes : elle renvoie une nouvelle liste triée dans l'ordre croissant.


```python
mylist = [4,2,8,6]
mynewlist = sorted(mylist)
print(mynewlist)
```

    [2, 4, 6, 8]


Mais comment trier un dictionnaire ? 


```python
test = sorted(joueurs)
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-14-de081d14a3da> in <module>
    ----> 1 test = sorted(joueurs)
    

    TypeError: '<' not supported between instances of 'dict' and 'dict'


Il est normal que cette tentative échoue : un dictionnaire possède plusieurs clés différentes.
Ici, plusieurs clés peuvent être des critères de tri : la taille, le poids.

### un exemple de tri de dictionnaire


```python
Simpsons = [{"Prenom" : "Bart", "age estimé": "10"},
           {"Prenom" : "Lisa", "age estimé": "8"},
           {"Prenom" : "Maggie", "age estimé": "1"},
           {"Prenom" : "Homer", "age estimé": "38"},
           {"Prenom" : "Marge", "age estimé": "37"}]
```


```python
def age(personnage):
    return int(personnage["age estimé"])
```


```python
age(Simpsons[0])
```




    10



La création de cette fonction `age()` va nous permettre de spécifier une clé de tri, par le paramètre `key` :


```python
triSimpsons = sorted(Simpsons, key = age)
```


```python
triSimpsons
```




    [{'Prenom': 'Maggie', 'age estimé': '1'},
     {'Prenom': 'Lisa', 'age estimé': '8'},
     {'Prenom': 'Bart', 'age estimé': '10'},
     {'Prenom': 'Marge', 'age estimé': '37'},
     {'Prenom': 'Homer', 'age estimé': '38'}]




```python
triSimpsons = sorted(Simpsons, key = age, reverse = True)
```


```python
triSimpsons
```




    [{'Prenom': 'Homer', 'age estimé': '38'},
     {'Prenom': 'Marge', 'age estimé': '37'},
     {'Prenom': 'Bart', 'age estimé': '10'},
     {'Prenom': 'Lisa', 'age estimé': '8'},
     {'Prenom': 'Maggie', 'age estimé': '1'}]



## Exercice 
1. Trier les joueurs du top14 par taille.
2. Trier les joueurs de Bordeaux par taille.
3. Trier les joueurs de Bordeaux suivant leur Indice de Masse Corporelle ([IMC](https://fr.wikipedia.org/wiki/Indice_de_masse_corporelle) )


```python
def taillePlayer(player) :
    return int(player['Taille'])
```


```python
joueurs_taille_croissant = sorted(joueurs, key = taillePlayer)
print(joueurs_taille_croissant)
```


```python
def IMC(player):
    masse = int(player['Poids'])
    taille_m = int(player['Taille']) / 100
    return masse / taille_m**2
    
```


```python
IMC(joueurs[0])
```




    36.42987249544626




```python
joueursUBB = [k for k in joueurs if k['Equipe'] == 'Bordeaux']
```


```python
joueursUBB_tri = sorted(joueursUBB, key = IMC)
```


```python
for k in joueursUBB_tri:
    print(k['Nom'], IMC(k))
```

    Yann LESGOURGUES 23.450918219051392
    Nicolas PLAZY 24.049343594386603
    Matthieu JALIBERT 24.382716049382715
    Blair CONNOR 24.48565200513601
    Geoffrey CROS 24.835646457268076
    Maxime LUCU 25.2162533116282
    Jean-Baptiste DUBIÉ 25.94548395958609
    Romain BUROS 26.023048986244955
    Santiago CORDERO 26.493025631204315
    Alexandre ROUMAT 26.527905315784103
    Cameron WOKI 26.81174510620575
    Lucas MÉRET 26.82742078020452
    Nans DUCUING 27.471688898385274
    Ulupano SEUTENI 27.757487216946675
    Clément MAYNADIER 28.59675712774171
    Cyril CAZEAUX 28.823589429650035
    Alexandre FLANQUART 28.835063437139564
    Semi RADRADRA 28.85921231326392
    Scott HIGGINBOTHAM 28.928336620644316
    Ben BOTICA 29.352354500694357
    Béka GORGADZE 29.394473838918284
    Mahamadou DIABY 29.708012675418743
    Masalosalo TUTAIA 30.036524413687044
    Jandré MARAIS 30.09896949290889
    Kane DOUGLAS 30.144103519262817
    Seta TAMANIVALU 30.794210688390585
    Rémi LAMERAT 31.01370510396975
    Marco TAULEIGNE 31.523258682601902
    Afa AMOSA 32.028367983070716
    Laurent DELBOULBÈS 32.35554470254266
    Adrien PÉLISSIÉ 33.576508653582
    Lasha TABIDZE 34.18553688823959
    Lekso KAULASHVILI 34.31610855329005
    Peni RAVAI 34.76990504017531
    Jefferson POIROT 35.713195567900854
    Vadim COBILAS 36.41975308641975
    Thierry PAÏVA 36.92107750472589


## Recherche des joueurs de profil  physique similaire

### Distance entre deux joueurs
Construire une fonction `distance(joueur1,joueur2)` qui renvoie la somme des carrés des différences de tailles et de poids entre les joueurs `joueur1` et `joueur2` : 
$$ d = (p_1-p_2)^2 + (t_1-t_2)^2$$


```python
def distance(joueur1,joueur2):
    p1 = int(joueur1['Poids'])
    p2 = int(joueur2['Poids'])
    t1 = int(joueur1['Taille'])
    t2 = int(joueur2['Taille'])
    return (p1-p2)**2+(t1-t2)**2
```

### Distance des joueurs avec Baptiste Serin

Retrouvons d'abord le numéro de Baptiste Serin dans notre classement de joueurs :


```python
for k in range(len(joueurs)) :
    if joueurs[k]['Nom'] == 'Baptiste SERIN' :
        print(k)
```

    530



```python
joueurs[530]
```




    {'Equipe': 'Toulon',
     'Nom': 'Baptiste SERIN',
     'Poste': 'Mêlée',
     'Date de naissance': '20/06/1994',
     'Taille': '180',
     'Poids': '79'}



Nous pouvons maintenant classer les joueurs suivant leur distance morphologique à Baptiste  SERIN :


```python
def distanceSerin(joueur2):
    return distance(joueurs[530],joueur2)
```


```python
distanceSerin(joueurs[530])
```




    0




```python
joueurs_VS_Serin = sorted(joueurs, key = distanceSerin)
```


```python
joueurs_VS_Serin
```


```python

```
