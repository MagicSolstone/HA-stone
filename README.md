# Chicken coop Home Assistant dashboard

Two views: **Overview** (live tiles, comfort gauge, 24h temp + humidity charts with coop vs outside overlaid, high/low tiles, cameras) and **Trends** (7d and 30d charts).

## Setup
1. **HACS > Frontend > install `apexcharts-card`.**
2. Copy `packages/chicken_coop.yaml` to `/config/packages/` and make sure `configuration.yaml` has
   `homeassistant: { packages: !include_dir_named packages }`. Restart HA. (Creates the high/low sensors.)
3. Create a dashboard, open it, then ⋮ > Edit > ⋮ > **Raw configuration editor** and paste `dashboards/chicken-coop.yaml`.
4. Replace the placeholder entity IDs (find/replace) with yours:

| Placeholder | Meaning |
|---|---|
| `sensor.coop_temperature` / `sensor.coop_humidity` | YoLink coop sensor |
| `sensor.openweathermap_temperature` / `sensor.openweathermap_humidity` | OpenWeatherMap |
| `camera.coop`, `camera.run` | Frigate camera entities |

The high/low sensors are named from the helper names (e.g. `sensor.coop_temp_high_24h`); check Developer Tools > States if yours differ.

Gauge ranges assume °F; edit the comment-marked values for °C.
