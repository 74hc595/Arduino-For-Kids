Arduino for Kids: A Proposal for a Logo-based IDE
=================================================

Inspiration
-----------
Today, I watched an episode of [Sylvia's Super Awesome Maker Show](http://blog.makezine.com/archive/2010/08/super-awesome-sylvia-shows-super-si.html)
covering the Arduino. Sylvia is an eight-year-old girl who, with the help of the
best parents ever, makes videos about electronics and physical computing.

In this episode, she talked about how to make an adjustable strobe light and a
"music machine" that generates random tones based on the levels of floating
analog pins. However, I was a little surprised that there was basically no
discussion of the coding behind these projects.

I wonder if this is because the C-based Arduino language might be too
complicated for most kids. All the braces, and semicolons, and weird keywords
like "int." How many eight-year-olds know what an integer is? How many
eight-year-olds even know what _fractions_ are? While some might argue that
programming could be an excellent opportunity to teach these mathematical
concepts, the complicated syntax could also stifle creativity.

This got me thinking. When I was about seven years old, we got to play with
["Lego Logo"](http://en.wikipedia.org/wiki/Lego_Logo) in school. This system,
a precursor to today's Lego Mindstorms, consisted of an Apple II with a special
card that allowed you to interact with Lego motors and sensors. Instead of C,
the system was based on the [Logo programming language](http://en.wikipedia.org/wiki/Logo_(programming_language).
Yes, the one with the turtle. If you haven't heard of Logo, it's a functional language, based on Lisp, with extremely simple syntax. If you want to write a function do draw a square on the screen, you just write
    to square
    repeat 4 [fd 100 rt 90]
    end
This tells the on-screen "turtle" to draw all four sides of the square by moving
forward 100 units, then turning right 90 degrees. This "turtle geometry" was
much easier for first-graders to understand than the Cartesian systems used in
other graphical programming languages.

Programming
-----------
If you want to blink an LED ten times on an Arduino, you'd write something like
this:
    for (int i = 0; i < 10; i++)
    {
      digitalWrite(13, HIGH);
      delay(500);
      digitalWrite(13, LOW);
      delay(500);
    }
Imagine teaching this to a seven-year-old. You'd have to explain the following:
* variables
* data types (i.e. what does "int" mean)?
* for loops (including all three clauses)
Even in a high-school programming class, it could take _days_ to cover those
topics. Now, imagine if all you had to do was this:
    repeat 10 [led on wait 500 led off wait 500]
I don't remember the exact Lego Logo syntax, but you get the idea. One line of
code, something that a child who has never programmed before could grasp.

The Logo implementation would, of course, include commands for blinking lights,
reading analog ports, playing tones, printing to and reading from the serial
port, etc. It could either translate to C or compile directly to AVR object 
code, but a C translator would make it easy to use existing third-party Arduino
libraries.

The environment
---------------
LCSI LogoWriter was the version of Logo I remember using (both on the Apple II
and the Macintosh) but unfortunately I cannont find any screenshots. In crude
ASCII art, it looked something like this:
    +------------------------+
    |                        |
    |                        |
    |           ^            |
    |                        |
    |                        |
    +------------------------+
    |                        |
    +------------------------+
The area above the line was used for graphics output (the '^' represents the 
turtle) and the area below the line was the "command center," basically, the
Logo read-eval-print loop.

Logo commands could be entered directly in the command center and executed
immediately, but if you wanted to write "procedures" (subroutines), you could
press Control-F to switch to the "flipside," a full-screen text editor.

An environment like this could work for Arduino as well. All three components
would be included:
* a read-eval-print loop would let users immediately control the Arduino (via
  Firmata or something similar) without having to upload code
* a full text editor (like the "flipside") where procedures can be written,
  similar to the current Arduino text editor
* an output area, which could be used for text and graphics I/O. A simple
  graphical system would be included that would allow the Arduino to "draw"
  directly in this graphics area (via serial commands), or on an LCD. This would
  let users do things like graph sensor data directly in the environment, or
  present point-and click interfaces.

The implementation
------------------
No work on this project has been done at this point, it's merely a proposal.
Since I have a full-time job and several side projects on my plate, I'm not sure
when I'll be able to work on it. Once I get around to it, the initial
implementation will likely be a Cocoa app for the Mac, with the core
interpreter/compiler written in C for easy porting. (College has instilled in me
a strong dislike of Java, sorry. :p) Everything will be open-source and ports to
other platforms would be encouraged.

Conclusions/Feedback
--------------------
The Logo language was one of the greatest educational programming languages of
all time (it's how I got started, nearly twenty years ago) and it saddens me
that it has been mostly forgotten. Arduino is one of the best ways to each
electronics and embedded programming to people of all ages. However, the C
language still prevents a significant barrier to entry. Coupled with Logo, this
barrier could be reduced to nearly zero.

If you'd like to talk about this idea, I'm on Twitter: @autorelease
Matt Sarnoff
February 5, 2011

