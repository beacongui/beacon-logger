# BEACON-Logger: A Multimodal Data Collection Framework for Behavioral Biometrics

## Overview
**BEACON-Logger** is a high-fidelity data acquisition suite developed for cybersecurity research, specifically targeting **Continuous Authentication** and **Zero Trust Architecture** in gaming environments. It synchronizes multiple data streams including keystroke dynamics, mouse kinematics, network traffic, and hardware metadata to provide a comprehensive behavioral profile of a user.

This tool was used to generate the **BEACON Dataset**, focusing on user identification via Valorant gameplay dynamics.

## 🛠 Features
* **Keystroke Dynamics**: Logs raw key press/release events, durations, inter-key latencies, and polling rates.
* **Mouse Kinematics**: Records X/Y coordinates, velocity, acceleration, and click-timing (scroll, double-clicks).
* **Network Sniffing**: Captures raw `.pcap` files using Scapy and Npcap for traffic fingerprinting.
* **Screen Recording**: Integrated `.mp4` recording via FFmpeg and a DirectShow filter for visual ground truth.
* **Hardware Inventory**: Collects snapshots of CPU, RAM, GPU, and connected HID devices via WMI.
* **Valorant Integration**: Automatically backs up local game configuration files to account for sensitivity and keybind variances.

## 📂 Output Structure
Data is saved in a timestamped directory (e.g., `data_YYYY-MM-DD_HH-MM-SS/`) containing:
* `keyboard_[User]_[Time].csv`: Raw keystroke data and durations.
* `mouse_[User]_[Time].csv`: High-resolution mouse movement and event logs.
* `captured_packets_[User]_[Time].pcap`: Raw network traffic logs.
* `hardware_info_[User]_[Time].json`: System metadata and HID inventory.
* `screen_record_[User]_[Time].mp4`: Session video recording.
* `valorant_config_[User]_[Time]/`: Backup of local game settings.

## 🚀 Setup & Installation
The logger is designed for **Windows** environments.

### Prerequisites
1.  **Python 3.x**
2.  **Npcap**: Required for packet sniffing.
3.  **FFmpeg**: Ensure the `ffmpeg/bin/` folder is present in the script directory.
4.  **Screen Capturer Recorder**: Required for the integrated video logging.

### Installation
```bash
pip install pynput scapy psutil screeninfo wmi numpy