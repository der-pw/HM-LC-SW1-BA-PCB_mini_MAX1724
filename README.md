# AskSin++ Batterieaktor mit MAX1724 Stepup

**HM-LC-SW1-BA-PCB_mini mit einer Ausgangsspannung von 3,3V, bspw. für Mini-Lichterketten.**

[![License: CC BY-NC-SA 4.0](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc-sa/4.0/)
[![GitHub issues](https://img.shields.io/github/issues/der-pw/HM-LC-Sw1-Pl-DN-R1_S26.svg)](https://github.com/der-pw/HM-LC-Sw1-Pl-DN-R1_S26/issues)

![Aktor](https://raw.githubusercontent.com/der-pw/HM-LC-SW1-BA-PCB_mini_MAX1724/master/files/actor.jpg)

* [Sketch](./Sketch/HM-LC-SW1-BA-PCB_extBatt.ino)
* [Gehäuse](./Case/)
* [Teileliste](./HM-LC-SW1-BA-PCB_mini_MAX1724-Parts.csv)

Der Ausgang wird über einen N-Channel MOSFET geschaltet und kann, je nach Versorgungsspannung, mit bis zu 150mA belastet werden.
Für kleine Mini-Lichterketten ist das ausreichend.
(Beispiel: eine Mini-Lichterkette aus den üblichen Grabbelschütten, mit 10 LEDs und 10Ohm Vorwiderstand benötigt ca 35mA).

**Batterie-Messung:**  
Desweiteren kann die Batteriespannung vor dem Stepup mittels Spannungsteiler gemessen werden. 
Ein angepasster Sketch liegt bei. Vielen Dank an Jérôme für die Unterstützung und das Aufzeigen, wie "einfach" doch die Batterieklasse ist. ;-)

Da in der CCU, bei diesem Aktor, die Batteriemeldung nur im Bereich von 5-15V auslöst, wird im Sketch unter ...
```
uint8_t lowbat = getList0().lowBatLimit() / 5; //factor 5 to get low bat
```
... die eingestellte Batterieschwelle durch 5 geteilt.
In der CCU müssen also die Spannungwerte mit "x5" angegeben werden.
Beispiel: Batteriemeldung bei 2,1V Versorgungsspannung. Heißt 2,1V x 5 = 10,5V. Es müssen demnach 10,5V in der CCU eingestellt werden.
Die Werte variieren je nach verwendetem Batterie.- Akkutyp und müssen "für sich selbst" gefunden werden.


## PCB

Das Platinendesign basiert auf dem [HMSensor](https://github.com/pa-pa/HMSensor/) Projekt.
Weitere Infos zur HMSensor gibt es auf [asksinpp.de](https://asksinpp.de/Projekte/psi/HMSensor/).

![PCB top](https://raw.githubusercontent.com/der-pw/HM-LC-SW1-BA-PCB_mini_MAX1724/master/files/top.jpg)
![PCB bottm](https://raw.githubusercontent.com/der-pw/HM-LC-SW1-BA-PCB_mini_MAX1724/master/files/bottom.jpg)


## FAQ

* `fatal error: ResetOnBoot.h: No such file or directory`  
  Es ist die aktuellste Version (ggf. master-Branch) der [AskSinPP](https://github.com/pa-pa/AskSinPP) Library zu verwenden
