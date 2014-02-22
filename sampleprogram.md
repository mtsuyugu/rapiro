
# Rapiro Sample Program


http://www.rapiro.com/downloads/


This document about its serial command specs. baud rate is 57600.

## \#M : preset motion

* #M0: Stop
* #M1: Forward
* #M2: Back
* #M3: Turn Right
* #M4: Turn Left
* #M5: Eye Color Green
* #M6: Eye Color Yellow
* #M7: Eye Color Blue
* #M8: Eye Color Red
* #M9: Push Motion


## \#P : set pose

### Full format

    #PS\d{2}A\d{3}R\d{3}G\d{3}B\d{3}T\d{3}

### S,A : set servo

    S\d{2}A\d{3}

* S: servo id (00-11)
* A: angle (000-180)

### R,G,B : set eye color

    R\d{3}
    G\d{3}
    B\d{3}

* max 255

### T : time

    T\{3}

T001 means 0.1sec, T010 means 1.0sec. max 255.

### Exapmle

Turn Head at 45 degree (right) with its duration 1sec.

    #PS00A045T010

Raise right hand and turn waist at 45 degree with its duration 1sec.

    #PS01A045S02A135T135

Set eye color yellow without motion

    #PR255G255B000T00

Turn head and change eye color

    #PS00A045R255T010

### Response

The #PT response is sent back when pose command sent to Rapiro is accepted. Its format is:

    #PT\d{3}

Value of T is the same as sent value. Otherwise, #EP is sent back.

    #EP
