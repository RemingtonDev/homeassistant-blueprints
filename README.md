# 🛡️ Alarmo ↔ Bosch Smart Home Two-Way Sync Blueprint

This Home Assistant blueprint creates **a two-way synchronization between Alarmo and the Bosch Smart Home alarm system**, ensuring that both alarm control panels stay in sync—including transitional states like **arming** (exit delay) and final states like `armed_away`, `armed_home`, `disarmed`, and more.

## 🔧 What This Blueprint Does

- Keeps **Alarmo and Bosch alarm panels in sync** when arming/disarming from either side.
- Ensures **exit delays start at the same time**, preventing misalignment between Alarmo and Bosch when arming.
- Mirrors final states (e.g., `armed_away`, `armed_home`, `disarmed`, `armed_night`) in both directions.
- Prevents infinite loops by only syncing when needed and checking the current state of the other system.

## 📦 Requirements

- [Alarmo](https://github.com/nielsfaber/alarmo) installed in Home Assistant.
- **Bosch Smart Home Controller** connected to Home Assistant using the `boschshc` integration.

### ⚠️ Important Bosch Integration Note

> **The official Bosch Smart Home integration in Home Assistant does NOT expose alarm system features like `alarm_control_panel`.**

To get full alarm functionality, you must install the **extended custom integration**:

👉 [tschamm/boschshc-hass (GitHub)](https://github.com/tschamm/boschshc-hass/tree/master)

This custom integration extends the official `boschshc` integration and adds support for the Bosch intrusion detection system (`alarm_control_panel.intrusion_detection_system`).

Please visit their repository for **installation, documentation, and support** related to Bosch Smart Home.

## 🧠 Why This Blueprint Exists

This project was created to support **a complete, bidirectional sync between:**

- A [Frient Zigbee keypad](https://frient.com/) (via Zigbee2MQTT)
- The **Alarmo** alarm system in Home Assistant
- A **Bosch Smart Home alarm system** using the `boschshc-hass` custom integration

The goal was to create **a fully integrated smart alarm experience**, where arming/disarming from the keypad, Bosch app, or Home Assistant would reflect instantly and accurately across all systems.

## 📥 How to Use

1. Make sure Alarmo and `boschshc-hass` are installed and configured.
2. Import this blueprint into Home Assistant via the Blueprint UI:
   - In Home Assistant, go to **Settings → Automations & Scenes → Blueprints**
   - Click **Import Blueprint**
   - Paste in the **raw GitHub URL** to the `alarmo_bosch_twoway_sync.yaml` file
3. Create an automation from the imported blueprint.
4. Select your Alarmo panel and your Bosch alarm panel entities.
5. Done! Your systems should now sync automatically.

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FRemingtonDev%2Fhomeassistant-blueprints%2Fblob%2Fmain%2Fblueprints%2Fautomation%2Falarmo_bosch_delay%2Falarmo_bosch_twoway_sync.yaml)

## 💬 Support

- For issues related to **this blueprint**, feel free to open an issue or discussion in this repository.
- For Bosch alarm integration issues, please go to the official [boschshc-hass GitHub repo](https://github.com/tschamm/boschshc-hass/tree/master).

## 🙌 Credits

Thanks to:
- [nielsfaber/alarmo](https://github.com/nielsfaber/alarmo) for the powerful Alarmo integration
- [tschamm](https://github.com/tschamm) for extending Bosch support in Home Assistant
