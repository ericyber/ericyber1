# Active Directory Attack & Detection with Splunk

This project simulates real-world Active Directory (AD) attacks using Kali Linux(Hydra) and monitors/detects them via Splunk. It's designed for blue and red team learning environments.

---

## Objective

- Simulate AD attacks from Kali Linux (attacker)
- Capture logs on a Windows Server (domain controller)
- Ingest logs into Splunk
- Detect and alert on suspicious behavior

---

## 🧱 Environment Setup

| Machine | Role                | OS                |
|--------:|---------------------|-------------------|
| Kali    | Attacker            | Kali Linux 2023.x |
| WinDC   | Domain Controller   | Windows Server 2019 |
| Splunk  | SIEM (log collector) | Ubuntu/Splunk Enterprise |

![Network Diagram](images/network_diagram.png)

---

## Attack Scenarios

(Dashboard](https://github.com/user-attachments/assets/5ce04e84-bb37-4f13-a4c2-9484e45927a0)

1. **Password Spray** – Using `hydra` against RDP


Scripts used are in [`attack-scripts/`](attack-scripts/)

![Kali Attack Demo](images/kali_attack_demo.gif)

---

## 📊 Splunk Detection & Alerts

Logs are ingested from WinDC via Universal Forwarder. Splunk content includes:

- Search queries ![Screenshot (31)](https://github.com/user-attachments/assets/fa9bd99b-4bc0-4cb8-9051-2ec9d0343c1f)

- Custom dashboards (JSON)
- Example alerts and correlations

![Splunk Alert](images/splunk_alert.png)

---

## 🚀 Quick Start (Simulation)

### 🛠️ 1. Set Up AD and Splunk
Follow setup in [docs/setup_guide.md](docs/setup_guide.md)

### 🧑‍💻 2. Run Attacks from Kali
```bash
# Example: LDAP enumeration
python3 attack-scripts/ldap_enum.py 192.168.1.10

# Pass-the-hash
pth-winexe -U 'Administrator%HASH' //192.168.1.10 cmd
