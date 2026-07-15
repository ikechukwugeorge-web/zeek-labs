Lab 04 – Zeek SQL Injection Investigation
Objective

Investigate HTTP traffic generated during a simulated SQL injection login attempt against OWASP Juice Shop using Zeek logs.

Environment
Platform: Kali Linux
Target: OWASP Juice Shop (Docker)
Zeek Version: Latest Docker image
Capture File: lab04-sqli.pcapng
Investigation Summary

The network capture contained HTTP traffic between the client and the Juice Shop application.

A POST request was observed targeting the application's login endpoint:

POST /rest/user/login

The request originated from:

Client IP: 192.168.43.178
Server IP: 172.17.0.2
Port: 3000

The HTTP request body contained 44 bytes of JSON data, while the server returned a 799-byte JSON response with HTTP status code 200 OK.

Although the capture was generated during a SQL injection exercise, the default Zeek HTTP logs record request metadata rather than the full HTTP request body. Therefore, the exact SQL injection payload cannot be recovered from the Zeek logs alone.

Evidence
HTTP Request
Method: POST
URI: /rest/user/login
Request Size: 44 bytes
Response Size: 799 bytes
Status: 200 OK

Files Analysis

files.log confirmed:

MIME Type: text/json
Request Size: 44 bytes
Response Size: 799 bytes


Findings

- Zeek identified an HTTP POST request to `/rest/user/login`.
- The request returned `HTTP 200 OK`.
- `files.log` recorded the JSON request and response bodies.
- The SQL injection payload itself was not visible in Zeek's logs because Zeek summarizes application-layer activity rather than displaying complete request bodies.
- The full SQL injection payload was verified separately in Wireshark during packet analysis.

Conclusion

Zeek provides excellent visibility into web application activity by recording request methods, URIs, response codes, MIME types, and transferred data sizes.
 However, deeper inspection of SQL injection payloads requires examination of the original packet capture using tools such as Wireshark or additional Zeek scripting.

