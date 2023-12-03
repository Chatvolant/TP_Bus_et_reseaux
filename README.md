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

### 2.3. Communication I²C
#### Communication avec le BMP280


## TP n°2 - TP2 - Interfaçage STM32 - Raspberry

## TP n°3 - Interface REST
### 4.1. Installation du serveur Python


