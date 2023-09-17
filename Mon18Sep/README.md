# Exercise 1 - RGB Hello World
## Process
### Step 1
- At first, i downloaded the library as mentioned in the
[guide]([https://yal.cc/r/19/upscale/](https://learn.adafruit.com/adafruit-feather-m4-express-atsamd51/circuitpython-internal-rgb-led)https://learn.adafruit.com/adafruit-feather-m4-express-atsamd51/circuitpython-internal-rgb-led).
I then started experimenting with concepts such as brightness, main loop, and RGB values to get a good idea of how to create the lightshow.
I then started thinking about my story, and wanted to base my lightshow on the cycle of the day and night, and how they are so distinctly different yet interchange so smoothly and effortlessly throughout a 24-hour cycle. Especially in the desert where only natural lighting is present, it is all
the more evident.
### Step 2
- to start, i knew i wanted to play around with the colors yellow, orange, blue, and purple only as these are the colors that come to mind when i
think of a sunset or sunrise. So to begin, i simply put these color intervals into the code:
''''''''''''''''''''''''''''''''''''''''''''''''
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
''''''''''''''''''''''''''''''''''''''''''''''''
