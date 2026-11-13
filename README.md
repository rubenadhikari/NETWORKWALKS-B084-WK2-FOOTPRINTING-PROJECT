<img width="1275" height="720" alt="WAFFW00F_Results" src="https://github.com/user-attachments/assets/d13a25ef-47df-43ab-96eb-42857238cff1" /># PENETRATION TESTING REPORT

### FOOTPRINTING & NETWORK SCANNING PHASES

**W2-PM-FINAL | CYBERSECURITY | NETWORKWALKS**

| Field | Detail |
|---|---|
| Pentester Name | Ruben Adhikari |
| Program/Batch | B084 – NetworkWalks |
| Date | 13 November 2026 |
| Modules Completed | W2-PM1 – Multiple Kali Tools; W2-PM5 – Zenmap Scanning |
| Client/Target | 1. networkwalks.com (instructor-authorized educational exercise) 2. My own local Wi-Fi network |
| Permission Secured? | Instructor approval for the assigned domain exercise; own home network for local scanning |
| Phases Covered | Phase 1: Reconnaissance & Footprinting; Phase 2: Scanning & Network Discovery |

---

# 1. Liability Disclaimer

I have performed these activities only on systems and networks that were within the authorized scope of my educational exercises or that I personally own or control.

The activities documented in this report were conducted for educational and cybersecurity learning purposes as part of the NetworkWalks program.

The footprinting exercise against networkwalks.com was performed with instructor approval. The Zenmap network scanning exercise was performed on my own home Wi-Fi network.

No exploitation, unauthorized access, or intentional disruption of services was performed.

All information in this report is intended for educational and research purposes only. Any misuse of the techniques described in this report is the responsibility of the individual performing such activities. Unauthorized access to computer systems and networks may result in legal consequences.

---

# 2. Introduction

This report covers the practical cybersecurity activities completed during Week 2 of the NetworkWalks Cybersecurity & Ethical Hacking program.

The project focuses on two main areas:

**W2-PM1 – Footprinting and Reconnaissance Using Multiple Kali Linux Tools**

This module involved using six Kali Linux tools to collect publicly observable information about the networkwalks.com domain. The tools included WHOIS, WhatWeb, Nslookup, cURL, Wafw00f, and DNSRecon.

**W2-PM5 – Network Scanning with Zenmap**

This module involved using Zenmap on a Windows 11 computer to discover live hosts on my own local network, identify their IP addresses and available MAC addresses, and generate a network topology diagram.

The main purpose of these activities was to understand how cybersecurity professionals gather information about a target and identify active devices within a network.

Throughout the exercises, I collected screenshots and saved command outputs to document the activities performed and the results obtained.

These activities helped me understand the importance of reconnaissance and network discovery as fundamental stages of cybersecurity assessment.

---

# 3. Tools Used

The following tools and technologies were used during the project.

| Tool | Purpose |
|---|---|
| Kali Linux | Operating system used for footprinting activities |
| WHOIS | Retrieve domain registration and name server information |
| WhatWeb | Identify publicly observable website technologies |
| Nslookup | Resolve domain names into IP addresses |
| cURL | Inspect HTTP response headers |
| Wafw00f | Identify possible Web Application Firewall protection |
| DNSRecon | Enumerate DNS records |
| Zenmap | Graphical interface for network scanning |
| Nmap | Network discovery engine used by Zenmap |
| Windows 11 | Operating system used for the Zenmap exercise |
| Windows CMD | Identify local network configuration |

---

# 4. Activities Performed

## 4.1 Footprinting & Reconnaissance – W2-PM1

For this activity, I performed footprinting and reconnaissance against the authorized educational target, `networkwalks.com`, using six Kali Linux tools.

Each tool provided a different type of information about the domain and its publicly observable infrastructure.

### 4.1.1 WHOIS – Domain Information Gathering

**Objective:** Collect publicly available domain registration information.

**Command used:**

```bash
whois networkwalks.com
```
<img width="1230" height="722" alt="WHOIS_Results" src="https://github.com/user-attachments/assets/f7f0aa8b-b881-4070-b185-2a0355decaa7" />

**Findings:**

- Domain: NETWORKWALKS.COM
- Registrar: GoDaddy.com, LLC
- Creation Date: November 6, 2019
- Expiration Date: November 6, 2027
- Name Server 1: NS6135.HOSTGATOR.COM
- Name Server 2: NS6136.HOSTGATOR.COM
- DNSSEC: Unsigned
- Registrant information: Protected through Domains By Proxy.

