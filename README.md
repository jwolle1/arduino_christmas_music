# arduino_christmas_music

This repository is based on the work of [robsoncouto](https://github.com/robsoncouto/arduino-songs). I modified some of their code and added more Christmas songs.

Melodies are limited to one or two verses.

The sketches do not rely on any external libraries, only the built-in `tone()` function. It uses pulse width modulation (PWM) to create a square wave at a particular frequency to emulate music notes. Most Arduino boards have several PWM-capable pins. Choose one and remember to define `BUZZERPIN` at the top of the sketch.

You can use an active buzzer, passive buzzer, or speaker. Different components will require different wiring. I used a 5V active buzzer wired as shown below. You must use a current-limiting resistor to avoid drawing too much current from the Arduino's GPIO pin. Larger resistor values will produce a quieter sound. I found a 470 Ω resistor worked best but it will depend on the component and your preference. Anything larger than 220 Ω should be safe to use with an Arduino Uno or Nano.

![Wiring Diagram](images/wiring.png)

You can add new songs by translating sheet music and following the pattern in the examples. Since there is only one buzzer you can think of it like playing a piano with one finger. It's helpful to use simple arrangements that play one note at a time.

Quarter notes are given a value of 4, half notes are 2, and so on. Dotted notes are multiplied by -1. Use the clef diagram below to translate.

![Clef Diagram](images/clef.png)
[Source: Wikipedia](https://en.wikipedia.org/wiki/Clef)

You may find that adding more than four or five melodies to a single sketch will cause an Uno or Nano to crash and reboot. This is because of the limited available RAM. You could modify sketches to store melody arrays in `PROGMEM` or look at using boards with more RAM like the [Nano Every](https://store.arduino.cc/usa/nano-every) or [Teensy](https://www.pjrc.com/teensy/). I included a `progmem_example` to show how it can be done. This sketch plays 12 songs and only uses 28 bytes (1%) of dynamic memory on a Nano.
