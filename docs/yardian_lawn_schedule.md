# Yardian – Fail-safe Lawn Watering

Runs Yardian Local zones one at a time. Needs the Yardian Local integration
1.1 or newer.

## Fail-safe by design

- Every zone is started **with a duration**, so the controller stops it on
  its own even if Home Assistant dies mid-cycle.
- A watchdog stops any zone that stays on longer than the per-zone cap
  plus 2 minutes.
- It never waters twice in a day, even after a crash or power cut.

## Schedule

- **Finish before sunrise:** the start time is worked out from your home
  location and the total cycle length.
- **Fixed start time:** starts at the time you set.
- **Late-start window:** if Home Assistant or the controller comes back
  within this many minutes after the start and today hasn't run yet, it
  starts then.

## Skips

Rain in the last day, raining now, low temperature, forecast rain or cold,
town watering days, a total ban, drought level, odd/even dates and pickup
days. Every sensor is optional; an unavailable sensor never blocks watering.
