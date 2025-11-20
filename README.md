
# Apollo Air Quality Templates (Optimistic & Pessimistic Models)

This repository contains two Jinja2 templates for Home Assistant that calculate an **Air Quality Score (0–100%)** using Apollo Air / Apollo AIR-1 sensor data.

Both templates require only one variable:

```jinja2
{% set slug = 'apollo_air_max' %}
```

## What is slug?
slug is the base name used by all your AIR-1 sensor entities in Home Assistant.

For example, if your AIR-1 device exposes entities like:
```jinja2
sensor.apollo_air_max_sen55_temperature
sensor.apollo_air_max_sen55_humidity
sensor.apollo_air_max_co2
sensor.apollo_air_max_pm_2_5_m_weight_concentration
sensor.apollo_air_max_methane
sensor.apollo_air_max_ammonia
```
**Then the correct slug is: apollo_air_max**

The template automatically builds all entity IDs using this prefix.

## 🚀 Usage

You can create sensors using:

**Settings → Devices & Services → Helpers → Template Sensor**

1. Choose one model (Optimistic or Pessimistic).
2. Create a new Template Sensor.
3. Paste the template.
4. Change the slug to match your device.

### 1. Optimistic Model (Higher, More Comfortable Scores)

This model:

* Sums all pollutant scores directly

* Does not normalize the total

* Outputs a pleasant score that tends to be higher 

* Still respects all pollutant logic and thresholds

### 2. Pessimistic Model (Stricter & More Realistic)

This model:

* Uses the exact same pollutant scoring logic

* Normalizes the raw score using the maximum possible score

* Produces a stricter and more consistent 0–100% value

# ⚠️ Disclaimer

I am not a scientist, and these air-quality score models are not professional health or environmental assessments.
They are simply the result of my own research, experimentation with Apollo Air sensors, and the help of AI to build a scoring system that felt reasonable for home use.

These templates are meant as examples or starting points, not authoritative AQI standards.
Everyone is free to:

* Adjust the scoring logic based on their needs

* Create their own custom AQI sensors

* Contribute improvements or ideas

* Use these at your own discretion and always refer to official air-quality guidelines for health-critical decisions.
