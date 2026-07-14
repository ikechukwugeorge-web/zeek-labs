Lab 01 – Web Browsing Investigation
Overview

This lab demonstrates how Zeek can be used to analyze a packet capture (PCAP) generated from normal web browsing activity. The captured traffic was processed with Zeek to produce structured network logs, allowing efficient investigation of DNS queries, HTTP requests, TLS sessions, QUIC connections, and overall network communications.

The objective of this lab is to understand how Zeek transforms raw packet captures into searchable metadata that can be used during network investigations and incident response.

Objectives
Analyze a PCAP using Zeek
Investigate network connections
Examine DNS queries and responses
Analyze HTTP requests and responses
Review TLS session metadata
Identify QUIC (HTTP/3) connections
Correlate activity across multiple Zeek logs
Tools Used
Kali Linux
Zeek
Docker
Wireshark
Files Included
lab01-web-browsing/
├── lab01-web-browsing.pcapng
├── zeek-logs/
│   ├── conn.log
│   ├── dns.log
│   ├── http.log
│   ├── ssl.log
│   └── quic.log
├── screenshots/
└── notes/
Zeek Logs Analyzed
conn.log

Used to investigate:

Source and destination IP addresses
Ports
Protocols
Connection states
Packets transferred
Bytes transferred
Connection duration
dns.log

Used to identify:

Domain names queried
DNS server
Returned IP addresses
Query types
DNS response codes
TTL values
http.log

Used to examine:

HTTP methods
Requested hosts
Requested URIs
HTTP status codes
User-Agent strings
Response sizes
ssl.log

Used to review:

TLS version
Cipher suite
Server Name Indication (SNI)
TLS handshake status
Encryption metadata
quic.log

Used to identify:

HTTP/3 traffic
QUIC connections
QUIC server names
HTTP/3 protocol usage
Investigation Summary

The analysis revealed normal web browsing activity. DNS lookups successfully resolved requested domains, HTTP traffic showed expected GET requests and server responses, TLS logs confirmed encrypted HTTPS sessions using TLS 1.3, and QUIC logs identified HTTP/3 communications.

No indicators of malicious activity were observed during this investigation.

Skills Demonstrated
PCAP analysis
Zeek log analysis
Network traffic investigation
DNS analysis
HTTP analysis
TLS investigation
QUIC analysis
Connection correlation
Network metadata interpretation
Digital forensics fundamentals

Author

ikechukwu George
