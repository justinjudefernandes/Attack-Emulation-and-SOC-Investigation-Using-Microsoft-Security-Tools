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

#### Persistence Simulation – MITRE ATT&CK T1547.001:
- Technique: Registry Run Keys / Startup Folder
  - A persistence mechanism was simulated by modifying Windows Registry Run Keys, allowing a program to execute automatically whenever a user logs on.

##### Skills Demonstrated:
- Attack emulation
- Persistence techniques
- Registry-based threat analysis
- Microsoft Defender alert validation

📌 Screenshots: T1547.001 execution and generated alerts
<img width="704" height="442" alt="image" src="https://github.com/user-attachments/assets/d60af591-0dd0-425e-aa0f-e08e2e445910" />
<img width="702" height="375" alt="image" src="https://github.com/user-attachments/assets/4227764d-e094-4ce5-8e86-cd1e8f5495b3" />
<img width="702" height="378" alt="image" src="https://github.com/user-attachments/assets/ca58b59c-c547-4959-9dbe-3e3cb3fdb075" />

#### Password Guessing Simulation – MITRE ATT&CK T1110.001:
- Technique: Brute Force / Password Guessing
  - Simulated repeated authentication attempts to mimic password guessing activity commonly observed during account compromise attempts.

##### Skills Demonstrated:
- Identity attack simulation
- Authentication monitoring
- Detection validation
- Security alert investigation

📌 Screenshots: T1110.001 execution and Defender detections

3. PowerShell Execution Simulation – MITRE ATT&CK T1059.001

Technique: PowerShell

Executed PowerShell-based commands designed to emulate attacker behavior and trigger endpoint detection mechanisms.

Skills Demonstrated

Command execution analysis
PowerShell threat detection
Endpoint telemetry investigation
MITRE ATT&CK mapping

📌 Screenshot: T1059.001 execution and generated alerts










📌 Refer to the below screenshots for policy configuration and summary details.
<img width="752" height="420" alt="image" src="https://github.com/user-attachments/assets/a6d4dfb9-f579-4f8e-b4b9-35d9a3a73eb5" />
<img width="752" height="411" alt="image" src="https://github.com/user-attachments/assets/3e73cd77-0e17-4e44-8fbd-413ce6f4480a" />

### Safe Attachments Policy Configuration:
- Implemented a Safe Attachments policy to provide detonation-based malware protection for email attachments.
  - Navigated to: Microsoft Defender → Email & collaboration → Policies & rules → Threat policies → Safe Attachments
  - Created a policy named: 'MyDFIR-Justin-SafeAttachments&Links'.
  - Configured attachment scanning to detect and block potentially malicious payloads before delivery.

📌 Refer to the below screenshots for policy summary and configuration settings.
<img width="751" height="410" alt="image" src="https://github.com/user-attachments/assets/eccb3733-9b03-4668-8e1c-086e94839590" />
<img width="753" height="413" alt="image" src="https://github.com/user-attachments/assets/feac727d-50dd-45a5-b7f3-df9be83aaac6" />

### Policy Validation and Testing:
- Performed controlled testing to validate enforcement of Safe Links and Safe Attachments policies.
  - Sent a test phishing-style email from a newly created external ProtonMail account: 'strangeaccount88@proton[.]me'
  - Verified policy behavior through message inspection in Defender.
  - Confirmed that Safe Links and Safe Attachments protections were actively applied to the message content.

📌The below screenshots demonstrate policy enforcement and inspection results within Microsoft Defender.
<img width="749" height="286" alt="image" src="https://github.com/user-attachments/assets/b1a55330-82df-4099-8c4c-7062c319b7eb" />
<img width="749" height="374" alt="image" src="https://github.com/user-attachments/assets/eb301f83-3db1-412c-ab57-d997452d69a1" />

### Email Investigation and Threat Analysis:
- Initiated an investigation using Microsoft Defender for a suspicious email alert.

#### Email Analysis Workflow:
- Navigated to: Email & collaboration → Explorer
- Extracted and analyzed the email message header for forensic inspection.
- Parsed key header fields using Notepad++ for structured review, including:
  - Received chain (mail routing path)
  - Authentication-Results (SPF/DKIM/DMARC validation)
  - From address
  - Message-ID
  - Return-Path
  - X-Forefront-Antispam-Report

📌 Below are the screenshots captured during the Email Workflow Analysis:
<img width="749" height="317" alt="image" src="https://github.com/user-attachments/assets/fdaca9c9-835b-4cb7-80cf-f1c9a2e992fa" />
<img width="748" height="418" alt="image" src="https://github.com/user-attachments/assets/62abcffd-af78-4f77-b29b-178c9fb39453" />
<img width="751" height="431" alt="image" src="https://github.com/user-attachments/assets/7a65c3e8-4909-4499-ab90-13199f030b59" />

#### Threat Intelligence Correlation (OSINT):
- Investigated embedded URL using VirusTotal.
  - URL was flagged as malicious by 5 security vendors.
