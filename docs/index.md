 En route vers Mkdocs ! à 22h20

# On teste Pyodide

## Une console ?

{{ terminal() }}

Il semblerait que ça marche...
Bon faudra peut-être retoucher le CSS

## Un IDE ?

bien ?

{{ IDEv() }}

$f(x)= \frac{x}{2}+5$



??? tip "indices"
    === "fidn"
        blabla

    === "fsjdlk"
        dfks,jlkf
    
    === "fsdlkfl"
        kdlfnln


[Combien y a-t-il de triangles sur cette figure ?](#réponses){ .md-button }


!!! Abstract "En résumé"
    Ce problème sera ensuite résolu de manière progressive, et c'est l'occasion d'utiliser :

    - des méthodes par 



!!! warning "Attention"
    Un exercice est inclus dans le script ci-dessous.


```python
def ens_triangle(n):
    """Renvoie l'ensemble des points
       - à coordonnées entières ;
       - inclus dans le triangle de côté n.
    """
    points = {}
    for i in range(n+1):
        for j in range(n+1):
            if i + j <= n:
                points.add( (i, j) )
    return points
```

## Réponses aux problèmes <a name="réponses"></a>

??? done "Réponses"
    === "_Problème_"
        Vous pouvez obtenir la réponse, mais avez-vous bien cherché avant ?

    === "Triangle ; $n=6$"
        Il y a $78$ triangles.

    === "Rectangle ; $n=6$ et $m=10$"
        Il y a $1155$ rectangles.
    
    === "Hexagone ; $n=5$"
        Il y a $496$ triangles.

    === "Hexagone étoilé ; $n=3$"
        Il y a $354$ triangles.


## test abréviations

Il suffit de faire comme ça

*[suffit]: c'est vite dit

et voilà.

## admonitions

???+ note
    fdsfjlk
    fdsjflk
    dskfl


vd

!!! info inline end
    fdjslkfs
    sdfkjdlk
    sdfklj

fjsdlfk


| Method      | Description                          |
| ----------- | ------------------------------------ |
| `GET`       | :material-check:     Fetch resource  |
| `PUT`       | :material-check-all: Update resource |
| `DELETE`    | :material-close:     Delete resource |




Hormis la base 10, deux bases sont utilisées en informatique :

- la base 2  (le système **binaire**)
- la base 16 (le système **hexadécimal**)

Dans toute la suite, la base dans laquelle le nombre est écrit sera précisée en indice.  
Exemple : $13_{10}=1101_2=\rm{D}_{16}$

## I. Le système binaire 

En base 2, on ne dispose que des chiffres `0` et `1`. Le système binaire est un système de numération de position (comme le système décimal, hexadécimal... mais pas comme le système romain). À chaque rang correspond une puissance de 2.

#### Du binaire vers le décimal :
|...|128|64|32|16|8|4|2|1|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|...|$2^7$|$2^6$|$2^5$|$2^4$|$2^3$|$2^2$|$2^1$|$2^0$|
|...|1|1|0|1|0|0|1|0|



 $11010010_2=1 \times 2^7+ 1 \times 2^6+0 \times 2^5+1 \times 2^4+0 \times 2^3+0 \times 2^2+1 \times 2^1+0 \times 2^0=128+64+32+2=210_{10}$
 
 Le nombre binaire 11010010 correspond donc au nombre décimal 210.
 
 ##### En python :
 En Python, on peut utiliser la fonction `int("nombre",base)`.

{{ terminal() }}
