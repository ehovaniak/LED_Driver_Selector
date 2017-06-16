This repository contains schematics and images for a LED selector circuit.

I drew this circuit and tested on a bread board to allow multiple LED configurations while using a 
single Photodiode AFE/LED driver IC for a project. Green LEDs have applications for Heart Rate
detection while RED/IR LEDs have applications for blood oxygenation measurements. The most obvious solution was to deploy two seperate AFE/Driver units. However, this approach would be physically more expensive and more costly in real estate. This would require area for another IC, as well as decoupling caps, communication traces, and other extras. This would be overkill as the IC is designed to handle any LED configuration desired.

This simple solution allows the desired LED configuration to be selected with a GPIO from an external 
microcontroller. When LED_CTRL is "high", the N-FETs will conduct and the P-FETs will not, allowing 
the LED drivers to sink constant current through the green LEDs. When LED_CTRL is "low", the opposite 
will occur.

LED_CTRL is gated by one extra N-FET. This is done to ensure the P-FETs gate potential match their 
Source potential. "PMID" is a variable DC potential, while the "GPIO" line from the microcontroller 
runs at a constant 1.8V. A "low" from the microcontroller will pull "LED_CTRL" up to PMID, while a 
"high" will pull "LED_CTRL" to GND. A large resistance is used to minimize current consumption.

I tested this circuit on a bread board, connected to the DK received from the AFE/Driver IC 
manufacturer. I did this as a precaution to ensure the extran series FETs did not affect the LED 
driver circuitry.
