# 📡 Yealink Auto-Provisioning with Zoom

## 📖 Overview

This document describes the end-to-end provisioning workflow of a Yealink device integrating with Zoom services.
It includes network initialization, security validation, cloud provisioning, and SIP registration.

---
## 🔄 Yealink Automatic Phone Provisioning Diagram with Zoom

<p align="center">
  <img src=Gemini_Generated_Image_r14b1tr14b1tr14b (2).png
       alt="Descripción de la imagen" 
       style="width: 1000px; 
              filter: contrast(150%); 
              display: block; 
              margin: 0 auto;">
</p>

```mermaid id="finalpro1"
sequenceDiagram
    autonumber
    participant T as Yealink Phone
    participant D as DHCP Server
    participant DNS as DNS Server
    participant F as Firewall
    participant R as Yealink RPS
    participant Z as Zoom Provisioning
    participant P as Zoom SIP Proxy

    %% DHCP
    T->>D: DHCP Discover
    D-->>T: DHCP Offer (IP Assigned)

    %% Firewall validation (once)
    T->>F: Initial Internet Access Request
    F-->>T: ✔ Traffic Allowed (HTTPS / DNS / SIP)

    %% DNS RPS
    T->>DNS: Query: rps.yealink.com?
    DNS-->>T: Response: 52.71.103.102

    %% RPS
    T->>R: HTTPS Request (Provisioning)
    R-->>T: Authentication Required

    T->>R: Send MAC / SN
    R-->>T: ✔ Valid → Redirect to Zoom

    %% DNS Zoom
    T->>DNS: Query: zoom.us?
    DNS-->>T: Response: 170.114.65.206

    %% Zoom Provisioning
    T->>Z: HTTPS Provisioning Request
    Z-->>T: ✔ Configuration Download

    %% DNS SIP
    T->>DNS: Query: us01sip0c.sp.zoom.us?
    DNS-->>T: Response: 64.211.144.246

    %% SIP Register
    T->>P: SIP REGISTER
    P-->>T: ✔ 200 OK (Registration Successful)
```


---

## Process Breakdown 

* **DHCP Server**
  Provides IP addressing and network parameters (IP, gateway, DNS) once the device connects to the customer network.

* **DNS Server**
  Resolves domain names to IP addresses (e.g., rps.yealink.com, zoom.us, SIP proxy), enabling communication with external services.

* **Firewall**
  Enforces security policies and allows required outbound traffic (HTTPS, DNS, SIP) after initial validation.

* **Yealink RPS**
  Authenticates the device using MAC/Serial Number and redirects it to the appropriate provisioning platform.

* **Zoom Provisioning Server**
  Delivers device configuration via HTTPS, including account settings and service param

* **Zoom SIP Proxy**
  Handles SIP registration, proxy and call signaling, confirming successful device registration (200 OK).

---


## 🌐 Network Requirements

| Service | Protocol | Port        |
| ------- | -------- | ----------- |
| DHCP    | UDP      | 67/68       |
| DNS     | UDP/TCP  | 53          |
| HTTPS   | TCP      | 443         |
| SIP     | UDP/TCP  | 5060 / 5061 |

---

## 🔐 Notes

* Ensure firewall policies allow outbound HTTPS, DNS, and SIP
* Verify DNS resolution for Yealink and Zoom services
* RPS access is required for zero-touch provisioning
* Arrival at ntp or sntp servers is required for date and time updates
---

