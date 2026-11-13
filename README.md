# Kali-linux---nmap---networkwalks

# Week 2 — Footprinting & Network Scanning

This repository documents authorized cybersecurity lab work completed during Week 2 of the Networkwalks Cybersecurity & Ethical Hacking program.

## Project Information

- **Author:** Gowri Balamurugan  
- **Program:** Cybersecurity program at Networkwalks  
- **Batch:** B084-Networkwalks  
- **Week:** 02  
- **Date:** 13 November 2026  
- **Modules completed:** W2-PM1 (Multiple Kali Tools), W2-PM5 (Zenmap Scanning)  
- **Repository purpose:** Document footprinting, reconnaissance, network scanning, findings, and recommendations  

## Scope and Authorization

- **Footprinting target:** `networkwalks.com`
- **Network scanning target:** Author-owned local LAN
- **Authorization:** Written permission was secured for the authorized client target.
- **Testing performed:** Reconnaissance, footprinting, and host discovery only.
- **Exploitation:** Not performed.
- **Purpose:** Education, research, and authorized security assessment practice.

All activities were performed only on systems and networks for which explicit authorization was obtained or that were owned by the author. Unauthorized access is illegal in most jurisdictions and can result in criminal charges, fines, employment consequences, and a permanent record. [1]

## Objectives

- Perform domain footprinting and open-source reconnaissance.
- Identify exposed web technologies, DNS records, HTTP headers, and WAF information.
- Discover live hosts on an authorized local network.
- Identify local IP address, subnet, IP addresses, and MAC addresses.
- Generate and save a network topology using Zenmap.
- Document observations, risk analysis, and remediation recommendations.

## Tools Used

| Tool | Purpose |
|---|---|
| Kali Linux | Footprinting and reconnaissance |
| Windows | Local-network scanning environment |
| WHOIS | Domain registration and nameserver information |
| WhatWeb | Web technology fingerprinting |
| nslookup | DNS resolution |
| curl | HTTP response-header inspection |
| wafw00f | Web Application Firewall detection |
| DNSRecon | DNS record enumeration |
| Zenmap / Nmap | Local-network host discovery and topology mapping |
| Windows Command Prompt | Local IP and MAC-address identification |

## Methodology

### Phase 1: Footprinting and Reconnaissance

Reconnaissance was performed against `networkwalks.com` using WHOIS, WhatWeb, nslookup, curl, wafw00f, and DNSRecon.

The activity collected publicly available information about domain registration, hosting infrastructure, web technologies, DNS records, HTTP response headers, and WAF protection. [1]

### Phase 2: Network Scanning and Discovery

Zenmap was used to scan the author’s local network. The activity identified the local IP address and subnet, discovered active hosts, collected IP and MAC information, and generated a network topology. [1]

### Phases 3–5

Phases 3 through 5 were marked as in progress in the Week 2 report. [1]

## Footprinting Commands

Run these commands only against systems for which you have explicit authorization.

### WHOIS

```bash
whois networkwalks.com
```

### Web technology fingerprinting

```bash
whatweb [https://networkwalks.com](https://networkwalks.com)
```

### DNS resolution

```bash
nslookup networkwalks.com
```

### HTTP response headers

```bash
curl -I [https://networkwalks.com](https://networkwalks.com)
```

### WAF detection

```bash
wafw00f [https://networkwalks.com](https://networkwalks.com)
```

### DNS enumeration

```bash
dnsrecon -d networkwalks.com
```

## Network Scanning Commands

Use these commands only on networks you own or are explicitly authorized to assess.

### Identify local IP configuration

```powershell
ipconfig /all
```

### Ping sweep using Nmap

```bash
nmap -sn 192.168.1.0/24
```

### Zenmap configuration

- **Target:** `192.168.1.0/24`
- **Scan profile:** Ping Scan
- **Output:** Network topology exported as PDF
- **Evidence:** Screenshots of live hosts, IP/MAC details, and topology

## Observations

### Footprinting Results

- WHOIS provided publicly available domain-registration and nameserver information.
- WhatWeb identified WordPress 7.0.4 and WP Download Manager 3.3.58.
- nslookup resolved `networkwalks.com` to `192.232.216.135`.
- curl exposed HTTP response headers and the WordPress REST API endpoint `/wp-json/`.
- wafw00f identified ModSecurity (SpiderLabs).
- DNSRecon identified name-server, mail-server, SPF/TXT, service-record, and DNS-software information. [1]

