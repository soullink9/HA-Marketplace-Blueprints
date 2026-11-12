# Indoor Air Helper (HVAC)

Watches CO₂, humidity, VOCs and PM2.5 and boosts the HVAC fan when any of
them goes over its limit.

## How a boost runs

1. A sensor stays above its limit for **Must Stay High For**.
2. The fan is set to **Fan Speed When Boosting** (and, if enabled, the
   system is switched to Fan Only while it is off).
3. The boost lasts at least **Minimum Boost Time**, then continues until
   every watched sensor is below its limit minus the **Clear Margin**.
4. The fan goes back to the speed it had before — but only if nobody
   changed it in the meantime.

A check every 10 minutes catches air that was already bad after a restart
or that went bad while the **When to Boost** condition wasn't met.

## Thermostat compatibility

Only thermostats that support fan modes are listed. If your thermostat
names its speeds differently (for example `med`), type the name in.
