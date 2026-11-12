# Docs

| Blueprint | Page |
|---|---|
| Adaptive Light Controller | [adaptive_light_controller.md](adaptive_light_controller.md) |
| Curtains – Morning Open / Night Close | [open_close_curtains.md](open_close_curtains.md) |
| Indoor Air Helper (HVAC) | [hvac_indoor_air_helper.md](hvac_indoor_air_helper.md) |
| Humidity Automation | [humidity_control.md](humidity_control.md) |
| Z2M Button | [z2m_button.md](z2m_button.md) |
| Yardian – Fail-safe Lawn Watering | [yardian_lawn_schedule.md](yardian_lawn_schedule.md) |

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

### Moving an existing copy over to GitHub updates

If you already have a copy saved by hand (for example under
`blueprints/automation/soullink/`), replace that file's contents with the
version from this repo once. It then carries the `source_url`, and
**Re-import blueprint** works on it from then on. The file path stays the
same, so the automations using it don't need to change.

## Versions

All blueprints share one version number, shown on the first line of each
file. It goes up together for every release, even for blueprints that
didn't change.
