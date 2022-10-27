from gpiozero import MotionSensor, LED, Buzzer
import Adafruit_SSD1306
from PIL import Image, ImageDraw, ImageFont
import time
import os
import requests
MIN_T_BETWEEN_ALERTS = 2
EVENT = 'intruderalert'
BASE_URL = 'https://maker.ifttt.com/trigger/'
KEY = 'nUBuLXk-298JqflL-qHyo5ifxF_BgsDw36usqNz1r1-'
pir = MotionSensor(18)
led = LED(22)
buzzer = Buzzer(17)


def send_notification():
    url = BASE_URL + EVENT + '/with/key/' + KEY
    response = requests.post(url)
    print(response.status_code)


def buzz(pitch, duration):
    period = 1.0/pitch
    delay = period/2
    cycles = int(duration * pitch)
    buzzer.beep(on_time=period, off_time=period, n=int(cycles/2))


# Setting up our display
disp = Adafruit_SSD1306.SSD1306_128_64(rst=None, i2c_address=0x3C)
small_font = ImageFont.truetype('FreeSans.ttf', 12)
large_font = ImageFont.truetype('FreeSans.ttf', 33)
disp.begin()
disp.clear()
disp.display()

# Making an image to draw on in 1-bit color.
width = disp.width
height = disp.height
image = Image.new('1', (width, height))
draw = ImageDraw.Draw(image)

# Displaying a message on 3 lines, first line big font
def display_message(top_line, line_2):
    draw.rectangle((0, 0, width, height), outline=0, fill=0)
    draw.text((0, 0), top_line, font=large_font, fill=255)
    draw.text((0, 35), line_2, font=large_font, fill=255)
    disp.image(image)
    disp.display()


while True:
    pir.wait_for_motion()
    print("Motion detected!")
    send_notification()
    led.on()
    buzz(2000, 10)
    display_message("Intruder", "Alert")
    time.sleep(30)
    led.off()
    time.sleep(MIN_T_BETWEEN_ALERTS * 60)
