import RPi.GPIO as GPIO

import time

GPIO.setwarnings(False)

GPIO.setmode(GPIO.BOARD)														#Use board GPIO numbering.


numbers = [
    "abcdef",   																#0
    "bc",       																#1
    "abdeg",    																#2
    "abcdg",    																#3
    "bcfg",    																    #4
    "acdfg",    																#5
    "acdefg",   																#6
    "abc",      																#7
    "abcdefg",  																#8
    "abcdfg",   																#9
    "abcefg",   																#10
    "cdefg",    																#11
    "adef",     																#12
    "bcdeg",    																#13
    "adefg",    																#14
    "aefg",     																#15
    ]

segments = {'a': 5, 'b': 3, 'c': 11, 'd': 15, 'e': 8, 'f': 10, 'g': 7}			#Connect the seven segment display to pins 5, 3, 11, 15, 8, 10, and 7 of the Raspberry Pi's GPIO.

def init():    
    for s in segments:
        GPIO.setup(segments[s], GPIO.OUT)
    reset()

def reset():
    for s in segments:
        GPIO.output(segments[s], True)

def num(number):																#To display a specific number, 0 to 15. (10 - 15 will be displayed in hex, i.e. 0x0A - 0x0F)
    segments_to_turn_on = numbers[number]
    for s in segments_to_turn_on:
            GPIO.output(segments[s], False)

def count(delay):																#Hexadecimal count. The 'delay' argument specifies the number of seconds between updates.
    for n in range (0, 16):
        segments_to_turn_on = numbers[n]
        time.sleep(delay)
        reset()
        for s in segments_to_turn_on:
            GPIO.output(segments[s], False)
            
       
#Example usage (Uncomment to test)	   

#init()

#num(4)

#time.sleep(5)

#count(0.5)
#time.sleep(5)   


#GPIO.cleanup()
