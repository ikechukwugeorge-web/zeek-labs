Lab 04 – Zeek SQL Injection Investigation

This lab demonstrates how Zeek can be used to investigate HTTP login activity generated during a simulated SQL injection exercise against OWASP Juice Shop.

Skills Demonstrated
HTTP traffic analysis
Zeek log interpretation
Login request investigation
Correlation between http.log and files.log
Understanding Zeek metadata limitations
Logs Analyzed
conn.log
http.log
files.log
Screenshots
HTTP login request
JSON request and response identified in files.log
Key Finding

Zeek successfully identified the login request and recorded metadata such as request method, URI, response code, MIME type, and transferred byte counts. The actual SQL injection payload was not present in the default logs because Zeek records metadata rather than HTTP request bodies.
