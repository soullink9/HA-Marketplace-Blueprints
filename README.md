<img src="brand/icon.png" alt="HA-Marketplace-Blueprints icon" width="128" align="right">

# Home Assistant Blueprints

My Home Assistant automation blueprints, one folder each. Every blueprint
imports straight from GitHub and can be updated later with **Re-import
blueprint**.

**Requires Home Assistant 2026.11 or newer.** The blueprints are built for
the current release only and use its newer features, such as settings that
appear only when they apply.

## Disclosure

These blueprints are written and maintained by me with the help of AI
(Claude). I run every one of them in my own home before it is published,
but they are shared as-is, with no warranty. Read what a blueprint does
before you point it at your lights, HVAC or water.

## Blueprints

### Adaptive Lights – Automatic Room Lighting

Turns a room's lights on and off with presence sensors or a schedule, and
can match brightness and color to the time of day.

[![Import blueprint](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fsoullink9%2FHA-Marketplace-Blueprints%2Fblob%2Fmain%2Fblueprints%2Fadaptive_light_controller%2Fadaptive_light_controller.yaml)
· [Docs](docs/adaptive_light_controller.md)

### Curtains – Morning Open and Evening Close

Opens curtains in the morning and closes them in the evening, using a light
sensor, the sun, or both.

[![Import blueprint](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fsoullink9%2FHA-Marketplace-Blueprints%2Fblob%2Fmain%2Fblueprints%2Fopen_close_curtains%2Fopen_close_curtains.yaml)
· [Docs](docs/open_close_curtains.md)

### Indoor Air – HVAC Fan Boost

Boosts the HVAC fan when CO₂, humidity, VOCs or PM2.5 get too high, then
puts the fan back once the air is clean.

[![Import blueprint](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fsoullink9%2FHA-Marketplace-Blueprints%2Fblob%2Fmain%2Fblueprints%2Fhvac_indoor_air_helper%2Fhvac_indoor_air_helper.yaml)
· [Docs](docs/hvac_indoor_air_helper.md)

### Bathroom Fan – Humidity and Shower Control

Runs the bathroom fan when you shower or the air gets humid, and turns it
off once the room has dried out.

[![Import blueprint](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fsoullink9%2FHA-Marketplace-Blueprints%2Fblob%2Fmain%2Fblueprints%2Fhumidity_control%2Fhumidity_control.yaml)
· [Docs](docs/humidity_control.md)

### Zigbee2MQTT Button – Single, Double, Hold and Release

Runs your actions when a Zigbee2MQTT button is pressed once, pressed twice,
held or released.

[![Import blueprint](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fsoullink9%2FHA-Marketplace-Blueprints%2Fblob%2Fmain%2Fblueprints%2Fz2m_button%2Fz2m_button.yaml)
· [Docs](docs/z2m_button.md)

### Lawn Watering – Yardian Fail-safe Schedule

Waters Yardian zones one at a time before sunrise or at a set time, and
skips days with rain, frost or local restrictions. Needs the Yardian Local
integration.

[![Import blueprint](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fsoullink9%2FHA-Marketplace-Blueprints%2Fblob%2Fmain%2Fblueprints%2Fyardian_lawn_schedule%2Fyardian_lawn_schedule.yaml)
· [Docs](docs/yardian_lawn_schedule.md)

## Learn more

Installing, updating and per-blueprint details are in the [docs](docs/)
folder. Changes are listed in [CHANGELOG.md](CHANGELOG.md).
