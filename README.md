# BLE Scanner — iOS App

A complete Bluetooth Low Energy scanner and inspector for iOS built with Swift + CoreBluetooth + SwiftUI.

## Features
- Scan for all nearby BLE devices
- Shows device name, UUID, signal strength (RSSI), manufacturer (if known), and connectability
- Connects to devices and enumerates all services and characteristics
- Displays characteristic values in Hex, UTF-8, and Int formats
- Read and Subscribe (notify) buttons on each characteristic
- Lookup table for 60+ known standard Bluetooth SIG UUIDs
- Known manufacturer ID lookup (Apple, Samsung, Google, etc.)
- Full event log with timestamps

## Project Setup in Xcode

1. Create a new **iOS App** project in Xcode
   - Interface: SwiftUI
   - Language: Swift

2. **Replace** the generated `ContentView.swift` and add `BLEManager.swift` to the project

3. **Update Info.plist** — add the keys from the provided `Info.plist`
   (or add them via: Target > Info > Custom iOS Target Properties)
   - `NSBluetoothAlwaysUsageDescription` — required string
   - `UIBackgroundModes` → `bluetooth-central` — if you want background scanning

4. **Enable Background Mode** (optional, for background scanning):
   - Target > Signing & Capabilities > + Background Modes > Bluetooth Central

5. **Build and run on a real iPhone** — the simulator cannot use Bluetooth hardware

## File Structure

```
BLEScannerApp/
├── BLEManager.swift     — Core Bluetooth logic, delegates, models, UUID table
├── ContentView.swift    — All SwiftUI views (Scanner, Device Detail, Log)
└── Info.plist           — Bluetooth permission keys
```

## How It Works

```
Scan → Discover Device → Connect →
Discover Services → Discover Characteristics →
Read/Subscribe → Display Data
```

## Known UUID Coverage
The app includes lookups for standard Bluetooth SIG UUIDs including:
- Generic Access / Attribute
- Device Information (model, serial, firmware, manufacturer)
- Battery, Heart Rate, Blood Pressure
- Environmental Sensing (temp, humidity, pressure)
- HID (keyboards, mice)
- Cycling, Location, and more
- Common vendor UUIDs (HM-10, TI, etc.)
