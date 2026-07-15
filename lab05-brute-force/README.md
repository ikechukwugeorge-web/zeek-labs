# Lab 05 – Zeek Brute Force Investigation

## Objective

Analyze a brute-force login attack using Zeek network logs.

## Files

- conn.log
- dns.log
- files.log
- http.log
- ssl.log
- weird.log
- x509.log

## Evidence Collected

- Repeated HTTP POST requests
- Hydra User-Agent detected
- Multiple connections to login endpoint
- Repeated HTTP 404 responses

## Screenshots

- 01-http-hydra-login-attempts.png
- 02-conn-multiple-http-connections.png

## Skills Practiced

- Zeek HTTP analysis
- Connection log analysis
- Identifying brute-force activity
- Recognizing automated attack patterns
- Network forensic documentation
