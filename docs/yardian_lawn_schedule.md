# Lawn Watering – Yardian Fail-safe Schedule

Runs Yardian Local zones one at a time. Needs the Yardian Local integration
1.1 or newer.

## Setting it up

1. **Controller:** pick the zones in the order they should run, and the
   stop button. Turn weather skips and local rules on or off; their
   sections only appear when they're on.
2. **Schedule:** finish before sunrise or start at a set time, the days,
   and the watering season.
3. Fill in the sensors you have in **Weather** and **Local watering
   rules**. Any you leave empty are simply not checked.

## Fail-safe by design

- Every zone is started with a duration, so the controller stops it even
  if Home Assistant goes down mid-cycle.
- A zone still on 2 minutes past the safety cap is stopped.
- It never waters twice in a day, even after a crash or power cut.
- If Home Assistant or the controller comes back within the late-start
  window, today's watering still runs.

## Skips

Rain in the last day, rain now, cold now or forecast, forecast rain, town
watering days, a watering ban, drought level, odd or even dates, and pickup
days. A sensor that's unavailable never blocks watering.
