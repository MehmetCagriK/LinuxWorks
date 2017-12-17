# How to Use GPIO Pins

Below is the simple code piece that is used to provide __high__ output at one
of the GPIO pins.
```
import RPi.GPIO as GPIO    # Import GPIO library 

GPIO.setmode(GPIO.BOARD)   # Standard setup to work with GPIO pins
GPIO.setup(7, GPIO.OUT)    # Set this pin to be output
GPIO.output(7, True)       # Provide high output at the pin

GPIO.cleanup()             # Clean up after using pins for certain setups.
                           # Pin setups are persistent and you will get the
                           # warning below if you do not cleanup;
                           # "blinkLED.py:6: RuntimeWarning: This channel is
                           # already in use, continuing anyway..."
```


