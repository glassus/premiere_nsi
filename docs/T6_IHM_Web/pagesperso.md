# Pages personnelles

### O. Installation du serveur Xampp

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


