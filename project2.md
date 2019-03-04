## Project 2

In project 2, you'll build a little robot, starting with the Remote Control Cardboard Box.

The goals are:
- Get comfortable with basic electronics, motors, and the Arduino platform.
- Get experience reading a schematic or Fritzing diagram and wiring circuits.
- Understand how a single-board computer, like the Raspberry Pi, can be used to bridge the physical and digital worlds.
- Build on your knowledge of the command line, web servers, and React.

### Week 1-2

In this two-week group assignment, you'll build a remote control cardboard box. 

So, what does this system need?

- A drive system: wheels, motors, and enough power to run them.
- An infrared receiver: to get signals from your remote.
- An Arduino: to process the remote signals and engage the drive system.

In class, we connected the infrared receiver to the Arduino, and confirmed that we can see what numbers are transmitted when we press specific buttons on the remote. We used the `irRecvDemo` code:

```arduino
/*
 * IRremote: IRrecvDemo - demonstrates receiving IR codes with IRrecv
 * An IR detector/demodulator must be connected to the input RECV_PIN.
 * Version 0.1 July, 2009
 * Copyright 2009 Ken Shirriff
 * http://arcfn.com
 */

#include <IRremote.h>

int RECV_PIN = 11;

IRrecv irrecv(RECV_PIN);

decode_results results;

void setup()
{
  Serial.begin(9600);
  // In case the interrupt driver crashes on setup, give a clue
  // to the user what's going on.
  Serial.println("Enabling IRin");
  irrecv.enableIRIn(); // Start the receiver
  Serial.println("Enabled IRin");
}

void loop() {
  if (irrecv.decode(&results)) {
    Serial.println(results.value, HEX);
    irrecv.resume(); // Receive the next value
  }
  delay(100);
}
```

For homework, your task is to complete the construction of the remote control cardboard box! You can do so by [following the instructions here](http://workshopweekend.net/arduino/projects/remote_control_cardboard) -- though note that you've already complete some of the steps, so keep that in mind as you go through.

Make sure to pay very close attention to how you wire up the motors -- [this pdf](https://github.com/workshopweekend/remote_control_cardboard/blob/master/project/l293d-one-sheet.pdf) that consolidates the diagrams may help, but **note that you have a different IR receiver, with a different "pinout", than in this diagram.**

Once you have a working box, make the following changes:

-  Some of the pins on the Arduino allow you to perform an `analogWrite` -- they can provide an output that isn't quite as strong as a full `HIGH` that you get from using `digitalWrite`. Those pins are makred with little `~` symbols. **Assignment**: Use `analogWrite` to:
   -  Change the speed of the `reverse` on your box.
   -  Make the box turn in place.

**Optional challenge:**

-  Add LEDs to your remote control cardboard box. Do something fun with them. If you can't think of something fun, do something engineering-y instead:
   -  Add "headlights" that turn on whenever the box is moving forward, and red "taillights" that turn off whenever the box is stopped.
   -  Add "turn signals" that blink whenever the box is turning.
   -  Add a "reverse" light that turns on when the box moves backwards.
-  Go crazy with the mechanics: add two more wheels, and figure out a way to turn them using a servo motor. (Some research will be required!)