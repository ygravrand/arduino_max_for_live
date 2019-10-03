In short
========
This Max patch and Arduino sketch together allow to make RGB leds pulse (or do whatever yout want, just edit the source code!)
in sync with Ableton Live's transport and tempo.

The arduino sketch is adapted from `adafruit
<https://learn.adafruit.com/12mm-led-pixels/code>`_.
Follow `Adafruit's guide
<https://learn.adafruit.com/12mm-led-pixels/>`_ and use `Adafruit WS2801 Led pixel library
<https://github.com/adafruit/Adafruit-WS2801-Library/archive/master.zip>`_ to set up the RGB lights.

Then upload ``tempo.ino`` to your arduino, put a ``tempo.amxd`` on a midi track in Ableton Live, connect your arduino to the computer USB port and fire up Play in Live!
Several parameters are exposed to control the device from a Live midi clip (change rate, fire everything up, shutdown everything...)

.. image:: http://img.youtube.com/vi/Q4UjbwEJwp4/0.jpg
   :width: 320px
   :height: 240px
   :alt: "Arduino controlled RGB led lights synchronised with Ableton tempo using Max for Live"
   :align: center
   :target: https://youtu.be/Q4UjbwEJwp4


Technical details
=================
A ``plugphasor~`` object sends a pulse synchronised with Live.
After a few tricks, this results in sending a character on a serial port;
The arduino program monitors the serial port and does different things with the leds depending on
the received character.

Troubleshooting
===============
On my computer, the Arduino serial port is ``b``, it may be ``a`` for you, just change this directly in the Max patch (``serial`` object).
