# MSI Modern 15 A5M Hackintosh EFI

An optimized OpenCore EFI configuration designed for the **MSI Modern 15 A5M** laptop running macOS. 

This EFI has been customized and optimized specifically for this hardware configuration to ensure maximum stability and performance.

---

## 💻 Hardware Specifications

| Component | Details |
| :--- | :--- |
| **Model** | MSI Modern 15 A5M |
| **CPU** | AMD Ryzen™ 5 5500U (6 Cores, 12 Threads, 2.1 GHz Base / 4.0 GHz Turbo) |
| **Graphics** | AMD Radeon™ Vega 7 Graphics (Lucienne) |
| **Memory** | 16 GB DDR4 Dual-Channel (2 x 8GB @ 3200MHz) |
| **Storage** | 512 GB M.2 NVMe SSD (Stock) |
| **Wi-Fi + Bluetooth** | Intel® Wi-Fi 6E AX210 (Replaced stock card due to lack of macOS support) |
| **Audio** | Realtek ALC256 (alcid=29) |
| **Bootloader** | OpenCore |
| **SMBIOS** | `MacBookPro16,3` |

---

## 🛠️ What Works & What Doesn't

### Works
- [x] **Graphics Acceleration:** Full QE/CI acceleration via `NootedRed.kext`.
- [x] **Wi-Fi & Bluetooth:** Supported out-of-the-box via Intel AX210 kexts (`AirportItlwm.kext`, `IntelBluetoothFirmware.kext`, `BlueToolFixup.kext`).
- [x] **Audio:** Internal speakers, microphone, and headphone jack (using Layout ID `29`).
- [x] **Keyboard & Trackpad:** Smooth multi-touch gestures and trackpad support via `VoodooI2C` and keyboard via `VoodooPS2Controller`.
- [x] **Battery Status:** Accurate percentage and status tracking via `SMCBatteryManager.kext` and `ECEnabler.kext`.
- [x] **Display Brightness:** Smooth slider and brightness keys functionality via `BrightnessKeys.kext`.
- [x] **USB Ports:** Mapped and stable.
- [x] **Sleep & Wake:** Functioning properly.

### Hardware Note
- [!] **Wi-Fi/Bluetooth Card Upgrade:** The original wireless card that comes with the laptop is **not supported** under macOS as there are no kexts available for it. It has been replaced with the **Intel® Wi-Fi 6E AX210**, which works perfectly with the included OpenIntelWireless drivers.

---

## ⚙️ BIOS Settings

To boot macOS successfully, ensure your BIOS settings are configured as follows:

### Disable
- Fast Boot
- Secure Boot
- Serial/COM Port

### Enable
- UEFI Boot Mode
- AHCI Mode (SATA Controller)
- Above 4G Decoding

---

## 🚀 Post-Install Notes (SMBIOS Configuration)

> [!IMPORTANT]
> The SMBIOS details (`MLB`, `SystemSerialNumber`, `SystemUUID`) provided in this repository's `config.plist` are placeholders or shared. For iCloud, iMessage, FaceTime, and other Apple Services to function correctly, you **must** generate your own unique serials.

1. Download [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS).
2. Generate serial numbers for model `MacBookPro16,3`.
3. Open `OC/config.plist` using a proper plist editor (like **ProperTree**).
4. Navigate to `PlatformInfo -> Generic` and replace the following values:
   - `SystemSerialNumber`
   - `MLB` (Board Serial)
   - `SystemUUID` (SmUUID)
5. Save the configuration.

---

## 🤝 Credits & Acknowledgements
- [Acidanthera](https://github.com/acidanthera) for OpenCore Bootloader and essential kexts (`Lilu`, `VirtualSMC`, `AppleALC`, etc.).
- [ChefKissInc](https://github.com/ChefKissInc) for `NootedRed.kext` enabling AMD Radeon integrated graphics.
- [OpenIntelWireless](https://github.com/OpenIntelWireless) for drivers enabling the AX210 card.
