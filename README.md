
![Topology](https://github.com/user-attachments/assets/bcd147bb-4387-4a57-b2a1-6b659e2c92dd)
# Implementing Suricata with Splunk for Network Threat Detection

## Overview
This project demonstrates the integration of **Suricata**, an open-source intrusion detection and prevention system (IDS/IPS), with **Splunk** for real-time network threat monitoring and analysis. By leveraging Suricata's powerful rule-based detection and Splunk's log aggregation capabilities, this setup provides a scalable solution for detecting, analyzing, and responding to cybersecurity threats.

## Features
- **Real-time network traffic monitoring** using Suricata
- **Custom rule-based threat detection** with Suricata
- **Log forwarding and indexing** in Splunk
- **Visualization and analysis** of security events using Splunk dashboards
- **Alerts and correlation rules** to identify and mitigate potential threats

## Architecture
The project consists of:
- **Suricata IDS/IPS**: Captures network traffic, analyzes packets, and generates alerts based on predefined rules.
- **Splunk Enterprise/Splunk Free**: Ingests Suricata logs for indexing, searching, and visualizing security events.
- **Syslog/Forwarder**: Sends Suricata logs to Splunk for centralized monitoring.

## Prerequisites
- A **Linux-based system** (Ubuntu/Debian preferred) or a **virtualized environment**
- Suricata **7.x** (or latest version)
- Splunk Enterprise **9.x** (or Splunk Free version)
- **Python 3.x** (for log parsing, if necessary)
- Basic knowledge of **network security and IDS/IPS systems**

## Installation & Configuration

### Step 1: Install Suricata
```bash
sudo apt update && sudo apt install -y suricata
```
Verify installation:
```bash
suricata --build-info | grep Suricata
```

### Step 2: Configure Suricata for Logging
Edit the **Suricata YAML configuration file**:
```bash
sudo nano /etc/suricata/suricata.yaml
```
Modify the `outputs` section to enable JSON logging:
```yaml
outputs:
  - eve-log:
      enabled: yes
      filetype: json
      filename: /var/log/suricata/eve.json
```
Restart Suricata to apply changes:
```bash
sudo systemctl restart suricata
```

### Step 3: Install and Configure Splunk
Download and install Splunk:
```bash
wget -O splunk.deb "https://download.splunk.com/products/splunk/releases/9.0.0/linux/splunk-9.0.0.deb"
sudo dpkg -i splunk.deb
```
Start Splunk and set admin credentials:
```bash
sudo /opt/splunk/bin/splunk start --accept-license
```

### Step 4: Ingest Suricata Logs into Splunk
- Navigate to Splunk Web UI: `http://localhost:8000`
- Add a new data input source (`Settings` → `Data Inputs` → `Files & Directories`)
- Select `/var/log/suricata/eve.json` as the log file source
- Assign a source type: `suricata_logs`

### Step 5: Create Dashboards & Alerts
- Use **Splunk Search** to filter logs:
```spl
index=main sourcetype=suricata_logs | table _time, src_ip, dest_ip, alert.signature
```
- Create **Splunk dashboards** for network traffic visualization
- Set up **real-time alerts** for high-severity Suricata events

## Testing & Validation
To test the integration, generate simulated alerts using the **ET Open Ruleset**:
```bash
sudo suricata-update
sudo suricata -T
```
Perform a network scan:
```bash
nmap -sS -p 22,80,443 <target-ip>
```
Check logs in Splunk:
```spl
index=main sourcetype=suricata_logs alert.severity>=3
```

## Future Enhancements
- Automate log forwarding using **Syslog or a Splunk Universal Forwarder**
- Integrate with **FortiGate firewall** for enhanced security visibility
- Implement **SOAR automation** for incident response

## Conclusion
This project provides an effective IDS/IPS and SIEM integration using Suricata and Splunk. By implementing this setup, security teams can enhance network monitoring, detect anomalies, and respond proactively to threats.

## Author
**Jahin** - Cybersecurity Enthusiast & SOC Analyst  
