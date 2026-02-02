# Network-Recon-Scripts
A collection of scripts and command-line techniques for network discovery and service enumeration.
# Network Reconnaissance Scripts & Techniques

This repository documents a series of hands-on exercises in network reconnaissance and analysis. It contains a collection of scripts and command-line techniques for network discovery and service enumeration, including examples of using tools like `nmap`, `grep`, and `tcpdump` to perform host discovery, identify services, and analyze network protocol behavior.

All work was performed in a sandboxed virtual environment against test machines like Metasploitable.

### Key Skills Demonstrated:
*   **Live Host Discovery:** Identifying active machines on a network.
*   **Service Enumeration:** Discovering open ports and identifying running software versions.
*   **Network Protocol Analysis:** Differentiating between TCP and UDP scan behaviors.
*   **Command-Line Fu:** Proficient use of `nmap`, `grep`, `cut`, and `tcpdump` for targeted data extraction and analysis.

---

## Live Host Discovery

### Objective
To efficiently identify all active hosts on a given subnet that respond to a ping request.

### Method
I constructed a bash one-liner that chains several commands together:
1.  `nmap -sn`: Performs a fast, "no-ports" ping scan to find live hosts.
2.  `grep`: Filters the output to isolate lines that contain host IP addresses.
3.  `cut`: Parses the filtered lines to extract only the IP address field.
4.  The final, clean list of IPs is redirected into a file named `live-hosts.lst`.

### Command
```bash
nmap -sn <target-subnet> | grep 'Nmap scan' | cut -d ' ' -f 5 > live-hosts.lst
