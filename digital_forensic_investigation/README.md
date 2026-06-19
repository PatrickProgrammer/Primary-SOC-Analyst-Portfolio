# Digital Forensics Case Study: Corporate Espionage & Anti-Forensic Triage

## 📋 Executive Summary
This repository details a comprehensive, court-ready digital forensics investigation into an incident of unauthorized data disclosure and corporate espionage. The investigation focuses on a suspect employee alleged to have extracted and leaked highly confidential proprietary data ("Seed Files") from a secure corporate network to an external competitor in exchange for financial compensation.

The forensic analysis successfully reconstructed a complete timeline of the insider threat lifecycle: from initial contact via compromised communication channels, to secure network data staging, unauthorized hardware exfiltration, and the final deployment of aggressive anti-forensic applications used to destroy evidence. 

Adhering to strict digital forensic workflow standards and legal parameters, the investigative findings established attribution to a high degree of certainty (exceeding 95%).

---

## 🛠️ Tools & Forensic Environment
To ensure forensic integrity and maintain a verifiable chain of custody, the investigation was conducted using industry-standard tools:
* **Digital Forensics Suites:** Autopsy, FTK Imager
* **Artifact Parsing & Triage:** Eric Zimmerman's Tools (`MFTECmd` for Master File Table analysis, `PECmd` for Prefetch execution validation, and `LECmd` for Windows Shortcut parsing)
* **Environment Utilities:** Windows Command Prompt and PowerShell for localized data triage and automated cryptographic hashing
* **Integrity Validation:** Cryptographic verification using SHA-1 and SHA-256 hashing to confirm the data preservation state of all forensic images

---

## 💾 Scope of Evidence Analyzed
The scope of work involved a correlated cross-media analysis of four distinct storage assets seized during the investigation:
1. **Target Workstation Image:** A Windows 7 Ultimate endpoint assigned to the subject of interest.
2. **Authorized Corporate Removable Storage:** A company-issued USB drive permitted for standard business activities.
3. **Unauthorized Personal Removable Storage:** An employee-owned USB drive seized at a security checkpoint.
4. **Unauthorized Optical Media (CD-ROM):** An ISO-formatted CD target confiscated during physical security screening.

---

## 🔍 Key Forensic Findings & Artifact Correlation

### 1. Compromised Communications & Cloud Staging
* **Corporate Email Analysis:** Forensic recovery of Outlook mail transport headers mapped a structured conversation between the suspect endpoint (`iaman-informant@nist.gov.ost`) and an outside handler (`spy.conspirator@nist.gov`), confirming explicit coordination to trade physical media for monetary gain.
* **Cloud Storage Artifacts:** Examination of localized Google Drive databases (`sync_config.db` and `snapshot.db`) revealed explicit file metadata remnants and upload paths, proving web-based data exposure attempts.

### 2. Network Intrusions & Removable Media Exfiltration
* **Secure Storage Access:** Timeline correlation validated that the endpoint initiated unauthorized traversal into the company's restricted network file storage repository over the network.
* **USB Device Identification:** Windows Registry forensics parsed from the `SYSTEM` hive extracted distinct hardware serial numbers, explicitly matching the unauthorized personal USB drive to connection logs on the endpoint within the data theft window.
* **File Access Verification:** Windows Shortcut (`.lnk`) file analysis confirmed the direct target path execution and extraction of 17 proprietary "Seed Files" directly onto the unauthorized removable device.
* **Bypassing Network Monitoring:** Shortcuts matching an optical path (`CD Drive.lnk`) validated the insertion and attempt to use alternative media to blind network-based Data Loss Prevention (DLP) filters.

### 3. Anti-Forensic Indicators & Evidence Tampering
* **Wiping Software Installation:** Parsing of the `$MFT` table and Windows Prefetch application files confirmed the simultaneous installation of two file-shredding suites: CCleaner and Eraser.
* **Data Destruction Tracking:** Prefetch analysis (`PECmd`) verified that `ERASER.EXE` and `CCLEANER.EXE` were sequentially executed on the system, resulting in the deep-wiping and unrecoverable mass deletion of more than 8,000 files in a deliberate attempt to clear system activity records.
* **MFT Timestomping Detection:** Comparative analysis of `$MFT` record attributes detected discrepancies in standard timestamp patterns, confirming that the subject programmatically manipulated file attributes to corrupt the evidentiary timeline.

---

## 💼 Professional Deliverables (Sanitized)
The complete findings, methodologies, and technical validations have been compiled into two distinct, professional forensic reporting components located within this repository:

* 📄 **[Technical Forensic Investigation Report](./technical-report.pdf)** - A granular engineering document engineered for Security Operations and Incident Response teams, breaking down raw byte offsets, specific registry paths, script outputs, and evidentiary screenshots.
* ⚖️ **[Court-Ready Expert Witness Report](./court-expert-report.pdf)** - A formalized legal document structured for litigation, translating complex system telemetry into an objective, chronological chain of facts tailored for corporate legal counsel and judicial presentation.
