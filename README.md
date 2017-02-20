**arduino-mini-pro-low-power**
Instructions pour abaisser au maximum la consomation d'un arduino pro mini qui doit fonctionner sur pile,

 1. les outils
 2. la configurations
 3. les modifications

**les outils**
Voici la liste d'outils à avoir pour les modifications :

 

 - poste à souder
 - un programmateur **USB -> ISP AVR** 
 - un programmateur **USB -> UART** 
 - le logiciel de programmation arduino avec quelques librairies
 - du temps

**Etape 1**
Installer le logiciel arduino ide disponible [ici](https://www.arduino.cc/en/Main/Software), une fois installé suivez ce [tuto](https://github.com/joe-speedboat/Arduino-LowPower) pour installer les version des bootloaders modifié pour fonctionner en 1Mhz.

**Etape 2**
branchement du programmateur **USB -> ISP AVR** sur l'arduino pro mini :

VCC -> VCC
Reset -> Reset
GND -> GND
Mosi -> pin 11 de l'arduino
Miso -> pin 12 de l'arduino
SCK -> pin 13 de l'arduino

dans l'interface arduino rendez-vous dans outils et sélectionner les options suivantes :
**type de carte :** ProMini LowPower - atmega328p.
**processeur :** 1Mhz - BOD dis - int. clock (CKDIV8)
**programmateur :** USBtinyISP

Ensuite cliquez sur graver la séquence d'initialisation, attendez un moment et vous devriez voir le message **thank you !**. Voilà c'est tout...

Modification de l'arduino, il va faloir enlever pas mal de composants électronique pour qu'il consomme le moin possible de courant quand il est en veille ainsi qu'en fonctionnement. Ce que nous allons supprimer, Le régulateur de tension, les leds, les résistances des leds, le résonateur quartz, le bouton reset, un condensateur qui ne sera plus utile. De plus avec cette modification l'arduino gagne plus de 25% sur la hauteur des composants on passe de 4mm à 1.1mm de hauteur donc ultra fin.

**avant modification :**

![arduino pro mini avant modification](https://github.com/prophetmaster/arduino-mini-pro-low-power/blob/master/arduino_pro_mini.png)

**après modification :**

![arduino pro mini après modification](https://github.com/prophetmaster/arduino-mini-pro-low-power/blob/master/arduino_pro_modification.png)
