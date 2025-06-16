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



![Kali Attack Demo](images/kali_attack_demo.gif)

---

## Splunk Detection & Alerts

Logs are ingested from WinDC via Universal Forwarder. Splunk content includes:

- Search queries ![SPl queries](https://github.com/user-attachments/assets/fa9bd99b-4bc0-4cb8-9051-2ec9d0343c1f)

- Custom dashboards ![Dashboard](https://github.com/user-attachments/assets/e1bd2101-7ba7-41a1-a2f0-14cbb5e8d594)

- Example alerts and correlations

![Splunk Alert](images/splunk_alert.png)

---

## (Simulation)

### 🛠️ 1. Set Up AD and Splunk
Follow setup in [docs/setup_guide.md](docs/setup_guide.md)

### 🧑‍💻 2. Run Attacks from Kali
```bash
# Example: LDAP enumeration
hydra -l jsmith -Password.txt rdp://20.0.107.139 -W3

