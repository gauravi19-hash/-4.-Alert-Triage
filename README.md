# SOC L1 Alert Triage

## Overview

This project demonstrates a hands-on SOC Analyst Level 1 alert triage workflow using a Security Operations Center (SOC) alert management platform.

The investigation focused on reviewing, prioritising, analysing, and classifying security alerts based on their severity, available evidence, and investigation findings.

The objective was to simulate the responsibilities of an SOC L1 analyst during the initial stages of security alert investigation.

---

## Objectives

- Review and prioritise incoming security alerts.
- Analyse alert severity, status, and relevant alert properties.
- Investigate suspicious security activity using available technical evidence.
- Identify potential Indicators of Compromise (IOCs).
- Determine whether an alert is a True Positive or False Positive.
- Document investigation findings.
- Close alerts according to the investigation outcome.

---

## Tools & Technologies

- TryHackMe – SOC L1 Alert Triage
- SOC Alert Management Platform
- Threat Intelligence / IOC Analysis
- Security Alert Triage
- Incident Investigation
- Windows Security Concepts

---

# Investigation Workflow

The investigation followed a typical SOC L1 workflow:

**Alert Queue → Prioritisation → Alert Analysis → Technical Investigation → Classification → Documentation → Closure**

---

## 1. Alert Prioritisation


### Finding

Five security alerts were reviewed and prioritised based on severity, status, and investigation state.

The **Critical – Potential Data Exfiltration** alert was identified as the highest-priority unresolved alert, followed by the **High – Double-Extension File Creation** alert.

Previously closed alerts were also reviewed based on their recorded True Positive and False Positive classifications.

### SOC L1 Skill Demonstrated

- Alert queue monitoring
- Severity-based prioritisation
- Identification of unresolved alerts
- Initial alert assessment

---

## 2. Alert Properties Analysis

### Finding

The selected alert was classified as **Critical** and reported **5.8 GB of sent data** and **5.2 GB of received data** between internal host `192.168.45.66` and the destination `*.zoom.us`.

The source was associated with the `UK04/MEETINGROOM` network.

The high volume of traffic required further investigation to determine whether the activity represented legitimate business traffic or potential data exfiltration.

### Key Alert Information

| Field | Value |
|---|---|
| Severity | Critical |
| Source IP | `192.168.45.66` |
| Source Network | `UK04/MEETINGROOM` |
| Destination | `*.zoom.us` |
| Sent Data | 5.8 GB |
| Received Data | 5.2 GB |

### SOC L1 Skill Demonstrated

- Alert field analysis
- Identifying relevant investigation data
- Understanding network activity
- Initial assessment of suspicious behaviour

---

## 3. Technical Investigation

### Finding

The High-severity **Double-Extension File Creation** alert was investigated using the affected host, user, process, file path, source URL, and MD5 hash.

The file:
`cats2025.mp4.exe`

used a suspicious **double extension**, which can be used to disguise an executable as a media file.

The source URL and associated MD5 hash were reviewed as additional indicators to assess the legitimacy of the downloaded file and determine the appropriate alert classification.

### Investigation Indicators

| Indicator | Observation |
|---|---|
| Host | `LPT-HR-009` |
| User | `S.Conway` |
| Process | `chrome.exe` |
| File | `cats2025.mp4.exe` |
| File Type | Executable disguised as media |
| Source | External download URL |
| Hash | MD5 associated with the file |

### SOC L1 Skill Demonstrated

- Technical alert investigation
- IOC identification
- File analysis
- Suspicious file masquerading detection
- Evidence-based alert classification

---

## 4. Triage Verdict & Resolution

### Finding

The investigation identified multiple indicators consistent with malicious file delivery, including the suspicious double extension, download source, and associated file hash.

The activity was classified as a **True Positive**.

The investigation findings were documented in the analyst comment and the alert was closed following the triage process.

### Analyst Comment

> Investigated `cats2025.mp4.exe` on `LPT-HR-009`. The double extension indicated possible executable masquerading. The source URL, browser process, and MD5 hash were reviewed as supporting indicators. Activity was confirmed as malicious and classified as **True Positive**. Alert documented and closed.

### SOC L1 Skill Demonstrated

- True Positive identification
- Analyst judgement
- Investigation documentation
- Alert closure
- SOC reporting

---

# Key Indicators Identified

### Suspicious File
cats2025.mp4.exe

The double extension is an indicator of potential file masquerading because the filename attempts to appear as a media file while retaining an executable extension.

Affected Host
LPT-HR-009
Affected User
S.Conway
Associated Process
chrome.exe
Investigation Outcome
Alert	Severity	Classification	Outcome
Potential Data Exfiltration	Critical	False Positive	Closed
Double-Extension File Creation	High	True Positive	Closed

The investigation demonstrated that SOC analysts must not automatically classify an alert as malicious based only on its severity. Alert context, affected assets, network activity, file characteristics, and available indicators must be reviewed before reaching a final verdict.

Skills Demonstrated
SOC L1 Alert Triage
Alert Prioritisation
Security Alert Analysis
Technical Investigation
IOC Identification
File Analysis
Network Activity Analysis
True Positive / False Positive Classification
Investigation Documentation
Alert Closure
SOC Workflow
Key Takeaways

This exercise provided practical experience in handling security alerts from initial prioritisation through final classification.

The investigation reinforced the importance of:

Prioritising critical and unresolved alerts.
Reviewing the complete alert context before making a decision.
Investigating technical indicators rather than relying only on alert severity.
Distinguishing legitimate activity from malicious behaviour.
Documenting investigation findings clearly.
Closing alerts only after reaching an evidence-based conclusion.
