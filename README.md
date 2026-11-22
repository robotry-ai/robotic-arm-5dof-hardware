# 5-DOF Robotic Arm — Hardware Research

India-focused hardware research for a feedback-capable 5-DOF robotic arm controlled by an ESP32.

> Status: initial research baseline, not a released design. Exact motor SKUs, mechanical dimensions, payload, speed and joint limits must be frozen before purchasing. Verify every specification against the exact manufacturer's datasheet.

## Goals
- Compare NEMA 17 steppers with external encoders, conventional RC servos with external joint encoders, and smart serial servos.
- Design for position feedback, repeatable movement, recording/playback and future web control.
- Use an ESP32 as the main controller; no separate computer is assumed.
- Size actuators and power supplies from calculated loads, not headline stall torque.

## Planning assumptions

| Parameter | Initial value | Status |
|---|---:|---|
| DOF | 5 | Requirement |
| Controller | ESP32 | Preferred |
| Payload | 250–500 g | Provisional |
| Shoulder-to-tool reach | 300–400 mm | Provisional |
| Structure | 3D printed | Planning assumption |
| Gripper | Separate actuator unless explicitly counted as a DOF | To confirm |

Joint convention: J1 base yaw, J2 shoulder pitch, J3 elbow pitch, J4 wrist pitch, J5 wrist roll. Gripper is separate in this convention.

## Documentation
- [Architecture comparison](docs/architecture-comparison.md)
- [Actuators and encoders](docs/actuators-and-encoders.md)
- [Drivers and electronics](docs/drivers-and-electronics.md)
- [Torque and power sizing](docs/torque-and-power-sizing.md)
- [Wiring and system architecture](docs/wiring-and-system-architecture.md)
- [India BOM and budget](docs/india-bom.md)
- [Validation and safety](docs/validation-and-safety.md)
- [Sources and datasheets](references/sources.md)

## Preliminary direction
- Smart serial servos are the simplest path to integrated telemetry; verify exact model, protocol, torque-speed curve and peak current.
- NEMA 17 + encoder is flexible, but an encoder alone does not close the control loop. Firmware or a closed-loop driver must compare commanded and measured position.
- RC servos plus an encoder mounted at the joint output are a budget prototype option. This measures output position but does not remove gearbox backlash.

No architecture is selected until CAD-based torque calculations and loaded bench tests are complete.

## Safety
Never power servos from the ESP32 board's 5 V pin or USB rail. Use a separately sized motor supply, common signal ground where required, branch protection and a physical power disconnect.
