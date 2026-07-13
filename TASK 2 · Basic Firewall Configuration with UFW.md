 # Basic Firewall Configuration with UFW

## CyberSecurity Project

RESEARCH REPORT
Basic Firewall Configuration with UFW
(Submitted as part of the Summer Internship Program)


Submitted by
Name :-ABHAY SHARMA

Organization :- OASIS INFOBYTE

Date :-July 2026  
## 1. Objective

The objective of this project is to demonstrate how the Uncomplicated Firewall (UFW) is configured on Kali Linux to secure a system. The exercise covers enabling the firewall, allowing and denying traffic for specific services, and verifying the active rule set — the core workflow behind 'Simple. Effective. Secure' host-based firewall management.

## 2. Environment / Tools Used

| Parameter | Details |
|-----------|---------|
| **Operating System** | Kali Linux (VirtualBox VM) |
| **Tool Used** | UFW – Uncomplicated Firewall (v0.36.2) |
| **Interface** | Terminal (Zsh Shell) |
| **Intern / Presenter** | Abhay Sharma – Cyber Security Intern |
| **Focus Area** | Enabling the firewall and configuring allow/deny rules |

## 3. Step-by-Step Procedure

## Step 1: Check UFW Version and Enable the Firewall

The terminal is opened inside the Kali Linux VM. The installed UFW version is checked, and the firewall is then enabled with sudo privileges:

$ ufw --version

$ sudo ufw enable

After entering the sudo password, the system confirms the firewall is active and will start automatically on boot.
<img width="781" height="520" alt="image" src="https://github.com/user-attachments/assets/1acc2bee-b362-42a0-b95f-9d8b1f079d1f" />

Figure 1: Checking the UFW version and enabling the firewall

## Step 2: Allow SSH Traffic

An allow rule is added for SSH (port 22) so remote administration traffic is permitted through the firewall:

$ sudo ufw allow ssh

Since a matching rule already existed from a prior run, UFW reports that it is skipping the duplicate addition (for both IPv4 and IPv6).

<img width="781" height="520" alt="image" src="https://github.com/user-attachments/assets/1b66e03b-eea0-4ea1-80f9-c0ae89c85014" />

Figure 2: Allowing SSH traffic through the firewall

## Step 3: Deny HTTP Traffic

A deny rule is added to block unencrypted HTTP traffic (port 80), forcing web access to use secure channels only:

$ sudo ufw deny http
<img width="781" height="520" alt="image" src="https://github.com/user-attachments/assets/3ff3e9c0-7031-49a2-9b86-b860d9e2d3eb" />

 Figure 3: Denying HTTP traffic through the firewall

## Step 4: Verify the Firewall Status

Finally, a verbose status check confirms the active configuration — logging level, default policies, and the individual allow/deny rules for both IPv4 and IPv6:

$ sudo ufw status verbose
<img width="781" height="520" alt="image" src="https://github.com/user-attachments/assets/b8fae339-c65f-4d3c-a3b6-957db7001d43" />

 Figure 4: Verifying firewall status, default policy, and rule set

## 4. Observations

•	UFW was successfully enabled and set to persist across system restarts.

•	SSH (port 22) was explicitly allowed, ensuring remote access is not blocked.

•	HTTP (port 80) was explicitly denied, reducing exposure from an unencrypted service.

•	The default policy was confirmed as deny (incoming) / allow (outgoing), a standard secure baseline.

•	The verbose status output confirmed rules applied consistently for both IPv4 and IPv6.

## 5. Conclusion

This exercise demonstrated a complete, practical UFW workflow on Kali Linux: verifying the tool, enabling the firewall, adding targeted allow/deny rules, and confirming the final rule set with a verbose status check. This forms a foundational host-hardening step and can be extended with rate-limiting, application profiles, or logging-level adjustments for management.
