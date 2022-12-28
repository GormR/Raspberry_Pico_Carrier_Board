(für Deutsch bitte runterscrollen)

# Raspberry Pico RP2040 Carrier Board for AC and Measurment Applications


# Raspberry Pico RP2040 Trägerplatine für Netz- und Messanwendungen
Die Raspberry-Pico-Plattform bietet ein zukunfsweisendes Programmierkonzept und ganz viel Funktionalität - neuerdings auch mit WiFi. Für Steuerungs- und Überwachungsaufgaben fehlt mir aber bisher ein geeignetes Trägerboard, mit dem man einige 230V-Leitungen überwachen und auch schalten kann. Außerdem fehlen Anschlüsse für eine größere Anzahl von Temperatursensoren. Das alles zusammen mit zeitgemäßen Push-In-Anschlüssen ist nun auf dem Board, das in ein Panasonic-Viko-Gehäuse passt.

![pic](3D.png?raw=true)

Um die gewünschte Anzahl von I/Os realisieren zu können, werden die digitalen (Temperatur-)Eingänge, sowie die Netzspannungseingänge und Relais über 8:1-Multiplexer, die gemeinsam über GP10(MSB)..GP12(LSB) gesteuert werden, geschaltet. 

Pico     I/O
------+-------------------
GP0      Temp1..8
GP1      Temp9..16
GP2      ACin0..7
GP3      Rel0..7

An den PushIn-Klemmen der Temperatureingänge liegt auch die 3.3V-Betriebsspannung an, so dass direkt ein digitaler Temperatursensor angeschlossen werden kann. Die Anschlüsse lassen sich natürlich auch als allgemeine Digitaleingänge nutzen.

Die Netzspannungseingänge "ACin7..0"" sind für 230V AC ausgelegt. Sie benötigen einen angeschlossenen Neutralleiter an der Netzspannungsklemme "AC-Mains". Die Relaisausgänge müssen noch passend über Drähte auf der Unterseite der Leiterplatte verdrahtet werden, um alle Möglichkeiten offen zu lassen. Klemmen sind z. B. für 8 230V-AC-Verbraucher vorhanden (jeweils L' und N). Ein Relais wird ein- oder ausgeschaltet, wenn bei entsprechender Multiplexereinstellung eine 1 oder 0 an GP3 geschrieben wird und der Pin als Ausgang deklariert ist. Ist GP3 ein Eingang, kann der Ausgangsstatus zurückgelesen werden. Voraussetzung ist ein high an GP9 ("Relay enable"). Ein low oder tristate an GP0 setzt alle Ausgänge zurück.

Alle weiteren Pico-Signale sind direkt über eine Schutzbeschaltung an Klemmblöcke geführt, die einzeln über eine mit Jumpern zwischen 3.3V und 5V umschaltbaren Versorgungsspannung verfügen.

Pico     I/O
------+-------------------
GP26      I/O1 (auch analog)
GP27      I/O2 (auch analog)
GP28      I/O3 (auch analog)
GP22      I/O4
GP19      I/O5
GP18      I/O6
GP17      I/O7
GP16      I/O8

GP20 und GP21 sind als I²C-Schnittstelle auf einem QUIIC-Stecker geführt.

GP5 und GP13 sind optokopplerisolierte Eingänge (Opto0 und Opto1). Dort kann eine Gleichspannung zwischen 3.3V und 24V angelegt werden.

GP14 und GP15 sind optokopplerisolierte Ausgänge (Opto2 und Opto3 - aktiv-low). Am ausgangsseitigen Phototransistor befindet sich keine Schutzbeschaltung.

Alle I/Os mit Ausnahme von I²C und Temperatur sind mit LEDs zur Statusanzeige versehen. Eine weiße LED zeigt das Vorhandensein der Versorgungsspannung an, die entweder über USB erfolgen kann oder über einen AC/DC-Wander aus der Netzspannung heraus. Display und Drehschalter sind optional.

