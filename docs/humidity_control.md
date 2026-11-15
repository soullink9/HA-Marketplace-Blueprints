# Bathroom Fan – Humidity and Shower Control

Runs the bathroom fan when you shower or the air gets humid, and turns it
off once the room has dried out.

## Setting it up

1. **Sensor and fan:** pick the humidity sensor, a humidity sensor
   elsewhere in the house (optional, recommended) and the fan, then turn on
   what you want:
   - **Detect showers:** the fan comes on as soon as humidity jumps.
   - **Turn the fan on when humidity is high:** also catches humidity that
     builds up slowly.
   - **Run a humidifier when it's too dry.**
2. Fill in the actions in each section that appears (usually "turn on the
   fan").
3. **Turning the fan off:** add the action that turns the fan off.

Picking the **Fan** is recommended. The automation then knows when the fan
is already on, and only turns off a fan it turned on itself.

## Shower detection

A shower is a rise of at least the set amount (default 8%) within the set
time (default 5 minutes), measured from the reading before the climb
started. Most sensors only report every one to two minutes, so the shower
is detected at the first reading that shows the jump. A sensor coming back
after a dropout never counts as a rise.

## Turning the fan off

The fan turns off at whichever comes first:

- **Below the limit:** humidity stays under the turn-on level minus the
  buffer (or back close to the rest of the house) for the set time.
- **Back close to the house** (with a house sensor): see below.
- **Stopped falling** (on by default): after a shower or high humidity, the
  automation waits for humidity to peak and start falling. Once there has
  been no new reading for the set time (default 10 minutes), the room has
  stopped drying out and the fan turns off. This stops the fan running all
  day when the room settles above the turn-on level, for example with the
  door open or on a humid day. A long flat stretch at the top while the
  water is still running doesn't count, because humidity hasn't started
  falling yet.

A Home Assistant restart cancels the "stopped falling" wait; after that,
only "below the limit" applies. A sensor dropping out and coming back
never turns the fan off.

## Comparing with the rest of the house

Pick a humidity sensor in another room (not outdoors) under **Humidity
elsewhere in the house**. The automation then cares about this room being
more humid than the rest of the house, not about the number on its own:

- **Showers:** a jump only counts if the room also ends up at least the set
  difference (default 10%) above the house. A rise the whole house shares
  isn't a shower.
- **High humidity:** the fan only turns on when the room is above the
  turn-on level *and* that far above the house, so a muggy day doesn't run
  it.
- **Turning off:** the fan turns off as soon as the room is back within the
  difference minus the buffer of the house. After a shower this works
  while "Turn off once humidity stops falling" is on (the default).

If the house sensor is unavailable, these checks are skipped and the
regular levels apply.

## Manual changes

After someone switches the fan (or humidifier) by hand, the automation
leaves it alone for the set time.
