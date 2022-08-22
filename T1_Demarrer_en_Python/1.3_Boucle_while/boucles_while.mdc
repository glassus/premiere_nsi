# Boucles non bornées : les boucles `while`

À la différence essentielle des boucles `for`, dont on peut savoir à l'avance combien de fois elles vont être exécutées, les boucles `while` sont des boucles indéterminées.  
Avec donc le risque de rester infiniment bloqué à l'intérieur !  


## Exemple 


```python
a = 0
while a < 3 :
    print("ok")
    a = a + 1
print("fini")
```

    ok
    ok
    ok
    fini


Vous pouvez visualiser l'exécution de ce code pas-à-pas sur le site [pythontutor](http://pythontutor.com/visualize.html#code=a%20%3D%200%0Awhile%20a%20%3C%203%3A%0A%20%20%20%20print%28%22ok%22%29%0A%20%20%20%20a%20%3D%20a%20%2B%201%0Aprint%28%22fini%22%29&cumulative=false&curInstr=0&heapPrimitives=nevernest&mode=display&origin=opt-frontend.js&py=3&rawInputLstJSON=%5B%5D&textReferences=false).

**Remarque** :  le code ci-dessous va-t-il donner un résultat différent ?


```python
a = 0
while a < 3 :
    a = a + 1
    print("ok")
print("fini")
```

    ok
    ok
    ok
    fini


**Conclusion** : l'évaluation de la condition ne se fait pas à chaque ligne mais bien au début de chaque tour de boucle. Si la variable qui déclenchera la sortie de boucle atteint sa valeur de sortie au milieu des instructions, les lignes restantes sont quand même exécutées.

## Les pièges ...

### piège n°1 : ne jamais sortir de la boucle


```python
a = 0
b = 0
while a < 10 :
    a = a * b
    print("flood")
    a = a + 1
print("ce texte ne s'écrira jamais")
```

### piège n°2 : ne jamais ENTRER dans la boucle


```python
a = 0
b = 0
while a > 10 :
    print("ce texte non plus ne s'écrira jamais")
    a = a + 1
    
print("fini") 
```

    fini


## Exercice 1
Trouver le plus petit nombre entier $n$ tel que $2^n$ soit supérieur à 1 milliard.



```python
n = 1
while 2**n < 10**9 :
    n = n + 1
    print("trop petit")
print("trouvé : ",n)
```

## Exercice 2
Demander à l'utilisateur de taper la lettre S (puis sur la touche Entrée). Recommencer tant qu'il n'a pas obéi.



```python
touche = ""  #chaine de caractère vide

while touche != 'S' :
    touche = input("appuyez sur S s'il vous plaît ")

print("ouf, merci !")
```
