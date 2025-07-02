# LD2410 Streamline Cards

This directory contains Home Assistant YAML card configurations for the LD2410 radar sensor. Each file provides a reusable card or chart for visualizing and controlling device features. Template variables like `device_title` and `device_base_name` should be assigned with actual device values.

---

The cards in this folder require the following Home Assistant frontend custom cards and tools:

- **Home Assistant Community Store (HACS):**
  - Used to easily install and manage custom integrations and frontend cards.
  - [HACS Documentation](https://hacs.xyz/docs/use/)

- **Streamline Card:**
  - Provides advanced, highly customizable entity cards for Lovelace dashboards.
  - Install via HACS: [Streamline Card on GitHub](https://github.com/brunosabot/streamline-card/)

- **Plotly Graph Card:**
  - Enables rich, interactive charts and graphs in Lovelace dashboards.
  - Install via HACS: [Plotly Graph Card on GitHub](https://github.com/dbuezas/lovelace-plotly-graph-card)

Make sure all dependencies are installed and up to date in your Home Assistant instance for these cards to function correctly.

---
## Streamline Variables by File

Variables listed in the `default` section of each YAML file are optional. If omitted, the following default values will be used:

### ld2410_controls.yaml
- device_title: The display name for the device (default: "LD2410").
- device_base_name: The base name used for all entity IDs related to the device (no default; must be set per device).

### ld2410_distances_chart.yaml
- device_title: The display name for the device (default: "LD2410").
- move_bar_color: Color for the movement bar in charts (default: `#4b0082`).
- still_bar_color: Color for the stillness bar in charts (default: `#274e13`).
- detection_bar_color: Color for the detection bar in charts (default: `#8b0000`).
- show_radar_targets: Boolean to show/hide radar target markers (default: `true`).
- show_zones: Boolean to show/hide zone bars and occupancy (default: `true`).
- show_distance: Boolean to show/hide distance bars (default: `true`).
- show_gates: Boolean to show/hide gate bars (default: `true`).
- show_max_gates: Boolean to show/hide max gate bars (default: `true`).
- bar_size: Size of bars in the chart (default: `35`).
- chart_unit_of_measurement: Unit of measurement for the chart (default: `input_entity`).
- chart_unit_of_measurement_entity: Entity ID to use for dynamic unit selection (default: `input_select.ld2410_distances_chart_unit_of_measurement`).
- device_base_name: The base name used for all entity IDs related to the device (no default; must be set per device).

### ld2410_gate_energy_chart.yaml
- device_title: The display name for the device (default: "LD2410").
- move_bar_color: Color for the movement bar in charts (default: `#4b0082`).
- move_threshold_color: Color for the movement threshold line (default: `#9467bd`).
- still_bar_color: Color for the stillness bar in charts (default: `#274e13`).
- still_threshold_color: Color for the stillness threshold line (default: `#8cb640`).
- device_base_name: The base name used for all entity IDs related to the device (no default; must be set per device).

### ld2410_gate_energy_configuration.yaml
- device_title: The display name for the device (default: "LD2410").
- device_base_name: The base name used for all entity IDs related to the device (no default; must be set per device).

### ld2410_occupancy_history.yaml
- device_title: The display name for the device (default: "LD2410").
- hours_to_show: Number of hours to show in the history graph (default: `1`).
- device_base_name: The base name used for all entity IDs related to the device (no default; must be set per device).

### ld2410_zone_configuration.yaml
- device_title: The display name for the device (default: "LD2410").
- device_base_name: The base name used for all entity IDs related to the device (no default; must be set per device).

### ld2410_zone_occupancy.yaml
- device_title: The display name for the device (default: "LD2410").
- device_base_name: The base name used for all entity IDs related to the device (no default; must be set per device).

---

## Streamline Variables (All Files)

The following variables are used as placeholders in the YAML files. Replace them with your actual values as needed (do not include the square brackets):

- device_title: The display name for the device (e.g., "LD2410").
- device_base_name: The base name used for all entity IDs related to the device (e.g., `sensor.livingroom_ld2410`).
- move_bar_color: Color for the movement bar in charts (e.g., `#4b0082`).
- still_bar_color: Color for the stillness bar in charts (e.g., `#274e13`).
- detection_bar_color: Color for the detection bar in charts (e.g., `#8b0000`).
- show_radar_targets: Boolean to show/hide radar target markers (e.g., `true`).
- show_zones: Boolean to show/hide zone bars and occupancy (e.g., `true`).
- show_distance: Boolean to show/hide distance bars (e.g., `true`).
- show_gates: Boolean to show/hide gate bars (e.g., `true`).
- show_max_gates: Boolean to show/hide max gate bars (e.g., `true`).
- bar_size: Size of bars in the chart (e.g., `35`).
- chart_unit_of_measurement: Unit of measurement for the chart (e.g., `cm`, `mm`, `m`, `in`, `ft`, `yd`, or `input_entity`).
- chart_unit_of_measurement_entity: Entity ID to use for dynamic unit selection (e.g., `input_select.ld2410_distances_chart_unit_of_measurement`).
- move_threshold_color: Color for the movement threshold line (gate energy chart).
- still_threshold_color: Color for the stillness threshold line (gate energy chart).
- hours_to_show: Number of hours to show in the history graph.

These variables allow you to easily customize the cards for different devices and preferences.

---

## ld2410_controls.yaml

Defines an entities card for controlling the LD2410 device, including:

- Radar Engineering Mode (switch)
- LD2410 Bluetooth (switch)
- Restart Radar (button)
- Factory Reset Radar (button)
- ESP Reboot (button)

---

## ld2410_distances_chart.yaml

Configures a custom Plotly graph card to visualize distance data from the LD2410. Features include:

- Customizable bar colors for movement, stillness, and detection
- Options to show radar targets, zones, distances, and gates
- Unit of measurement selection via an input entity
- Advanced initialization and utility functions for dynamic charting

---

## ld2410_gate_energy_chart.yaml

Provides a custom Plotly graph card to display gate energy data:

- Visualizes movement and stillness energy per gate
- Customizable colors for bars and thresholds
- Includes utility functions for fetching and validating entity states

---

## ld2410_gate_energy_configuration.yaml

Entities card for configuring gate energy thresholds and maximum gate distances:

- Max Move/Still Gate settings
- Move/Still threshold settings for gates G0–G7

---

## ld2410_occupancy_history.yaml

History graph card showing recent occupancy detection:

- Displays detection and occupancy for up to three zones
- Configurable time window (`hours_to_show`)

---

## ld2410_zone_configuration.yaml

Entities card for configuring radar zone boundaries and timeout:

- Radar Timeout
- Start and end positions for zones 1–3

---

## ld2410_zone_occupancy.yaml

Entities card for monitoring target and zone occupancy:

- Radar Target, Moving Target, Still Target
- Occupancy status for zones 1–3

---

Let me know if you want to expand or further detail any section!
