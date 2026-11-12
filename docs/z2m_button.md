# Z2M Button – Single / Double / Hold (+ Release)

Runs your own actions for each press type on a Zigbee2MQTT button.

## Setup

Pick the button's device, then fill in the actions you want. Leave any press
type empty to ignore it.

## Notes

- Zigbee2MQTT creates each press type's trigger the first time the button
  sends it, so after pairing press each type once before relying on it.
- Buttons that use other action names (for example `on`, `off`,
  `brightness_move_up`) aren't covered by this blueprint.
- **Automation Mode** defaults to *Restart*, so a new press cancels a run
  still in progress (useful for "hold to dim, release to stop").