- Performed OSINT analysis on source IP address: 79.135.106.97
  - IP had prior malicious reports. (last seen ~5 months ago)
  - Associated with suspicious activity patterns consistent with phishing infrastructure.

📌 Below are the screenshots of the OSINT performed:
<img width="750" height="412" alt="image" src="https://github.com/user-attachments/assets/51c431c0-4be2-449b-8081-a90c1a128be9" />
<img width="749" height="457" alt="image" src="https://github.com/user-attachments/assets/950fa6c8-9d41-494a-b4c6-fe89911c637a" />

### Incident Response Action:
- Based on corroborated OSINT findings and Defender telemetry:
  - Confirmed email contained malicious URL and suspicious origin infrastructure.
  - Executed remediation by deleting the email from user mailboxes.
  - Prevented further user interaction with the phishing content.

 📌 Screenshot as below:
 
<img width="749" height="412" alt="image" src="https://github.com/user-attachments/assets/bad41887-5f9b-412a-a7af-0dd5a54e033f" />


## SOC Phishing Investigation Report:

### Incident Overview:
- Timestamp: June 18, 2026 – 21:04 (UTC +04:00)
- Recipient: bob@corp88[.]onmicrosoft[.]com
- Subject: Salary Revision
- Sender Email: strangeaccount88@proton[.]me
- Sender IP Address: 79.135.106.97
- Attachment: Salary Revision[.]docx
- Embedded URL: hxxps[://]shareholds[.]com/nam/…

A phishing email impersonating an HR-related salary update was delivered to the target mailbox. The message contained both a malicious document attachment and a credential-harvesting URL designed to prompt user interaction.

### Indicators of Compromise (IOCs):
- Malicious URL: Flagged by VirusTotal as malicious across multiple security vendors.
- Sender IP (79.135.106.97): Reported as malicious on AbuseIPDB.
- Phishing Infrastructure: External ProtonMail sender used to deliver payload.

### Investigation Summary:
- At 21:04 UTC+04:00 on June 18, 2026, a phishing email titled “Salary Revision” was delivered to the organization’s mailbox. The email leveraged a social engineering lure related to payroll updates and contained:
  - A Microsoft Word attachment (Salary Revision[.]docx).
  - A malicious URL intended to redirect the user to an external resource.
- OSINT validation confirmed multiple malicious indicators associated with both the URL and the sender infrastructure. VirusTotal detections classified the URL as malicious, while AbuseIPDB reports confirmed prior malicious activity associated with the source IP address.
- Further investigation is required to determine:
  - Whether additional users were targeted.
  - Whether the URL or attachment was accessed.
  - Whether credential theft, malware execution, or unauthorized access occurred.

### Triage (5W1H Analysis):
- Who:
  - Sender: strangeaccount88@proton.me
  - Source IP: 79.135.106.97 (malicious reputation confirmed via AbuseIPDB)
- What:
  - Phishing email containing:
    - Malicious URL
    - Suspicious attachment (Salary Revision.docx)
- When:
  - June 18, 2026 – 21:04 (UTC +04:00)
- Where:
  - Recipient: bob@corp88.onmicrosoft.com
  - Subject: Salary Revision
- Why:
  - Likely objective: credential harvesting, malware delivery, or unauthorized access to internal resources.
- How:
  - Email successfully bypassed email security controls and was delivered to the user mailbox; bypass vector under investigation.

### Response Actions:
- Removed phishing email from all affected mailboxes.
- Blocked malicious indicators:
  - Sender email
  - Sender IP address
  - URL domain and path
  - Associated attachment indicators
- Conducted tenant-wide search across:
  - Sender address
  - IP address
  - URL
  - Attachment name and related artifacts
- Investigated user interaction with:
  - URL access
  - Credential submission attempts
  - Attachment execution or download
- Deployed targeted user awareness notification referencing the “Salary Revision” phishing attempt.

### Recommendations:
- Enhance email security posture using:
  - Microsoft Defender for Office 365 Safe Links
  - Safe Attachments detonation policies
  - Anti-phishing impersonation protections
- Strengthen email authentication enforcement:
  - SPF, DKIM, and DMARC alignment and strict policy enforcement.
- Improve detection tuning for HR/payroll-themed phishing campaigns.
- Enable continuous monitoring for anomalous authentication and credential abuse patterns.
- Conduct periodic phishing simulation exercises to reinforce user awareness.
- Perform gap analysis on email security controls to identify bypass conditions.

### Lessons Learned:
- Email-based threats can bypass initial filters when using trusted-looking HR or payroll lures.
- OSINT validation (VirusTotal, AbuseIPDB) is critical for confirming malicious indicators quickly.
- Message header analysis provides key visibility into email authenticity and routing.
- Early user interaction prevention is essential to limit credential theft and payload execution.
- Regular tuning of Safe Links and Safe Attachments policies improves detection coverage.
- Tenant-wide hunting helps assess blast radius and identify additional impacted users.