### Network Scanning Results

- The local IP address and subnet were identified using Windows `ipconfig`.
- Zenmap Ping Scan identified live hosts in the example local subnet.
- The example results identified hosts at `192.168.1.1`, `192.168.1.4`, and `192.168.1.5`.
- Four MAC addresses were included in the example results.
- A network topology was generated and saved in PDF format. [1]

## Risk Register

| ID | Finding | Evidence / Observation | Potential Impact | Initial Risk |
|---|---|---|---|---|
| R-01 | Web technology information exposed | WhatWeb identified WordPress and WP Download Manager | Attackers may use exposed technology/version information to identify software requiring further security review | Medium |
| R-02 | Server IP address identifiable | nslookup resolved the domain to `192.232.216.135` | Provides information about the network location of the web service | Low |
| R-03 | HTTP technical information exposed | curl returned HTTP response headers and exposed `/wp-json/` | May assist technology fingerprinting and further enumeration | Low |
| R-04 | WAF technology identifiable | wafw00f identified ModSecurity (SpiderLabs) | Reveals information about the web application’s security architecture | Low |
| R-05 | DNS infrastructure information exposed | DNSRecon identified DNS, mail, SPF/TXT, and service-related records | DNS information can help build a broader infrastructure profile | Medium |
| R-06 | Multiple live hosts visible on local network | Zenmap identified live hosts in the example network | Unknown or unauthorized devices may potentially be present | Medium |

These findings are reconnaissance observations, not confirmed vulnerabilities. The presence of a software version, IP address, or DNS record does not by itself prove that a system is vulnerable. Further authorized testing would be required to validate any actual security issue. [1]

## Recommendations

1. **Review publicly exposed technology information** — Regularly review what information about web technologies, CMS platforms, and plugins is publicly visible.

2. **Keep software updated** — Keep WordPress, plugins, server components, and other web technologies updated and reviewed against current security advisories.

3. **Review HTTP headers** — Review HTTP response headers and reduce unnecessary technical disclosure.

4. **Review DNS records regularly** — Check DNS records periodically and remove unnecessary public exposure.

5. **Properly configure and monitor the WAF** — Keep ModSecurity enabled, tuned, and monitored.

6. **Perform regular internal network discovery** — Periodically scan authorized internal networks to identify active devices.

7. **Investigate unknown devices** — Investigate and verify any unexpected device discovered during network scanning.

8. **Maintain network documentation** — Keep network topology, device inventory, and asset information current.

9. **Perform security testing with authorization** — Conduct reconnaissance and scanning only against systems and networks where appropriate authorization has been provided. [1]

## Repository Structure

```text
week2-footprinting-network-scanning/
├── README.md
├── LICENSE
├── .gitignore
├── reports/
│   └── Week2-report-NW.pdf
├── evidence/
│   ├── screenshots/
│   └── topology/
├── commands/
│   ├── footprinting-commands.md
│   └── network-scanning-commands.md
├── findings/
│   ├── risk-register.md
│   └── recommendations.md
└── docs/
    ├── scope-and-authorization.md
    └── methodology.md
```

## Evidence Handling

Before publishing this repository publicly:

- Blur or remove real MAC addresses, internal hostnames, usernames, and sensitive screenshots.
- Do not upload raw Nmap XML, packet captures, credentials, authorization documents, or unredacted client evidence.
- Keep the signed authorization record private.
- Publish only a redacted scope and authorization summary.
- Mark the repository private if it contains identifiable client information or full internal-network evidence. [1]

## Ethical Use

This repository is for educational and authorized security-testing purposes only. Do not use any commands, techniques, or information here against systems or networks without explicit permission.

Misuse can lead to criminal charges, heavy fines, loss of employment, and a permanent record. The author, instructor, and Networkwalks are not responsible for unauthorized use of this material. [1]

## Author

**Gowri Balamurugan**  
Cybersecurity Professional — B084, Networkwalks  
LinkedIn: https://www.linkedin.com/in/gowri-balamurugan-2ba36b313
