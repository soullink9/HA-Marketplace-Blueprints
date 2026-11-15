# Docs

| Blueprint | Page |
|---|---|
| Adaptive Lights – Automatic Room Lighting | [adaptive_light_controller.md](adaptive_light_controller.md) |
| Curtains – Morning Open and Evening Close | [open_close_curtains.md](open_close_curtains.md) |
| Indoor Air – HVAC Fan Boost | [hvac_indoor_air_helper.md](hvac_indoor_air_helper.md) |
| Bathroom Fan – Humidity and Shower Control | [humidity_control.md](humidity_control.md) |
| Zigbee2MQTT Button | [z2m_button.md](z2m_button.md) |
| Lawn Watering – Yardian Fail-safe Schedule | [yardian_lawn_schedule.md](yardian_lawn_schedule.md) |

## Requirements

Home Assistant 2026.11 or newer. Every blueprint sets this as its
`min_version`, so older versions refuse to import it with a clear message.
The blueprints are built only for the current release, so this minimum
goes up when a release uses a newer Home Assistant feature.

## Installing

Use the **Import blueprint** button for the blueprint on the
[front page](../README.md), or in Home Assistant go to
**Settings → Automations & scenes → Blueprints → Import blueprint** and
paste the GitHub link to the blueprint's `.yaml` file. Home Assistant saves
it under `blueprints/automation/soullink9/`.

## Updating

Every blueprint has a `source_url`, so Home Assistant knows where it came
from. To update: **Settings → Automations & scenes → Blueprints**, open the
⋮ menu on the blueprint and choose **Re-import blueprint**. Automations that
use it pick up the new version after the re-import; their settings are kept.

If a release adds a new input, it always has a default, so existing
automations keep working without being edited.

## Settings that only show when they apply

Each blueprint starts with what you have and what you want it to do.
Sections and settings for a feature only appear once you turn that feature
on, so you only see what applies to you. A hidden setting
goes back to its default and is ignored, so turning a feature off and on
again resets its settings to the defaults.

### Moving an existing copy over to GitHub updates

If you already have a copy saved by hand (for example under
`blueprints/automation/soullink/`), replace that file's contents with the
version from this repo once. It then carries the `source_url`, and
**Re-import blueprint** works on it from then on. The file path stays the
same, so the automations using it don't need to change.

## Writing style

New and changed blueprints follow the [writing and layout guide](STYLE.md).

## Versions

Each blueprint shows its version in its name in Home Assistant (for
example "Bathroom Fan – Humidity and Shower Control · v0.6.0") and at the
top of its description, so after a **Re-import blueprint** you can see at a
glance which version you have. It's also on the first line of each file.

A blueprint's version only goes up when that blueprint changes. It matches
the release (git tag) it last changed in, so different blueprints can show
different versions.
