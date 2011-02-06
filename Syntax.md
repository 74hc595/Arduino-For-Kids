Syntax ideas
============

Pins would be treated as "objects" instead of regular integers

You should be able to assign a pin to a name:
    make "button pin 11
    make "redLED pin 12
    make "greenLED pin 13

Instead of functions, send messages to pins
    pin 11 input
    pin 12 output

Messages should return the pin object itself so they can be chained
    make "button pin 11 input
    make "redLED pin 12 output
    make "greenLED pin 13 output

Shorthand for assigning pins with mode:
    make-input "button pin 11
    make-output "redLED pin 12

Instead of `digitalWrite()`:
    pin 12 on
    pin 13 off
    :redLed on
    :greenLED off
    :redLED set-value 0

Instead of `digitalRead()`:
    on? / high? / not-pressed? / open?
    off? / low? / pressed? / closed?
    pin 9 high?
    pin 10 off?
    :button pressed?
    :button value

Instead of `analogRead()`:
    pin 9 value

Instead of `analogWrite()`:
    set-value / set-brightness
    pin 3 set-value 128
    pin 4 set-brightness 96

Instead of `shiftOut()`, use "shifter" objects. Have one global shifter, and the
ability to create others
    shift-data (pin 8)
    shift-clock (pin 9)
    shift-data-pin 8
    shift-clock-pin 9
    shift-msb-first
    shift-lsb-first
    shift-order msb-first
    shift-order lsb-first
    shift-out 127
    shift-out [1 2 3 4]
    shift-out [high-byte :x low-byte :x]

    make :myShifter shifter data-pin 6 clock-pin 7
    :myShifter shift-out 33

Serial port is always initialized, at 9600 baud
    can-read?
    bytes-available
    read-number
    read-character
    read-string
    print (adds newline)

    waituntil [can-read?]
    make "value read-number
    :blueLED set-brightness :value

Fade example:
    to fade
      make "LED pin 9 output
      make "brightness 0
      make "fadeAmount 5

      loop [
        :LED set-value brightness
        make "brightness [:brightness + :fadeAmount]
        if :brightness = 0 or :brightness = 255
          [make "fadeAmount -fadeAmount]
        wait 30
      ]
    end