**Analysis:**

The WHOIS lookup provided information about the domain's registration history, registrar, name servers, and registration privacy protection.

This information is useful during the initial reconnaissance stage because it helps establish basic details about a target domain and its DNS infrastructure.

### 4.1.2 WhatWeb – Website Technology Identification

**Objective:** Identify technologies and frameworks used by the target website.

**Command used:**

```bash
whatweb networkwalks.com
```
<img width="1272" height="717" alt="WHATWEB_Results" src="https://github.com/user-attachments/assets/2817853f-0a6e-4f97-8d83-38e64269353b" />

**Findings:**

- HTTP redirected to HTTPS.
- HTTPS returned status code 200 OK.
- Web server: Apache.
- WordPress detected.
- Bootstrap detected.
- jQuery version: 3.7.1.
- WordPress Download Manager detected.
- Google Tag Manager detected.
- Website title: Networkwalks Academy.
- Resolved IP address: 192.232.216.135.

**Analysis:**

WhatWeb identified several technologies used by the website.

Technology identification is useful during reconnaissance because publicly observable information about software and frameworks can help security professionals understand the website's technology stack.

However, identifying a technology does not automatically mean that the website contains a vulnerability.

### 4.1.3 Nslookup – DNS Resolution

**Objective:** Identify the IP address associated with the target domain.

**Command used:**

```bash
nslookup networkwalks.com
```
<img width="1275" height="725" alt="NSLOOKUP_Results" src="https://github.com/user-attachments/assets/19a64743-79d1-4c5e-b5b6-a468930bb537" />

**Findings:**

- DNS Server: 10.0.0.1
- Domain: networkwalks.com
- Resolved IPv4 Address: 192.232.216.135

**Analysis:**

Nslookup successfully resolved the domain name to its corresponding IPv4 address.

This demonstrates how DNS resolution can be used to identify the IP address associated with a website.

### 4.1.4 cURL – HTTP Response Header Inspection

**Objective:** Inspect the HTTP response headers returned by the target website.

**Command used:**

```bash
curl -I https://networkwalks.com
```
<img width="1272" height="722" alt="CURL-I_Results" src="https://github.com/user-attachments/assets/e34db34c-c847-4cf9-8e28-f38b2362cc82" />

**Findings:**

- HTTP Response: 200 OK
- Server: Apache
- Content-Type: text/html; charset=UTF-8
- The server returned HTTP response headers.

**Analysis:**

The cURL command successfully retrieved the HTTP response headers without downloading the complete webpage.

This activity demonstrated how HTTP metadata can provide information about a web server and its response behavior.

### 4.1.5 Wafw00f – Web Application Firewall Detection

**Objective:** Identify whether the target website uses a Web Application Firewall.

**Command used:**

```bash
wafw00f https://networkwalks.com
```
<img width="1275" height="720" alt="WAFFW00F_Results" src="https://github.com/user-attachments/assets/ef56b314-8ee6-4096-86fd-88963497a22e" />

**Findings:**

- WAF detected: ModSecurity.
- Associated identification: SpiderLabs.
- Number of requests: 2.

**Analysis:**

Wafw00f identified ModSecurity as the Web Application Firewall associated with the target website.

A WAF is used to help monitor and filter potentially malicious web traffic. Identifying the presence of a WAF provides information about the website's security architecture.

The detection result does not independently establish how effectively the WAF is configured.

### 4.1.6 DNSRecon – DNS Enumeration

**Objective:** Collect DNS records associated with the target domain.

**Command used:**

```bash
dnsrecon -d networkwalks.com
```
<img width="1267" height="865" alt="DNSRECON-D_Results" src="https://github.com/user-attachments/assets/6e332f07-32d6-4a2e-ba54-1f871e623c77" />

**Findings:**

- SOA record identified.
- Authoritative name servers identified:
  - ns6135.hostgator.com
  - ns6136.hostgator.com
- MX record identified: mail.networkwalks.com.
- A record identified: 192.232.216.135.
- TXT records included Google site verification and SPF information.
- SRV autodiscover records identified.
- DNSSEC query returned no answer.

**Analysis:**

DNSRecon successfully identified multiple DNS records associated with the domain.

The results provided information about the domain's name servers, mail configuration, TXT records, and service-related records.

This activity demonstrated how DNS enumeration can help build an understanding of a domain's publicly observable infrastructure.

### 4.1.7 PM1 Summary

