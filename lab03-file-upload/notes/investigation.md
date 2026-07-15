Lab 03 – File Upload Investigation
Objective

Analyze a Zeek-generated network capture to identify and investigate a file upload event performed against the OWASP Juice Shop application.

Investigation Summary

The capture contains a successful HTTP POST request to the /file-upload endpoint of the local Juice Shop instance (172.17.0.2:3000).

The uploaded file was named shell.php.pdf. Although the filename suggests a PDF document, Zeek identified the transferred file as text/x-php, indicating that the uploaded content was PHP code rather than a PDF file.

This demonstrates how attackers may disguise executable files using misleading filenames.

Evidence
Connection
Client: 192.168.43.178
Server: 172.17.0.2
Protocol: HTTP
TCP State: SF (Successful connection)
HTTP Activity

Request Method:

POST

URI:

/file-upload

HTTP Status:

204 No Content

The HTTP response indicates that the upload completed successfully.

Uploaded File

Filename:

shell.php.pdf

Detected MIME Type:

text/x-php

Seen Bytes:

134

Zeek analyzed the transferred data and identified the content as PHP instead of relying solely on the filename extension.

Findings
A successful file upload occurred.
The uploaded file was named shell.php.pdf.
Zeek identified the file as PHP (text/x-php).
The upload completed successfully with HTTP status 204 No Content.
The file transfer was confirmed in both http.log and files.log.

Conclusion

This investigation demonstrates how Zeek can correlate HTTP requests with transferred files to detect potentially suspicious uploads.
 Although the uploaded filename ended with .pdf, Zeek determined that the file contents matched a PHP script, illustrating why content inspection is more reliable than trusting file extensions alone.
