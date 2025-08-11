 Here’s a **README.md** file for your **firewall configuration task**:

---

````markdown
# Firewall Configuration and Testing Guide

## Overview
This guide demonstrates how to view, configure, test, and restore firewall rules using either **Windows Firewall** or **UFW** (on Linux). It includes blocking an insecure service (Telnet), allowing SSH, and understanding how firewall traffic filtering works.

---

## Steps

### 1. Open Firewall Configuration Tool

**Windows (GUI)**
1. Press `Win + R`, type `wf.msc`, and press Enter.
2. This opens the Windows Defender Firewall with Advanced Security.

**Linux (UFW - Uncomplicated Firewall)**
```bash
sudo ufw status
````

If UFW is not installed:

```bash
sudo apt install ufw -y
```

---

### 2. List Current Firewall Rules

**Windows (PowerShell)**

```powershell
netsh advfirewall firewall show rule name=all
```

**Linux (UFW)**

```bash
sudo ufw status verbose
```

---

### 3. Add a Rule to Block Inbound Traffic on a Specific Port (Example: Telnet on port 23)

**Windows (PowerShell)**

```powershell
netsh advfirewall firewall add rule name="Block Telnet" dir=in action=block protocol=TCP localport=23
```

**Linux (UFW)**

```bash
sudo ufw deny 23/tcp
```

---

### 4. Test the Rule

* Attempt to connect to port 23 locally or from another machine using:

```bash
telnet <IP> 23
```

* The connection should be refused or timed out.

---

### 5. Add Rule to Allow SSH (Port 22) on Linux

```bash
sudo ufw allow 22/tcp
```

Verify:

```bash
sudo ufw status
```

---

### 6. Remove the Test Block Rule

**Windows**

```powershell
netsh advfirewall firewall delete rule name="Block Telnet"
```

**Linux**

```bash
sudo ufw delete deny 23/tcp
```

---

### 7. Document Commands or GUI Steps Used

Example Documentation:

* Used UFW on Kali Linux.
* Commands executed:

```bash
sudo ufw deny 23/tcp
sudo ufw allow 22/tcp
sudo ufw delete deny 23/tcp
```

* Verified rules using:

```bash
sudo ufw status verbose
```

---

### 8. Summary: How Firewalls Filter Traffic

A firewall acts as a **network security barrier** that filters inbound and outbound traffic based on predefined rules.

* **Allow rules** permit specified traffic (e.g., SSH on port 22).
* **Deny/block rules** prevent unwanted or insecure traffic (e.g., Telnet on port 23).
* Filtering can be based on:

  * **Port number**
  * **Protocol** (TCP/UDP)
  * **IP address**
  * **Traffic direction** (inbound/outbound)
* This helps protect systems from unauthorized access and network-based attacks.

---

```

---

If you want, I can merge this **firewall README** with the **vulnerability scanning README** so you have one complete cybersecurity lab manual. That would make it easier to submit as a single document.
```
