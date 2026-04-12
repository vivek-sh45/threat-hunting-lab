# Threat Hunting Lab

## Overview
This project demonstrates a basic threat hunting investigation using network traffic analysis. The objective is to identify suspicious activity and possible attacker communication within captured network traffic.

## Tools Used
- Wireshark
- PCAP Network Dataset
- Packet Analysis

## Investigation Methodology

### 1. DNS Traffic Analysis
Filtered DNS queries to identify suspicious domain names and repeated DNS requests.

Wireshark Filter
dns

### 2. HTTP Traffic Analysis
Analyzed HTTP requests to detect unusual web traffic and potential malicious downloads.

Wireshark Filter
http

### 3. Suspicious IP Investigation
Identified external IP addresses communicating frequently with the host.

Wireshark Filter
ip.addr

### 4. Network Conversation Analysis
Reviewed TCP streams to observe communication patterns between hosts.

Wireshark Filter
tcp.stream

## Indicators of Compromise (IOC)

Example indicators discovered during analysis:

- Suspicious IP Address
- Repeated DNS Queries
- Possible command-and-control communication

## Findings

The analysis revealed abnormal network communication patterns including repeated DNS queries and connections to unknown external IP addresses which may indicate malicious activity.

## Conclusion

Threat hunting techniques using network traffic analysis can help identify potential malware communication and suspicious activity within a network.

## Author

Vivek Sharma  
Cybersecurity Enthusiast
