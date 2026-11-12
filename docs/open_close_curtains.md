# Curtains – Morning Open / Night Close

Opens curtains in the morning and closes them at night. Either side can be
turned off on its own.

## How it decides

- **Evening:** close when the illuminance sensor stays below the evening
  threshold, or (optionally) when the sun drops below an elevation.
- **Morning:** open when the sensor stays above the morning threshold, or
  (optionally) when the sun rises above an elevation — only between the
  **Earliest** and **Latest Allowed Time**.
- **Failsafe times (optional):** force-close / force-open at a fixed time
  no matter what the sensors say.

Triggers only wake the automation up. Every time it runs, it re-reads the
sensor and the sun and decides from what they say *now*.

## Outer protections

- **Re-check on restart:** re-evaluates on every Home Assistant start, so a
  crossing that happened while HA was down still gets acted on.
- **Periodic safety check:** every 15 minutes, checks whether the curtains
  match current conditions.
- **Treat Sensor As Dead After:** a sensor that hasn't reported for this
  many minutes is ignored and the sun elevation thresholds take over, even
  if the sun options are off. Home Assistant keeps showing a weather
  station's last value when it stops sending, so without this a station
  that went quiet overnight would keep saying "dark" all morning.
- **Ignore Readings That Don't Match the Sun:** never closes on a "dark"
  reading while the sun is above 10°, and never opens on a "bright" reading
  while the sun is below -6°. Failsafe times ignore this.

## Why there is a Latest Allowed Time

Without an end to the morning window, the 15-minute check could open the
curtains any time after the Earliest Allowed Time until midnight — for
example 15 minutes after the evening failsafe closed them, if the sensor
was stuck on a bright value. It also means curtains you close in the
afternoon stay closed.

## If the curtains move the wrong way

The blueprint only ever calls `cover.open_cover` / `cover.close_cover` and
reads the cover's `open` / `closed` state. If pressing **Open** on the
curtain in Home Assistant closes it, or the state says `open` while it is
closed, fix that on the device first (in Zigbee2MQTT: the device's
*Settings (specific)* → `invert_cover`, or the motor's direction /
calibration setting). The blueprint can't tell the difference.
