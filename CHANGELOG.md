# Changelog

All blueprints share one version number.

## 0.2.0

### Adaptive Light Controller

- Added **Treat Lux Sensor As Dead After** (default 30 min) and **Use Sun
  Position When the Lux Sensor Is Dead** (default on). A lux sensor that
  stops reporting no longer leaves the lights on all day or off all night.
- Minimum Lux to Keep ON ignores a dead sensor.
- Fixed: lights switched by Self-Healing or a configured time were treated
  as a manual change, blocking the next automatic ON/OFF for the Override
  Duration.
- Debug log shows `lux_ok`, `lux_use_sun` and `lux_value`.

### Curtains – Morning Open / Night Close

- Fixed: the morning branch had no end time, so the 15-minute check could
  open the curtains in the evening or at night (right after the evening
  failsafe closed them) whenever the sensor read bright. New input
  **Latest Allowed Time** (default 12:00).
- Fixed: an empty illuminance sensor made the "is it dark" check pass on
  every run. Sensors are now truly optional.
- Added **Treat Sensor As Dead After** (default 30 min): a sensor that stops
  reporting is ignored and the sun takes over.
- Added **Ignore Readings That Don't Match the Sun** (default on).
- Overlapping runs are dropped quietly instead of logging a warning.

### Humidity Automation

- Fixed: "must stay high / normal for N minutes" only compared the reading at
  the start and end of the wait. It now uses the triggers' own `for:`, so the
  value has to stay there the whole time.
- Fixed: every reading started its own delayed run; a sensor reporting every
  few seconds hit the 10-run limit and filled the log with warnings.
- Fixed: shower detection only compared two consecutive readings, so sensors
  that report in small steps never registered a shower.
- The fan now switches when humidity crosses into high / normal, instead of
  being re-sent on every reading. A one-off check runs after a restart.

### Z2M Button

- Moved to the current `triggers:` / `actions:` syntax (needs Home Assistant
  2024.10 or newer). No change in behaviour.

### Indoor Air Helper (HVAC)

- Fixed: a restart in the middle of a boost left the fan on the boost speed
  for good. New input **Finish a Boost Cut Short by a Restart** (default on).

## 0.1.0

- Imported the existing blueprints: Adaptive Light Controller, Curtains –
  Morning Open / Night Close, Indoor Air Helper (HVAC), Humidity Automation,
  Z2M Button and Yardian – Fail-safe Lawn Watering.
- Added `source_url` to each blueprint so **Re-import blueprint** works.
