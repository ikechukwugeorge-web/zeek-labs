Lab 03 – File Upload Investigation
Overview

This lab investigates a file upload performed against an OWASP Juice Shop application using Zeek network logs.

The objective was to identify the upload request, correlate it with Zeek's file analysis, and determine the true type of the uploaded file.

Skills Demonstrated
Network traffic analysis
HTTP log investigation
File transfer analysis
MIME type identification
Event correlation across Zeek logs
Digital forensics documentation
Evidence Sources
http.log
files.log
conn.log
Key Findings
Successful HTTP POST request to /file-upload
Uploaded file: shell.php.pdf
Zeek detected MIME type: text/x-php
HTTP response: 204 No Content
Successful TCP connection (SF)
Screenshots
HTTP file upload request
Files log correlation
Lessons Learned

This investigation demonstrated that file extensions cannot always be trusted. Zeek inspected the transferred content and correctly identified the uploaded file as PHP, despite the filename ending in .pdf. Correlating evidence between http.log and files.log provided strong confirmation of the upload event.
