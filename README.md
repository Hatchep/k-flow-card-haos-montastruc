# ⚡ K‑Flow Card for Home Assistant

A real‑time, animated energy flow dashboard card – monitor solar, battery, grid, and home consumption with a sleek SVG diagram.

!

---

## ✨ Features

- Real‑time data via `hass.states` – **no long‑lived token required**
- Animated sun arc with dynamic sky colours and moon
- Variable‑speed flow lines (Grid, Battery, Home)
- Battery fill with colour‑coded SOC
- PV block bar, Power bar, inverter summary, temperature & cell data
- Fully configurable entities via YAML editor
- Optional **dual‑battery** support (two compartments in one icon)
- Optional **multi‑PV** support (up to 4 strings, auto‑total if combined sensor missing)
- Custom grid & home icons (PNG)

---

## 🛠 Installation

### Manual
1. Download the desired variant (see below) and rename it to `k-flow-card.js`.
2. Place it in your `config/www` folder.
3. Add it as a **module** resource:
   - **Settings → Dashboards → Resources → + Add Resource**
   - URL: `/local/k-flow-card.js`
   - Type: **JavaScript Module**
4. Reload your dashboard (F5).

### HACS (custom repository)
1. In HACS, go to **Frontend → ⋮ → Custom repositories**.
2. Paste `https://github.com/thekhan1122/k-flow-card` (without `.git`).
3. Category: **Lovelace**.
4. Install the card – the resource is added automatically.

> ⚠️ The default HACS installation provides the **standard single‑battery, two‑PV version** (`k-flow-card.js`).  
> For dual‑battery or up to 4 PV strings, replace the file manually (see below).

---

## 📋 Card Configuration

Add a **Manual** card with the following YAML (edit entity IDs to match your system):

```yaml
type: custom:k-flow-card
pv1_power: sensor.goodwe_pv1_power
pv2_power: sensor.goodwe_pv2_power
pv_total_power: sensor.goodwe_pv_power
grid_active_power: sensor.goodwe_active_power
grid_import_energy: sensor.goodwe_today_energy_import
consump: sensor.goodwe_house_consumption
today_pv: sensor.goodwe_today_s_pv_generation
today_batt_chg: sensor.goodwe_today_battery_charge
today_load: sensor.goodwe_today_load
battery_soc: sensor.jk_soc
battery_power: sensor.jk_power
battery_current: sensor.jk_current
battery_voltage: sensor.jk_voltage
battery_temp1: sensor.jk_temp1
battery_temp2: sensor.jk_temp2
battery_mos: sensor.jk_mos
battery_min_cell: sensor.jk_cellmin
battery_max_cell: sensor.jk_cellmax
battery_rem_cap: sensor.jk_remain
goodwe_battery_soc: sensor.goodwe_battery_state_of_charge
goodwe_battery_curr: sensor.goodwe_battery_current
inv_temp: sensor.goodwe_inverter_temperature_module
batt_dis: sensor.goodwe_today_battery_discharge
