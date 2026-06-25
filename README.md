# Attack Emulation and SOC Investigation Using Microsoft Security Tools

## Objective:
The objective of this project was to gain hands-on experience with adversary emulation and endpoint detection by deploying Atomic Red Team on a Windows 11 environment and executing MITRE ATT&CK-based attack simulations. The project focused on validating Microsoft Defender for Endpoint detections, analyzing generated security alerts, investigating malicious behaviors, and strengthening SOC analyst skills in threat detection, incident investigation, and endpoint response.

## Project Overview:
This project focused on deploying and configuring Atomic Red Team on a Windows 11 virtual machine to simulate real-world adversary techniques mapped to the MITRE ATT&CK framework. Multiple attack scenarios were executed, including Registry Run Key persistence (T1547.001), Password Guessing (T1110.001), and PowerShell execution (T1059.001), to validate detection capabilities within Microsoft Defender for Endpoint.

Following the simulations, I investigated the generated security alerts, analyzed endpoint telemetry, reviewed process and registry activity, and performed incident analysis to determine the root cause of the detections. This project provided hands-on experience in adversary emulation, threat detection, alert triage, incident investigation, and endpoint detection and response (EDR) operations using Microsoft security technologies.

### Tools Used:
- Atomic Red Team
- Windows PowerShell
- Windows 11
- Microsoft Defender for Endpoint
- Microsoft Defender XDR
- MITRE ATT&CK Framework
- Windows Registry Editor
- Microsoft Defender Security Portal

### Skill Developed:
- Adversary emulation
- Attack simulation and validation
- Endpoint Detection and Response (EDR)
- Threat detection and analysis
- Alert triage and investigation
- Incident response
- Threat hunting
- PowerShell analysis
- Registry persistence analysis
- MITRE ATT&CK mapping
- Endpoint telemetry analysis

### Key Deliverables:
- Atomic Red Team deployment and configuration
- MITRE ATT&CK attack simulations
- Registry Run Key persistence testing (T1547.001)
- Password Guessing simulation (T1110.001)
- PowerShell execution simulation (T1059.001)
- Microsoft Defender alert validation
- Threat investigation report
- Incident response documentation
- Detection analysis and findings
- Security recommendations and remediation actions

## Steps Performed:
### Atomic Red Team Installation:
- Before executing the simulations, I configured my Windows 11 lab environment.
- Excluded the VM's C:\ drive from Microsoft Defender Antivirus to prevent interference with the attack simulations.
- Installed Atomic Red Team using PowerShell and downloaded the full Atomic test library containing hundreds of MITRE ATT&CK techniques.

#### Key Activities:
- Installed Invoke-AtomicRedTeam PowerShell module
- Downloaded Atomic Red Team test cases
- Modified PowerShell Execution Policy to RemoteSigned
- Verified installation of Atomic test libraries under C:\AtomicRedTeam\atomics

📌 Screenshots: Atomic Red Team installation and configuration
<img width="704" height="440" alt="image" src="https://github.com/user-attachments/assets/6f81ec95-e027-45f2-8daa-8f721fec9120" />
<img width="704" height="425" alt="image" src="https://github.com/user-attachments/assets/34e38799-132a-45ae-a3da-8671b66ccc0e" />
<img width="704" height="425" alt="image" src="https://github.com/user-attachments/assets/dc3b8d5c-8554-44b3-a3bc-194a0179a04d" />
<img width="704" height="425" alt="image" src="https://github.com/user-attachments/assets/c579963e-8e03-4666-a627-12b27640793c" />
<img width="703" height="406" alt="image" src="https://github.com/user-attachments/assets/d2bd37a5-2c04-4ab2-9833-69867c40303b" />

### Attack Simulations:

#### 1) Persistence Simulation – MITRE ATT&CK T1547.001
- Technique: Registry Run Keys / Startup Folder
- A persistence mechanism was simulated by modifying Windows Registry Run Keys, allowing a program to execute automatically whenever a user logs on.

#### Skills Demonstrated:
- Attack emulation
- Persistence techniques
- Registry-based threat analysis
- Microsoft Defender alert validation

📌 Screenshots: T1547.001 execution and generated alerts
<img width="704" height="442" alt="image" src="https://github.com/user-attachments/assets/d60af591-0dd0-425e-aa0f-e08e2e445910" />
<img width="702" height="375" alt="image" src="https://github.com/user-attachments/assets/4227764d-e094-4ce5-8e86-cd1e8f5495b3" />
<img width="702" height="378" alt="image" src="https://github.com/user-attachments/assets/ca58b59c-c547-4959-9dbe-3e3cb3fdb075" />

#### 2) Password Guessing Simulation – MITRE ATT&CK T1110.001
- Technique: Brute Force / Password Guessing
- Simulated repeated authentication attempts to mimic password guessing activity commonly observed during account compromise attempts.

#### Skills Demonstrated:
- Identity attack simulation
- Authentication monitoring
- Detection validation
- Security alert investigation

📌 Screenshots: T1110.001 execution and Defender detections
<img width="704" height="408" alt="image" src="https://github.com/user-attachments/assets/fca1fd29-089f-4514-842f-1c431eaaff0d" />
<img width="704" height="388" alt="image" src="https://github.com/user-attachments/assets/7609c335-b1b2-4542-b42e-277927350077" />
<img width="704" height="387" alt="image" src="https://github.com/user-attachments/assets/e84c5ebf-8a86-46d2-b2e5-8cd422e20bfa" />

