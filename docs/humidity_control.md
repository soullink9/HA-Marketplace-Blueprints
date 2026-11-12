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
Rise Must Happen**, measured from the reading where the climb started — so
it works with sensors that report in 1–2 % steps. If you set the Manual
Override high-side entity (your fan), detection is skipped while the fan is
already on, which also stops the shower actions running twice for one
shower. Without it, keep the shower actions safe to repeat (e.g. "turn on").

## Ambient blocker

Pick a humidity sensor elsewhere *inside* the house. The fan then only
turns on when this room is noticeably more humid than the rest of the
house, so a muggy day doesn't run the fan. Don't use an outdoor sensor.

## Manual override protection

Point it at the fan (and/or humidifier). After you change it by hand, the
automation leaves it alone for the protection duration.
