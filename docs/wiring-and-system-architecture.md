# Wiring and system architecture

## Conceptual topology
- Wi-Fi control UI (future) communicates with ESP32.
- ESP32 interfaces with stepper drivers, RC servo PWM, encoder buses and/or smart-servo serial bus.
- Separate protected actuator supply powers motors/servos.
- Regulated logic supply powers ESP32 and low-power sensors.
- Signal grounds are common where required by the selected interfaces.

This is a conceptual design, not a pin-by-pin wiring diagram. Pin assignments depend on the exact ESP32 board and drivers.

## Wiring rules
1. Never draw motor/servo current through the ESP32 board or USB connector.
2. Use a separate motor supply sized for simultaneous current demand.
3. Join signal grounds where required; respect isolation on isolated drivers.
4. Add fuse/branch protection to actuator power.
5. Use suitably rated wire, connectors and PCB traces.
6. Keep encoder wiring away from motor phase wires.
7. Verify logic voltage levels before connecting 5 V signals to ESP32 GPIO.
8. Add an accessible physical emergency power disconnect.

## Firmware layers
- Hardware abstraction for drivers, PWM servos, encoders and serial servos.
- Calibration for zero offsets, direction, limits and sensor plausibility.
- Motion planner with bounded speed/acceleration trajectories.
- Feedback monitor for following error, stale packets and voltage faults.
- Safety supervisor that inhibits motion on faults.
- Communications layer that queues commands without blocking control loops.
- Recorder storing timestamps, five joint targets and optional measured positions.

## Motion recording
Record timestamped joint targets and measured angles where available. Replay with interpolation and speed/acceleration limits. Test at low speed with no payload first.
