# Indoor Air – HVAC Fan Boost

Boosts the HVAC fan when the air gets bad, then puts it back.

## Setting it up

1. **Thermostat and what to watch:** pick the thermostat and turn on each
   thing to watch: CO₂, humidity, VOCs, PM2.5.
2. A section appears for each one: pick its sensors and the limit.
3. **Fan boost:** the boost speed and when boosting is allowed.

## How a boost runs

1. A sensor stays above its limit for the set time (default 2 minutes).
2. The fan goes to the boost speed.
3. The boost lasts at least the minimum time, then until every sensor is
   below its limit by the margin.
4. The fan goes back to the speed it had before, unless someone changed it
   in the meantime.

A check every 10 minutes catches air that was already bad after a restart.

## Restarts during a boost

A restart ends the run that would put the fan back. With **Finish a boost
cut short by a restart** on, the automation sets the fallback speed after a
restart if the fan is still on the boost speed and the air is clean. It
can't tell that apart from a boost speed you picked yourself.

## Thermostat compatibility

Every thermostat is listed, so pick one with fan speeds (a fan mode setting
on its card). If yours names its speeds differently (for example `med`),
type the name in.
