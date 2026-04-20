# DengueGuard SL

A lightweight, browser-based dengue fever risk assessment tool for Sri Lanka. No server, no dependencies — just a single HTML file.

---

## Overview

DengueGuard SL takes environmental and epidemiological inputs for a given district and produces an instant risk score using a rule-based scoring model. It is designed for community health workers, local authority officers, or individuals who want a quick situational awareness check.

---

## Features

- District selection covering 12 Sri Lankan districts
- Environmental inputs: temperature, rainfall, humidity
- Epidemiological inputs: recent case count, standing water duration
- Urbanization level weighting (urban / suburban / rural)
- Color-coded risk levels: Low, Moderate, High, Very High
- Visual risk progress bar
- Actionable prevention tips per risk tier
- Field-by-field input validation with clear error messages
- Fully self-contained — no internet connection required after download

---

## How to Use

1. Open `dengue_guard_sl.html` in any modern web browser.
2. Select your **district** from the dropdown.
3. Enter the current **temperature** (°C), **rainfall** (mm), and **humidity** (%).
4. Enter the number of **recent dengue cases** reported in your area (enter `0` if unknown).
5. Enter the number of days **standing water** has been present nearby (enter `0` if none).
6. Select the **urbanization level** of the area.
7. Click **Predict Risk**.

The result panel on the right will show:
- A risk probability percentage
- A risk level badge (Low / Moderate / High / Very High)
- A visual bar
- Recommended actions for that risk level

---

## Risk Model

The tool uses a weighted scoring system across six factors:

| Factor | Optimal Range | Max Score |
|---|---|---|
| Temperature | 25 – 32 °C | 3 |
| Rainfall | 80 – 200 mm | 3 |
| Humidity | 70 – 90 % | 3 |
| Standing Water | ≥ 3 days | 2 |
| Recent Cases | ≥ 20 cases | 3 |
| Urbanization | Urban | 1 |

**Maximum possible score: 13**

The raw score is divided by 13 to produce a probability (0.02 – 0.98), then mapped to a risk tier:

| Probability | Risk Level |
|---|---|
| ≥ 75% | Very High |
| 55 – 74% | High |
| 35 – 54% | Moderate |
| < 35% | Low |

> **Note:** This is a heuristic scoring model for awareness purposes only. It is not a clinical diagnostic tool and does not replace advice from the Epidemiology Unit of the Ministry of Health, Sri Lanka.

---

## Input Reference

| Field | Unit | Valid Range | Notes |
|---|---|---|---|
| Temperature | °C | 0 – 60 | Dengue mosquitoes are most active at 25 – 32 °C |
| Rainfall | mm | ≥ 0 | Monthly or recent weekly accumulation |
| Humidity | % | 0 – 100 | Relative humidity |
| Recent Cases | count | ≥ 0 | Reported cases in your area in the past 2 – 4 weeks |
| Standing Water | days | ≥ 0 | Days stagnant water has been present near the location |
| Urbanization | — | Urban / Suburban / Rural | Reflects population density and vector density |

---

## Files

```
dengue_guard_sl.html   Main application — open this in a browser
README.md              This file
```

---

## Browser Compatibility

Tested on:
- Google Chrome 110+
- Mozilla Firefox 110+
- Microsoft Edge 110+
- Safari 16+

No build step, no npm install, no backend required.

---

## Limitations

- The scoring weights are based on general dengue epidemiology literature, not a trained machine learning model.
- The tool does not connect to live surveillance data or real-time weather feeds.
- District granularity is coarse — risk can vary significantly within a single district.
- Always cross-reference with official bulletins from the **Epidemiology Unit, Ministry of Health, Sri Lanka**: [https://www.epid.gov.lk](https://www.epid.gov.lk)

---

## License

This project is provided for educational and public health awareness purposes. Free to use, adapt, and redistribute with attribution.
