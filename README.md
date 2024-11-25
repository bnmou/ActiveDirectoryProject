# Active Directory Project with Splunk, Kali Linux & Atomic Red Team

## Lab Setup
### Prerequisites
- **Virtual Machines:**
  - Ubuntu (Splunk Server)
  - Windows Server (Active Directory)
  - Kali Linux (Attacker)
  - Windows 10 (Target Machine)
- **Software:**
  - Splunk
  - Splunk Universal Forwarder
  - Sysmon
  - Crowbar (Brute Force Tool)
  - Atomic Red Team

---

## Step-by-Step Configuration

### **1. Network Configuration**
- Created a NAT network for VMs.
- Configured network settings for each VM.

<details>
<summary>View Screenshots</summary>

![NAT Network](screenshots/nat_network.png)  
*NAT Network Configuration*

![VM Network Settings](screenshots/vm_network_settings.png)  
*VM Network Settings*

</details>

---

### **2. Splunk Setup**
- Installed and configured Splunk on Ubuntu.
- Ensured Splunk was accessible on all machines.
- Configured the Splunk Universal Forwarder on the server and target machine.

<details>
<summary>View Screenshots</summary>

![Splunk Installation](screenshots/splunk_installation.png)  
*Splunk Installation on Ubuntu*

![Splunk Web Access](screenshots/splunk_web_access.png)  
*Splunk Web Interface Confirmation*

![Universal Forwarder Config](screenshots/universal_forwarder_config.png)  
*Splunk Universal Forwarder Configuration*

</details>

---

### **3. Active Directory Setup**
- Configured Active Directory on the Windows server.
- Created organizational units and users for IT and HR.
- Joined the target machine to the domain.

<details>
<summary>View Screenshots</summary>

![AD Setup](screenshots/ad_setup.png)  
*Active Directory Setup*

![Organizational Units](screenshots/organizational_units.png)  
*Organizational Units for IT and HR*

![Domain Join](screenshots/domain_join.png)  
*Target Machine Successfully Joined to Domain*

</details>

---

### **4. Attack Simulation**

#### **Brute Force Attack**
- Used Crowbar on Kali Linux to brute force the user account password on the target machine via the RDP protocol.
- Detected failed logon attempts (Event ID 4625) on Splunk.

<details>
<summary>View Screenshots</summary>

![Crowbar Brute Force](screenshots/crowbar_brute_force.png)  
*Crowbar Brute Force Execution*

![Splunk Detection](screenshots/splunk_detection.png)  
*Splunk Detection of Failed Logons*

</details>

#### **Atomic Red Team Execution**
- Ran MITRE ATT&CK techniques to create local accounts.
- Verified telemetry on Splunk showing newly created accounts.

<details>
<summary>View Screenshots</summary>

![Atomic Red Team](screenshots/atomic_red_team_execution.png)  
*Atomic Red Team Command Execution*

![Splunk New Accounts](screenshots/splunk_new_accounts.png)  
*Splunk Telemetry Showing New Local Accounts*

</details>

---

## **Key Telemetry and Findings**
- **Event ID 4625:** Detected 20 failed logon attempts in a short time frame from the attacker machine, confirming a brute force attack.
  - **Source IP:** 192.168.10.250 (Kali Linux).
  - **Target Machine:** Windows 10.
- **Event ID 4720:** Detected new local accounts created using Atomic Red Team simulations.
  - **Technique:** MITRE ATT&CK T1136.001 (Create Account: Local Account).
  - **Generated Telemetry:** Splunk captured all relevant account creation events and mapped them to the source machine.

---

## **Skills Demonstrated**
- **SIEM Integration:** Configured Splunk to ingest logs from multiple sources (Windows, Linux).
- **Active Directory Management:** Set up domain controllers, DNS, organizational units, and user accounts.
- **Attack Simulation:** 
  - Executed a brute force attack using Crowbar and detected it using telemetry.
  - Simulated MITRE ATT&CK techniques using Atomic Red Team to generate relevant logs.
- **Threat Detection:** Identified and analyzed suspicious activity (e.g., brute force and unauthorized account creation) in Splunk.
- **Networking:** Configured VM networks for seamless communication within the lab.
- **Security Monitoring:** Investigated and verified log activity with event codes and source telemetry.

---

## **Next Steps**
- **Detection Enhancements:**
  - Create custom Splunk alerts for Event IDs 4625 and 4720 to detect brute force attacks and unauthorized account creation in real-time.
  - Integrate MITRE ATT&CK threat detection rules directly into Splunk dashboards for faster analysis.
- **Lab Expansion:**
  - Add additional attack vectors, such as phishing or malware deployment, to simulate more advanced threats.
  - Experiment with other SIEM tools like Elastic SIEM or Graylog for comparison.
- **Automation:**
  - Implement PowerShell or Python scripts to automate log analysis and threat response.
- **Career Development:**
  - Share insights and findings from this project on LinkedIn and cybersecurity forums.
  - Use this lab experience to pursue advanced certifications like Splunk Enterprise Security Certified Admin or Azure Security Engineer.
