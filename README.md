# RAMPSDC
RAMPS Due Converter. 
See the Wiki here: http://reprap.org/wiki/RAMPSSB (still working on it)

Goes between a standard 5V RAMPS, and a 3.3V Arduino Due. Uses the Vin from the RAMPS board to power the 5V rail, and then uses that 5V supply to power pins on the RAMPS, allowing more current for the Heater and Servo pins outputs. 
Steps down voltage of the X Max, Y max, Y min, Xmin, and Z min endstops (The Z MAX Enstop is unconnected), so they dont damage the Due, and a 5V-3.3V voltage divider is used to propotionally drop the voltage of the Thermistors.
Also adds the EEPROM required for use as a 3D printer controller.

Uses three generic bidirectional level shifter modules (two if you arn't using servos). These can be bought from Ebay or Aliexpress for maybe 50 cents each. Just make sure you get the kind with the powers and grounds (HV, GND, LV, GND) in the middle. Other than that, its a pretty generic part.

Most other pins are connected to the RAMPS as if it was a mega (Digital pin 51 > digital pin 51, RX > RX, TX > TX, ETC). It is worth noting that since the pins dont perfectly match up, I2C 1 (which is normally broken out on the RAMPS), is used by the EEPROM, so the 2nd I2C header is broken out on the RAMPS. The SPI pins are not in the same place as the mega, and are broken out behind the RAMPS connector.

As a reminder, all inputs, INCLUDING the Analog inputs, MUST be reduced to 3.3V before hitting the due. This means you cannot use an LCD screen with this, without some sort of voltage regulation on the encoder. I'm still working on a workaround for this, and that may show up in V2. 
