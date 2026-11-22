# Torque and power sizing

Final motor selection is blocked until CAD provides link lengths, masses, centre-of-mass locations, payload and target acceleration.

## Static gravity torque
For a horizontal arm, a first-pass joint torque is:

tau_j = sum(m_i * g * r_ij)

where m_i is each downstream link/actuator/cable/payload mass, g = 9.81 m/s^2, and r_ij is the perpendicular moment arm from joint j to that item's centre of mass.

## Dynamic torque
A first-pass estimate is:

tau_design = (tau_gravity + tau_inertia) * safety_factor

Calculate inertia torque from mass moments of inertia and desired angular acceleration. Select a safety factor based on uncertainty, duty cycle, shock loading and printed-part reliability.

## Gear reduction
tau_output is approximately tau_motor * gear_ratio * drivetrain_efficiency. Also check output speed, gearbox backlash, bearing loads and reflected inertia.

## Electrical sizing
For every actuator, record rated/continuous current, peak/stall current, duty cycle and supply voltage. Estimate simultaneous peak demand from the planned motion profile, then add margin and verify with current measurements. Stall current is a fault condition, not a normal operating target.

## Required CAD inputs
- Link lengths and joint-axis positions.
- Mass and centre of mass of every link.
- Actuator, bracket and cable masses.
- Payload mass and centre of mass.
- Joint speed, acceleration, travel and hard stops.
- Intended duty cycle.

Create one worksheet row per joint and worst-case pose. Include gravity torque, inertia torque, efficiency, safety factor, required output torque/speed, selected actuator torque at that speed and margin. Test the horizontal extended pose and acceleration/reversal cases.
