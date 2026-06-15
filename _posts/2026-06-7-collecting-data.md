As you might know, I am currently working on a project to make my own pulse oximeter at home from scratch using an Arduino, and comparing
it to a commercial one. With the commercial pulse oximeter finally here, I could start the real test: how well does my homemade device actually 
measure up?

The pulse oximeter that I had gotten contained 4 outputs that we could analyze. The two simpler ones were
SpO2, which is your blood oxygen percentage and PR, which is your heart rate/BPM. The other two that I didn't
understand  at first were a graph that corresponds to your heartbeat and IR. The graph represents the blood flow as
it pulses through your finger, and I could see the graph matching up with my heart rate every time I felt my
heart beat. The last one, IR, represents the strength of the pulse signal reaching the sensor.

To take data, we used 5 different conditions: 
  -Resting
  -Exercise
  -Cold hands 
  -Using a different finger (in this case I used my pinky instead of my index finger)
  -And less pressure on the sensor. 
For this project, I decided to measure the heart rate and SpO2, the main part. I started off by wiring everything from 
the sensor to the Arduino. The wires, as a reminder, are four wires for power, ground, and two for I2C, which is how the sensor 
talks to the Arduino. Then, I ran the code and put the pulse oximeter on my left and right hand simultaneously. I then looked for the numbers
on the Arduino to start comparing them to the pulse oximeter, but there was an issue. I didn't see any data, but the code
said it was working and wasn't showing any errors. After digging around for a while, I saw that the serial
monitor hadn't opened. The reason this happened was because on the app I use for Arduino at school, the serial monitor is
automatically open, and you don't need to manually open it.

When I reran the code and looked for the data, the heart rate was working fine, but the same can't be said for the SpO2.
When I looked at that section of the code, it showed that my SpO2 was -999. I looked up what this meant, and the -999 is an error code
that shows up when a finger isn't detected or that the data is insufficient. To fix this, I ran the code while my finger was on the
sensor instead of running the code then putting my finger on. After all of these problems were fixed, I started collecting data for
all 5 of the sections. 

For resting, I collected data normally as a "control" section to compare against all of the other groups.
For exercise, I did a set of 20  burpees for each round of collecting heart rate and SpO2. For cold hands, I got an ice pack from the freezer and
put it on my fingers for 30 seconds, then collected the data. For the different fingers, it was the same format as resting but just using my
pinky, which I thought would be the most different from my index finger due to its size. One other thing to consider for the pinky test is that
I'm comparing the pinky on my left hand to the index finger on my right hand, which is adding two different aspects that might affect the data.
For less pressure, I tried to have not all of my fingers touching the light/sensor, and having it "levitate" over it. One other issue that came
up in between collecting the data was that the code I was using gave the SpO2 and heart rate, but the SpO2 was having problems with consistency
and giving reasonable numbers. I then found code that was explicitly for SpO2, and that code worked.

I also researched the questions I had from the last post, which was about the base code that only showed IR and R numbers (infrared and red light),
as well as how those numbers affect blood oxygen. The R and IR numbers show how much of the oxygen is getting absorbed, as oxygen-rich blood
absorbs more infrared light and less red light compared to deoxygenated blood, which absorbs more red light. Pulse oximeters use the ratio of red
to infrared absorption to calculate SpO2, which helps cancel out other factors like finger thickness and skin tone.

Looking at the data, I was surprised by how closely the two devices agreed. SpO2 readings were within 1-2% on every measurement, and heart rate was
within 1-3 BPM on most. Even cold hands, which I expected to mess things up based on what I saw in Phase 1, gave clean readings on both devices.
This was surprising because it contradicted my original hypothesis. Instead of causing unreliable readings, cold hands had very little effect on either device.
One disclaimer I want to add is that the fact that my device and the commercial one agree doesn't necessarily mean they're both accurate. It could
mean they're both wrong in the same way, as they're both optical sensors using similar physics, so they might both struggle with the same situations.

I have a lot more new questions after collecting data, here they are:

Would having the MAX 30102 on my left hand and the commercial pulse oximeter on the right hand affect anything?
How reliable really is the data from the MAX 30102?
How can I actually write the code, instead of taking it from a library?
Are there any other inconsistencies that need to be considered when testing the 5 groups, other than the control group?

Here's the data that I collected:
| Reading # | Condition       | My SpO2 | Commercial SpO2 | My Heart Rate | Commercial Heart Rate |
| --------- | --------------- | ------- | --------------- | ------------- | --------------------- |
| 1         | Resting         | 99      | 99              | 87            | 87                    |
| 2         | Resting         | 99      | 99              | 79            | 78                    |
| 3         | Resting         | 98      | 97              | 78            | 75                    |
| 4         | Resting         | 97      | 98              | 76            | 76                    |
| 5         | Resting         | 96      | 98              | 79            | 76                    |
| 6         | Exercise        | 98      | 99              | 106           | 103                   |
| 7         | Exercise        | 99      | 98              | 112           | 109                   |
| 8         | Exercise        | 98      | 99              | 118           | 115                   |
| 9         | Exercise        | 99      | 99              | 110           | 108                   |
| 10        | Exercise        | 98      | 98              | 104           | 101                   |
| 11        | Cold Hands      | 97      | 98              | 71            | 72                    |
| 12        | Cold Hands      | 98      | 99              | 72            | 75                    |
| 13        | Cold Hands      | 99      | 98              | 71            | 71                    |
| 14        | Cold Hands      | 99      | 98              | 69            | 71                    |
| 15        | Cold Hands      | 97      | 98              | 71            | 72                    |
| 16        | Fingers (pinky) | 97      | 98              | 75            | 77                    |
| 17        | Fingers (pinky) | 98      | 99              | 83            | 84                    |
| 18        | Fingers (pinky) | 99      | 98              | 81            | 82                    |
| 19        | Fingers (pinky) | 97      | 96              | 77            | 78                    |
| 20        | Fingers (pinky) | 98      | 97              | 78            | 78                    |
| 21        | Pressure (soft) | 98      | 99              | 75            | 76                    |
| 22        | Pressure (soft) | 99      | 98              | 77            | 77                    |
| 23        | Pressure (soft) | 98      | 99              | 76            | 76                    |
| 24        | Pressure (hard) | 97      | 98              | 71            | 73                    |
| 25        | Pressure (hard) | 96      | 97              | 70            | 72                    |
