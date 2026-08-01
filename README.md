# FTP vs SFTP Security Analysis

## Overview
A live demonstration comparing the security of FTP (File Transfer Protocol) 
and SFTP (Secure File Transfer Protocol) using Wireshark packet capture. 
The project proves that FTP transmits all data including credentials in 
plaintext, while SFTP encrypts everything through SSH — making it the only 
acceptable choice for secure file transfer.

## Objectives
- Set up a functional FTP environment using FileZilla Server
- Configure an SFTP environment using OpenSSH on Kali Linux
- Capture live network traffic during both FTP and SFTP sessions
- Analyse Wireshark captures to compare security characteristics
- Demonstrate the risk of using FTP in real-world environments

## Tools Used
| Tool | Purpose |
|---|---|
| FileZilla Server | FTP server configuration |
| Kali Linux | FTP client and SFTP demonstration environment |
| OpenSSH | SFTP server |
| Wireshark | Network packet capture and analysis |

## What Was Done

### 1. FTP Environment Setup
Configured a local FTP server using FileZilla with a test user account. 
A file (myproject4.txt.txt) was transferred from Kali Linux to the 
FileZilla server using the FTP protocol.

### 2. FTP Traffic Capture
Wireshark captured all traffic during the FTP session. The packet capture 
clearly showed:
- Username visible in plaintext: USER ftpuser
- Password visible in plaintext: PASS ftpuser12345
- File contents readable in the TCP stream

**Conclusion:** Any attacker monitoring the network could intercept 
credentials and file contents in real time.

### 3. SFTP Environment Setup
OpenSSH was configured on Kali Linux as the SFTP server. A file 
(sftp_groupproject4.txt) was transferred through the encrypted SFTP 
connection.

### 4. SFTP Traffic Capture
Wireshark captured all traffic during the SFTP session. Results:
- All packets appeared as SSHv2 encrypted data
- Credentials were not visible
- File contents were completely unreadable

**Conclusion:** SFTP encrypts all traffic through SSH — credentials and 
file contents are fully protected.

## Comparison

| Feature | FTP | SFTP |
| Encryption | None — plaintext | Full SSH encryption |
| Credentials | Visible in Wireshark | Encrypted and hidden |
| File Contents | Readable in packet capture | Unreadable |
| Port | 21 | 22 |
| MITM Vulnerability | High | Neutralized by SSH |
| Recommended | No | Yes |

## SFTP Security Mechanisms
- **Confidentiality:** SSH tunnel encrypts all data before transmission
- **Integrity:** Hash-based verification detects any tampering in transit
- **Authentication:** Key-based or password authentication over encrypted channel

## Real-World Implication
Banks, healthcare systems and enterprises use SFTP to transfer sensitive 
records. Using FTP in these environments would expose financial data, 
patient records and credentials to anyone monitoring network traffic.

## Skills Demonstrated
- Network protocol analysis
- FTP and SFTP configuration
- Wireshark packet capture and TCP stream analysis
- Security comparison and risk assessment
- Encryption concepts — SSH, confidentiality, integrity
- Wireshark packet capture and TCP stream analysis
- Security comparison and risk assessment
- Encryption concepts — SSH, confidentiality, integrity
