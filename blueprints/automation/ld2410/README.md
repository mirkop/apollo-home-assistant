# LD2410 Automations Blueprint

This blueprint provides an automation for Home Assistant to manage switches using the LD2410 sensor. It automatically turns off specified switches after a set period, with an optional notification to prompt the user to turn off the switch early or wait until the timeout.

## Features
- **Auto-Off**: Turns off selected switches after a configurable duration.
- **Reminder Notification**: Optionally sends a notification to your mobile app before the timeout, allowing you to turn off the switch immediately or keep it on until the end.
- **User Interaction**: Supports actionable notifications so you can choose to turn off the switch early or keep it on.
- **Flexible Timing**: Both the total on-time and the reminder delay are configurable.

## Inputs
| Input                  | Description                                                                                 | Default                |
|------------------------|---------------------------------------------------------------------------------------------|------------------------|
| `switch_entities`      | The switches to control. Supports multiple switches.                                         | *(required)*           |
| `notify_mobile_app`    | The notify service for your mobile app (e.g., `notify.mobile_app_pixel_fold`).               | `notify.mobile_app`    |
| `total_minutes_on`     | Total number of minutes the switches will remain on before auto-off.                         | `30`                   |
| `reminder_delay_minutes` | Minutes before sending a reminder notification. Set to 0 to skip notifications.             | `15`                   |

## How It Works
1. **Trigger**: When any of the selected switches is turned on, the automation starts.
2. **Wait for Reminder**: If `reminder_delay_minutes` > 0, waits for the specified delay.
3. **Send Notification**: Sends a notification to your mobile app, asking if you want to turn off the switch now or keep it on.
4. **Wait for Response or Timeout**:
    - If you choose to turn off now, the switch is turned off immediately.
    - If you choose to keep on, waits the remaining time, then turns off the switch.
    - If no response, turns off the switch after the total timeout.

## Example Usage
```
blueprint:
  source_url: <your_github_repo_url>
```

## Notes
- Make sure to set the correct `notify_mobile_app` service for your device.
- The automation supports multiple switches and can run in parallel for each.

---

For questions or improvements, please open an issue or pull request in this repository.
