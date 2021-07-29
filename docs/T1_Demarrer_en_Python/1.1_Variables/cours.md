# 1.1 Variables

## A. Pourquoi des variables ?

### A.1 Introduction
Imaginons à l'oral l'expression *«nous allons stocker le prix du spectacle dans une variable  ```a```, qui vaudra donc au départ 32.»*

Il y a plusieurs commentaires à faire sur une telle annonce :

- Dans le problème que l'on cherche à modéliser, le prix du spectacle est une donnée importante, qui va peut-être évoluer (ou pas !).
- Pour la manipuler plus simplement, on va la désigner par un nom, le **nom de la variable** (ici, le nom ```a``` est particulièrement mal choisi, voir D. Bonnes pratiques de nommage)
- Comme en mathématiques, le nom de cette variable va désigner une valeur qui peut changer (*varier*) au cours du temps (encore une fois : ou pas).
- Cette valeur est fixée *au départ* à 32. On dira en informatique qu'elle est *initialisée* à 32.
- Si cette valeur ne change pas, on dira qu'elle est constante. Cela peut paraître inutile de donner un nom à quelque chose qui ne change pas, mais cela est très utile de définir les constantes au début d'un programme. 

### A.2 On code !
La phrase précédente donnera donc lieu à la ligne Python suivante :

```python
a = 32
```
!!! warning "Attention"
    Le symbole ```=``` ici utilisé n'a **rien à voir** avec le symbole = utilisé en mathématique. On dit qu'on a **affecté** à ```a``` la valeur 32, et il faut se représenter mentalement cette action par l'écriture ```a ← 32```.

!!! note "Comparaison de la syntaxe dans différents langages"

    === "Python"

        ```python
        a = 32
        ```

    === "C"

        ```c
        int a = 32;
        ```

    === "PHP"

        ```PHP
        $a = 32;
        ```


    === "Java"

        ```java
        int a = 32;
        ```

    === "Javascript"

        ```javascript
        var a = 32;
        ```
    === "Rust"

        ```rust
        let a = 32;
        ```
    === "Go"

        ```go
        a := 32
        ```
 


## B. Le fonctionnement interne
### B.1 Explication simplifiée
### B.2 Une réalité bien plus complexe...

## C. Différents types de variables

## D. Bonnes pratiques de nommage