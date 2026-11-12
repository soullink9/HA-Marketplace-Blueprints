# Curtains – Morning Open / Night Close

Opens curtains in the morning and closes them at night. Either side can be
turned off on its own.

## How it decides

- **Evening:** close when the illuminance sensor stays below the evening
  threshold, or (optionally) when the sun drops below an elevation.
- **Morning:** open when the sensor stays above the morning threshold, or
  (optionally) when the sun rises above an elevation — never before the
  Earliest Allowed Time.
- **Failsafe times (optional):** force-close / force-open at a fixed time
  no matter what the sensors say.

## Outer protections

- **Re-check on restart:** re-evaluates on every Home Assistant start, so a
  crossing that happened while HA was down still gets acted on.
- **Periodic safety check:** every 15 minutes, checks whether the curtains
  match current conditions.
