# Pages personnelles

### O. Installation du serveur Xampp

[lien téléchargement XAMPP](https://sourceforge.net/projects/xampp/files/XAMPP%20Linux/8.1.17/xampp-linux-x64-8.1.17-0-installer.run/download){. target="_blank"}

Dans le dossier Téléchargements :

```sudo chmod +x xampp-linux....run``` 

puis 

```sudo ./xampp-linux....run``` 


### 1. Démarrage

#### 1.1 Serveur démarré ou pas ?

Dans la barre d'adresse de son navigateur, taper ```localhost``` ou bien ```127.0.0.1```.

Si aucune page n'apparaît, c'est que le serveur n'est pas démarré.

#### 1.2 Démarrer le serveur
Dans un terminal, taper

```sudo /opt/lampp/lampp start``` 

#### 1.3 Connaître son adresse IP

Dans un terminal,

```ip addr``` 

regarder 4 lignes avant la fin, chercher une adresse IP commençant par ```192.168.1.XXX```.


### 2. Mettre en production son site

Dans un terminal **ouvert depuis le dossier contenant ses pages** :

```sudo cp mapage.html /opt/lampp/htdocs/```

Si on veut tout copier :

```sudo cp * /opt/lampp/htdocs/```

### 3. Liens vers la page de chaque élève
{#
- [page de M. Lassus](http://192.168.1.198){. target="_blank"}
- [page de Malone](http://192.168.1.102){. target="_blank"}
- [page de Timéo](http://192.168.1.114){. target="_blank"}
- [page de Moustapha](http://192.168.1.173){. target="_blank"}
- [page de Jean](http://192.168.1.151){. target="_blank"}
- [page de Sarah](http://192.168.1.154){. target="_blank"}
- [page d'Antoine](http://192.168.1.150){. target="_blank"}
- [page de Nathanaël](http://192.168.1.127){. target="_blank"}
- [page de Lucas](http://192.168.1.119){. target="_blank"}
- [page de Nathan](http://192.168.1.121){. target="_blank"}
- [page de Périne](http://192.168.1.158){. target="_blank"}
- [page de Rita](http://192.168.1.109){. target="_blank"}
- [page de Tesnime](http://192.168.1.100){. target="_blank"}
- [page de Max](http://192.168.1.126){. target="_blank"}
- [page de Noé](http://192.168.1.133){. target="_blank"}
- [page de Gead](http://192.168.1.172){. target="_blank"}
- [page de Mikhaïlo](http://192.168.1.190){. target="_blank"}

#}
