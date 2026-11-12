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
