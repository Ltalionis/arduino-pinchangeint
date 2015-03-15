**What's New? Jan. 15, 2015: _Latest version: 2.40-rc2. Get it at http://dl.bintray.com/greygnome/generic/pinchangeint-2.40-rc2.zip. A number of changes to this release; see https://github.com/GreyGnome/PinChangeInt/blob/master/RELEASE_NOTES_

As always, go to https://github.com/GreyGnome/PinChangeInt for the bleeding edge source.**

See [the Wiki pages for Installation instructions.](http://code.google.com/p/arduino-pinchangeint/wiki/Installation)

Go [here to discuss this library.](http://groups.google.com/group/arduino-pinchangeint-discuss) Use [the Issues tab above to register bugs or feature requests.](http://code.google.com/p/arduino-pinchangeint/issues/list)

I was inspired by a recent Ted video. As Itay Talgam's friend Peter says, "If you love something, give it away." See https://www.youtube.com/watch?feature=player_detailpage&v=R9g3Q-qvtss#t=1160. That sounds good; therefore, the license for the code has been changed to the Apache 2.0 license.

The PinChangeInt library implements Pin Change interrupts for the Arduino environment.  This library was designed for the Arduino Uno/Duemilanove/Mega 2560/Mega ADK.  It will likely work with other ATmega328- or ATmega168-based Arduinos; it has been reported to work just fine on the Nano. It will not work on ARM-based Arduinos, but then, attachInterrupt() is a complete solution there.

What are Pin Change interrupts?  The ATmega328p processor at the heart of the Arduino has two different kinds of interrupts: “external”, and “pin change”.  There are only two external interrupt pins, INT0 and INT1, and they are mapped to Arduino pins 2 and 3.  These interrupts can be set to trigger on RISING or FALLING signal edges, or on low level.  The triggers are interpreted by hardware, and the interrupt is very fast.  On the other hand there are only 2 such pins on the ATmega328p in the Arduino Uno and Duemilanove.

On the other hand the pin change interrupts can be enabled on any or all of the Arduino's signal pins.  They are triggered equally on RISING or FALLING signal edges, so it is up to the interrupt code to set the proper pins to receive interrupts, to determine what happened (which pin?  ...did the signal rise, or fall?), and to handle it properly.  Furthermore, the pin change interrupts are grouped into 3 “port”s on the MCU, so there are only 3 interrupt vectors (subroutines) for the entire body of 20 pins.  This makes the job of resolving the action on a single interrupt even more complicated.  The interrupt routine should be fast, but complication is the enemy of speed.  The PinChangeInt library is designed to handle the Arduino's pin change interrupts as quickly and reasonably as possible.

Version 1.4 (and later) puts all the code in the .h file, to allow the programmer to configure it through their sketch for minimum ram usage.  In earlier versions, it must be configured through the PinChangeIntConfig header file instead.

See the Wiki pages for more information.