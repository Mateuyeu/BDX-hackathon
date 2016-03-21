# Hackathon Abilympics

- [Hackathon Abilympics](#)
	- [Presentation My Human Kit](#)
	- [Objectifs du hackathon](#)
- [Guide de demarrage](# Guide de demarrage)
	- [Creer un compte github](#)
	- [installer git](#)
		- [Mac](#)
- [Outils hardware et software](#)
	- [Rotonde](#)
	- [Main openbionics](#)
	- [Myoware](#)
	- [Piezo](#)
	- [Accelerometre](#)
	- [Force resistive sensor](#)
	- [Leds neopixel](#)
	- [Gyroscope](#)
	- [Temperature sensor](#)



## Presentation My Human Kit



## Objectifs du hackathon

Vous avez à disposition le Dev kit Bionico, une prothèse de main équipé d'un raspberryPI.
Il va vous permettre de facilement:

- controler les doigts de la main
- recevoir les évènements de contrôle par myo ou myoware
- travailler à plusieurs sur le même bras
- et bien sûr, ajouter des features pour Bionico:)

# Guide de demarrage

Pondre du code c'est bien, pouvoir l'ouvrir efficacement aux autres, c'est mieux:)

À la fin de cette partie vous aurez un compte github, et vous saurez ce qu'il faut connaitre pour participer à projet un open source:
- forker un projet
- sauvegarder vos modifications
- créer une pull request

Si vous connaissez déjā tout ça, passez direct à [Outils hardware et software](#)

## Creer un compte github

Si vous ne possédez pas encore de compte github, créez en un ici --> https://github.com/join

Github est un service basé sur le système de versionnage Git. Il permet de facilement partager et contribuer à plusieurs sur un même projet de developpement.

## installer git

### OSX/Linux

Téléchargez la dernière version de Git sur : http://git-scm.com/downloads
Ouvrez le fichier ainsi téléchargé et suivez les instructions en laissant toutes les valeurs par défaut.

Lancez l’application “Terminal” que vous pouvez trouver dans le dossier 'Utilitaires' de vos Applications ou bien en faisant une recherche avec spotlight.

Ajouter votre nom à vos commits en tapant cette commande
```sh
git config --global user.name "YOUR GITHUB USERNAME"
```
Puis associer votre email (celui utilisé pour votre github)

```sh
git config --global user.email "YOUR EMAIL ADDRESS"
```
## Fork, Clone & Pull-request

Rendez vous sur la page du repository https://github.com/MHKit/BDX-hackathon
Ensuite, cliquez sur le bouton “fork” en haut à droite pour créer une copie du repository sur votre propre compte github.

Une fois le fork terminé, le repository existe sous votre compte avec l’url https://github.com/TonUsername/BDX-hackathon

Pour le télécharger sur votre ordinateur, ouvrez un terminal et tapez
```sh
git clone https://github.com/TonUsername/BDX-hackathon.git
```
Ajouter votre nom aux contributeurs dans le fichier contributors.md à la racine du repo, puis en enregistrez vos modifications en réalisant un commit.
Pour cela, tapez cette commande à la racine du repository BDX-hackathon dans votre ordinateur

```sh
git add .
```
Puis
```sh
git commit -m “ajout contributeur“
```
et enfin
```sh
git push origin master
```

Vous devez alors spécifier votre login et password github.

Une fois la sync complete, vous pouvez vous rendre sur l'url de votre repository https://github.com/TonUsername/BDX-hackathon.git

Cliquez sur le bouton create a pull request

![Pull request button](http://i.imgur.com/q1mHtgB.png)

Vous pouvez maintenant comparer votre repository avec le repository de reference sur le compte MHKIT
![Compare changes](http://i.imgur.com/2yUIRDj.png) 

Cliquez sur le bouton create a pull request, ajoutez un titre et crez la pull request.
L'administrateur du compte github mhkit pourra alors valider votre ajout et l'intégrer dans le repository de référence.

## Bionico Dev Kit

Le Dev Kit peut être utilisé avec n'importe quel language, son utilisation ne nécessite pas d'interface en particulier,
le seul requis est d'être sur le même réseau wifi.

Connectez vous au wifi [NOM_DU_WIFI].

### principe de base

Toutes les fonctions du Dev Kit sont accessibles via une connection WebSocket. Il s'agit d'un standard introduit pour le web.
Une websocket est une connection persistente permettant à deux programmes de s'échanger des messages (un peu à la manière d'un port série d'arduino).
Tout les languages fournissent une librairie websocket.

Le développement d'une application pour le Dev Kit consiste donc à se connecter à sa websocket, et intéragir avec les différents périphériques qui y sont connectés, via des actions et des events.

![Compare changes](http://i.imgur.com/SI4LcJ2.png) 

### premier contact

Ce premier contact a pour but de montrer l'usage le plus basique du Dev Kit, aucune programmation requise.

Nous allons nous connecter au Dev Kit via une extension chrome qui va nous donner un accès direct à la websocket,
et nous permettre de voir ce qui vient de la websocket, et d'y écrire des messages.

Installer cette [chrome extension](https://chrome.google.com/webstore/detail/simple-websocket-client/pfdhoblngboilpfeibdedpjgfnlcodoo?hl=en).

A partir de cette extension vous pouvez vous connecter à la websocket tournant sur le Dev Kit et contrôlant la main.

Pour cela, connectez vous en indiquant l'adresse du Dev Kit
```
ws://bionicodevkit.local:4224/
```

Cliquez sur "Open", vous etes maintenant connecté à la main

Copiez coller ce json dans la console de l'extension

```js
{
  "type": "action",
  "payload": {
    "identifier": "HAND_FINGERS",
    "data": {
      "fingers": [
        {"position": 0, "speed": 1},
        {"position": 0, "speed": 1},
        {"position": 0, "speed": 1},
        {"position": 0, "speed": 1},
        {"position": 0, "speed": 1}
      ]
    }
  }
}
```

Le main s'ouvre.

Concrètement ce qui vient de se passer c'est que l'on vient d'envoyer un action `HAND_FINGERS`, à destination du module qui pilote les doigts.

![Compare changes](http://i.imgur.com/WyTvfwS.png) 

L'action `HAND_FINGERS` fournis une série de positions et de vitesses associées à chaque doigts (`position` et `speed` dans l'exemple).
Pour chaque doigt, du pouce à l'auriculaire, vous pouvez définir une position de 0 à 1 et une vitesse de 0 à 1.

Vous pouvez modifier le message, et commencer à expérimenter les comportements de la main en fonction des paramètres

```js
{
  "type": "action",
  "payload": {
    "identifier": "HAND_FINGERS",
    "data": {
      "fingers": [
        {"position": 0, "speed": 1},
        {"position": 1, "speed": 1},
        {"position": 0, "speed": 1},
        {"position": 0, "speed": 1},
        {"position": 0, "speed": 1}
      ]
    }
  }
}
```

Félicitation, vous contrôlez désormais la main :)

### Premier code

L'extension chrome est un outils pratique pour tester les fonctionnalités présentes.

Mais la websocket permet aussi un usage par code, et preésente l'avantage de ne pas forcer l'utilisation d'un language plutot qu'un autre.

#### Javascript

Le Dev Kit fournis une librairie permettant de faciliter son usage en Javascript, c'est pourquoi à ce stade du projet c'est le language conseillé.

Il est neécessaire d'avoir [installé nodeJS sur son ordinateur pour commencer](https://nodejs.org/en/download/)

L'idée de ce premier projet est de controller la main en utilisant le myo.

Commencez par installer la librairie facilitant l'usage du Dev Kit:



```sh
npm install --save HackerLoop/rotonde-client.js
```

Créez un fichier `index.js` et copiez collez le contenu suivant:

```js

'use strict'

const _ = require('lodash');

const client = require('rotonde-client/node/rotonde-client')('ws://bionicodevkit.local:4224');

client.onReady(() => {
  console.log('Connected');
});

client.connect();

```

Lancez le script avec:

```sh
node index.js
```

normalement il sera écrit:

```sh
$ node index.js
Connected
```

L'idée maintenant est de recevoir les évènements provenant du myo, ils nous indiqueront la gesture detectée par les capteurs musculaires, et nous les transmets via un évènement nommé `MYO_POSE_EDGE`.

![Compare changes](http://i.imgur.com/aVABc1o.png)

Grâce à la librairie Javascript, on peut facilement s'inscrire à un évènement:

```js

'use strict'

const _ = require('lodash');

const client = require('rotonde-client/node/rotonde-client')('ws://bionicodevkit.local:4224');

// ===================
// Code pour la reception d'un evenement MYO_POSE_EDGE

client.eventHandlers.attach('MYO_POSE_EDGE', (event) => {
  console.log(event.identifier);
  
  // Inserer ici le code de control de la main
});

// ===================

client.onReady(() => {
  console.log('Connected');
});

client.connect();

```

Le paramètre `event` fournis lors de la reception d'un `MYO_POSE_EDGE`, est sous la forme:

```js

{
  "identifier": "MYO_POSE_EDGE",
  "data": {
    "pose": "", // Nom de la pose
    "edge": "", // Indique si c'est le début ou la fin de la pose
  }
}

```

On veut commencer par un usage simple, si la pose est `wave_left`, on ferme la main, si la pose est `wave_right`, on ouvre la main.

```js

client.eventHandlers.attach('MYO_POSE_EDGE', (event) => {
  console.log(event.identifier);
  
  // Inserer ici le code de control de la main
  if (event.data.pose == 'wave_right') {
    client.sendAction('HAND_FINGERS', { // même structure que le champs data du paquet envoyé via l'extension chrome
      "fingers": [
        {"position": 0, "speed": 1},
        {"position": 0, "speed": 1},
        {"position": 0, "speed": 1},
        {"position": 0, "speed": 1},
        {"position": 0, "speed": 1}
      ]
    });
  } else {
    client.sendAction('HAND_FINGERS', { // comme le cas précédent, sauf que les positions sont à 1
      "fingers": [
        {"position": 1, "speed": 1},
        {"position": 1, "speed": 1},
        {"position": 1, "speed": 1},
        {"position": 1, "speed": 1},
        {"position": 1, "speed": 1}
      ]
    });
  }
});

```

Bien sûr c'est le strict minimum, par exemple on pourrait ajouter un capteur de contact sur les doigt, et detecter quand la main est assez serrée sur un objet.

#### Python

# Outils hardware et software

## MHKit hand dev kit
### Description
https://github.com/MHKit/bionicohand-firmware
### 

## Main openbionics
### Description

![Ada](http://static1.squarespace.com/static/56376cfde4b078ea32822fff/56377acde4b04be2960adf9c/56c443d2ab48de876b5aea39/1457368833873/IMG_7479+%282000x1333%29.jpg?format=750w)

http://www.openbionics.com/shop/ada
The Ada Hand is a fully articulated robot hand from Open Bionics. This product is a robotic hand kit and comes as a kit of parts that can be assembled in around 1 hour using standard tools. The hand has 5 degrees of freedom (DOF) and can be controlled from a PC or MAC over USB connection. The Ada hand houses all of the actuators required to move the fingers as well as its own custom control printed circuit board (PCB). The PCB is  based around the ATMEGA2560 microcontroller and can be programmed using the Arduino programming environment which will be familiar to many developers.

### Documentation
Assembly guide http://www.openbionics.com/obtutorials/ada-v1-assembly

## Myo
### Description

![](http://tr1.cbsistatic.com/hub/i/2014/08/19/5f0dd998-122c-4d90-92c2-766da175ea8a/front-view.jpg)

Le MYO est un bracelet qui permet de detecter les contractions musculaires de l'avant bras ainsi que sa position dans l'espace.


### Ressources

Rotonde Myo module
https://github.com/MHKit/rotonde-pyoconnect


## Myoware
### Description

![](https://a.pololu-files.com/picture/0J6842.250.jpg?079ca2904c5d27f9e41f71bbb3edd9a4)

This sensor uses EMG (electromyography) to sense the electrical activity of your muscles. It then converts that into a varying voltage that can be read on the analog input pin of any microcontroller.

### Documentation
https://learn.adafruit.com/getting-started-with-myoware-muscle-sensor/about-emg

## Piezo
### Description

![](https://cdn-shop.adafruit.com/1200x900/1739-00.jpg)

Piezo elements convert vibration to voltage or voltage to vibration. That means you can use this as a buzzer for making beeps, tones and alerts AND you can use it as a sensor, to detect fast movements like knocks. You can also use it under a drum pad to make a drum/crash sensor

### Documentation
https://www.adafruit.com/products/1739
https://www.arduino.cc/en/Tutorial/Knock

## Accelerometre
### Description

![](https://learn.adafruit.com/system/assets/assets/000/002/469/original/sensors_ADXL335_LRG.jpg?1396783433)

An accelerometer is a device that measures proper acceleration ("g-force"). Proper acceleration is not the same as coordinate acceleration (rate of change of velocity). For example, an accelerometer at rest on the surface of the Earth will measure an acceleration g= 9.81 m/s2 straight upwards. By contrast, accelerometers in free fall (falling toward the center of the Earth at a rate of about 9.81 m/s2) will measure zero.

### Documentation
https://learn.adafruit.com/adafruit-analog-accelerometer-breakouts

## Force resistive sensor
### Description

![](https://learn.adafruit.com/system/assets/assets/000/000/427/original/force___flex_402FSR_large.jpg?1396762936)

FSRs are sensors that allow you to detect physical pressure, squeezing and weight. They are simple to use and low cost. This sensor is a Interlink model 402 FSR with 1/2 diameter sensing region.
FSR's are basically a resistor that changes its resistive value (in ohms Ω) depending on how much its pressed. These sensors are fairly low cost, and easy to use but they're rarely accurate. They also vary some from sensor to sensor perhaps 10%. So basically when you use FSR's you should only expect to get ranges of response. While FSRs can detect weight, they're a bad choice for detecting exactly how many pounds of weight are on them.

### Documentation
https://learn.adafruit.com/force-sensitive-resistor-fsr

## Leds neopixel
### Description

![](https://learn.adafruit.com/system/guides/images/000/000/350/medium800/glamour.jpg?1448301391)

The WS2812 Integrated Light Source — or NeoPixel in Adafruit parlance — is the latest advance in the quest for a simple, scalable and affordable full-color LED. Red, green and blue LEDs are integrated alongside a driver chip into a tiny surface-mount package controlled through a single wire. They can be used individually, chained into longer strings or assembled into still more interesting form-factors.

### Documentation
https://learn.adafruit.com/adafruit-neopixel-uberguide/overview

## Gyroscope
### Description

![](https://learn.adafruit.com/system/assets/assets/000/003/288/medium800/sensors_2012_12_30_IMG_1141-1024.jpg?1396794950)

A gyroscope is a type of sensor that can sense twisting and turning motions. Often paired with an accelerometer, you can use these to do 3D motion capture and inertial measurement (that is - you can tell how an object is moving!) As these sensors become more popular and easier to manufacture, the prices for them have dropped to the point where you can easily afford a triple-axis gyro! Only a decade ago, this space-tech sensor would have been hundreds of dollars.

### Documentation
https://learn.adafruit.com/adafruit-triple-axis-gyro-breakout

## Temperature sensor
### Description

![](https://learn.adafruit.com/system/assets/assets/000/000/470/medium800/temperature_TMP36_LRG.jpg?1396763327)

Wide range, low power temperature sensor outputs an analog voltage that is proportional to the ambient temperature. To use, connect pin 1 (left) to power (between 2.7 and 5.5V), pin 3 (right) to ground, and pin 2 to analog in on your microcontroller. The voltage out is 0V at -50°C and 1.75V at 125°C. You can easily calculate the temperature from the voltage in millivolts: Temp °C = 100*(reading in V) - 50
### Documentation
https://learn.adafruit.com/tmp36-temperature-sensor