The six Kali Linux tools provided different types of information about networkwalks.com.

WHOIS provided registration information, WhatWeb identified website technologies, Nslookup resolved the domain, cURL inspected HTTP headers, Wafw00f identified WAF protection, and DNSRecon enumerated DNS records.

Using multiple tools provided a broader understanding of the target than using a single reconnaissance tool.

---

## 4.2 Network Scanning with Zenmap – W2-PM5

For the second activity, I used Zenmap on Windows 11 to discover active hosts on my own local Wi-Fi network.

The practical exercise required identifying my local IP address and subnet, discovering live hosts, recording IP and MAC address information, and generating a network topology diagram.

### 4.2.1 Zenmap Installation

Zenmap was downloaded and installed on my Windows 11 computer using the official Nmap download page.

Official website:

https://nmap.org/download.html

After installation, I opened Zenmap successfully.

### 4.2.2 Local IP Address and LAN Subnet

I used the Windows Command Prompt and the `ipconfig` command to identify my computer's network configuration.

**Network Information:**

| Field | Result |
|---|---|
| Local IP Address | 192.168.1.74 |
| Subnet Mask | 255.255.255.0 |
| LAN Subnet | 192.168.1.0/24 |
| Default Gateway | 192.168.1.254 |

This information was used to determine the correct local network range for the Zenmap exercise.

### 4.2.3 Ping Scan – Live Host Discovery

**Objective:** Identify active devices on the local subnet.

**Target:**

```text
192.168.1.0/24
```

**Selected Profile:** Ping Scan

**Nmap Command:**

```bash
nmap -sn 192.168.1.0/24
```

The `-sn` option performs host discovery without conducting a port scan.

**Findings:**

The scan examined the local subnet and identified three live hosts.

| Host | IP Address | Status |
|---|---|---|
| Windows PC | 192.168.1.74 | Up |
| Discovered Device | 192.168.1.76 | Up |
| Default Gateway | 192.168.1.254 | Up |

**Total Live Hosts: 3**

### 4.2.4 MAC Address Identification

The Zenmap scan displayed MAC address information for two discovered devices.

| IP Address | MAC Address |
|---|---|
| 192.168.1.76 | 86:65:CD:XX:XX:CF |
| 192.168.1.254 | C4:48:EA:XX:XX:28 |
| 192.168.1.74 | Not displayed in Zenmap output |

The MAC addresses have been partially redacted in this public report to protect device privacy.

The Windows PC's MAC address was not displayed in the Zenmap scan output.

### 4.2.5 Network Topology

After completing the Ping Scan, I opened the Topology tab in Zenmap.

I enabled the topology legend to understand the displayed network diagram and used the Save Graphic option to export the topology.

The topology was saved in PDF format as required by the project instructions.

The topology diagram is included in the W2-PM5 evidence folder.

### 4.2.6 Online Practice Lab

After completing the Zenmap practical exercise, I also completed the official NetworkWalks Zenmap Network Scanning Practice Lab.

**Final Score: 100%**

Practice Lab:

https://networkwalks.com/zenmap-network-scanning-practice-lab/

This exercise helped reinforce my understanding of Zenmap, Nmap, network discovery, and host identification.

### 4.2.7 PM5 Summary

The Zenmap exercise successfully identified three live hosts on my local `/24` network.

The activity demonstrated how Ping Scan can be used to identify active devices and how Zenmap can visualize discovered hosts through its topology feature.

The scan was limited to host discovery. No exploitation or unauthorized access was attempted.

---

# 5. Risk Analysis / Impact

Based on the information collected during the footprinting and network scanning activities, the following potential security observations were identified.

| No. | Risk / Finding | Evidence / Observation | Potential Impact | Risk Level |
|---|---|---|---|---|
| 1 | Web technology information exposed | WhatWeb identified WordPress and other website technologies. | May help attackers identify technologies requiring further security review. | Low |
| 2 | Server IP address identifiable | Nslookup resolved the domain to 192.232.216.135. | Provides information about the network location of the web service. | Low |
| 3 | HTTP technical information exposed | cURL returned HTTP response headers. | May assist technology fingerprinting and further enumeration. | Low |
| 4 | WAF technology identifiable | Wafw00f identified ModSecurity. | Reveals information about the web application's security architecture. | Low |
| 5 | DNS infrastructure information exposed | DNSRecon identified DNS, mail, and service-related records. | DNS information can help build a broader infrastructure profile. | Low |
| 6 | Multiple live hosts visible on local network | Zenmap identified three live hosts on the local subnet. | Unknown devices on a network may require investigation. | Low |

