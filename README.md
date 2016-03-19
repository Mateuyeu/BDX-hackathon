# Hackathon Abilympics

- [Hackathon Abilympics](#)
	- [Presentation My Human Kit](#)
	- [Objectifs du hackathon](#)
- [Guide de demarrage](#)
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

# Guide de demarrage

## Creer un compte github

Si vous ne possédez pas encore de compte github, créez en un ici --> https://github.com/join

Github est un service basé sur le système de versionnage Git. Il permet de facilement partager et contribuer à plusieurs sur un même projet de developpement.

## installer git

### OSX/Linux

Téléchargez la dernière version de Git sur : http://git-scm.com/downloads
Ouvrez le fichier ainsi téléchargé et suivez les instructions en laissant toutes les valeurs par défaut.

Lancez l’application “Terminal” que vous pouvez trouver dans le dossier 'Utilitaires' de vos Applications ou bien en faisant une recherche avec spotlight.

Ajouter votre nom à vos commits en tapant cette commande
```
git config --global user.name "YOUR GITHUB USERNAME"
```
Puis associer votre email (celui utilisé pour votre github)

```
git config --global user.email "YOUR EMAIL ADDRESS"
```
## Fork, Clone & Pull-request

Rendez vous sur la page du repository https://github.com/MHKit/BDX-hackathon
Ensuite, cliquez sur le bouton “fork” en haut à droite pour créer une copie du repository sur votre propre compte github.

Une fois le fork terminé, le repository existe sous votre compte avec l’url https://github.com/TonUsername/BDX-hackathon

Pour le télécharger sur votre ordinateur, ouvrez un terminal et tapez
```
git clone https://github.com/TonUsername/BDX-hackathon.git
```
Ajouter votre nom aux contributeurs dans le fichier contributors.md à la racine du repo, puis en enregistrez vos modifications en réalisant un commit.
Pour cela, tapez cette commande à la racine du repository BDX-hackathon dans votre ordinateur

```
git add .
```
Puis
```
git commit -m “ajout contributeur“
```
et enfin
```
git push origin master
```

Vous devez alors spécifier votre login et password github.

Une fois la sync complete, vous pouvez vous rendre sur l'url de votre repository https://github.com/TonUsername/BDX-hackathon.git

Cliquez sur le bouton create a pull request
(http://imgur.com/q1mHtgB)



# Outils hardware et software

## MHKit hand dev kit
### Description
https://github.com/MHKit/bionicohand-firmware
### 

## Main openbionics
### Description
http://www.openbionics.com/shop/ada
The Ada Hand is a fully articulated robot hand from Open Bionics. This product is a robotic hand kit and comes as a kit of parts that can be assembled in around 1 hour using standard tools. The hand has 5 degrees of freedom (DOF) and can be controlled from a PC or MAC over USB connection. The Ada hand houses all of the actuators required to move the fingers as well as its own custom control printed circuit board (PCB). The PCB is  based around the ATMEGA2560 microcontroller and can be programmed using the Arduino programming environment which will be familiar to many developers.

### Documentation
Assembly guide http://www.openbionics.com/obtutorials/ada-v1-assembly

## Myo
### Description
Le MYO est un bracelet qui permet de detecter les contractions musculaires de l'avant bras ainsi que sa position dans l'espace.


### Ressources

Rotonde Myo module
https://github.com/MHKit/rotonde-pyoconnect


## Myoware
### Description
This sensor uses EMG (electromyography) to sense the electrical activity of your muscles. It then converts that into a varying voltage that can be read on the analog input pin of any microcontroller.

### Documentation
https://learn.adafruit.com/getting-started-with-myoware-muscle-sensor/about-emg

## Piezo
### Description
Piezo elements convert vibration to voltage or voltage to vibration. That means you can use this as a buzzer for making beeps, tones and alerts AND you can use it as a sensor, to detect fast movements like knocks. You can also use it under a drum pad to make a drum/crash sensor

### Documentation
https://www.adafruit.com/products/1739
https://www.arduino.cc/en/Tutorial/Knock

## Accelerometre
### Description
An accelerometer is a device that measures proper acceleration ("g-force"). Proper acceleration is not the same as coordinate acceleration (rate of change of velocity). For example, an accelerometer at rest on the surface of the Earth will measure an acceleration g= 9.81 m/s2 straight upwards. By contrast, accelerometers in free fall (falling toward the center of the Earth at a rate of about 9.81 m/s2) will measure zero.

### Documentation
https://learn.adafruit.com/adafruit-analog-accelerometer-breakouts

## Force resistive sensor
### Description
FSRs are sensors that allow you to detect physical pressure, squeezing and weight. They are simple to use and low cost. This sensor is a Interlink model 402 FSR with 1/2 diameter sensing region.
FSR's are basically a resistor that changes its resistive value (in ohms Ω) depending on how much its pressed. These sensors are fairly low cost, and easy to use but they're rarely accurate. They also vary some from sensor to sensor perhaps 10%. So basically when you use FSR's you should only expect to get ranges of response. While FSRs can detect weight, they're a bad choice for detecting exactly how many pounds of weight are on them.

### Documentation
https://learn.adafruit.com/force-sensitive-resistor-fsr

## Leds neopixel
### Description
The WS2812 Integrated Light Source — or NeoPixel in Adafruit parlance — is the latest advance in the quest for a simple, scalable and affordable full-color LED. Red, green and blue LEDs are integrated alongside a driver chip into a tiny surface-mount package controlled through a single wire. They can be used individually, chained into longer strings or assembled into still more interesting form-factors.

### Documentation
https://learn.adafruit.com/adafruit-neopixel-uberguide/overview

## Gyroscope
### Description
A gyroscope is a type of sensor that can sense twisting and turning motions. Often paired with an accelerometer, you can use these to do 3D motion capture and inertial measurement (that is - you can tell how an object is moving!) As these sensors become more popular and easier to manufacture, the prices for them have dropped to the point where you can easily afford a triple-axis gyro! Only a decade ago, this space-tech sensor would have been hundreds of dollars.

### Documentation
https://learn.adafruit.com/adafruit-triple-axis-gyro-breakout

## Temperature sensor
### Description
Wide range, low power temperature sensor outputs an analog voltage that is proportional to the ambient temperature. To use, connect pin 1 (left) to power (between 2.7 and 5.5V), pin 3 (right) to ground, and pin 2 to analog in on your microcontroller. The voltage out is 0V at -50°C and 1.75V at 125°C. You can easily calculate the temperature from the voltage in millivolts: Temp °C = 100*(reading in V) - 50
### Documentation
https://learn.adafruit.com/tmp36-temperature-sensor


