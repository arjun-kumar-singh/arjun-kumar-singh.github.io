As stated in my last post, I am currently working on making a pulse oximeter from scratch 
using an Arduino. Today I further experimented with the sensor, a MAX30102, to see how it
works.

I started with wiring up the sensor to the Arduino Uno, four wires for power, ground, and the 
I2C, which is how the sensor communicates with the Arduino. I then tried to test the sensor to
start off, but there was an issue. When I attempted to run the code, an error popped up saying that 
the computer wasn't able to communicate with the port. I tried to change the port, board, and the cable,
none of which worked. After that, I tried rebooting my computer to see if anything would change, and a 
new port popped up. After trying that one, the code finally uploaded to the Arduino.

While looking at the code, I noticed a part of the code that was called the baud rate. In the serial 
monitor, a bunch of gibberish was showing instead of the numbers that showed blood oxygen levels. While
researching, I realized the baud rate in the code didn't match the one that it was set to. The baud rate controls
the speed that the Arduino and sensor communicate. After matching them up to 115200, the sensor began to
show data. After looking at the numbers, I noticed there were 3 categories. R, IR, and G (representing red, infared,
and green light). The red and infared numbers were around 100000 and 110000 respectively. The green number however,
was very low (around 50-100). After doing some exploration, this is because the MAX30102 doesn't have a green LED in
comparison with the other models. 

After sorting out all of the technical and hardware issue, I finally got to testing the sensor with different conditions.
When trying the sensor with colder fingers and in less sensitive areas, I noticed the numbers for the blood oxygen were
lower or more inconsistent. I learned that the temperature can affect the numbers by shinking the blood vessels to conserve heat, and 
therefore affecting the distance the light has to travel to reach a blood vessel. This can make the numbers smaller or more 
inconsistent. The postion can affect it in the same way due to how the sensor calculates blood oxygen levels, and will give 
more accurate results in areas with more vessels. One other thing that I found interesting was how age can affect the numbers.
When trying it on my parents, the numbers were lower by about 10000 each. This is normal, and age is a factor that can change 
the numbers.

This session answered a lot of my questions, but I have some new ones.
  - I understand how the sensor gets the numbers, but what do they actually mean?
  - How do these numbers affect blood oxygen, does it have to do with the code?