**Risk Level Key:**

- Low: Information exposure or observation with limited demonstrated impact.
- Medium: Potentially greater impact requiring further investigation.
- High: Significant security concern requiring prompt attention.
- Critical: Severe security issue with potentially substantial consequences.

The risk levels above are preliminary assessments based on the observations from the exercises. They are not confirmed vulnerability ratings.

The practical exercises primarily involved information gathering and host discovery. No exploitation, vulnerability validation, or penetration into the identified systems was performed.

Therefore, the presence of software information, IP addresses, DNS records, or active network devices does not independently establish that a vulnerability exists.

Further authorized security testing would be necessary to confirm any actual security weaknesses.

---

# 6. Recommendations

Based on the observations from these activities, I recommend the following security improvements:

### 1. Review Publicly Exposed Technology Information

Organizations should periodically review the information exposed about their website technologies, CMS platforms, frameworks, and plugins.

### 2. Keep Software Updated

CMS platforms, plugins, frameworks, and other web technologies should be regularly updated to address known security issues.

### 3. Review HTTP Security Configuration

HTTP response headers should be reviewed to identify unnecessary technical information and ensure appropriate security configurations.

### 4. Review DNS Records Regularly

DNS records should be reviewed periodically to ensure that only necessary information and services are publicly exposed.

### 5. Properly Configure and Monitor the WAF

Web Application Firewalls should be properly configured, maintained, and monitored to help identify and filter potentially malicious web traffic.

### 6. Perform Regular Internal Network Discovery

Organizations should periodically scan their own networks to identify active devices and maintain an accurate inventory.

### 7. Investigate Unknown Devices

Any unfamiliar device discovered during network scanning should be investigated and verified before being considered authorized.

### 8. Maintain Network Documentation

Network topology diagrams and device inventories should be documented and updated regularly.

### 9. Perform Security Testing with Authorization

All reconnaissance, scanning, and penetration-testing activities should be performed only within an explicitly authorized scope.

---

# 7. Conclusion

During Week 2 of my Cybersecurity & Ethical Hacking internship with NetworkWalks, I completed practical activities covering footprinting, reconnaissance, and network scanning.

In W2-PM1, I used six Kali Linux tools to collect information about the authorized target domain. I learned how WHOIS provides domain registration information, WhatWeb identifies web technologies, Nslookup resolves domain names, cURL inspects HTTP headers, Wafw00f identifies WAF protection, and DNSRecon enumerates DNS records.

In W2-PM5, I used Zenmap on Windows 11 to identify my local network configuration and discover active hosts. The scan identified three live hosts on my local network. I also collected the available MAC address information and generated a network topology diagram in PDF format.

I additionally completed the official Zenmap Network Scanning Practice Lab with a score of 100%.

These exercises improved my understanding of how reconnaissance and network discovery are performed during the early stages of cybersecurity assessments.

I also learned the importance of collecting accurate evidence, documenting technical findings, identifying potential security implications, and providing appropriate recommendations.

Most importantly, these activities reinforced the importance of performing cybersecurity testing within an authorized scope.

Overall, Week 2 provided valuable practical experience with Kali Linux reconnaissance tools, DNS enumeration, network discovery, and Zenmap.

---

# 8. Evidences Collected

All screenshots, terminal outputs, and supporting files are organized in the corresponding module folders in this repository.

## W2-PM1 – Multiple Kali Linux Tools

The following evidence was collected:

1. WHOIS – Domain registration information.
2. WhatWeb – Website technology identification.
3. Nslookup – DNS resolution results.
4. cURL – HTTP response headers.
5. Wafw00f – WAF detection results.
6. DNSRecon – DNS enumeration results.

Evidence folders:

- `W2-PM1-Multiple-Kali-Tools/screenshots/`
- `W2-PM1-Multiple-Kali-Tools/outputs/`

## W2-PM5 – Zenmap Network Scanning

The following evidence was collected:

1. Zenmap installation screenshot.
2. Ping Scan results showing three live hosts.
3. Network topology screenshot with legend.
4. Zenmap Network Scanning Practice Lab result showing 100%.
5. Network topology exported in PDF format.

Evidence folders:

- `W2-PM5-ZENMAP-NETWORK-SCANNING/screenshots/`
- `W2-PM5-ZENMAP-NETWORK-SCANNING/topology/`

---

**END OF REPORT**
