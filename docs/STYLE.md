# Writing and layout guide

Every blueprint follows these rules, so they look and read the same. The
goal: someone who has never seen the blueprint can set it up in a minute,
and it just works.

## Names

- **Blueprint:** `Subject – What it does · vX.Y.Z`, for example
  `Bathroom Fan – Humidity and Shower Control · v0.5.0`. The subject is the
  thing in the house, not the technology.
- **Sections:** a short noun phrase in sentence case: `Shower detection`,
  `Brightness and color`.
- **Settings:** sentence case.
  - A picker names the thing: `Humidity sensor`, `Lights`.
  - A switch says what happens when it's on: `Detect showers`,
    `Put the fan back afterwards`.
  - A number says what the value means: `Turn on above`, `Pause for`.
    The unit goes in the selector (`%`, `minutes`), not in the name.
- Use the words people use at home: "light sensor", not "illuminance";
  "pause", not "override protection".

## Descriptions

- **Blueprint:** first line is `**Version X.Y.Z** · [What's new](…)`, then
  one or two sentences on what it does and what you need.
- **Section:** only when the name isn't enough, in one sentence.
- **Setting:** one short sentence, two at most. Say what it does or when to
  change it. Give an example only if it helps you pick a value.
- No entity IDs, YAML, template names, or "see section 8". If two settings
  depend on each other, the layout should make that obvious.

## Layout

1. **First section:** what you have and what you want. Required pickers,
   plus a switch or choice for each feature.
2. **One section per feature.** It shows only when that feature is on
   (`visible:`), so people only see what applies to them.
3. **Tuning sections** (timing, pausing, reliability) are collapsed.
4. **Advanced** is last and collapsed: debug logging and settings almost
   nobody changes.

Inside a section, a setting that only matters for one choice also gets
`visible:`. A hidden setting goes back to its default, so the logic must
treat that default as "off" or "not used".

## Compatibility

- Never rename an input key. Change its name and description freely.
- Every new input has a default.
- Don't hide an input whose stored value still matters when it's hidden.

## Versions

- Only bump the version (first line, name and description) of blueprints
  that changed in a release. Unchanged blueprints keep their version.
