
Home SOC Lab: Wazuh SIEM Deployment & Attack Simulation
📋 Project Overview
This project involves the setup of a functional Security Operations Center (SOC) lab environment. I deployed a Wazuh SIEM on Ubuntu to monitor a Windows 11 endpoint. To test the lab's effectiveness, I conducted various network attacks from a Kali Linux machine and mapped the detections to the MITRE ATT&CK Framework.

🛠️ Technologies Used
SIEM: Wazuh (Manager, Indexer, and Dashboard)

Virtualization: Oracle VirtualBox

Operating Systems: Ubuntu 26.04 (SOC Manager), Windows 11 (Victim), Kali Linux (Attacker)

Tools: Nmap, Hydra, NetExec (nxc), PowerShell

🌐 Network Topology
Wazuh Manager: 10.0.2.6

Windows Victim: 10.0.2.15

Kali Attacker: 10.0.2.3

Network Type: Isolated NAT Network

🚀 Implementation Steps
1. SIEM Installation & Configuration
Deployed Wazuh on a hardened Ubuntu 26.04 instance.

Troubleshooting: Encountered and resolved a 404/XML download error by verifying the correct installation script paths for version 4.14.5.

Successfully configured the Wazuh Dashboard and identified initial resource requirements (50GB Storage / 6GB RAM) for stable operation.

2. Endpoint Security Telemetry
Installed the Wazuh Agent on the Windows 11 machine.

Manually configured the agent via PowerShell to point to the SOC Manager IP.

Hardening: Enabled advanced audit policies on Windows to capture failed login attempts (Event ID 4625).

3. Attack Simulation & Detection
Reconnaissance: Conducted nmap stealth scans from Kali to map open ports on the victim.

Credential Access: Simulated a brute-force attack against SMB using NetExec.

Detection: Verified that Wazuh generated Level 10+ High Severity alerts for multiple failed authentication attempts.

📊 Results: MITRE ATT&CK Mapping
The lab successfully categorized malicious activity into the following tactics:

Reconnaissance: Active Scanning via Nmap.

Credential Access: Brute-force via SMB/RDP.

Defense Evasion: Simulated disabling of the Windows Firewall via PowerShell.

🧠 Challenges & Key Learnings
Resource Management: Learned the importance of proper VM provisioning (RAM/CPU) to prevent SIEM service crashes.

Tool Evolution: Pivoted from CrackMapExec to NetExec to maintain compatibility with modern Windows security protocols.

Protocol Troubleshooting: Resolved 403 Forbidden errors during agent deployment by utilizing manual MSI installation and directory navigation in PowerShell.
