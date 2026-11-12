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

## Ambient blocker

Pick a humidity sensor elsewhere *inside* the house. The fan then only
turns on when this room is noticeably more humid than the rest of the
house, so a muggy day doesn't run the fan. Don't use an outdoor sensor.

## Manual override protection

Point it at the fan (and/or humidifier). After you change it by hand, the
automation leaves it alone for the protection duration.
