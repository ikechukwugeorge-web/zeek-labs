# Lab 02 – Web Application Traffic Investigation

## Objective

Analyze Zeek logs generated from browsing the OWASP Juice Shop web application and identify normal web application activity, HTTP requests, DNS lookups, encrypted HTTPS sessions, and supporting network evidence.

---

## Environment

- Analyst Machine: Kali Linux
- Target Application: OWASP Juice Shop
- Zeek Version: Latest Docker Image
- Capture File: lab02-web-application.pcapng

---

## Investigation Summary

The packet capture contains normal user interaction with the OWASP Juice Shop application. Zeek successfully extracted HTTP, DNS, SSL/TLS, QUIC, and file metadata logs.

No indicators of compromise or malicious traffic were identified.

---

# HTTP Analysis

The browser connected to the Juice Shop web server over HTTP on port 3000.

Observed requests included:

- GET /
- GET /main.js
- GET /styles.css
- GET /chunk-*.js
- GET /rest/admin/application-configuration
- GET /rest/admin/application-version
- GET /rest/products/search?q=
- GET /rest/languages
- GET /assets/i18n/en.json

These requests show the browser loading the web application, downloading JavaScript bundles, stylesheets, images, fonts, and communicating with backend REST API endpoints.

---

# DNS Analysis

DNS queries resolved several legitimate domains, including:

- fonts.googleapis.com
- fonts.gstatic.com
- owasp.org
- ads.mozilla.org
- push.services.mozilla.com
- api.dynu.com

These lookups support normal browser activity and external resource loading.

---

# SSL/TLS Analysis

Encrypted HTTPS sessions were established with multiple external services.

Observed TLS versions:

- TLS 1.3
- TLS 1.2

Example destinations:

- fonts.googleapis.com
- fonts.gstatic.com
- owasp.org
- Mozilla services

Modern cipher suites were negotiated, indicating secure encrypted communications.

---

# QUIC Analysis

A QUIC (HTTP/3) connection was observed to:

- fonts.gstatic.com

The browser used HTTP/3 over UDP port 443 to retrieve Google Fonts resources.

This activity correlates with the DNS and SSL logs.

---

# File Analysis

Zeek extracted metadata for multiple transferred files.

Observed content types included:

- text/html
- text/plain
- text/json
- image/png

These correspond to normal web application resources such as HTML pages, JavaScript files, JSON API responses, and images.

---

# Conclusion

The analyzed traffic represents legitimate interaction with the OWASP Juice Shop web application.

Evidence across HTTP, DNS, SSL, QUIC, and Files logs correlates consistently and demonstrates how Zeek reconstructs network activity from packet captures.

No malicious indicators were observed during this investigation.
