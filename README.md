# Arduino-Joystick-with-4-LED-blink-connection-and-code
Here's how you can connect and code an Arduino Joystick with 4 LEDs to blink according to joystick movements.
Components Needed:
Arduino board (UNO, Nano, etc.)
Joystick module (with X, Y, and SW pins)
4 LEDs (any color)
4 resistors (220Ω or similar for each LED)
Breadboard and jumper wires
Circuit Connections:
Joystick connections:

GND to Arduino GND
VCC to Arduino 5V
VRX (X-axis output) to Arduino A0
VRY (Y-axis output) to Arduino A1
SW (button) to Arduino Pin 2 (for button press)
LED connections:

LED 1 (representing X-axis left): Connect the anode (longer leg) of LED 1 to Pin 3 of the Arduino and the cathode (shorter leg) to GND via a 220Ω resistor.
LED 2 (representing X-axis right): Connect the anode of LED 2 to Pin 4 of the Arduino and the cathode to GND via a 220Ω resistor.
LED 3 (representing Y-axis up): Connect the anode of LED 3 to Pin 5 of the Arduino and the cathode to GND via a 220Ω resistor.
LED 4 (representing Y-axis down): Connect the anode of LED 4 to Pin 6 of the Arduino and the cathode to GND via a 220Ω resistor.
How It Works:
The joystick outputs two analog signals: one for the X-axis and one for the Y-axis.
The Arduino reads the joystick's position using analogRead().
If the X-axis value is below a threshold, the left LED turns on, and if it's above a threshold, the right LED turns on.
Similarly, the Y-axis controls the up and down LEDs.
Adjust the thresholds (400 and 600) if needed, depending on the sensitivity of the joystick.
This setup should allow you to move the joystick and see the corresponding LED blink depending on the direction.
