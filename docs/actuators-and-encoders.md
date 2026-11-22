# Actuators and encoders

## NEMA 17 steppers
NEMA 17 describes a mounting frame size, not a guaranteed torque or current rating. Select a specific motor using its datasheet. Record holding torque, torque-speed curve, phase current, resistance, inductance, shaft dimensions, body length, mass and thermal limits.

### Encoder candidates

| Encoder | Interface | Notes |
|---|---|---|
| AS5600 | I2C / analog / PWM | 12-bit magnetic angle sensor; low-cost candidate |
| AS5048A | SPI / PWM | 14-bit absolute angle sensor |
| AS5047P | SPI / ABI/PWM options | Check exact variant and configuration |

An encoder on the motor shaft cannot observe backlash downstream of a gearbox. For joint-output measurement, mount the magnet and sensor across the actual joint axis.

## Conventional RC servos
MG996R-class metal-gear servos are common budget candidates, but genuine and clone products vary. A commonly published TowerPro MG996R specification lists 4.8–6.6 V and stall torque around 9.4 kg-cm at 4.8 V / 11 kg-cm at 6 V. Treat these as model-specific stall figures, not continuous usable torque. Verify the exact unit.

### External encoder mounting
Attach a diametrically magnetized magnet concentrically to the joint output. Fix the sensor PCB to the stationary frame, observe the encoder's magnet gap/alignment limits, calibrate zero and direction, and compare measured output angle with the command. This measures joint output but does not eliminate backlash.

## Smart serial servos
SC15-class devices are examples of smart serial servos with onboard position/load/voltage telemetry and TTL serial bus control. Public documentation describes model-dependent voltage and torque figures. Verify the exact revision before use.

Check supply range, peak current, torque-speed curve, position range/resolution, bus voltage levels, baud rate, packet protocol, feedback fields, ID assignment, mounting and connector pinout.

## Selection rule
Use the full load model in [torque and power sizing](torque-and-power-sizing.md). Do not choose shoulder or elbow actuators by stall torque alone.
