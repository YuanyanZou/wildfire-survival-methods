# Analytic Variable Dictionary

This dictionary covers variables referenced by the public R and Python workflows. It is not a complete competition data dictionary.

| Variable | Role | Description |
|---|---|---|
| `event_id` | Identifier | Wildfire-event identifier; used only as an index and never as a predictor. |
| `event` | Outcome | Equals 1 when the fire reaches within 5 km of an evacuation zone during follow-up; otherwise 0 (right-censored). |
| `time_to_hit_hours` | Outcome time | Time from the 5-hour landmark to observed hit or last available follow-up. |
| `low_temporal_resolution_0_5h` | Observation process | Equals 1 for limited observation density in the 0-5 hour feature window. |
| `log1p_area_first` | Fire geometry | Log-transformed initial fire area. |
| `area_growth_rate_ha_per_h` | Fire geometry | Area growth rate during the early feature window. |
| `log1p_growth` | Fire geometry | Log-transformed early area growth. |
| `log_area_ratio_0_5h` | Fire geometry | Log ratio of final to initial area in the feature window. |
| `radial_growth_rate_m_per_h` | Fire dynamics | Radial growth rate. |
| `centroid_displacement_m` | Fire dynamics | Centroid displacement during the feature window. |
| `centroid_speed_m_per_h` | Fire dynamics | Centroid movement speed. |
| `alignment_cos` | Direction | Signed cosine of alignment between fire movement and the evacuation-zone direction. |
| `alignment_abs` | Direction | Absolute alignment magnitude; removes toward-versus-away sign. |
| `spread_bearing_sin`, `spread_bearing_cos` | Direction | Cyclical encoding of absolute spread bearing. |
| `event_start_hour` | Time | Hour of initial detection. |
| `event_start_dayofweek` | Time | Day of week encoded as an integer. |
| `event_start_month` | Time | Month of initial detection. |
| `hour_sin`, `hour_cos` | Engineered | Cyclical hour encodings created by the public code. |
| `dow_sin`, `dow_cos` | Engineered | Cyclical day-of-week encodings created by the public R code. |
| `week_sin`, `week_cos` | Engineered | Equivalent day-of-week encodings used by the Python notebook. |
| `is_summer` | Engineered | Equals 1 for June through September. |
| `log_centroid_speed` | Engineered | `log1p()` transform of centroid speed. |
| `log_radial_growth` | Engineered | `log1p()` transform of radial growth rate. |
| `log_area_growth_rate` | Engineered | `log1p()` transform of area growth rate. |

Distance-based and distance-derived fields are audited only to document their relationship to the outcome definition; they are excluded from model matrices.

