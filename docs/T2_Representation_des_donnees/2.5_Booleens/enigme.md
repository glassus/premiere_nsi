# Énigme

Vous pouvez faire cette énigme sur Thonny (pensez à bien travailler dans le dossier qui contient vos deux images) ou bien sur Capytale 
[https://capytale2.ac-paris.fr/web/c/5912-1397991](https://capytale2.ac-paris.fr/web/c/5912-1397991){. target="_blank"}

## 1. À la recherche du personnage mystère

Vous avez trouvé une image bien étrange :

![](data/mystere.bmp){: .center}

Un visage semble se deviner derrière un champ de fleurs... mais quel est ce visage ?

L'image du champ de fleurs ne vous est pas inconnue, d'ailleurs en cherchant bien vous l'avez retrouvée dans vos dossiers :

![](data/mask.jpg){: .center}


On dirait que le personnage-mystère a voulu se fondre dans le champ de fleurs...

**XORez-vous découvrir qui est ce personnage-mystère ?**


## 2. Aide pour la manipulation d'images et l'extraction de pixels

### 2.1 Code de démarrage

```python linenums='1'
from PIL import Image

img_myst = Image.open("mystere.bmp")
img_mask = Image.open("mask.jpg")

largeur = img_myst.width
hauteur = img_myst.height

img_new = Image.new('RGB', img_myst.size)
```
### 2.2 Manipulation de pixels

Les expressions ci-dessous sont à tester pour en comprendre le fonctionnement. 

#### 2.2.1 Récupérer le code ```RGB```  un pixel

```python
>>> img_myst.getpixel((125, 80))
(54, 217, 174)
```
Le pixel de coordonnées (125, 80) a pour composantes RGB (54, 217, 174).

### 2.2.2 Modifier la couleur d'un pixel

```python
>>> img_new.putpixel((30,70), (255,0,0))
>>> 
```
Le pixel de coordonnées (30, 70) est maintenant un pixel rouge.

#### 2.2.3 Afficher une image

```python
>>> img_mask.show()
```

#### 2.2.4 Sauvegarder une image
```python
>>> img_new.save("solution.png")
```

{{
correction(False,
"""
??? success \"Correction\" 
    ```python linenums='1'
    from PIL import Image

    img_myst = Image.open('mystere.bmp')
    img_mask = Image.open('mask.jpg')

    largeur = img_myst.width
    hauteur = img_myst.height

    img_new = Image.new('RGB', img_myst.size)

    for x in range(largeur):
        for y in range(hauteur):
            pix_myst = img_myst.getpixel((x, y))
            pix_mask = img_mask.getpixel((x, y))
            new_pix = (pix_myst[0] ^ pix_mask[0], pix_myst[1] ^ pix_mask[1], pix_myst[2] ^ pix_mask[2])
            img_new.putpixel((x,y), new_pix)

    img_new.show() 
    ```
"""
)
}}