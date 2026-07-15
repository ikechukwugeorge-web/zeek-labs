# Lab 05 – Zeek Brute Force Investigation

## Objective

Investigate a suspected brute-force login attack using Zeek logs.

---

## Findings

The HTTP log recorded numerous POST requests to the `/rest/user/login` endpoint.

The requests originated from the same client IP and were submitted using the Hydra password-cracking tool, identified by the User-Agent string:

Mozilla/5.0 (Hydra)

Each login attempt received an HTTP 404 Not Found response, indicating that the login attempts were unsuccessful against the requested endpoint.

The repeated POST requests over a very short time period demonstrate the behavior of an automated brute-force attack.

---

## Indicators

Source IP:
192.168.43.178

Destination:
192.168.43.178:80

HTTP Method:
POST

Target:
`/rest/user/login`

User-Agent:
Mozilla/5.0 (Hydra)

Observed Response:
404 Not Found

---

## Conclusion

Zeek successfully identified repeated automated login attempts originating from Hydra. Although the attack did not succeed, the logs clearly reveal brute-force behavior through repetitive POST requests, consistent User-Agent strings, and rapid request frequency.
