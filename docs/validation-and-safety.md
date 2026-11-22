# Validation and safety plan

## Before power-on
- Verify supply polarity and voltage with a multimeter.
- Check driver current limits and motor wiring against datasheets.
- Verify ESP32 GPIO voltage compatibility.
- Secure the arm and clear the workspace.
- Test the physical power disconnect.
- Start with current-limited supplies and reduced speed/acceleration.

## Bench-test each actuator
Record exact part number, supplier, voltage, idle/moving/loaded current, temperature after a defined cycle, output torque and speed, repeatability from both directions, backlash, following error and fault behavior.

## Joint acceptance checks
- Calibrated zero and direction.
- Software limits plus mechanical hard stops.
- No unexpected movement at startup.
- Smooth low-speed movement through intended range.
- Feedback agrees with an independent angle measurement.
- Communication/sensor fault causes a safe stop.
- No overheating or supply brownout during repeated cycles.

## Whole-arm progression
1. Test one joint unloaded.
2. Test each joint with representative load.
3. Test the full arm without payload at low speed.
4. Add payload gradually.
5. Test extended horizontal reach and controlled reversals.
6. Increase speed only after thermal and current checks.

## Safety
Keep hands clear of pinch points. Do not hold a stalled motor energized. Add cable strain relief. A software stop is not a substitute for a physical disconnect. Inspect printed parts, layer orientation, fasteners and bearing seats regularly. Never leave the prototype powered unattended.
