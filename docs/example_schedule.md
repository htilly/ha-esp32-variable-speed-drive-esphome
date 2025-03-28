# Example: Energy-Efficient Schedule for Pool Pump with Frequency Regulator

If you want to calculate how to setup a schedule for your pump, I suggest you head over to ChatGPT and use the following prompt:

---

**Prompt:**

Replace the values so it reflects your data.

```
I have a frequency regulator that can set the RPM on my poolpump, help me calculate a schedule to minimize energy and also reduce noice level. The goal is to have all of the water in the pool passing the pump at least three times a day.

My pool measure: 8x4x1.5 meters
Pump: 0.75 hkp
Max RPM on the pump: 2900
Max Numbers of schedules: 3
During night schedule, max RPM: 1200
```

---

This is an example output of that question:

---

## 📐 Step 1: Calculate Pool Volume

Pool size: `8 x 4 x 1.5 = 48 m³`  
Total water turnover goal: `48 m³ x 3 = 144 m³/day`

---

## ⚙️ Step 2: Estimate Flow at Different RPMs

Assuming the pump at 2900 RPM flows ~16 m³/h:

| RPM   | Flow (m³/h) | Relative Power Use |
|-------|-------------|--------------------|
| 2900  | 16.0        | 100%               |
| 2200  | 12.1        | ~53%               |
| 1600  | 8.8         | ~24%               |
| 1200  | 6.6         | ~12%               |

---

## 🕒 Step 3: Build the Schedule

Aiming for max 3 schedules and low noise at night:

### Initial Schedule (~2.4x turnover):

| Time        | RPM  | Flow (m³/h) | Duration (h) | Water Moved (m³) | Notes                |
|-------------|------|-------------|--------------|------------------|----------------------|
| 00:00–06:00 | 1200 | 6.6         | 6            | 39.6             | Night – low noise    |
| 08:00–12:00 | 2200 | 12.1        | 4            | 48.4             | Morning – efficient  |
| 16:00–19:00 | 1600 | 8.8         | 3            | 26.4             | Afternoon – moderate |
| **Total**   |      |             | **13 h**     | **114.4 m³**     |                      |

### Optimized Schedule (~3x turnover):

| Time        | RPM  | Flow (m³/h) | Duration (h) | Water Moved (m³) |
|-------------|------|-------------|--------------|------------------|
| 00:00–06:00 | 1200 | 6.6         | 6            | 39.6             |
| 08:00–13:00 | 2200 | 12.1        | 5            | 60.5             |
| 16:00–19:00 | 1600 | 8.8         | 3            | 26.4             |
| **Total**   |      |             | **14 h**     | **126.5 m³**     |

To hit exactly 144 m³, extend a daytime period or slightly increase RPM.

---

Let ChatGPT help you tweak based on your actual pump specs!