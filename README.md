# TPs Bus et Réseaux

## TP n°1 - Bus I2C

### 2.1. Capteur BMP280
#### Mise en œuvre du BMP280

* D'après la datasheet (p.28), la I2C slave adress = 0x76 (si SDO connecté au GND) ou 0x77 (si SDO connecté à VDDIO)
Dans notre cas, l'adresse de la I2C slave était **0x77** (écrit sur le composant)

* Le registre et la valeur permettant d'identifier ce composant : Register 0xD0 « id », valeur 0x58 (p.24)

* Le registre et la valeur permettant de placer le composant en mode normal (1 of the 3 power mode) : peut être sélectionner en utilisant les bits mode[1 :0] dans le registre de contrôle 0xF4 (en mettant 11)

* Etalonnage : calibration data, @ : 0xA1 -> 0x88 

* Registres température : temp_xlsb (@ :0xFC), temp_lsb(@ :0xFB), temp_msb (@ : 0xFA)

* Registres pression : press_xlsb (@ :0xF9), press_lsb(0xF8), press_msb(0xF7)

* Fonctions pour calculer la pression et température compensée en format entier 32 bits à la page 45 de la datasheet


### 2.2. Setup du STM32
#### Identification du BMP280

![alt text](https://github.com/Chatvolant/TP_Bus_et_reseaux/blob/main/code_identif1.png)
![alt text](https://github.com/Chatvolant/TP_Bus_et_reseaux/blob/main/code_identif2.png)
![alt text](https://github.com/Chatvolant/TP_Bus_et_reseaux/blob/main/code_identif3.png)

On nous retourne bien le bon identifiant du composant

#### Identification du BMP280
![alt text](https://github.com/Chatvolant/TP_Bus_et_reseaux/blob/main/code_identif4.png)
![alt text](https://github.com/Chatvolant/TP_Bus_et_reseaux/blob/main/code_identif5.png)

**Note** : on a une erreur si on déclare le tableau puis qu’on initialise les valeurs de cette façon :  
uint8_t transmission_data[2] ;  
transmission_data[0]=0xF4;  
transmission_data[1]=0x5F;  


#### Récupération de l'étalonnage, de la température et de la pression
![alt text](https://github.com/Chatvolant/TP_Bus_et_reseaux/blob/main/code_identif6.png)
![alt text](https://github.com/Chatvolant/TP_Bus_et_reseaux/blob/main/code_identif7.png)
![alt text](https://github.com/Chatvolant/TP_Bus_et_reseaux/blob/main/code_identif8.png)
![alt text](https://github.com/Chatvolant/TP_Bus_et_reseaux/blob/main/code_identif9.png)

Nous on a mis la valeur 010 dans le registre, donc on a une résolution de 17 bits pour la température et une précision de 0.0025°C.

#### Calcul des températures et des pression compensées

On récupère les valeurs de dig_T1, dig_T2, dig_T3, nécessaire au calcul de la compensation de la température.
Pour cela, on récupère les valeurs qui sont stockées dans le registre calib_data (mais que de 0x88 à 0x9D, pas tout le registre)



### 2.3. Communication I²C




## TP n°2 - TP2 - Interfaçage STM32 - Raspberry
### Premier démarrage
> Installez la carte SD dans le Raspberry et branchez l'alimentation.
Utilisez ssh pour vous connecter à votre Raspberry. Comment le Raspberry a obtenu son adresse IP? 

On a configuré au préalable la carte SD du Rasberry Pi afin qu'elle puisse se connecter au réseau ESE_Bus_Network, associée à un routeur.
Je pense que c'est le  routeur qui a attribué une adresse IP à notre Rasberry en utilisant le protocole DHCP vu qu'on ne l'a pas fait manuellement.


### Se connecter à la Rasberry Pi en ssh 
Commande à executer sur cmd : ssh eleveA@192.168.88.96
eleveA était le nom d'hôte de la Rasberry Pi

**ATTENTION** Avant de débrancher la Rasberry Pi quand on a fini de l'utiliser, il faut l'éteindre via le cmd. On peut le faire avec cette commande : sudo shutdown -h now


## TP n°3 - Interface REST
### 4.1. Installation du serveur Python

#### Premier fichier Web

Test serveur web avec 1er code du hello.py  
![alt text](https://github.com/Chatvolant/TP_Bus_et_reseaux/blob/main/code_identi10.png)

On ajoute des lignes de code à notre fichier hello.py comme indiqué dans l'énoncé du TP

![alt text](https://github.com/Chatvolant/TP_Bus_et_reseaux/blob/main/code_identi11.png)

> Quel est le rôle du décorateur @app.route?  

Permet de créer des pages web dans le chemin spécifié  

Quel est le role du fragment <int:index>?
Pour afficher sur une page chaque caractère individuel, spécifié avec l'indice, de la chaine de caractères qu’on a  mis sur la page welcome  
![alt text](https://github.com/Chatvolant/TP_Bus_et_reseaux/blob/main/code_identi12.png)

#### Première page REST
#### Réponse JSON
#### 1re solution
Avec firefox:  
![alt text](https://github.com/Chatvolant/TP_Bus_et_reseaux/blob/main/code_identi13.png)




