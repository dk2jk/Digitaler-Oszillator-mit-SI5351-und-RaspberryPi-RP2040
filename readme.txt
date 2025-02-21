Digitaler Oszillator mit SI5351 und RaspberryPi RP2040

Es wird ein RaspberrPi Pico RP2040 Zero Modul verwendet.

(MicroPython v1.20.0 on 2023-04-26; Raspberry Pi Pico with RP2040 )

Das Programmm startet nach Reset in 'main.py'.
Von dort aus wird aus "i2c.si_bake.py"  'run()' gestartet.

In "i2c.si_bake.py" wird ein Text zum Morsen definiert z.B.:
text='vvv de dk2jk = bake mit raspi pico und si5351 +'

Aus dem Text wird jedem Buchstaben eine Kurz-Lang-Lolge zugeordnet.
Aufruf zum Beispiel:  lookup['F']   ---> '..-.'
Aus 'test'  wird eine liste:    ['-', '.', '...', '-']

Diese Liste wird in einer Schleife
    for morsezeichen in kurz_lang_liste
interpretiert: 
Eine Zeiteinheit T ist die Länge von einem 'dit'.
'.' kurzes Morse-Element 'dit' = 1 *T an, 1 *T aus
'-' langes Morse-Element 'dah' = 3 *T an, 1 *T aus

Nach einem Buchstaben, wenn ein Element der Liste abgearbeitet ist, 
folgt ein extra Buchstabenzwischenraum der Länge 3 *T.

Der Sender wird eingeschaltet mit 
si.frequenz (freq, 0) und ausgeschaltet mit
si.frequenz (0, 0)   ( Frequenz=0)

Mit led(0) bzw. led(1) wird eine Kontroll-Led geschaltet
Mit ton.off() ,ton.on() kann ein Mithörton geschaltet 
werden; dieser wurde hier nicht verwendet.

Zur Arbeitsweise des Moduls 'si5351_jk.py' wird auf das Datenblatt "si5351.pdf"
 ( Internetsuche ) verwiesen.

