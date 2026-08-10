# Metasploitable2 — Penetration Testing & Vulnerability Assessment Lab

Two-week cybersecurity lab exercise: reconnaissance, exploitation-path identification, and automated vulnerability
scanning against **Metasploitable2**, an intentionally vulnerable Linux VM built for security training.

All testing was performed in an **isolated, host-only VirtualBox network** — no external or production systems
were touched at any point.

## 📋 Contents

| File | Description |
|---|---|
| `Security_Threat_Identification_Report_gopika.pdf` | Week 1 — Nmap reconnaissance, Wireshark traffic analysis, and Nessus vulnerability scan against Metasploitable2 |
| `Week2_Vulnerability_Assessment_Report_gopika.pdf` | Week 2 — Deeper automated vulnerability assessment with CVE cross-referencing and risk analysis |

## 🧪 Lab Environment

| Component | Details |
|---|---|
| Attacker machine | Kali Linux 2026.1 — `192.168.56.101` |
| Target | Metasploitable2 — `192.168.56.102` |
| Network | VirtualBox Host-only adapter (isolated, no internet-facing exposure) |
| Tools | Nmap 7.98, Wireshark, Tenable Nessus Essentials |

## 🔍 What was done

**Week 1 — Threat Identification**
- Full TCP service/version/OS-detection scan with Nmap (`nmap -sS -sV -O`)
- Packet capture and analysis of FTP and HTTP traffic with Wireshark to demonstrate plaintext credential exposure
- Unauthenticated external vulnerability scan with Nessus (Basic Network Scan policy)
- Documented 10 Critical-severity findings, including a known FTP backdoor (CVE-2011-2523) and an
  unauthenticated root-level bind shell on port 1524

**Week 2 — Vulnerability Assessment**
- Follow-up automated scan cross-referencing findings against published CVEs and vendor advisories
- Risk analysis of what an external, unauthenticated attacker could realistically achieve
- Prioritized mitigation roadmap (patch, reconfigure, or replace end-of-life components)

## ⚠️ Key findings (summary)

- **Unauthenticated root bind shell** (port 1524) — full system takeover with zero credentials
- **vsftpd 2.3.4 backdoor** (CVE-2011-2523) — remote code execution via FTP
- **UnrealIRCd backdoor** (CVE-2010-2075) — remote code execution via IRC daemon
- **Default VNC credential** (`password`) — full graphical remote-desktop takeover
- **End-of-life OS** (Ubuntu 8.04, EOL since 2013) — no vendor patches available for any future CVE
- **Plaintext credentials** over FTP and Telnet, confirmed via live packet capture
- **World-readable NFS shares**, **SMB Badlock** (CVE-2016-2118), **SSLv2/v3 & SWEET32** weak ciphers

Full severity breakdowns, CVSS scores, and remediation steps are in the reports.

## 🎯 Purpose & Disclaimer

This work was completed as part of a structured cybersecurity training program (Batch 9.145) for educational
purposes only. Metasploitable2 is a publicly available, deliberately vulnerable virtual machine distributed by
Rapid7 specifically for practicing these techniques in a legal, contained environment.

**Do not run these techniques against any system you do not own or do not have explicit written authorization
to test.** Unauthorized scanning or exploitation of systems is illegal in most jurisdictions.

## 👤 Author

**Gopika**
Cyber Security 

---
*Screenshots and evidence captures are included in the appendix of each report.*
