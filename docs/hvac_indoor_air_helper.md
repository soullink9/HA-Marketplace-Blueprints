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

## Restarts during a boost

A restart (or editing this automation) while a boost is running ends the
run that would have put the fan back. With **Finish a Boost Cut Short by a
Restart** on (default), when Home Assistant starts it waits up to 5 minutes
for the sensors and thermostat to come back; if the fan is still on the
boost speed and the air is clean, the fan goes to the **Fallback Fan
Speed**. If the air is still bad, the 10-minute check starts a new boost.

It can't tell a boost speed you picked yourself from one it left behind,
so a manual high speed is also reset if HA restarts while the air is clean.
Fan Only mode switched on for a boost isn't undone after a restart.

## Thermostat compatibility

Only thermostats that support fan modes are listed. If your thermostat
names its speeds differently (for example `med`), type the name in.
