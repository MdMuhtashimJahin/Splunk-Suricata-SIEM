
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



## Future Enhancements
- Automate log forwarding using **Syslog or a Splunk Universal Forwarder**
- Integrate with **FortiGate firewall** for enhanced security visibility
- Implement **SOAR automation** for incident response

## Conclusion
This project provides an effective IDS/IPS and SIEM integration using Suricata and Splunk. By implementing this setup, security teams can enhance network monitoring, detect anomalies, and respond proactively to threats.

## Author
**Jahin** - Cybersecurity Enthusiast & SOC Analyst  
