# Exercise 1 - RGB Hello World
## Process
- At first, i downloaded the library as mentioned in the
[guide]([https://yal.cc/r/19/upscale/](https://learn.adafruit.com/adafruit-feather-m4-express-atsamd51/circuitpython-internal-rgb-led)https://learn.adafruit.com/adafruit-feather-m4-express-atsamd51/circuitpython-internal-rgb-led).
I then started experimenting with concepts such as brightness, main loop, and RGB values to get a good idea of how to create the lightshow.
I then started thinking about my story, and wanted to base my lightshow on the cycle of the day and night, and how they are so distinctly different yet interchange so smoothly and effortlessly throughout a 24-hour cycle. Especially in the desert where only natural lighting is present, it is all
the more evident.
- to start, i knew i wanted to play around with the colors yellow, orange, blue, and purple only as these are the colors that come to mind when i
think of a sunset or sunrise. So to begin, i simply put these color intervals into the code:

```
# SPDX-FileCopyrightText: 2018 Kattni Rembor for Adafruit Industries
#
# SPDX-License-Identifier: MIT

"""CircuitPython Essentials Internal RGB LED red, green, blue example"""
import time
import board

if hasattr(board, "APA102_SCK"):
    import adafruit_dotstar

    led = adafruit_dotstar.DotStar(board.APA102_SCK, board.APA102_MOSI, 1)
else:
    import neopixel

    led = neopixel.NeoPixel(board.NEOPIXEL, 1)

led.brightness = 0.3

while True:
    # Yellow
    led[0] = (255, 255, 0)
    time.sleep(1)

    # Blue
    led[0] = (0, 0, 255)
    time.sleep(1)

    # Purple
    led[0] = (128, 0, 128)
    time.sleep(1)

    # Orange
    led[0] = (255, 165, 0)
    time.sleep(1)
```

- Then, to mimick smooth transitions between the different colors, i used the `time.sleep()` function to create spaces between the neopixel changing RGB values. this is the result:

```
while True:
    # Yellow to Blue
    led[0] = (255, 255, 0)
    time.sleep(1)
    led[0] = (204, 204, 0)
    time.sleep(1)
    led[0] = (153, 153, 0)
    time.sleep(1)
    led[0] = (102, 102, 0)
    time.sleep(1)
    led[0] = (51, 51, 0)
    time.sleep(1)
    led[0] = (0, 0, 255)
    time.sleep(1)
    led[0] = (0, 0, 204)
    time.sleep(1)
    led[0] = (0, 0, 153)
    time.sleep(1)
    led[0] = (0, 0, 102)
    time.sleep(1)
    led[0] = (0, 0, 51)
    time.sleep(1)

    # Blue to Purple
    led[0] = (0, 0, 51)
    time.sleep(1)
    led[0] = (0, 0, 102)
    time.sleep(1)
    led[0] = (0, 0, 153)
    time.sleep(1)
    led[0] = (0, 0, 204)
    time.sleep(1)
    led[0] = (0, 0, 255)
    time.sleep(1)
    led[0] = (128, 0, 128)
    time.sleep(1)
    led[0] = (102, 0, 102)
    time.sleep(1)
    led[0] = (76, 0, 76)
    time.sleep(1)
    led[0] = (51, 0, 51)
    time.sleep(1)
    led[0] = (25, 0, 25)
    time.sleep(1)

    # Purple to Orange
    led[0] = (25, 0, 25)
    time.sleep(1)
    led[0] = (51, 0, 51)
    time.sleep(1)
    led[0] = (76, 0, 76)
    time.sleep(1)
    led[0] = (102, 0, 102)
    time.sleep(1)
    led[0] = (128, 0, 128)
    time.sleep(1)
    led[0] = (255, 165, 0)
    time.sleep(1)
    led[0] = (204, 136, 0)
    time.sleep(1)
    led[0] = (153, 102, 0)
    time.sleep(1)
    led[0] = (102, 68, 0)
    time.sleep(1)
    led[0] = (51, 34, 0)
    time.sleep(1)

    # Orange to Yellow
    led[0] = (51, 34, 0)
    time.sleep(1)
    led[0] = (102, 68, 0)
    time.sleep(1)
    led[0] = (153, 102, 0)
    time.sleep(1)
    led[0] = (204, 136, 0)
    time.sleep(1)
    led[0] = (255, 165, 0)
    time.sleep(1)
    led[0] = (255, 255, 0)
    time.sleep(1)
    led[0] = (204, 204, 0)
    time.sleep(1)
    led[0] = (153, 153, 0)
    time.sleep(1)
    led[0] = (102, 102, 0)
    time.sleep(1)
    led[0] = (51, 51, 0)
    time.sleep(1)
```

- Although i was really happy with the smooth transitions within each color, the transition between the different colors was still choppy. The only transition that was smooth was between orange and yellow and that was because they shared very little distinctions in terms of values. To remedy this, i created more intervals between transitions. here is the result:

```
    # Yellow to Blue
    led[0] = (255, 255, 0)
    time.sleep(1)
    led[0] = (204, 204, 0)
    time.sleep(1)
    led[0] = (153, 153, 0)
    time.sleep(1)
    led[0] = (102, 102, 0)
    time.sleep(1)
    led[0] = (51, 51, 0)
    time.sleep(1)
    led[0] = (45, 45, 25)
    time.sleep(1)
    led[0] = (40, 40, 51)
    time.sleep(1)
    led[0] = (30, 30, 84)
    time.sleep(1)
    led[0] = (25, 25, 110)
    time.sleep(1)
    led[0] = (20, 20, 135)
    time.sleep(1)
    led[0] = (13, 13, 170)
    time.sleep(1)
    led[0] = (7, 7, 200)
    time.sleep(1)
    led[0] = (4, 4, 233)
    time.sleep(1)
    led[0] = (0, 0, 255)
    time.sleep(1)
    led[0] = (0, 0, 255)
    time.sleep(1)
    led[0] = (0, 0, 204)
    time.sleep(1)
    led[0] = (0, 0, 153)
    time.sleep(1)
    led[0] = (0, 0, 102)
    time.sleep(1)

    # Blue to Purple
    time.sleep(1)
    led[0] = (0, 0, 153)
    time.sleep(1)
    led[0] = (0, 0, 204)
    time.sleep(1)
    led[0] = (0, 0, 255)
    time.sleep(1)
    led[0] = (10, 0, 243)
    time.sleep(1)
    led[0] = (21, 0, 230)
    time.sleep(1)
    led[0] = (34, 0, 214)
    time.sleep(1)
    led[0] = (45, 0, 207)
    time.sleep(1)
    led[0] = (53, 0, 190)
    time.sleep(1)
    led[0] = (65, 0, 183)
    time.sleep(1)
    led[0] = (78, 0, 176)
    time.sleep(1)
    led[0] = (100, 0, 152)
    time.sleep(1)
    led[0] = (107, 0, 144)
    time.sleep(1)
    led[0] = (114, 0, 130)
    time.sleep(1)
    led[0] = (128, 0, 128)
    time.sleep(1)
    led[0] = (102, 0, 102)
    time.sleep(1)
    led[0] = (76, 0, 76)
    time.sleep(1)
    led[0] = (51, 0, 51)
    time.sleep(1)
    led[0] = (25, 0, 25)
    time.sleep(1)

    # Purple to Orange
    led[0] = (25, 0, 25)
    time.sleep(1)
    led[0] = (51, 0, 51)
    time.sleep(1)
    led[0] = (76, 0, 76)
    time.sleep(1)
    led[0] = (102, 0, 102)
    time.sleep(1)
    led[0] = (128, 10, 128)
    time.sleep(1)
    led[0] = (131, 20, 116)
    time.sleep(1)
    led[0] = (145, 43, 103)
    time.sleep(1)
    led[0] = (167, 61, 95)
    time.sleep(1)
    led[0] = (185, 79, 83)
    time.sleep(1)
    led[0] = (191, 91, 77)
    time.sleep(1)
    led[0] = (205, 110, 69)
    time.sleep(1)
    led[0] = (213, 135, 53)
    time.sleep(1)
    led[0] = (229, 146, 37)
    time.sleep(1)
    led[0] = (243, 151, 20)
    time.sleep(1)
    led[0] = (255, 165, 0)
    time.sleep(1)
    led[0] = (204, 136, 0)
    time.sleep(1)
    led[0] = (153, 102, 0)
    time.sleep(1)
    led[0] = (102, 68, 0)
    time.sleep(1)
    led[0] = (51, 34, 0)
    time.sleep(1)

    # Orange to Yellow
    led[0] = (51, 34, 0)
    time.sleep(1)
    led[0] = (102, 68, 0)
    time.sleep(1)
    led[0] = (153, 102, 0)
    time.sleep(1)
    led[0] = (204, 136, 0)
    time.sleep(1)
    led[0] = (255, 165, 0)
    time.sleep(1)
    led[0] = (255, 255, 0)
    time.sleep(1)
    led[0] = (204, 204, 0)
    time.sleep(1)
    led[0] = (153, 153, 0)
    time.sleep(1)
    led[0] = (102, 102, 0)
    time.sleep(1)
    led[0] = (51, 51, 0)
    time.sleep(1)
```

- I was really happy with this modifyed version of the code as it gave me the exact result that i wanted and aligned with my initial idea.
