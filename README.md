# Digitaler Oszillator mit SI5351 und RaspberryPi RP2040
Ein RaspberrPi Pico RP2040 Zero Modul  wird zur Steuerung eines SI5351 verwendet.

Das Programmm startet nach Reset in 'main.py'. Von dort aus wird aus "i2c.si_bake.py"  'run()' gestartet.

In "i2c.si_bake.py" wird ein Text zum Morsen definiert.

Aus diesem Text wird jedem Buchstaben aus einer Lookup-Tabelle eine Kurz-Lang-Folge zugeordnet.
Zum Beispiel wird aus  lookup['F']  die   Kurz-Lang-Folge '..-.'.
Aus dem Wort 'test'  wird die  Liste:    ['-', '.', '...', '-'].

Diese Liste wird in einer Schleife  als Morsezeichen interpretiert. ( '.' ) bedeutet  Kurz .  ('-')  bedeutet Lang. 
Nach einem Buchstaben, wenn ein Element der Liste abgearbeitet ist, folgt ein extra Buchstabenzwischenraum .

Der Oszillator wird gesteuert mit " si.frequenz (freq, 0) ".
Bei freq=0 ist der Oszillator aus. Der 2. Parameter 0 bedeutet "SI5351 Clock 0 Ausgang"

Mit led(0) bzw. led(1) wird eine Kontroll-Led geschaltet.
Mit ton.off() ,ton.on() kann ein Mithörton geschaltet werden; dieser wurde hier nicht verwendet.

Zur Arbeitsweise des Moduls 'si5351_jk.py' wird auf das Datenblatt "si5351.pdf" (Internetsuche) verwiesen.

