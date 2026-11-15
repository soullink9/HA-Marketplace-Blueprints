# Changelog

All blueprints share one version number.

## 0.4.0

### All blueprints

- The version now shows in Home Assistant: in each blueprint's name (for
  example "Indoor Air Helper · v0.4.0") and at the top of its description,
  with a link to this changelog. After **Re-import blueprint** you can see
  which version you have.

### Humidity Automation

- Added **Turn Off Once Humidity Stops Falling** (default on) and **Stopped
  Falling After** (default 10 min). After the automation turns the fan on
  for a shower or high humidity, it waits for humidity to peak and fall,
  then turns the fan off once readings stop changing. A room that settles
  above the High Humidity Level (door open, humid day) no longer leaves the
  fan on. With the Fan Entity set, it only turns off a fan it turned on.
- Fixed: a humidity sensor dropping out and coming back re-armed "back to
  normal" and ran the off actions 5 minutes later, even with humidity
  unchanged. With a light/fan combo this could switch off a light someone
  was using. Only a real reading can trigger the off actions now (low side
  too).
- **How Fast the Rise Must Happen** now defaults to 5 minutes (was 2). Many
  sensors report only every one to two minutes, so 2 minutes often covered
  a single reading.
- The fan entity and the off actions moved to a new **Fan and turning it
  off** group, because shower detection and the high side both use them.
  "What To Do When Humidity Is Back to Normal" now always shows, so it works
  with shower detection alone. Input names are unchanged.

## 0.3.0

Built for Home Assistant 2026.11. Older versions are no longer supported.

### All blueprints

- **Breaking:** every blueprint now needs Home Assistant 2026.11 or newer
  (`min_version: 2026.11.0`). Adaptive Light Controller had no minimum
  before.
- Settings that only matter when another one is on are hidden until then,
  using the new conditional inputs in 2026.11. A hidden setting goes back
  to its default. Every hidden setting was already ignored in that case,
  so existing automations behave the same.
- Entity and device pickers use the current `filter:` form.
- Added `author` to each blueprint.
- Added the repo icon (`brand/icon.svg`, with `icon.png` at 256 px and
  `icon@2x.png` at 512 px) and shown it on the front page.

### Adaptive Light Controller

- Hidden until they apply: Time Window times, Lux ON/OFF thresholds and the
  dead-sensor sun fallback, all Circadian settings, Media Player Entities,
  OFF Block Window times, and the Manual Override direction and duration.
  The lux sensor and Treat Lux Sensor As Dead After always show, because
  Minimum Lux to Keep ON uses them too.
- The own-clock check for manual override now only counts the Time Window,
  Quiet Hours and OFF Block Window times that are turned on.
- Removed the fallback for the old `auto` Ambient Logic Preset value. An
  automation still set to `auto` must pick a preset again.

### Curtains – Morning Open / Night Close

- Settings are grouped into Curtains, Evening close, Morning open and
  Protections. The Evening and Morning groups hide when that side is off,
  and each failsafe time hides until its failsafe is on.

### Indoor Air Helper (HVAC)

- Each pollutant's sensors and limit hide until it is turned on. Fallback
  Fan Speed and Finish a Boost Cut Short by a Restart hide when Return Fan
  Afterwards is off. Switch to Fan Only hides unless When to Boost is
  "Any time".

### Humidity Automation

- Settings are grouped into Sensor, High humidity, Low humidity, Shower
  detection, Manual override protection and Debugging, and each side's
  settings hide until it is turned on. The fan entity for manual override
  always shows, because shower detection uses it too.
- The humidity and ambient sensor pickers only list humidity sensors.

### Yardian – Fail-safe Lawn Watering

- Finish This Long Before Sunrise shows only in sunrise mode, and Fixed
  Start Time only in fixed mode.

## 0.2.1

### Indoor Air Helper (HVAC)

- Fixed: Home Assistant 2026.11 refused to load the blueprint ("expected str
  at …supported_features[0][0]. Got None"). The thermostat picker no longer
  filters on fan-mode support, so it lists every thermostat.

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
