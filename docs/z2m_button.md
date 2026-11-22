# Zigbee2MQTT Button – Single, Double, Hold and Release

Runs your actions for each kind of press on a Zigbee2MQTT button.

## Setting it up

Pick the button, then fill in the actions you want. Leave any press type
empty to ignore it.

## Notes

- Your actions run with the same rights as any automation. Only paste
  actions you understand, from a source you trust.

- Zigbee2MQTT learns each press type the first time the button sends it,
  so after pairing, press each type once.
- Buttons that use other action names (for example `on`, `off`,
  `brightness_move_up`) aren't covered.
- Under **Advanced**, "When pressed again while running" defaults to
  **Start over**, so a new press cancels a run still in progress (useful
  for "hold to dim, release to stop").
