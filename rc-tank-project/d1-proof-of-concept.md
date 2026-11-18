# Day 1 - Proof of concept

**Date:** November 18, 2026
**Phases:** [Phase 0: Separate control experiments](https://github.com/HiMyNamesSeb/rc-tank/tree/main/phase-0-separate-control) · [Phase 1: Proof of concept](https://github.com/HiMyNamesSeb/rc-tank/tree/main/phase-1-proof-of-concept)

Today was the first real day of the RC tank. The plan for the tank is treads, a turret that turns left and right, and a barrel that tilts up and down. Today was all about the turret and barrel, on a breadboard, using parts from my ELEGOO starter kit.

## Part 1 - Getting each motor to move (Phase 0)

Before anything else I wanted to know I could actually make the motors move. I hooked up a joystick module, an SG90 servo and a 28BYJ-48 stepper motor with its ULN2003 driver board.

- **tankV1** used the built-in `Stepper` library. Joystick Y moved the servo, joystick X stepped the stepper.
- **tankV2** switched to `AccelStepper` so the joystick could set the stepper's **speed** instead of a step count.

Both worked, but neither felt right:

- In V1, `Stepper.step()` **blocks**. While the stepper is stepping, the Arduino can't do anything else, so the servo and stepper can't move at the same time.
- In V2, `runSpeed()` only takes one step each time it's called, and my `delay(30)` meant it only got called about 33 times a second. So the stepper was capped at around 33 steps per second no matter how far I pushed the joystick.

## Part 2 - The demo (Phase 1)

Next I set it up the way the tank will actually use it, on an Arduino Nano:

- **Servo = barrel elevation** (up/down), signal on D9
- **Stepper = turret rotation** (left/right), ULN2003 IN1-IN4 on D4-D7

I used the kit's breadboard power module at 5V for the motors, kept the Nano running off the computer's USB, and tied all the grounds together on one GND rail.

Before the full demo I ran two small sketches, one for just the servo and one for just the stepper, to make sure the wiring was right on its own.

The demo sketch is controlled by typing commands in the Serial Monitor (`e120` for barrel angle, `u`/`d` to nudge it, `t90` to turn the turret, `demo` to move both). The big difference from Phase 0 is that the loop **never waits**. Every pass it just checks: is it time to move the servo one degree? Is it time to take one stepper step? That's why both motors can move together.

**First run: nothing happened.** I thought something was wrong, but the sketch was just sitting there waiting for me to type a command. Typing `demo` made the barrel tilt and the turret spin at the same time. 🎉

## What I learned
- `delay()` and blocking functions are the enemy when you want two things moving at once. Checking `millis()` / `micros()` and only acting when it's time fixes it.
- The 28BYJ-48 needs its pins in the order IN1, IN3, IN2, IN4 with the `Stepper` library, or it just buzzes.
- Every ground has to meet on the same rail. A missing shared ground makes the servo twitch and things act random.
- The microcontroller and the motors can run from different power sources, as long as they share ground.
- When a sketch "does nothing", check whether it's waiting for input before assuming the wiring is wrong.

## Next up
Phase 2: drive motors and treads. That means a tread chassis, a TB6612FNG motor driver, a battery and a 5V buck converter, none of which I've bought yet.

---

## Credits
Built with help from online electrical engineering tutorials. Claude was used for formatting and presentation.
