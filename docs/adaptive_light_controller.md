# Adaptive Light Controller

Controls one room's lights. Every setting in Home Assistant has its own
explanation, so this page covers how the pieces fit together.

## How it decides

1. **Ambient Logic (Sections 3–6)** combines up to three votes — Time
   Window, Sun Position and Lux — into one ON/OFF answer using the preset
   you pick.
2. **Presence (Section 2, optional)** is the main trigger when set: presence
   turns the lights on if Ambient Logic agrees, and clearing for the OFF
   Delay turns them off.
3. **Self-Healing (Section 10)** re-applies the Ambient Logic answer every 5
   minutes, so a missed trigger fixes itself. With no presence sensors this
   is what drives the lights.
4. **Guards (Sections 8–9)** get the final say: Media Guard, Minimum Lux to
   Keep ON, OFF Block Window, Block Entities and Manual Override.

## When the lux sensor stops reporting

Home Assistant keeps showing a sensor's last value after it stops sending.
A weather station that goes quiet overnight would keep saying "dark" all
morning (lights on in daylight), or one that dies in the afternoon would
keep saying "bright" all night.

- **Treat Lux Sensor As Dead After** (Section 5, default 30 minutes): if the
  sensor hasn't reported for this long, its value is ignored.
- **Use Sun Position When the Lux Sensor Is Dead** (Section 5, default on):
  while the sensor is dead or unavailable, the sun casts the lux vote using
  the Sun Elevation Threshold from Section 4.

The debug log line shows `lux_ok`, `lux_use_sun` and `lux_value`.

## Manual override and the automation's own clock

Manual-override protection treats a change with no parent context as
"manual" (physical switches look like this). Runs started by a clock —
Self-Healing every 5 minutes and the Time Window, Quiet Hours and OFF Block
Window times — have no parent context either, so the automation's own
clock-driven ON/OFF used to count as manual and block the opposite action
for the whole Override Duration. Changes in the first 10 seconds of those
minutes are now treated as the automation's own.

Lights that drop off the Zigbee network and come back also have no parent
context, so they can still briefly look like a manual change.

## Circadian brightness

When on, every automatic ON sets brightness and colour temperature from the
sun's elevation, capped during Quiet Hours. Lights that are already on fade
toward the target on each 5-minute check.

## Only `light.*` targets

To control a plain switch, wrap it first: **Settings → Devices & services →
Helpers → Create helper → Switch as X → Light**.

## Troubleshooting

Turn on **Debug Logging** (Section 11). Each run writes one line to
**Settings → System → Logs** with every vote and guard, so you can see why
it did or didn't act.
