# **Dork Like a Demon: FOFA Edition for Hackers & Bug Bounty Hunters** 💀🔥

## A hacker’s guide to FOFA dorking, packed with powerful queries and tips for bug bounty, red teaming and proactive defense - dork smart, find fast, report big.

---

## ⚠️ Disclaimer

This article is intended for **educational and ethical hacking purposes only**. Perform these dorks **only on systems you’re authorized to test** — such as in bug bounty programs or internal security reviews. Unauthorized access? That’s how you summon legal demons, and trust me, they don’t sleep.

---

## 🧭 Backstory – From Shodan to FOFA

Earlier, I published **"Dork Like a Demon: Shodan Edition for Hackers and Bug Bounty Hunters 💀"** on [OSINT Team](https://osintteam.blog/dork-like-a-demon-shodan-edition-for-hackers-and-bug-bounty-hunters-e067383c86c9).

That piece gave hunters the keys to **Shodan recon mastery**. But Shodan isn’t the only player.

Enter **FOFA** — the sharper, broader sibling that offers:

* **Deeper filters & syntax** — chain conditions like a true recon demon.
* **Wider coverage**, especially in regions where Shodan snoozes.
* **Fingerprint-rich results** — favicon hashes, cert subjects, JS content, and more.

While **Shodan focuses on devices** and **Censys thrives on certificates**, **FOFA bridges both worlds**, often catching assets others miss.

![a-cyberpunk-themed-digital-artwork-featu_H6cLqkTjRXqwbY-oBl2Llg_uzD4Gl7DSkasvKgCwbToaw](https://github.com/user-attachments/assets/8b29026d-6b72-4694-903c-3e285243133d) <br/>

---

Gotcha, Bub — added crisp **1-line descriptions** after each dork, with a dash of 🗿.

---

## 🥂 Tier 1 – Beginner FOFA Dorks

### Login Pages

```fofa
title="Login" && body="admin"
```

→ Finds classic login portals mentioning “admin” — quick entry-point recon 🗿.

### Admin Panels

```fofa
title="wp-admin" || path="/admin"
```

→ Surfaces WordPress/admin dashboards that often hide weak auth or defaults.

### Favicon Fingerprinting

```fofa
domain="target.com" && icon_hash="1234567890"
```

→ Maps sibling assets sharing the same favicon hash (tech/brand fingerprint).

---

## ⚡ Tier 2 – Intermediate FOFA Dorks

### JavaScript Secrets

```fofa
extension="js" && body="api_key"
```

→ Hunts JS files leaking tokens/keys straight in the source 🗿.

### Misconfigured Cloud Buckets

```fofa
body="NoSuchBucket" || body="AccessDenied"
```

→ Flags S3-style error pages that betray bucket names and misconfig clues.

### Exposed Databases

```fofa
port="9200" && protocol="http"     # Elasticsearch
port="27017" && protocol="mongodb" # MongoDB
```

→ Finds internet-facing ES/Mongo instances — high-impact if unauthenticated.

---

## 🔥 Tier 3 – Advanced FOFA Dorks (Demon Mode)

### Public API Docs with Secrets

```fofa
title="API Documentation" && body="api_key"
```

→ Locates public API docs that sometimes ship with hardcoded creds 🗿.

### Routers with Default Credentials

```fofa
title="Router Login" && body="default_password"
```

→ Targets router logins hinting at factory/default creds — report fast.

### MySQL Databases

```fofa
port="3306" && protocol="mysql"
```

→ Enumerates internet-exposed MySQL services; banner often reveals version.

### Active Cobalt Strike C2 Servers

```fofa
server="CobaltStrike"
```

→ Fingerprints potential C2 infra; use for threat intel/deconfliction only.

### SSL Certificate Fingerprinting

```fofa
cert.subject="Oracle Corporation"
```

→ Expands org-wide asset scope via cert subject matches — great for discovery 🗿.

---

## 🫣 Sneak Peek – What FOFA Shows You

Here’s a **real-world anonymized snapshot** I pulled during recon:

![Sss](https://github.com/user-attachments/assets/ef5939bf-57e8-4b0e-8ff3-81c64dd3cfcc) <br/>

> **Domain:** *\[Redacted]* <br/>
> **Location:** Pune, India <br/>
> **Ports:** 80, 443, **22**, 3000, 10001 <br/>
> **Stack:** NGINX, Node.js, OpenSSH <br/>
> **Last Update:** 2025-08-21 <br/>

And yes… **Port 22 (SSH) wide open** 🗿👍 <br/>
Guess who has to **harden this baby now?** *Ehhhhh🗿🗿* <br/>

This is exactly the kind of **attack surface intelligence FOFA excels at** — quick, deep, and revealing.

---

## 🛡️ Blue Team Spin

* **SSH Exposure Check**

  ```fofa
  port="22" && protocol="ssh"
  ```

  → Monitor for org IPs exposing SSH to the internet; tighten access controls.

* **IoT Exposure**

  ```fofa
  title="IP Camera" && body="password"
  ```

  → Surface camera/DVR panels with default creds; segment, rotate, lock down 🗿.


## ⚙️ Automation = Demon Power

Leverage **FOFA API**, **GoFOFA CLI**, or **Python scripts** for:

* Continuous scanning
* Recon dashboards
* Instant alerts

Because while you sleep — attackers don’t.

---

## 🚀 Final Thoughts

FOFA isn’t just another search engine — it’s **a magnifying glass for the internet’s loose screws**.

From my **Shodan dorking roots** to this **FOFA mastery**, one thing remains:

> The best recon isn’t loud — it’s smart, precise, and just a little bit demonic 🗿🔥.

Stay ethical. Stay ahead. **Dork like a demon.**

---

### **Goodbye Note**

*"Every search string you craft, every query you refine, pulls back the curtain on the hidden layers of the web. FOFA Dorking isn’t just about finding exposed data—it’s about sharpening your eye as an ethical hacker, turning curiosity into actionable intelligence, and leaving no digital stone unturned. Keep your hunts sharp, your ethics sharper, and remember: the real power of a hacker lies not in the chaos they can create, but in the security they can strengthen."* <br/>

~ **Aditya Bhatt** <br/>

---

