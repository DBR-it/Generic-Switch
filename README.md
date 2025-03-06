# Generic Switch Project (Package-Based)

This **Generic Switch** configuration is published as an **ESPHome package**, allowing you to include it directly from GitHub without copying YAML files locally.

## Usage
In your **own** ESPHome YAML, add:
```yaml
esphome:
  name: my_switch

packages:
  remote_package_files:
    url: https://github.com/DBR-it/Generic-Switch
    ref: main
    files: [generic_switch.yaml]
```

1. **`my_switch`** is an example name for your device.
2. The **`packages`** section references this GitHub repository at the `main` branch.
3. `files` points to the `generic_switch.yaml` within the repo.

## Secrets & Customization
- You can still override **substitutions** by defining them **after** the `packages:` block in your local YAML. For example:
  ```yaml
  substitutions:
    device_name: "my_custom_switch"
    fallback_ssid: "My-Fallback-AP"
    fallback_password: "AnotherPassword"
  ```
- Make sure you have a `secrets.yaml` if you’re referencing `!secret wifi_ssid` and `!secret wifi_password`.

## What It Does
- Uses an **ESP8266** (D1 Mini) with a GPIO-based button.
- Exposes a **web server** on port 80.
- Connects to **Home Assistant** via the ESPHome API.
- Supports **OTA** for wireless firmware updates.
- Creates a **fallback hotspot** if Wi-Fi fails.

That’s it! This approach keeps your local configs clean while pulling updates from the GitHub repo automatically.

