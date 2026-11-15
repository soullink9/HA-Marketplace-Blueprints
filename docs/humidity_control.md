# Humidity Automation (Fan Control + Shower Detection)

Bathroom fan control. Turns the fan on when humidity is high or rises
quickly (a shower) and off again when the room dries out.

## Sides

- **High humidity (fan):** on above the High Humidity Level, off below it
  minus the Buffer Zone.
- **Low humidity (humidifier, optional):** on below the Low Humidity Level,
  off above it plus the Buffer Zone.
- **Shower detection (optional):** a fast rise in humidity runs its own
  actions.

## Timing

"Must stay high / normal for N minutes" means continuously: any reading
back across the line restarts the wait. The fan is switched when humidity
*crosses* into high or normal and stays there, not on every reading, so a
fan you turn on by hand while the room is dry is left on. After a Home
Assistant restart the automation checks once where humidity is and switches
the fan to match.

## Shower detection

A shower is a rise of **How Much Humidity Must Rise** within **How Fast the
Rise Must Happen** (default 5 minutes), measured from the reading before the
climb started, so it also catches a rise spread over a few readings. Many
sensors only report every one to two minutes, so the shower is detected at
the first reading that shows the jump. A reading coming back from
`unavailable` or `unknown` never counts as a rise.

If you set the **Fan Entity**, detection is skipped while the fan is already
on, which also stops the shower actions running twice for one shower.
Without it, keep the shower actions safe to repeat (e.g. "turn on").

## Turning the fan off

The fan turns off in whichever of these happens first:

- **Back to normal:** humidity stays below the High Humidity Level minus the
  Buffer Zone (or back near ambient) for the set time.
- **Stopped falling** (on by default): after this automation turns the fan
  on for a shower or high humidity, it waits for humidity to peak and start
  falling, then turns the fan off once no new reading has arrived for
  **Stopped Falling After** (default 10 minutes). This catches a room that
  settles above the High Humidity Level, for example with the door open or
  on a humid day, which used to leave the fan on until humidity finally
  dropped. A long flat stretch at the top while the water is still running
  doesn't count, because humidity hasn't started falling yet.

With the Fan Entity set, "Stopped falling" only turns off a fan this
automation turned on, and never one that is already off. A Home Assistant
restart cancels the wait, and then only the "back to normal" rule applies.

A sensor dropping out (`unavailable`) and coming back never turns the fan
off on its own. Before 0.4.0 it could, 5 minutes after the sensor returned.

## Ambient blocker

Pick a humidity sensor elsewhere *inside* the house. The fan then only
turns on when this room is noticeably more humid than the rest of the
house, so a muggy day doesn't run the fan. Don't use an outdoor sensor.

## Manual override protection

Uses the Fan Entity (and the humidifier entity for the low side). After you
change it by hand, the automation leaves it alone for the protection
duration.
