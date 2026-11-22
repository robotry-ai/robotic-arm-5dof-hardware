# Actuator architecture comparison

| Architecture | Feedback | Strengths | Drawbacks | Best use |
|---|---|---|---|---|
| NEMA 17 + magnetic encoder | External encoder at motor or joint | Flexible gearing, widely available, many driver options | Bulkier, heavier, more tuning; open-loop steppers can lose steps | Experimental precision joints |
| Metal-gear RC servo + external encoder | Encoder on actual joint output | Low entry cost, simple PWM control | Internal servo loop is opaque; backlash remains; high current spikes | Budget prototype |
| Smart serial bus servo (SC15 class) | Onboard position/load/voltage telemetry | Compact wiring, addressable bus, integrated feedback | Model-specific protocol, limited travel/torque, cost per axis | Compact feedback arm |

## Preliminary recommendation
Build a single-joint test rig before buying five actuators. Measure output repeatability, backlash on reversal, torque at target speed, peak/continuous current, temperature and ESP32 integration effort.

Smart servos are the most straightforward route to integrated telemetry. NEMA 17 systems offer flexibility but require more mechanical/control engineering. RC servos are economical but an external encoder does not make the servo's internal loop closed-loop at the joint.

## Weighted decision matrix template

| Criterion | Weight | Stepper + encoder | RC servo + encoder | Smart servo |
|---|---:|---:|---:|---:|
| Output feedback | 20% | TBD | TBD | TBD |
| Torque at speed | 20% | TBD | TBD | TBD |
| Cost in India | 15% | TBD | TBD | TBD |
| Mechanical integration | 10% | TBD | TBD | TBD |
| Wiring/control simplicity | 15% | TBD | TBD | TBD |
| Backlash/repeatability | 10% | TBD | TBD | TBD |
| Availability/support | 10% | TBD | TBD | TBD |

Score only after checking datasheets and bench measurements.
