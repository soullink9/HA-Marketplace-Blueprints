# Adaptive Lights – Automatic Room Lighting

One automation per room. You answer three questions, and only the settings
for your answers are shown.

## Setting it up

1. **Lights:** pick the room's lights, then choose how they turn on and off:
   - **Motion or presence sensors:** lights come on when someone is there
     (and the schedule allows it), and go off once nobody has been there
     for the time you set.
   - **A schedule only:** lights simply follow the schedule.
2. **Presence** (sensors only): pick the sensors and how long the room must
   be empty before the lights go off.
3. **When lights should be on:** pick one rule. Only its settings appear.

| Rule | Settings shown |
|---|---|
| Any time someone is there (presence only) | none |
| Between set times | From, Until |
| When the sun is down | Sun counts as down below |
| When the room is dark (light sensor) | Light sensor settings |
| When the sun is down and the room is dark | Sun and light sensor settings |
| Between set times, once it's dark (light sensor) | From, Until, light sensor settings |
| Between set times, or when the sun is down and the room is dark | All three |
| Between set times, when the sun is down, or when the room is dark | All three |

That's a working setup. Everything below is optional and collapsed.

## Common setups

- **Hallway or closet light:** presence sensors, "Any time someone is there".
- **Living room in the evening:** presence sensors, "When the sun is down".
- **Porch light:** schedule only, "When the sun is down".
- **Night light:** schedule only, "Between set times".
- **Yard or string lights, on at dusk and off at bedtime:** schedule only,
  "Between set times, once it's dark". Set **From** to the earliest time
  they may come on (for example 16:00) and **Until** to bedtime (for
  example 22:00). They come on when it gets dark after From, go off at
  Until, and stay off until From the next day.

## Optional sections

- **Brightness and color:** bright and cool at midday, dim and warm after
  sunset, with quiet hours that stay dim even after an early sunrise.
  Lights that are already on fade slowly to match.
- **Manual changes:** after someone switches a light by hand, the
  automation leaves it alone for a while.
- **Exceptions:** don't change the lights while media is playing, don't turn
  on or off while certain sensors are on (for example "in bed"), or never
  turn off during set hours.
- **Advanced:** the 5-minute re-check and debug logging.

## Rules with "or"

"Or" rules keep the lights on while any part says on. With "Between set
times, or when the sun is down and the room is dark", lights stay on after
Until for as long as it's dark, so they're on all night. For lights that
should go off at a set time even in the dark, use "Between set times, once
it's dark".

The automation never asks for on and off at the same time, so it can't
toggle the lights back and forth, whatever the settings.

A light reading must stay dark or bright for 2 minutes before it switches
the lights, and "Bright above" is always at least 1.5 × "Dark below", so a
passing cloud doesn't flicker them.

Unchecked **Days** only stop the lights turning on. They still turn off,
so a window that runs past midnight into an unchecked day still ends.

## When the light sensor goes offline

Home Assistant keeps showing a sensor's last value after it stops
reporting. A light sensor that hasn't reported for **Treat the light
sensor as offline after** (default 30 minutes) is ignored, and with **Use
the sun while the light sensor is offline** on, the sun takes its place.

## Manual changes and the automation's own timers

A change with no automation behind it looks manual (physical switches look
like this). The automation's own timed runs look the same, so a change in
the first 10 seconds of a 5-minute mark, or of one of your set times, is
treated as the automation's own.

After a restart, every light looks freshly changed. Changes in the first 5
minutes after Home Assistant starts (or automations reload) aren't counted
as manual, so a restart doesn't start the pause.

## Troubleshooting

Turn on **Debug logging** under Advanced. Each run writes one line to
**Settings → System → Logs** with every check, so you can see why it did or
didn't act. The lines include entity IDs and states, so turn it off when
you're done and check the log before sharing it.

## Only lights

To control a plain switch, wrap it first: **Settings → Devices & services →
Helpers → Create helper → Switch as X → Light**.
