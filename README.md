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
 
### Project Workflow
![Project Workflow](https://github.com/user-attachments/assets/dd282a03-2bd3-4915-9320-38d9cac664ba)

---

## Step-by-Step Configuration

### **1. Network Configuration**
- Created a NAT network for VMs.
- Configured network settings for each VM.

<details>
<summary>View Screenshots</summary>

*NAT Network Configuration*
![created nat network for VMs](https://github.com/user-attachments/assets/35737fb8-5a8f-47a8-a4d3-d3f29a79c39e)

*VM Network Settings*
![VMs setup](https://github.com/user-attachments/assets/953c66c6-8e84-4c64-9696-c07093037023)

</details>

---

### **2. Splunk Setup**
- Installed and configured Splunk on Ubuntu.
- Ensured Splunk was accessible on all machines.
- Configured the Splunk Universal Forwarder on the server and target machine.

<details>
<summary>View Screenshots</summary>

*Splunk Installation on Ubuntu*
![setting up Splunk in Ubuntu](https://github.com/user-attachments/assets/9d0c46df-a2fd-47d2-a388-6b9cb2d6f0e8)

*Splunk Web Interface Confirmation*
![ensuring splunk works on our machines (server and pc)](https://github.com/user-attachments/assets/3d8a4a49-83e1-4f04-8dcf-847bfa149924)

*Splunk Universal Forwarder Configuration*
![configuring splunk universal forwarder on our server and machine](https://github.com/user-attachments/assets/e4517482-d8e4-4ffd-b2c6-2f9b97cb2c81)

</details>

---

### **3. Active Directory Setup**
- Configured Active Directory on the Windows server.
- Created organizational units and users for IT and HR.
- Joined the target machine to the domain.

<details>
<summary>View Screenshots</summary>

*Active Directory Setup*
![configuring Active Directory onto our server](https://github.com/user-attachments/assets/b019b916-4876-4ebd-ad2b-6b17378c4215)

*Organizational Units for IT and HR*
![created organizational unit and user for IT](https://github.com/user-attachments/assets/bd05db4d-70e7-499e-8482-ed14a323d61b)
![created organizational unit and user for HR](https://github.com/user-attachments/assets/8ea733af-c1ab-4212-9b4e-95d8bb6f925f)

*Target Machine Successfully Joined to Domain*
![successfully added to domain](https://github.com/user-attachments/assets/746dad2b-aa56-4618-8b1f-adbca74fe101)
![users successfully added to domain through target PC](https://github.com/user-attachments/assets/3d974ca1-fbe8-488b-9310-cec0a1d52ecb)

</details>

---

### **4. Attack Simulation**

#### **Brute Force Attack**
- Used Crowbar on Kali Linux to brute force the user account password on the target machine via the RDP protocol.
- Detected failed logon attempts (Event ID 4625) on Splunk.

<details>
<summary>View Screenshots</summary>

*Crowbar Brute Force Execution*
![used crowbar tool on Kali linux to brute force user account password on target machine with RDP protocol](https://github.com/user-attachments/assets/894d664d-b603-43a4-9d52-ff39d8be2f25)
 
*Splunk Detection of Failed Logons*
![account alerted for 20 instances of eventcode 4625 which is 20 attempted and failed logons](https://github.com/user-attachments/assets/bd9316ed-db51-4b93-93c2-bd8e80c1bca8)
![multiple logon attempts within the minute confirm attempted brute force activity](https://github.com/user-attachments/assets/ff73a0f1-c148-4820-99e7-7557b846d39f)
![description of event ID 4625](https://github.com/user-attachments/assets/e7399118-0c79-4e04-9828-1b65185ab3de)


</details>

#### **Atomic Red Team Execution**
- Ran MITRE ATT&CK techniques to create local accounts.
- Verified telemetry on Splunk showing newly created accounts.

<details>
<summary>View Screenshots</summary>
 
*Atomic Red Team Command Execution*
![ran atomic command related to MITRE ATT CK framework for persistance techniques creating new local accounts](https://github.com/user-attachments/assets/39c95922-6701-43e6-afb9-0818d24649bc)

*Splunk Telemetry Showing New Local Accounts*
![Telematry generated by splunk showing newlocal account created by atomic red team](https://github.com/user-attachments/assets/9b986497-8c06-45cf-98c8-7ca9983df0ad)


</details>

---

## **Key Telemetry and Findings**
- **Event ID 4625:** Detected 20 failed logon attempts in a short time frame from the attacker machine, confirming a brute force attack.
  - **Source IP:** 192.168.10.250 (Kali Linux).
  - **Target Machine:** Windows 10.
- **Event ID 4726:** Detected new local accounts created using Atomic Red Team simulations.
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
  - Create custom Splunk alerts for Event IDs 4625 and 4726 to detect brute force attacks and unauthorized account creation in real-time.
  - Integrate MITRE ATT&CK threat detection rules directly into Splunk dashboards for faster analysis.
- **Lab Expansion:**
  - Add additional attack vectors, such as phishing or malware deployment, to simulate more advanced threats.
  - Experiment with other SIEM tools like Elastic SIEM or Graylog for comparison.
- **Automation:**
  - Implement PowerShell or Python scripts to automate log analysis and threat response.
- **Career Development:**
  - Share insights and findings from this project on LinkedIn and cybersecurity forums.
  - Use this lab experience to pursue advanced certifications like Splunk Enterprise Security Certified Admin or Azure Security Engineer.
