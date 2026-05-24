I started a project a few weeks ago, to build a pulse oximeter from
scratch using an Arduino. Today was the first time I tested it out
and saw how the sensor works.

First I tried setting up a basic red LED on a breadboard to experiment with the Arduino. It was fun to start wiring things, but I then started to wire the sensor I got for this project.

![Wiring a basic LED](/images/basic-arduino-testing.jpg)

The setup is just an Arduino Uno and a sensor called the MAX30102
on a breadboard. The sensor shines a red LED and an infrared LED
into your finger and measures how much light comes back. Apparently
oxygen-carrying blood and oxygen-poor blood absorb these two colors
differently, so by comparing them you can figure out blood oxygen
saturation. Each heartbeat also pushes a pulse of blood through
your finger, which briefly changes how much light gets through,
that's how it counts heart rate.

The wiring took about twenty minutes. Four wires for power, ground,
and two for something called I2C, which is how the sensor
talks to the Arduino. Then I uploaded a basic example program
from the SparkFun library and opened the Serial Monitor.

When I put my finger on the sensor, numbers started
coming out. They kept shifting as I changed how my 
finger was placed, based on how it was blocking the light.

I tried it out with different temperatures and positions, and I have some questions.

- The library does the heart rate math for me, but I don't really
  understand how. I want to look at the signal and try to
  count it myself.
- The temperature/position of your finger seems to change how the numbers come out, why?
