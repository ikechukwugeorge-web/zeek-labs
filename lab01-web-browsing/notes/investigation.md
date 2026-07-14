Investigation Notes – Lab 01
Objective

Analyze a packet capture containing normal web browsing activity using Zeek and identify the network activity recorded in each generated log.

Evidence
Original PCAP captured with Wireshark
Zeek-generated logs
Screenshots of important findings
Investigation Process
Step 1

Loaded the packet capture into Zeek for analysis.

Step 2

Reviewed conn.log to identify network connections, protocols, connection states, packet counts, transferred bytes, and communication duration.

Step 3

Reviewed dns.log to determine which domain names were resolved and the IP addresses returned by the DNS server.

Step 4

Reviewed http.log to examine HTTP requests, requested resources, server responses, status codes, and User-Agent strings.

Step 5

Reviewed ssl.log to inspect encrypted TLS sessions, TLS versions, cipher suites, and Server Name Indication (SNI) values.

Step 6

Reviewed quic.log to identify HTTP/3 traffic and QUIC connections.

Findings
Multiple successful DNS resolutions were observed.
Standard HTTP GET requests were identified.
HTTPS sessions used TLS 1.3 encryption.
HTTP/3 traffic was present through QUIC.
Network communications appeared consistent with legitimate web browsing behavior.
Conclusion

The captured traffic represents normal web browsing activity. No evidence of malicious communications, suspicious domains, or abnormal network behavior was identified during this investigation.

This lab demonstrates how Zeek converts raw packet captures into structured logs that significantly simplify network investigations and forensic analysis.
