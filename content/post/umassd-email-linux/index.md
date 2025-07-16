---
title: "How to Set Up Your UMassD Email on Linux with Evolution & Exchange Online"
date: 2025-07-16T09:00:00-04:00
draft: false
categories:
  - Tutorials
  - Linux
tags:
  - Hugo
  - Evolution
  - Office365
  - UMassD
  - HPC
  - Email
---

As an Linux user at UMass Dartmouth, you might find yourself frustrated by keep opening a browser tab to monitor your emails. If you are in the neef of seamless access to your UMassD Office 365 email. This guide walks you through installing and configuring GNOME Evolution with the Evolution‑EWS plugin so you can send and receive mail with your `@umassd.edu` account.

---

## Prerequisites

- A valid UMassD Microsoft 365 email account.  
- A Linux distribution with:
  - **Evolution** version 3.27.91 or later (3.44.4+ recommended)  
  - The **evolution‑ews** plugin  
- Internet connectivity.

---

## Installing Evolution & Evolution‑EWS

Depending on your distro, run one of the following:

**Debian / Ubuntu**
```bash
sudo apt update
sudo apt install evolution evolution-ews
```

---

## Setting Up Your UMassD Email Account

1. Open Evolution.
2. Select **File > New > Mail Account**, then click **Next**.
3. Enter your name and UMassD email address, uncheck **Look up mail server details...**, then click **Next**.
4. Change **Server Type** to **Exchange Web Services**.
5. Enter your UMassD email address as your username.
6. Enter `https://outlook.office365.com/EWS/Exchange.asmx` as the **Host URL**.
7. Change the **Authentication type** to **OAuth2 (Office365)**.
9. Click the **Fetch URL** button, which will ask for your password and, if successful, fill the **OAB URL** field.
10. Complete the rest of the steps in the account setup wizard as you see fit.

You should have the UMassD email account setup now.


