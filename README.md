# 🏥 PulseGuard – Secure Patient Monitoring System

### An ESP32-Based Secure Healthcare Monitoring Gateway Using ECDH and AES-256-GCM Encryption

PulseGuard is an IoT-based secure patient monitoring system designed to collect health and environmental parameters using ESP32 microcontrollers and sensors. It uses a Python-based hospital gateway to securely receive, decrypt, process, and display sensor data through a real-time web dashboard.

The system integrates cryptographic key exchange, authenticated encryption, and device monitoring to provide secure communication between ESP32 sensor nodes and the hospital gateway.

---

## 🚀 Project Overview

PulseGuard consists of four ESP32 sensor nodes connected to a central Python gateway.

Each ESP32 establishes a secure communication session with the gateway using Elliptic Curve Diffie-Hellman (ECDH). A shared secret is derived using HKDF-SHA256 and used to generate an AES-256-GCM session key.

The gateway processes incoming encrypted packets and provides device status and monitoring information through a browser-based dashboard.

## 🛠️ Technologies Used

| Component | Technology |
|---|---|
| Microcontroller | ESP32 |
| Programming | Embedded C/C++, Python |
| Gateway | Python |
| Dashboard | HTML, CSS, JavaScript |
| Key Exchange | P-256 ECDH |
| Key Derivation | HKDF-SHA256 |
| Encryption | AES-256-GCM |
| Communication | TCP/IP over Wi-Fi |
| Sensors | MAX30102, DHT11 |
| IDE | Arduino IDE |

## 🔬 Hardware Configuration

The project uses four ESP32 sensor nodes.

| Device | Sensors | Parameters |
|---|---|---|
| ESP32-01 | MAX30102 + DHT11 | Heart Rate, SpO₂, Temperature, Humidity |
| ESP32-02 | MAX30102 | Heart Rate, SpO₂ |
| ESP32-03 | DHT11 | Temperature, Humidity |
| ESP32-04 | DHT11 | Temperature, Humidity |

### Sensors

- **MAX30102:** Measures heart rate and blood oxygen saturation (SpO₂).
- **DHT11:** Measures temperature and humidity.

## 🔐 Security Architecture

PulseGuard implements multiple cryptographic mechanisms to protect sensor communication.

### 1. P-256 ECDH Key Exchange
Establishes a shared secret between the ESP32 device and the hospital gateway.

### 2. HKDF-SHA256
Derives a cryptographic session key from the ECDH shared secret.

### 3. AES-256-GCM Encryption
Encrypts sensor data and provides authenticated encryption to detect unauthorized modifications.

### 4. Replay Protection
Uses sequence-number checks to identify repeated or out-of-order packets according to the gateway's validation logic.

### 5. Security Event Logging
Records rejected packets and security-related events for monitoring and analysis.

## ⚙️ System Workflow

1. ESP32 initializes the connected sensors.
2. The device connects to the Wi-Fi network.
3. The ESP32 establishes a TCP connection with the hospital gateway.
4. ECDH public keys are exchanged.
5. Both sides derive a shared secret.
6. HKDF-SHA256 generates the AES-256 session key.
7. Sensor data is encrypted using AES-256-GCM.
8. The gateway receives and authenticates encrypted packets.
9. Validated data is processed for monitoring.
10. Device information and security status are displayed on the dashboard.

## 🖥️ Dashboard Features

- Four ESP32 device monitoring cards.
- Individual device identification.
- Heart rate and SpO₂ monitoring fields.
- Temperature and humidity monitoring fields.
- Online and offline device status.
- Secure session status.
- Packet sequence tracking.
- Encrypted packet reception status.
- Security event monitoring.

## 📂 Project Structure

```text
PulseGuard-Secure-Patient-Monitoring/
│
├── gateway.py
│
├── requirements.txt
│
├── README.md
│
└── .gitignore
```

## 💻 Installation and Setup

### Prerequisites

- Python 3.9 or above
- Arduino IDE
- ESP32 development boards
- MAX30102 and DHT11 sensors
- Wi-Fi network
- Compatible ESP32 firmware

### Step 1: Clone the Repository

```bash
git clone https://github.com/YOUR-USERNAME/PulseGuard-Secure-Patient-Monitoring.git
```

### Step 2: Navigate to the Project

```bash
cd PulseGuard-Secure-Patient-Monitoring
```

### Step 3: Create a Virtual Environment

```bash
python -m venv .venv
```

Activate it on Windows:

```bash
.venv\Scripts\activate
```

### Step 4: Install Dependencies

```bash
pip install -r requirements.txt
```

### Step 5: Run the Gateway

```bash
python gateway.py
```

### Step 6: Open the Dashboard

Open the following address in your browser:

```text
http://127.0.0.1:8080
```

## 🌐 Network Configuration

The current gateway configuration uses:

| Configuration | Value |
|---|---|
| TCP Gateway Port | 5000 |
| Dashboard Port | 8080 |
| Gateway Host | 0.0.0.0 |
| Dashboard Host | 127.0.0.1 |

The current device profiles use the following observed hotspot IP addresses:

| Device | IP Address |
|---|---|
| ESP32-01 | 192.168.1.7 |
| ESP32-02 | 192.168.1.9 |
| ESP32-03 | 192.168.1.8 |
| ESP32-04 | 192.168.1.6 |

**Note:** Device identification currently uses source IP mapping because the existing firmware handshake does not transmit an authenticated device ID. These addresses may change when DHCP leases change. Update the device profiles and dashboard mapping in `gateway.py` if necessary.

## 🎯 Project Objectives

- Develop a secure IoT-based patient monitoring platform.
- Collect health and environmental data using ESP32 sensor nodes.
- Implement secure key exchange using ECDH.
- Protect sensor data using AES-256-GCM encryption.
- Monitor device connectivity and secure communication.
- Display monitoring information through a centralized dashboard.

## 🔮 Future Enhancements

- Authenticated device identity independent of IP addresses.
- Cloud-based healthcare monitoring.
- Mobile application integration.
- Automated abnormal-reading alerts.
- Historical patient data visualization.
- Advanced intrusion detection and device authentication.

## ⚠️ Disclaimer

PulseGuard is an academic prototype developed for educational and research purposes. It is not a certified medical device and must not be used for clinical diagnosis or treatment. Security and sensor functionality should be validated before any real-world deployment.

## 👨‍💻 Project Team

Developed as an academic IoT and secure healthcare monitoring project.

**Technologies:** ESP32 | Python | IoT | Cryptography | Healthcare Monitoring

---

⭐ If you find this project interesting, consider giving the repository a star!
