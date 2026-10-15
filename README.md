# OVERRIDE
# Override V5 PID Competition Template

This is a VEXcode V5 C++ competition project for the 2026-2027 game, **Override**.  It includes:

- PID distance driving that holds the starting heading with the inertial sensor.
- PID turns using the inertial sensor.
- Competition callbacks for autonomous and driver control.
- Five autonomous routine slots (red / blue, positive / negative, and skills).
- Arcade driver control plus example intake, lift, and pneumatic-clamp controls.

## Use it in VEXcode V5

1. Create a **C++ Competition Template** project in VEXcode V5.
2. Replace its `src/main.cpp` and `include/robot-config.h` with the files here. Add `src/robot-config.cpp` to the project.
3. In `include/robot-config.h` and `src/robot-config.cpp`, change the ports, reversed flags, cartridge ratios, wheel size, and external gearing to match the robot exactly.
4. Put the intended path in the selected autonomous routine in `src/main.cpp`. Start with slow, open-field tests and tune one PID loop at a time.

## Controls

| Control | Action |
| --- | --- |
| Left stick up/down | Drive forward / reverse |
| Right stick left/right | Turn |
| R1 / R2 | Intake forward / reverse |
| L1 / L2 | Lift up / down |
| A | Toggle pneumatic clamp |
| B | Toggle drive brake between coast and hold |

## Before running

- The **inertial sensor must be mounted rigidly** and facing forward. Do not move the robot while it calibrates.
- Verify that `driveDistance(+)` drives forward and `turnToHeading(90)` turns clockwise. Correct motor reversals first; then tune PID.
- The factory PID values are safe starting points, not universal values. Tune `kDriveP`, `kDriveD`, `kTurnP`, and `kTurnD` in `src/main.cpp` with the robot on its actual wheels.
- Driver input is limited to 100%. The autonomous helper limits output to 10 V by default; raise only after it drives reliably.

## Tune order

1. Set I gains to zero (they already are).
2. Increase P until each motion begins to oscillate, then back it off.
3. Increase D just enough to stop the overshoot.
4. Add a very small I gain only if a consistent final-position error remains.

The Override autonomous period is 15 seconds and driver control is 1:45. Design the chosen routine to end comfortably before the autonomous cutoff and update it after field testing.