#### 3) PowerShell Execution Simulation – MITRE ATT&CK T1059.001
- Technique: PowerShell
- Executed PowerShell-based commands designed to emulate attacker behavior and trigger endpoint detection mechanisms.

#### Skills Demonstrated:
- Command execution analysis
- PowerShell threat detection
- Endpoint telemetry investigation
- MITRE ATT&CK mapping

📌 Screenshots: T1059.001 execution and generated alerts
<img width="749" height="390" alt="image" src="https://github.com/user-attachments/assets/a0886506-12f5-4b68-8ad4-3556f0a055be" />
<img width="748" height="416" alt="image" src="https://github.com/user-attachments/assets/fcc3c973-ccb8-4f80-ba4b-ab153b6a4fc1" />

## SOC Investigation Report: Suspicious PowerShell Command Line:

### Incident Overview:
- Alert Name: Suspicious PowerShell Command Line
- First Activity: June 19, 2026 – 14:53:39 (UTC +04:00)
- Last Activity: June 19, 2026 – 15:36:06 (UTC +04:00)
- Affected Endpoint: Windows11
- User: jenny
- Severity: High
- Detection Source: Microsoft Defender for Endpoint
- MITRE ATT&CK Technique: T1059.001 – PowerShell
- Category: Execution

Microsoft Defender for Endpoint generated a high-severity alert after detecting suspicious PowerShell-related activity on a Windows 11 endpoint. Investigation revealed that a command was executed to modify a Windows Registry Run key, establishing persistence by configuring an application to launch automatically upon user logon.

### Indicators of Compromise (IOCs):
- Registry Modification:
    - HKCU\SOFTWARE\Microsoft\Windows\CurrentVersion\Run
- Executed Command:
    - cmd.exe /c REG ADD "HKCU\SOFTWARE\Microsoft\Windows\CurrentVersion\Run" /V "Atomic Red Team" /t REG_SZ /F /D "C:\Path\AtomicRedTeam.exe"
- Processes Involved:
    - powershell.exe
    - cmd.exe
- Persistence Mechanism:
    - Registry Run Key Persistence (MITRE ATT&CK T1547.001)
 
### Investigation Summary:
At 14:53:39 UTC+04:00 on June 19, 2026, Microsoft Defender for Endpoint generated a "Suspicious PowerShell Command Line" alert categorized under the Execution tactic and mapped to MITRE ATT&CK Technique T1059.001 – PowerShell.

Analysis of endpoint telemetry identified the execution of a command that modified the Windows Registry Run key within the current user's profile. The modification created a persistence mechanism designed to automatically launch an executable during user logon.

Registry-based persistence is a commonly observed adversary technique used to maintain access across system reboots and user sessions. Such activity may also be observed during authorized security testing and adversary emulation exercises.

Further analysis confirmed that the alert was triggered due to the creation of a Run key entry associated with Atomic Red Team activity, resulting in Microsoft Defender classifying the behavior as suspicious and assigning a High severity rating.

📌 Screenshot of Evidence:
<img width="749" height="413" alt="image" src="https://github.com/user-attachments/assets/38aa1887-2be3-4250-8a3c-dd287456ab11" />

### Triage (5W1H Analysis):

#### Who:
- User: jenny
- Endpoint: Windows11
- Processes: powershell.exe and cmd.exe
- Detection Source: Microsoft Defender for Endpoint

#### What:
- High-severity "Suspicious PowerShell Command Line" alert generated.
- Registry Run key modified to establish persistence.
- Automatic execution configured through a Windows startup mechanism.

#### When:
- First Activity: June 19, 2026 – 14:53:39 (UTC +04:00)
- Last Activity: June 19, 2026 – 15:36:06 (UTC +04:00)

#### Where:
- Endpoint: Windows11
- Registry Location:
        - HKCU\SOFTWARE\Microsoft\Windows\CurrentVersion\Run

#### Why:
- Intended to establish persistence through automatic program execution during user logon.
- Technique commonly associated with adversary persistence behavior and red-team simulations.

#### How:
- PowerShell activity triggered Defender detection logic.
- Investigation revealed a cmd.exe process modifying the Run registry key.
- The persistence mechanism configured Atomic Red Team to execute automatically upon user login.
- Microsoft Defender flagged the activity due to registry-based persistence behavior.

### Response Actions:
- Validated whether the activity was authorized and associated with Atomic Red Team testing.
- Isolated the affected endpoint during the investigation.
- Removed the identified Run key entry and associated executable.
- Conducted threat hunting for similar indicators across the environment.
- Reviewed Microsoft Defender and Windows event logs for related activity.
- Performed a full endpoint scan and remediated identified threats.
- Reset user credentials and revoked active sessions where required.

### Recommendations:
- Enable comprehensive PowerShell logging and monitoring.
- Implement enhanced monitoring for registry-based persistence techniques.
- Tune EDR detection rules for PowerShell abuse and startup persistence mechanisms.
- Conduct periodic threat hunting for unauthorized Run key modifications.
- Strengthen endpoint hardening controls to reduce persistence opportunities.
- Regularly validate detection capabilities through adversary emulation exercises.

### Lessons Learned:
- Registry Run Keys remain a common and effective persistence mechanism.
- PowerShell activity provides valuable indicators of attacker behavior.
- EDR telemetry enables rapid identification of persistence-related activity.
- MITRE ATT&CK mapping improves investigation accuracy and threat classification.
- Adversary emulation exercises help validate detection and response capabilities.
- Early containment actions reduce the risk of persistence and lateral movement.



