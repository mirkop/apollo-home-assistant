# LD2450 Zone Creation Automation Blueprint

This Home Assistant automation blueprint is designed for the LD2450 radar sensor included in the Apollo MTR-1 and R-PRO-1 devices:

- [Apollo MTR-1](https://github.com/ApolloAutomation/MTR-1)
- [Apollo R-PRO-1](https://github.com/ApolloAutomation/R_PRO-1)

## Features

- Automatically switches the LD2450 to single target mode for accurate zone creation, then restores the previous mode.
- Allows users to select which zone to set (1, 2, or 3) and the duration for data collection (default: 60 seconds, user-configurable).
- Collects X/Y position data of the target during the set duration.
- Tracks minimum and maximum X/Y positions to define the zone boundaries.
- Optionally adds user-defined padding to the zone boundaries.
- Ignores outlier values that fall far outside the collected data.
- Sets the selected zone's coordinates (X1/Y1, X2/Y2) based on the collected data.
- Supports both Zone Types: Disabled/Detection and Filter.

## Installation

1. In Home Assistant, go to **Settings > Automations & Scenes > Blueprints**.
2. Click **Import Blueprint** and paste the URL to this blueprint's YAML file on GitHub (e.g., `https://github.com/<your-username>/<your-repo>/blob/main/blueprints/automation/ld2450/ld2450_zone_creation.yaml`).
3. Alternatively, copy the automation YAML file into your Home Assistant `blueprints/automation/ld2450` directory.
4. Reload automations or restart Home Assistant to detect the new blueprint.
5. In Home Assistant, go to **Configuration > Automations & Scenes > Blueprints** and import the new blueprint.

## Usage

1. Ensure your LD2450 is integrated with Home Assistant and is accessible.
2. Place the desired target in the coverage area for the zone you wish to create:
   - For **Detection/Disabled** or **Filter** zones, ensure the target is present in the area during the setup.
3. Start the automation from the Home Assistant UI:
   - Select the zone to set (1, 2, or 3).
   - Set the duration for data collection (default is 60 seconds, but you can adjust as needed).
   - (Optional) Set the padding value to expand the zone boundaries.
4. The automation will:
   - Switch the LD2450 to single target mode.
   - Collect X/Y position data for the specified duration.
   - Ignore outlier values.
   - Calculate the min/max X/Y positions and apply padding.
   - Set the selected zone's coordinates accordingly.
   - Restore the LD2450 to its previous mode.
5. Review the results and adjust as needed.

## Notes

- The automation is designed to be user-friendly and robust, automatically handling mode switching and outlier filtering.
- Padding and outlier filtering methods can be adjusted in the blueprint as needed.
- For best results, ensure only the desired target is present in the coverage area during data collection.

## Feedback & Support

If you have suggestions, encounter issues, or want to contribute improvements, please open an issue or pull request in this project's repository.

---

**Let us know if you have additional requirements or questions!**
