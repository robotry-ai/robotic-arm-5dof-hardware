# Drivers and electronics

## Stepper drivers

| Driver | Control | Typical role | Cautions |
|---|---|---|---|
| TMC2209 | STEP/DIR, UART | Compact quiet axes | Board cooling and continuous current vary |
| TMC5160-based board | STEP/DIR, SPI | Higher-current stepper systems | Check external MOSFET stage, cooling and board layout |
| TB6600-style module | STEP/DIR | External stepper driver | Clone quality varies; verify actual current and logic levels |
| DM542-class driver | STEP/DIR | More robust external drive | Match motor current, supply and pulse requirements |

Verify continuous phase current, peak current, thermal design, supply range, microstep settings and ESP32 logic compatibility. Do not rely on the driver's label alone.

## Servo control
- ESP32 LEDC or a PWM driver such as PCA9685 can generate RC-servo PWM.
- PCA9685 provides PWM outputs; it does not provide position feedback.
- Smart serial servos need the vendor-specified TTL/half-duplex interface. Check whether direction control or a transceiver is required.

## ESP32 responsibilities
- Generate motion commands and parse feedback.
- Maintain calibrated zero, direction and joint limits.
- Apply speed/acceleration limits and smooth trajectories.
- Detect stale feedback, following error, undervoltage and overtemperature where available.
- Stop safely after communication loss.
- Keep Wi-Fi/websocket handling from blocking time-critical control tasks.

## Power
Use a logic rail for ESP32/sensors and a separately sized actuator rail. Share signal ground where required by the interface. Size the supply using simultaneous peak demand and measured current, not idle current. Include branch protection and suitable wire gauge.
