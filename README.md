# Server Setup: Comprehensive Guide

This document outlines the steps and best practices for setting up a secure and modular server. Follow this guide to reproduce the initial server setup with Dockerized services.

## 1. Firewall and Network Security
- **UFW (Uncomplicated Firewall):**
   - Configured to allow only necessary traffic (e.g., SSH, API ports).
- **Rate Limiting for SSH via Fail2Ban:**
   - Protects against brute-force attacks.
- **SSH Hardening:**
   - Disabled root login (`PermitRootLogin no`).
   - Enforced SSH key-based authentication.
- **Automatic Kernel Updates:**
   - Ensures the latest security patches are applied without manual intervention.

## 2. Intrusion Detection and File Integrity
- **Fail2Ban:**
   - Actively monitors and bans IPs showing malicious behavior (e.g., multiple failed SSH login attempts).
- **AIDE (Advanced Intrusion Detection Environment):**
   - Detects unauthorized changes to critical system files.

## 3. Kernel Hardening
- **Sysctl Configurations:**
   - Applied to mitigate common kernel-level attacks:
      - Disabled IP forwarding.
      - Enabled SYN cookie protection.
      - Restricted core dumps.
      - Hardened network parameters to prevent spoofing and packet injection attacks.
- **AppArmor or SELinux:**
   - Enforcing mandatory access control (likely AppArmor on Ubuntu).

## 4. Docker Security
- **Rootless Docker:**
   - Ensured Docker runs without root privileges, isolating it from the host system.
- **Seccomp Profile:**
   - Enforced default seccomp profiles for Docker containers to limit syscalls.
- **Image Scanning:**
   - Using only verified and secure container images.

## 5. Software and Updates
- **Automatic Security Updates:**
   - Ensured all critical security patches are applied automatically via `unattended-upgrades`.
- **Minimal Installed Packages:**
   - Limited installed software to only necessary applications, reducing the attack surface.

## 6. Access Controls
- **User Account Management:**
   - Restricted unnecessary users and groups.
   - Enforced strong password policies.
- **Privilege Escalation:**
   - Configured `sudo` access carefully to avoid over-permissioning.

## 7. API Rate Limiting (Planned or Implemented)
- Conceptually planned rate limiting to mitigate abuse of exposed APIs, possibly at the application or reverse proxy level.

## 8. Monitoring and Logging
- **Centralized or Local Logging:**
   - Logging of key system events (e.g., SSH logins, firewall actions).
- **Regular Log Review:**
   - Monitoring logs for unusual activity, possibly automated.

## 9. Backup and Disaster Recovery
- While not explicitly mentioned, regular automated backups (if set up) are critical for recovery in case of compromise.

---

This document provides a solid foundation for setting up a secure and flexible server. Additional sections can be added as new services or modules are introduced.

