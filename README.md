# Ordnen-in-Natur-und-Sammlung

## Inhaltsverzeichnis
* [Kurzbeschreibung](#Kurzbeschreibung)
* [Hardware](#Hardware)
* [Installation](#Installation)
* [Verwendung](#Verwendung)
* [Lizenz](#Lizenz)
* [Credits](#Credits)
* [Förderhinweis](#Förderhinweis)

### Kurzbeschreibung:

Mit der Medienstation "Examiner" können Objekte, die mit einem RFID-Tag ausgestattet sind, untersucht werden. Dazu werden die Objekte, die sich in Schubladen befinden, auf einen RFID-Sensor gelegt. Der RFID-Sensor ist an einen Computer angeschlossen, der über einen Monitor und einen Touchscreen verfügt. Über den Touchscreen können Daten zum Objekt abgerufen werden. Interaktive Elemente werden auf dem Touchscreen angeboten, korrespondierende Inhalte werden auf den zweiten Monitor angezeigt. Bei den Objekten handelt es sich um transparente Kunstharzpucks, in die Tiere, Teile von Tieren oder Teile von Pflanzen eingegossen worden sind.

## Hardware

Die Medienstation ist ein kompakter Tisch, der alle Elemente in sich vereint. Fünf Schubladen beeinhalten insgesamt 33 Objekte. PC, Touchscreen, zweiter Bildschirm und RFID-Sensor sind integriert.

Der Aufbau und die Funktion der Anwendunge sind in diesem Video zu sehen:
https://vimeo.com/832694324

### Hardware-Voraussetzungen

- Die Software ist für zwei Bildschirme (Auflösung 1920 x 1080) entwicklt. Der erste Bildschirm ist dabei der Touchscreen

- Zum Einlesen der RFID-Tags wird ein RFID-Sensor benötigt

- Windows 10 Pro, NVIDIA GeForce RTX 3060 mit 12GB, AMD Ryzen 9 16x3950X, 32GB RAM

- Das Projekt kann ohne zweiten Bildschirm und RFID-Lesegerät in Unity simuliert werden

## Installation

### Unity-Projekt: OrderInNatureAndForrest_001

Der vollständige Quellcode des Unity Projektes kann bei Senckenberg Museum für Naturkunde Görlitz oder dem nhm Mainz angefragt werden.

Kontaktinformationen:
- Senckenberg Görlitz: post-gr@senckenberg.de
- nhm Mainz: naturhistorisches.museum@stadt.mainz.de

Das Unity-Projekt (Unity 2022.1.23f1) ist vollständig und enthält folgende Packages:

- TextMeshPro


## Verwendung:

### Zuordnung der RFID-Tags

Der Sensor ließt die RFID-Tags ein und gibt diese als Tastatur-Eingabe aus. Jedes RFID-Tag hat eine einzigartige Nummer, die als Zahlenfolge mit einem Return am Ende übergeben wird. Die Medienstation enthält Daten zu 34 Objekten.

Im Ordner "StreamingAssets" befindet sich eine Text-Datei, die wie folgt Zeilenweise aufgebaut ist:

1. Begriff für die Zuordnung
2. RFID-Tag ID
3. Referenz auf die zugehörige visuelle ID (jedes reale Objekt hat ein eigenes ID-Bild)

Diese Daten werden über Doppelpunkte getrennt und sehen dann pro Zeile so aus:

MeinSchlüsselbegriff:12341234:MeineVisuelleID

bzw. am lebenden Beispiel:

01_Trypocopris_vernalis:1747627:01A

### Simualtion des RFID-Sensors:

Ohne RFID-Lesegerät werden die 34 Objekte über zweistellige Zahlen+Enter aufgerufen.

01 + Return
02 + Return
03 + Return

...

33 + Return

Eine Ausnahmen im Datensatz ist die Nummer 04, hier gibt es:

04 + Return (weibliches Tier)
04m + Return (männliches Tier)

Um neue Tags einzupflegen, wird einfach eine Zeile mit Schlüsselbegriff, neuer RFID-ID und zugehöriger visueller ID angefügt.

In der Unity-Scene verwaltet das Objekt "RFID", welche Objekte in der Anwendung aufgerufen werden. In der Liste "Keywords" finden sich alle Keywords. Zu jedem Keyword gehört ein Game-Object, dass sich an gleicher Stelle in der Liste "RFID_TAGS" befindet. Beide Listen müssen die gleiche Anzahl von Einträgen haben und jeder Eintrag verweisst auf genau ein GameObject.

Die Zuordnung der visuellen IDs erfolgt über die beiden Listen "RFID_Keywords" (eine Liste mit allen Keywords die in der Datei RFID-TAGS.txt aufgerühft sind, mit Dopplungen) und der Lsite "VisualID_List" in der zu jedem Keyword die gefundene visuelle ID aufgelistet ist. Beide Listen sind gleich lang. Die eigentlichen visuellen IDs sind in der Liste "Visual IDs" hinterlegt.

### Simulation der beiden Monitore:

Um beide Monitore In Unity zu simulieren, werden zwei "Game"-Views verwendet.

- Oberer Monitor = Display 2
- Unterer Touchscreen = Display 1


## Lizenz:

Dieses Projekt steht unter der Lizenz CC BY 3.0 DE (https://creativecommons.org/licenses/by/3.0/de/)

## Credits:

Auftraggeber:
- Senckenberg Gesellschaft für Naturkunde (https://senckenberg.de)
- nhm Mainz (https://www.mainz.de/microsite/naturhistorisches-museum/)
- Entwicklung/Urheber: Lutz Westermann, .hapto GmbH (www.hapto.de, www.vimeo.com/hapto)

## Förderhinweis:

Diese Anwendungen sind Teil des Projektes museum4punkt0 - Digitale Strategien für das Museum der Zukunft, Teilprojekt "Grundwasser digital". Das Projekt museum4punkt0 wird gefördert durch die Beauftragte der Bundesregierung für Kultur und Medien aufgrund eines Beschlusses des Deutschen Bundestages.
Weitere Informationen: www.museum4punkt0.de

![alt text](https://github.com/museum4punkt0/media_storage/blob/2c46af6cb625a2560f39b01ecb8c4c360733811c/BKM_Fz_2017_Web_de.gif) ![alt text](https://github.com/museum4punkt0/media_storage/blob/e87f37973c3d91e2762d74d51bed81de5026e06e/BKM_Neustart_Kultur_Wortmarke_pos_RGB_RZ_web.jpg)

