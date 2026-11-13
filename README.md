<img src="brand/icon.png" alt="HA-Marketplace-Blueprints icon" width="128" align="right">

# Home Assistant Blueprints

My Home Assistant automation blueprints, one folder each. Every blueprint
imports straight from GitHub and can be updated later with **Re-import
blueprint**.

## Disclosure

These blueprints are written and maintained by me with the help of AI
(Claude). I run every one of them in my own home before it is published,
but they are shared as-is, with no warranty. Read what a blueprint does
before you point it at your lights, HVAC or water.

## Blueprints

### Adaptive Light Controller

One room's lights on presence and/or a time / sun / lux schedule, with
circadian brightness, OFF guards and manual-override protection.

[![Import blueprint](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fsoullink9%2FHA-Marketplace-Blueprints%2Fblob%2Fmain%2Fblueprints%2Fadaptive_light_controller%2Fadaptive_light_controller.yaml)
· [Docs](docs/adaptive_light_controller.md)

### Curtains – Morning Open / Night Close

Opens curtains in the morning and closes them at night from an illuminance
sensor and/or the sun, with restart, periodic and failsafe-time protection.

[![Import blueprint](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fsoullink9%2FHA-Marketplace-Blueprints%2Fblob%2Fmain%2Fblueprints%2Fopen_close_curtains%2Fopen_close_curtains.yaml)
· [Docs](docs/open_close_curtains.md)

### Indoor Air Helper (HVAC)

Boosts the HVAC fan when CO₂, humidity, VOCs or PM2.5 go above a limit,
then puts the fan back the way it was.

[![Import blueprint](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fsoullink9%2FHA-Marketplace-Blueprints%2Fblob%2Fmain%2Fblueprints%2Fhvac_indoor_air_helper%2Fhvac_indoor_air_helper.yaml)
· [Docs](docs/hvac_indoor_air_helper.md)

### Humidity Automation (Fan Control + Shower Detection)

Bathroom fan on high humidity or a fast rise (shower), off when the room
dries out, with an optional whole-house ambient blocker.

[![Import blueprint](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fsoullink9%2FHA-Marketplace-Blueprints%2Fblob%2Fmain%2Fblueprints%2Fhumidity_control%2Fhumidity_control.yaml)
· [Docs](docs/humidity_control.md)

### Z2M Button – Single / Double / Hold (+ Release)

Actions for single, double, hold and release on a Zigbee2MQTT button.

[![Import blueprint](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fsoullink9%2FHA-Marketplace-Blueprints%2Fblob%2Fmain%2Fblueprints%2Fz2m_button%2Fz2m_button.yaml)
· [Docs](docs/z2m_button.md)

### Yardian – Fail-safe Lawn Watering

Runs Yardian Local zones one at a time before sunrise or at a fixed time,
with weather and town-rule skips. Needs the Yardian Local integration.

[![Import blueprint](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fsoullink9%2FHA-Marketplace-Blueprints%2Fblob%2Fmain%2Fblueprints%2Fyardian_lawn_schedule%2Fyardian_lawn_schedule.yaml)
· [Docs](docs/yardian_lawn_schedule.md)

## Learn more

Installing, updating and per-blueprint details are in the [docs](docs/)
folder. Changes are listed in [CHANGELOG.md](CHANGELOG.md).
