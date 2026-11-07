# Aquivo ATO · signed firmware releases

Public, token-free OTA updates for **Aquivo / AQUIVO-ATO-ZB**, ESP32-C6. Customer downloads never require a GitHub account, access token or periodic key renewal. Firmware sources, private signing keys and device backups are not distributed in this repository.

## Version 1.1.1

Offline web interface, Wi-Fi setup and installation guide in **Slovenčina, Čeština, Magyar, Polski, English, Deutsch and Français**. Language follows the browser; a selector remembers your choice in that browser. Translations require no internet. Bundled Home Assistant card1.1.0 follows the HASS user’s language, with an editor/YAML override.

Device mode, calibration, counters, NVS schema6, GPIO wiring, Zigbee identity/endpoints and MQTT topics are unchanged. Language changes send no device commands. Updates require SERVICE and a stopped pump; the device stays in SERVICE after restart. Settings are preserved.

Firmware1.1.1 also fixes version reporting: status HTTP API, OTA metadata and Zigbee SW Build ID now use the same compiled application version. Firmware1.1.0 had two stale1.0.2 labels and is retained as a pre-release for the validation record. The independently published HASS card remains version1.1.0.

## Install an update

Open the device web interface → New firmware versions → Check for updates. Confirm the offered version while in SERVICE. The device downloads and verifies the manufacturer signature, model, length and SHA256 before activating the inactive OTA slot. Keep power connected. Boot health verification and rollback remain enabled. Automatic checking runs after boot and every6 hours when Wi-Fi and verified time are available; installation is manually confirmed.

For a manual upload, download both `Aquivo-ATO-OTA-1.1.1.bin` and `Aquivo-ATO-OTA-1.1.1.manifest.json` from Releases. Choose both in the device’s Firmware update form. Use the application image only, never a complete flash backup or bootloader. If the result is uncertain, reconnect and check the version before trying again.

`latest.json` is a signed manifest. ECDSA-P256/SHA256 covers the exact model, version, byte length and full image digest. The private key is never present in the device or public files. Signatures authenticate OTA updates; hardware Secure Boot/flash encryption and clone protection are separate.

## Home Assistant / HACS

Card repository: [maros22/aquivo-ato-card](https://github.com/maros22/aquivo-ato-card).

[Open custom repository in HACS](https://my.home-assistant.io/redirect/hacs_repository/?owner=maros22&repository=aquivo-ato-card&category=plugin), category **Dashboard**. The card repository includes installation instructions in all seven languages. This is a custom HACS repository; default catalog inclusion is separate. The same card and guide are downloadable directly from ATO at `/hass`, even offline.

Card and firmware updates are separate. Existing devices, entities, history and Homey MQTT mappings can be retained. MQTT topics remain `aquivo/ato-<MAC>/…`.

First devices on the old1.0.0 technical model require the manufacturer’s private one-time migration to the Aquivo model before these public manifests can be used. Devices already on1.0.2 can update normally. No pairing reset, factory reset or erase-flash is required.
