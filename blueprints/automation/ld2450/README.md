# LD2450 Zone Creation Automation Blueprint

This Home Assistant automation blueprint is designed for the LD2450 radar sensor included in the Apollo MTR-1 and R-PRO-1 devices:

**Product Pages:**
- [Apollo MTR-1 Product Page](https://apolloautomation.com/products/mtr-1)
- [Apollo R-PRO-1 Product Page](https://apolloautomation.com/products/r-pro-1)

**GitHub Repositories:**
- [Apollo MTR-1 GitHub](https://github.com/ApolloAutomation/MTR-1)
- [Apollo R-PRO-1 GitHub](https://github.com/ApolloAutomation/R_PRO-1)

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

You have two easy options to install this blueprint:

### Option 1: One-Click Import (Recommended)

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fmirkop%2Fapollo-home-assistant%2Fblob%2Fmaster%2Fblueprints%2Fautomation%2Fld2450%2Fld2450_zone_creation.yaml)

Click the badge above to open your Home Assistant instance and import the blueprint directly.

### Option 2: Manual Installation

1. Download or copy the automation YAML file into your Home Assistant `blueprints/automation/ld2450` directory.
2. Reload automations or restart Home Assistant to detect the new blueprint.
3. In Home Assistant, go to **Settings > Automations & Scenes > Blueprints** and import the new blueprint if needed.

## Usage

### 1. Prerequisite: Apollo Device Integration

Before using this blueprint, ensure your Apollo device (MTR-1 or R-PRO-1) is integrated with Home Assistant and is accessible. The integration should expose the required sensor and number entities for zone configuration.

> **Note:** If you have modified any of the entity ID names for your Apollo device in Home Assistant, this blueprint automation may not work as expected. The automation expects the following entity ID naming patterns:
>
> - X position sensor:
>   - `sensor.<device_base_name>_target_1_x`
> - Y position sensor:
>   - `sensor.<device_base_name>_target_1_y`
> - Zone coordinate numbers:
>   - `number.<device_base_name>_zone_<zone#>_x1`
>   - `number.<device_base_name>_zone_<zone#>_x2`
>   - `number.<device_base_name>_zone_<zone#>_y1`
>   - `number.<device_base_name>_zone_<zone#>_y2`
> - Multi-target tracking switch (if present):
>   - `switch.<device_base_name>_multi_target_tracking`
>
> If you have changed any of these entity IDs, the blueprint may not be able to find or update the correct entities. It is recommended to keep the default entity IDs for full compatibility. Alternatively, you can update the blueprint YAML yourself to use the custom names you have given to your entities. Information on how to do this can be found online or by asking others in the community—support for this is not provided here.

### 2. Create an Automation from the Blueprint

After installing the blueprint (see Installation above):

1. Go to **Settings > Automations & Scenes > Automations** in Home Assistant.
2. Click **+ Create Automation**.
3. Select **Start with a blueprint**.
4. Choose **LD2450 Zone Creation** from the list.

### 3. Configure the Automation

- **Zone X1 Entity:**  
  Select the `number` entity for the X1 coordinate of the zone you want to set (e.g., `number.apollo_r_pro_1_w_bad455_zone_1_x1`).  
  The automation will automatically determine the other zone entities (X2, Y1, Y2) and the correct sensor entities for X/Y data collection.

- **Collection Duration (seconds):**  
  Set how long to collect X/Y data for zone creation. Default is 20 seconds.

- **Padding (mm):**  
  Set the padding to add to the zone boundaries (in millimeters).  
  (Tip: There are approximately 304.8 mm in a foot.)

### 4. Prepare for Zone Creation

- Place the desired target in the coverage area for the zone you wish to create.
- For best results, ensure only the desired target is present in the area during data collection.

### 5. Trigger the Automation

- **Button Helper (Recommended):**  
  Press the button helper you created (e.g., `input_button.ld2450_zone_create`) from your dashboard or the Helpers page.
- **Event Trigger (Advanced):**  
  Fire the `ld2450_zone_create` event from Developer Tools > Events.

### 6. Review Results

- After the automation runs, a persistent notification will summarize the created zone or indicate if no valid data was collected.

## How to Trigger the Automation

This blueprint supports two easy ways to start the zone creation process:

### 1. Button Helper (Recommended for Manual Use)
- Go to **Settings > Devices & Services > Helpers** in Home Assistant.
- Click **Add Helper** and choose **Button**.
- Name it (e.g., `LD2450 Zone Create`) and save.
- When creating your automation from this blueprint, select the button entity (e.g., `input_button.ld2450_zone_create`) as the trigger.
- You can add this button to your dashboard for one-click access.

### 2. Event Trigger (Advanced/Developer)
- You can trigger the automation by firing a custom event named `ld2450_zone_create`.
- Go to **Developer Tools > Events** in Home Assistant.
- Enter `ld2450_zone_create` as the event type and click **Fire Event**.
- This is useful for advanced users or for triggering from other automations/scripts.

You can use either method, or both, depending on your preference and setup. For most users, the button helper is the easiest and most visible way to run the automation.

## Notes

- The automation is designed to be user-friendly and robust, automatically handling mode switching and outlier filtering.
- Padding and outlier filtering methods can be adjusted in the blueprint as needed.
- For best results, ensure only the desired target is present in the coverage area during data collection.

## Feedback & Support

If you have suggestions, encounter issues, or want to contribute improvements, please open an issue or pull request in this project's repository.

---

**Let us know if you have additional requirements or questions!**
