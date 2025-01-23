# 4.1 Extremums et moyennes

![image](data/BO.png){: .center}


:arrow_right: [Activité d'introduction](../intro_cours/){. target="_blank"}

## 1. Algorithme de recherche de maximum
La fonction ```recherche_max``` prend un tableau ```tab```  en entrée et renvoie la valeur maximale de ce tableau.

!!! note "Recherche de maximum :heart:"
    ```python
    def recherche_max(tab):
        '''renvoie le maximum de la liste tab'''
        maxi = tab[0]           # (1)
        for elt in tab:
            if elt > maxi:
                maxi = elt
        return maxi
    ```

    1. On initialise le maximum avec la première valeur du tableau (surtout pas avec 0 ou «moins l'infini» !)

**Utilisation :**
```python
>>> recherche_max([4, 3, 8, 1])
  8
```



## 2. Algorithme de calcul de moyenne
La fonction ```moyenne``` prend un tableau ```tab``` en entrée et renvoie la valeur moyenne de ce tableau.


!!! note "Calcul de moyenne :heart:"
    ```python
    def moyenne(tab):
        ''' renvoie la moyenne de tab'''
        somme = 0
        for elt in tab:
            somme += elt
        return somme / len(tab)
    ```

   
**Utilisation :**
```python
>>> moyenne([4, 3, 8, 1])
  4.0
```


## 3. Algorithme de recherche d'occurrence

La fonction ```recherche_occurrence``` prend un élément ```elt``` et un tableau ```tab``` en entrées et renvoie un tableau (éventuellement vide) contenant les indices d'apparition de l'élément ```elt``` dans ```tab``` .



!!! note "Recherche d'occurrence :heart:"
    ```python
    def recherche_occurrence(elt, tab):
        ''' renvoie la liste (éventuellement vide)
        des indices de elt dans tab'''
        liste_indices = []
        for i in range(len(tab)):
            if tab[i] == elt:
                liste_indices.append(i)
        return liste_indices
    ```

   
**Utilisation :**
```python
>>> recherche_occurrence(3, [1, 6, 3, 8, 3, 2])
[2, 4]
>>> recherche_occurrence(7, [1, 6, 3, 8, 3, 2])
[]
```