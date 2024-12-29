# Arduino-Joystick-with-4-LED-blink-connection-and-code
# Arduino Joystick with 4 LEDs Blink

This project connects an Arduino joystick module with 4 LEDs to blink based on joystick movements.

## Components Needed:
- Arduino board (UNO, Nano, etc.)
- Joystick module (with X, Y, and SW pins)
- 4 LEDs (any color)
- 4 resistors (220Ω or similar for each LED)
- Breadboard and jumper wires

## Circuit Connections:

### Joystick Connections:
| **Joystick Pin** | **Arduino Pin** | **Description**          |
|-------------------|-----------------|--------------------------|
| GND              | GND             | Ground connection.       |
| VCC              | 5V              | Power connection.        |
| VRX (X-axis)     | A0              | Reads X-axis movement.   |
| VRY (Y-axis)     | A1              | Reads Y-axis movement.   |
| SW (button)      | 2               | Detects button press.    |

### LED Connections:
| **LED** | **Anode (Long Leg)** | **Cathode (Short Leg)** |
|---------|-----------------------|-------------------------|
| LED 1   | Pin 3                | GND via 220Ω resistor   |
| LED 2   | Pin 4                | GND via 220Ω resistor   |
| LED 3   | Pin 5                | GND via 220Ω resistor   |
| LED 4   | Pin 6                | GND via 220Ω resistor   |

## How It Works:
- The joystick outputs two analog signals: one for the X-axis and one for the Y-axis.
- The Arduino reads the joystick's position using `analogRead()`.
- If the X-axis value is below a threshold, the left LED turns on; if it's above a threshold, the right LED turns on.
- Similarly, the Y-axis controls the up and down LEDs.
- Adjust thresholds (e.g., 400 and 600) for joystick sensitivity.

## Arduino Code:
```cpp
const int xPin = A0;  // X-axis pin
const int yPin = A1;  // Y-axis pin
const int swPin = 2;  // Joystick button pin

const int ledLeft = 3;
const int ledRight = 4;
const int ledUp = 5;
const int ledDown = 6;

void setup() {
  pinMode(swPin, INPUT_PULLUP);
  pinMode(ledLeft, OUTPUT);
  pinMode(ledRight, OUTPUT);
  pinMode(ledUp, OUTPUT);
  pinMode(ledDown, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  int xValue = analogRead(xPin);
  int yValue = analogRead(yPin);
  int swState = digitalRead(swPin);

  // X-axis LEDs
  if (xValue < 400) {
    digitalWrite(ledLeft, HIGH);
  } else {
    digitalWrite(ledLeft, LOW);
  }

  if (xValue > 600) {
    digitalWrite(ledRight, HIGH);
  } else {
    digitalWrite(ledRight, LOW);
  }

  // Y-axis LEDs
  if (yValue < 400) {
    digitalWrite(ledUp, HIGH);
  } else {
    digitalWrite(ledUp, LOW);
  }

  if (yValue > 600) {
    digitalWrite(ledDown, HIGH);
  } else {
    digitalWrite(ledDown, LOW);
  }

  // Button press detection (optional, print to Serial Monitor)
  if (swState == LOW) {
    Serial.println("Button Pressed");
  }

  delay(100); // Adjust delay for smoother operation
}

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
