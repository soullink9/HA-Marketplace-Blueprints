# Curtains – Morning Open and Evening Close

Opens curtains in the morning and closes them in the evening. Either side
can be turned off.

## Setting it up

1. **Curtains:** pick the curtains and turn on "Open in the morning" and/or
   "Close in the evening".
2. In **Morning** and **Evening**, choose what decides it:
   - **It gets bright / dark (light sensor or sun, whichever is first)**
   - **The sun rises / sets**
   - **The light sensor reads bright / dark**

   The light sensor settings only appear when a sensor is part of the
   choice.
3. Optionally set **Not before** and **Not after** for the morning, and a
   time by which the curtains always open or close.

## How it decides

Every time it runs, it re-reads the sensor and the sun and decides from
what they say now. In the morning it only opens between **Not before** and
**Not after**, so curtains you close later in the day stay closed.

## Reliability (collapsed)

- **Catch up after Home Assistant restarts**, and **Re-check every 15
  minutes**: catch anything that was missed. Neither does anything if the
  curtains are already right.
- **Treat a light sensor as offline after:** Home Assistant keeps showing a
  sensor's last value after it stops reporting. Past this time it's
  ignored and the sun is used instead.
- **Ignore light readings that don't match the sun:** never closes for
  "dark" in full daylight or opens for "bright" at night.

## If the curtains move the wrong way

The blueprint only calls open and close and reads the curtain's open or
closed state. If pressing **Open** in Home Assistant closes the curtain, fix
that on the device first (in Zigbee2MQTT: the device's *Settings
(specific)* → `invert_cover`, or the motor's direction setting).
