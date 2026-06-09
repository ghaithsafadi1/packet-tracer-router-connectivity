# 🔧 Packet Tracer Lab — Configure Initial Router Settings

## 📋 Lab Overview

This lab covers the **initial configuration of a Cisco router (R1)** using Cisco Packet Tracer. It walks through verifying the default state, applying security settings, and saving the configuration to NVRAM and Flash.

---

## 🎯 Objectives

- **Part 1:** Verify the default router configuration
- **Part 2:** Configure and verify initial router settings
- **Part 3:** Save the running configuration file

---

## 🛠️ Skills Practiced

- Navigating Cisco IOS modes (User EXEC → Privileged EXEC → Global Config)
- Setting a router hostname
- Securing privileged EXEC mode with `enable secret`
- Securing console access with a password and `login`
- Configuring a legal **MOTD banner**
- Encrypting plaintext passwords with `service password-encryption`
- Saving configuration to **NVRAM** and **Flash**
- Using `show running-config` and `show startup-config`

---

## ⚙️ Configuration Applied

```
Router> enable
Router# configure terminal

Router(config)# hostname R1
R1(config)# banner motd #Unauthorized access is strictly prohibited.#
R1(config)# enable secret itsasecret
R1(config)# line console 0
R1(config-line)# password letmein
R1(config-line)# login
R1(config-line)# exit
R1(config)# service password-encryption
R1(config)# end

R1# copy running-config startup-config
```

---

## 🔑 Key Commands Reference

| Command | Purpose |
|---|---|
| `enable` | Enter privileged EXEC mode |
| `configure terminal` | Enter global configuration mode |
| `hostname R1` | Set the device hostname |
| `enable secret itsasecret` | Set encrypted privileged EXEC password |
| `line console 0` | Enter console line configuration |
| `password letmein` | Set console password |
| `login` | Require password on console login |
| `service password-encryption` | Encrypt all plaintext passwords |
| `banner motd #message#` | Set message-of-the-day banner |
| `show running-config` | Display active configuration in RAM |
| `show startup-config` | Display saved configuration in NVRAM |
| `copy running-config startup-config` | Save config to NVRAM |
| `copy startup-config flash` | Backup config to Flash memory |
| `show flash` | Display contents of Flash storage |

---

## 💡 Key Concepts

- **`startup-config is not present`** — This message appears on a fresh router because no configuration has been saved to NVRAM yet.
- **Why MOTD banners matter** — They provide a legal warning to unauthorized users and are required in many enterprise and government environments.
- **`service password-encryption`** — Encrypts all currently unencrypted passwords in the config file. Any passwords configured afterward are also encrypted.
- **Flash backup** — Saving startup-config to Flash provides an extra recovery option if NVRAM becomes corrupt.

---

## 📁 Lab Files

| File | Description |
|---|---|
| `lab.pkt` | Cisco Packet Tracer file |

---

