# 🎯 Threat Hunting Lab — Network Traffic Investigation

![Tool](https://img.shields.io/badge/Tool-Wireshark-1679A7?style=for-the-badge&logo=wireshark&logoColor=white)
![Type](https://img.shields.io/badge/Type-Threat%20Hunting-purple?style=for-the-badge)
![MITRE](https://img.shields.io/badge/MITRE-T1071%20%7C%20T1059-red?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge)

> **Real-world threat hunting investigation** — analyzed a PCAP capture containing actual malicious traffic, identified a compromised internal host communicating with a suspicious external C2 server, detected PowerShell malware download, and documented full IOC set with MITRE ATT&CK mapping.

---

## 🎯 Objective

Unlike reactive SOC work (responding to alerts), **threat hunting is proactive** — analysts search for hidden threats that evaded detection. This lab simulates that workflow: start with raw PCAP, find the attacker, document the attack chain.

---

## 🛠️ Tools & Environment

| Component | Details |
|---|---|
| **Tool** | Wireshark |
| **Data Source** | PCAP network capture file |
| **Analysis Focus** | DNS queries, HTTP traffic, C2 communication |
| **Outcome** | Full IOC documentation + MITRE ATT&CK mapping |

---

## 📋 Hunting Methodology

### Phase 1 — DNS Analysis (Find suspicious domains)
```wireshark
dns
```
- Reviewed all DNS queries for unusual or newly-registered domains
- Identified external domain queries not matching known-good baselines

### Phase 2 — HTTP Traffic Investigation
```wireshark
http
```
- Examined all HTTP GET/POST requests
- Identified file downloads from external IPs

### Phase 3 — C2 Communication Detection
```wireshark
ip.addr == 5.252.153.241
```
- Confirmed sustained communication between internal host and external server
- Analyzed packet payload to identify downloaded content

### Phase 4 — IOC Extraction & Documentation
- Extracted all IPs, domains, file names as Indicators of Compromise
- Mapped behavior to MITRE ATT&CK framework

---

## 🔴 Indicators of Compromise (IOC)

| IOC Type | Value | Significance |
|---|---|---|
| **Infected Host IP** | `10.1.17.215` | Internal victim machine |
| **Attacker C2 IP** | `5.252.153.241` | External command & control server |
| **Malicious File** | `29842.ps1` | PowerShell malware script |
| **Protocol** | HTTP (port 80) | Unencrypted C2 channel |
| **Method** | HTTP GET request | File download from C2 |

---

## ⚔️ Attack Chain Reconstruction

```
[Internal Host: 10.1.17.215]
         |
         | DNS query → resolved attacker domain
         |
         | HTTP GET request to 5.252.153.241
         |
         | ← Downloaded: 29842.ps1 (PowerShell script)
         |
         | PowerShell script execution → potential malware install
         |
[Attacker C2: 5.252.153.241]
```

---

## 🛡️ MITRE ATT&CK Mapping

| Tactic | Technique | ID | Evidence |
|---|---|---|---|
| Command & Control | Application Layer Protocol: Web Protocols | T1071.001 | HTTP C2 communication |
| Execution | Command and Scripting Interpreter: PowerShell | T1059.001 | `29842.ps1` downloaded & executed |
| Initial Access | Drive-by Compromise | T1189 | Malicious file delivery via HTTP |
| Exfiltration | Exfiltration Over C2 Channel | T1041 | Sustained C2 session |

---

## 📸 Investigation Screenshots

> Screenshots in `/screenshots` folder:
> - `dns-traffic-analysis.png` — DNS query investigation
> - `suspicious-domain-detection.png` — Attacker domain identified
> - `http-request-analysis.png` — HTTP GET to C2 server
> - `powershell-download-detection.png` — PowerShell script download captured

---

## 💡 Skills Demonstrated

- ✅ Proactive threat hunting methodology
- ✅ PCAP analysis with Wireshark
- ✅ C2 communication identification
- ✅ DNS & HTTP traffic investigation
- ✅ IOC extraction & documentation
- ✅ Full MITRE ATT&CK kill chain mapping
- ✅ Incident-quality written findings

---

## 🔗 Related Projects

| Project | Description |
|---|---|
| [Wireshark Network Analysis](https://github.com/vivek-sh45/wireshark-network-traffic-analysis) | Network traffic monitoring & anomaly detection |
| [Splunk SOC Investigation](https://github.com/vivek-sh45/splunk-soc-incident-investigation) | SIEM-based brute-force detection |
| [SOC Alert Detection Lab](https://github.com/vivek-sh45/soc-alert-detection-lab) | System log alert triage |

---

## 👤 Author

**Vivek Sharma** — Cybersecurity Analyst (Fresher) | Threat Detection & SOC Operations

[![LinkedIn](https://img.shields.io/badge/LinkedIn-vivek--sharma--cybersec-0077B5?style=flat&logo=linkedin)](https://linkedin.com/in/vivek-sharma-cybersec)
[![GitHub](https://img.shields.io/badge/GitHub-vivek--sh45-181717?style=flat&logo=github)](https://github.com/vivek-sh45)
[![Email](https://img.shields.io/badge/Email-thecybervivek@gmail.com-D14836?style=flat&logo=gmail)](mailto:thecybervivek@gmail.com)
