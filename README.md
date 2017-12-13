<!--

author:   Georg Jäger

email:    gjaeger@ovgu.de

version:  1.0.0

language: de_DE

narrator:  Deutsch Female

-->

# Einführung

Willkommen zurück im eLearning-System *eLab*.

--{{1}}--
In der letzten Aufgabe habt ihr bereits zwei wichtige Sensortypen (Distanzsensoren, IMU) kennengelernt. Während ihr mit Hilfe der Distanzsensoren die Umgebung des Roboters wahrnehmen könnt, erlaubt euch die IMU Bewegungen des Roboters selber festzustellen. 

--{{2}}--
Neben der IMU, wird vor allem aber auch die Odometrie genutzt, um die Ausführung von Bewegungsbefehlen eines Roboters zu überwachen. Daher wird das erste Ziel dieser Aufgabe sein, die Odometrie unseres Roboters in Betrieb zu nehmen.

--{{3}}--
Nachdem wir nun alle relevanten Sensoren und Aktoren unseres Roboters auslesen bzw. ansteuern können, nutzen wir diese Möglichkeiten zur Umsetzung einer intelligenten Bewegungsstrategie. 

--{{4}}--
Ziel wird es sein, sowohl eine Kollisionsvermeidung, als auch einen [Wall Follower](https://en.wikipedia.org/wiki/Maze_solving_algorithm) zu implementieren. Während die Kollisionsvermeidung sicherstellt, dass unser Roboter nicht frontal mit einem Objekt kollidiert, erlaubt die Wandverfolgung unserem Roboter durch ein Labyrinth zu finden (sofern schon beim Eingang des Labyrinths der Algorithmus begonnen wird und das Labyrinth "einfach zusammenhängend" ist).


## Themen und Ziele

--{{1}}--
Das Ziel dieser Aufgabe ist einen *Wall Follower* zu implementieren. Da dieser von unserem Roboter verlangt, nicht nur seine Umgebung wahrzunehmen, sondern auch seine Bewegungen zu planen und korrekt auszuführen, muss zunächst ein weitere Sensor, die Odometrie, in Betrieb genommen werden. Da sie auf der Abhandlung von Interrupts basiert, bilden diese einen Schwerpunkt der Aufgabe.

--{{2}}--
Mit Hilfe der Odometrie wird es uns ermöglicht, zu überprüfen, ob unser Roboter auch unsere Steuerungskommandos so ausführt, wie wir sie geplant haben. Wie uns auffallen wird, ist das nicht immer der Fall, sodass wir eine weiter Komponente zur Motoransteuerung hinzufügen müssen: eine Regelung. 

--{{3}}--
Zwar gibt es eine Vielzahl von Möglichkeiten Regelung, weit verbreitet sind allerdings die PID-Regler. Daher werden wir uns auf diese beschränken.

--{{4}}--
Letztlich bieten uns die verschiedenen Komponenten unseres Roboters nun die Möglichkeit eine intelligente Bewegungsstrategie zu implementieren. Daher bildet das Thema des *Motion Planning* den letzten Schwerpunkt dieser Aufgabe.


**Themen:**

* Interrupts
* Odometrie
* PID Regler
* Motion Planning


**Ziel(e):**

* Implementierung einer Interrupt-basierten Odometrie
* Geschwindigkeitsregelung der Motoren mit Hilfe von PID Reglern
* Implementierung einer Bewegungsstragtegie zur Wandverfolgung.


## Weitere Informationen

--{{1}}--
Da zur korrekten Implementierung der Odometrie die Konfiguration und Nutzung von Interrupts benötigt wird, haben wir euch, neben der Vorlesung, weitere einführende Referenzen aufgelistet. 

--{{2}}--
Darüber hinaus könnt ihr Informationen sowohl zur Odometrie als auch zu Rotationsencoder finden. 

--{{3}}--
Wie schon erwähnt sollen die Daten der Odometrie zur Geschwindigkeitsregelung der Motoren genutzt werden. Daher haben wir auch einführende Artikel zu PID Reglern aufgelistet.

--{{4}}--
Letztlich sind die bisher besprochenen Komponenten unseres Roboters lediglich Voraussetzungen zur Umsetzung von abstrakten Bewegungsstrategien und Verhaltensmustern. Da diese allerdings nicht in dieser Veranstaltung behandelt werden können, wollen wir euch zumindest Ansatzpunkte für weitere Recherchen geben. Zum einen bietet das (allgemeine) Gebiet der autonomen Roboter vielseitige Herausforderungen die zunehmend durch Algorithmen und Methodiken der künstlichen Intelligenz gelöst werden. Zum anderen bilden aber vor allem die Bereiche des *Simultaneous localization and mapping (SLAM)* und des *Motion Planning* konkrete Bereiche der Robotik, die Grundlegend für die Autonomie von Robotern sind.

--{{5}}--
Wie immer findet ihr hier aber auch die Datenblätter der Komponenten unserer Robotterplattform.

**Interrupts:**

* [Mikrocontroller.net](https://www.mikrocontroller.net/articles/Interrupt)
* [Übersicht](https://en.wikipedia.org/wiki/Interrupt)

**Odometrie:**

* [Odometrie](https://en.wikipedia.org/wiki/Odometry)
* [Rotationsencoder](https://en.wikipedia.org/wiki/Rotary_encoder)

**PID-Controller:**

* [Einfache Einführung](https://www.csimn.com/CSI_pages/PIDforDummies.html)
* [Überblick](https://en.wikipedia.org/wiki/PID_controller)
* Einführende Erklärungen:

  !![PIDIntroduction](https://www.youtube.com/embed/UR0hOmjaHp0)<!--
    width: 560px;
    height: 315px;
  -->
  
**Robotik:**

* [Allgemeine Einführung in das Gebiet der autonomen Roboter](https://github.com/correll/Introduction-to-Autonomous-Robots/releases/download/v1.9/book.pdf) 
  
**Simultaneous localization and mapping (SLAM):**

* [Übersicht bei Wikipedia](https://en.wikipedia.org/wiki/Simultaneous_localization_and_mapping)
* [Vorlesung zu SLAM (YouTube)](https://www.youtube.com/watch?v=U6vr3iNrwRA&list=PLgnQpQtFTOGQrZ4O5QzbIHgl3b1JHimN_)
* Visualisierung von SLAM:

  !![SimplePresentationSLAM](https://www.youtube.com/embed/SeNLUW79_-c)<!--
    width: 560px;
    height: 315px;
  -->

**Motion Planning:**

* [Vorlesungsfolien](https://ipvs.informatik.uni-stuttgart.de/mlr/marc/teaching/14-Robotics/04-pathPlanning.pdf)
* Erklärungen zu Motion Planning in relation zu SLAM:

  !![Visualisierungsvideo](https://www.youtube.com/embed/qXZt-B7iUyw?list=PLKwqbLx4DLDGkT0Tc6yiqsjDmH395hgvF)<!--
    width: 560px;
    height: 315px;
  -->

**PKeS:**

* [Datenblatt IMU (MPU-9255)](https://stanford.edu/class/ee267/misc/MPU-9255-Datasheet.pdf)
* [Datenblatt IMU (MPU-9255) Register Map](https://stanford.edu/class/ee267/misc/MPU-9255-Register-Map.pdf)
* [Datenblatt infrarot Distanzsensor Sharp GP2Y0A41SK0F](http://sharp-world.com/products/device/lineup/data/pdf/datasheet/gp2y0a41sk_e.pdf)
* [Datenblatt infrarot Distanzsensor Sharp GP2Y0A02YK0F]( http://sharp-world.com/products/device/lineup/data/pdf/datasheet/gp2y0a02yk_e.pdf)
* [Datenblatt Motortreiber](http://www.st.com/content/ccc/resource/technical/document/datasheet/59/d0/ce/41/56/bb/4b/10/DM00034699.pdf/files/DM00034699.pdf/jcr:content/translations/en.DM00034699.pdf)
* [Schaltbelegungsplan](https://github.com/liaScript/PKeS0/blob/master/materials/robubot_stud.pdf?raw=true)
* [Arduinoview](https://github.com/fesselk/Arduinoview/blob/master/doc/Documetation.md)
* [Datenblatt des AVR ATmega32U4](http://www.atmel.com/Images/Atmel-7766-8-bit-AVR-ATmega16U4-32U4_Datasheet.pdf)
* [Interrupt Reference in der AVR Libc](http://www.atmel.com/webdoc/avrlibcreferencemanual/group__avr__interrupts.html)


# Aufgabe 4

--{{1}}--
Wie schon beschrieben, besteht die erste Teilaufgabe darin, die Odometrie des Roboters auszulesen. Dazu müsst ihr vor allem die Möglichkeiten der externen Interrupts nutzen.

--{{2}}--
Basierend auf den Daten könnt ihr dann eine Geschwindigkeitsregelung für die Motoren (links und rechts) implementieren. 

--{{3}}--
Nachdem wir dann die Umgebung unseres Roboters wahrnehmen können und darauf reagieren können, sollte das erste Ziel unserer Bewegungsstrategie sein, eine Kollisionsvermeidung zu implementieren. So soll verhindert werden, dass unser Roboter mit einem Objekt kollidiert.

--{{4}}--
Da die Kollisionsvermeidung allerdings lediglich reaktiv ist, wollen wir darüber hinaus auch eine aktive Bewegungsstrategie implementieren. In unserem Fall soll der Roboter eine Wandverfolgung durchführen.


**Hinweis:**

**Verwendet bei der Bearbeitung der Aufgabe keine Funktionen aus der Arduino-Bibliothek. Lediglich die Funktionen der `Serial`-Klasse zur Ansteuerung der seriellen Schnittstelle, der Funktion `millis()` zur einfachen Zeitmessung, sowie der Funktionen aus `Wire.h` für die I^2^C Kommunikation können genutzt werden.**


**Teilaufgaben**

* *4.1:* Implementierung der Odometrie.
* *4.2:* PID-Regelung der Geschwindigkeit der Motoren.
* *4.3:* Kollisionsvermeidung auf Basis der IR-Distanzsensoren.
* *4.4:* Wandverfolgung.

Die Aufgabe ist bis zu der Woche vom **22.01. - 26.01.2018** vorzubereiten.


## Aufgabe 4.1

--{{1}}--
Das Ziel dieser Aufgabe ist es, die Odometrie an unserem Roboter in Betrieb zu nehmen. Dazu müsst ihr zunächst die entsprechenden Interrupts konfigurieren und Interruptroutinen schreiben.

--{{2}}--
Ausgabe der Odometrie soll die aktuelle Geschwindigkeit des jeweiligen Motors sein.


**Ziel:**
Implementierung der Odometrie.

**Teilschritte:**

1. Interruptroutinen schreiben
2. Interrupts konfigurieren.
3. Interruptroutinen eintragen.

## Aufgabe 4.2

--{{1}}--
Die Odometrie, die wir in der vorhergehenden Aufgabe implementiert haben, erlaubt es uns nun, die Geschwindigkeit der Motoren/Räder zu regeln. Dazu sollt ihr in dieser Teilaufgabe einen PID-Regler implementieren und parametrisieren.


**Ziel:**
Regelt die Drehgeschwindigkeit der Motoren mit Hilfe von PID Reglern.

**Teilschritte:**

1. Implementierung eines PID-Reglers.
2. Erweiterung der Motor-API.
3. Parametrisierung des Reglers für beide Motoren.

## Aufgabe 4.3

--{{1}}--
Mit der Regelungsstrategie unserer Motoren können wir nun eine intelligente Bewegungsstrategie implementieren. Da dies bedeutet, dass unser Roboter autonom die Geschwindigkeitsvorgaben für die Motoren bestimmen wird, müssen wir dabei auch die Sicherheit des Systems beachten. Dies bedeutet zunächst, dass wir Kollisionen unseres Roboters mit Objekten in der Umgebung vermeiden sollten. Daher ist das Ziel dieser Teilaufgabe, eine Kollisionsvermeidung auf Basis der IR-Distanzsensoren zu implementieren.


**Ziel:**
Nutzt die IR-Distanzsensoren um eine Kollisionsvermeidung zu implementieren.

**Teilschritte:**

1. Implementiert eine Schutzfunktion zur Vermeidung von Kollisionen.
2. Legt empirisch einen minimalen Distanzwert für die Kollisionsvermeidung fest.

## Aufgabe 4.4

--{{1}}--
Nachdem unsere Sensoren und Aktoren, sowie eine einfache Kollisionsvermeidung einsatzbereit sind, können wir diese Komponenten nutzen um eine intelligentere Bewegungsstrategie zu implementieren: eine Wandverfolgung.

--{{2}}--
Ein Problem beim Lösen dieser Aufgabe ist, dass unsere Distanzsensoren lediglich an Front unseres Roboters montiert sind. Da wir dementsprechend nicht direkt unsere aktuelle, seitliche Distanz zur Wand messen können, müsst ihr den Roboter in bestimmten Abständen anhalten und erneut orientieren. Die Parametrisierung dieses Vorgehens hängt von den Ungenauigkeiten eurer Sensorik und Aktorik ab. Ermittelt diese Werte daher empirisch.


**Ziel:**
Implementiert eine Wandverfolgung.

**Teilschritte:**

1. Implementiert eine initiale Lokalisierung: "Wo ist die nächste Wand?"
2. Plant eine Bewegung zur Wand, sodass ihr in einer gewissen Distanz *d* neben der Wand steht.
3. Beginnt die Wandverfolgung.

# Quizze

--{{1}}--
Wie auch in der letzten Aufgabe haben wir noch ein paar kurze Fragen an euch.

## Interrupts

**Welche Kategorien von Interrupts können allgemein unterschieden werden?**

  [[ ]] Gleitende Interrupts
  [[X]] Maskierbare Interrupts
  [[X]] nicht-maskierbare Interrupts
  [[X]] Inter-Prozess Interrupts 
  [[ ]] Asynchrone Interrupts
  [[ ]] Synchrone Interrupts
  [[X]] Software Interrupts
  [[X]] Spurious Interrupts

**Was versteht man unter *nested interrupts*?**

  [( )] Programmabläufe, die lediglich aus Interrupts bestehen.
  [(X)] Interrupts, die während der Abarbeitung eines vorhergehenden Interrupts bearbeitet werden.
  [( )] Interrupts, die weitere Interrupts auslösen.
  [( )] Programmabläufe, die Interrupts aus Sicherheitsgründen verbieten.
        

**Welche Typen von Interrupts unterscheidet der AVR ATmega32U4?**

  [( )] Externe und interne Interrupts.
  [(X)] Interrupts mit und ohne Interrupt Flag.
  [( )] Kurze und Lange Interrupts.
  
**Was bezeichnet die *Interrupt Response Time*?**

  [( )] Die Abarbeitungsdauer eines Interrupts.
  [(X)] Die Zeit gemessen von dem Auftreten eines Interrupt-Signals bis zum Beginn der Abarbeitung der Interruptroutine.
  [( )] Die Zeit gemessen von dem Sprung aus dem Programmablauf bis zum Sprung zurück in den Programmablauf.

**Was ist die *Interrupt Response Time* des AVR ATmega32U4?**

  [(X)] 5 Clock Cylces
  [( )] 10 Clock Cylces
  [( )] 15 Clock Cylces

## Odometrie

**Welchen Vorteil hat ein Absolutwertgeben (engl. *absolute encoder*) gegenüber einem Inkrementalgeber (engl. *incremental encoder*)?**

  [(X)] Er ermöglicht die direkte Schätzung der Position eines Motors/Rades.
  [( )] Er kann bei höheren Frequenzen betrieben werden.
  [( )] Er hat einen einfacheren Aufbau.

## PID Regler

**Wofür steht PID im Namen des PID Reglers?**

  [( )] Passing, Integrating, Deviating 
  [(X)] Proportional, Integral, Derivative
  [( )] Proportional, Interfacing, Deviating 
  
**Wozu wird der I-Anteil in einem PID Regler benötigt?**

  [(X)] Um einen durch sinkende Fehlerwerte verbleibenden Regelfehler auszugleichen.
  [( )] Um das Verhalten des geregelten Systems auszugleichen.
  [( )] Um Fehler des Sensors auszugleichen.

## Bewegungsstrategien

**Wofür steht die Abkürzung SLAM?**

  [( )] Self-centered localization and motion
  [( )] Similarity based labeling and motion
  [( )] Simultaneous localization and motion
  [(X)] Simultaneous localization and mapping

