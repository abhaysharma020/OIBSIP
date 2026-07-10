# OBISIP 

## CyberSecurity Project

RESEARCH REPORT
Basic network scanning with Nmap 
(Submitted as part of the Summer Internship Program)


Submitted by
Name :-ABHAY SHARMA

Organization :- OASIS INFOBYTE

Date :-July 2026 

## Basic Network Scanning with Nmap 


#  1. Objective

The objective of this project is to demonstrate how the Nmap (Network Mapper) tool is used on Kali Linux to discover live hosts and services on a local network. The exercise covers starting network services, verifying the scanning tool, and performing a service-version scan across a subnet, with the results saved to a file for later analysis.

# 2. Environment / Tools Used

| Parameter | Details |
|-----------|---------|
| **Operating System** | Kali Linux |
| **Tool Used** | Nmap (Network Mapper) v7.95 |
| **Interface** | Terminal (Zsh Shell) |
| **Target Network** | 10.0.2.0/24 (Local Subnet) |
| **Services Involved** | Apache2 (Web Server), SSH |

# 3. Step-by-Step Procedure
## Step 1: Open the Terminal

The Kali Linux desktop is loaded and a terminal window is opened, ready to accept commands. This is the starting point of the exercise.

<img width="781" height="520" alt="image" src="https://github.com/user-attachments/assets/eef0f3a2-8cb7-4ae1-bb0d-53a4ced365d1" />

 
 Figure 1: Kali Linux desktop with terminal window open

## Step 2: Verify Nmap Installation and Start Required Services

The command below confirms that Nmap is installed and displays its version and build details:

$ nmap --version

Next, the Apache2 web server and SSH services are started in the background so that the scan has live services to detect on the machine:

$ sudo service apache2 start && sudo service ssh start

<img width="781" height="520" alt="image" src="https://github.com/user-attachments/assets/560f54b0-4efb-48b9-a074-d39aa59098f3" />

Figure 2: Verifying Nmap version and starting Apache2 / SSH services

## Step 3: Authenticate with sudo

Since starting system services requires elevated privileges, the terminal prompts for the sudo password before the services are started. The scan command is then typed out:

[sudo] password for kali: ********

$ nmap -Pn -sV ...

<img width="781" height="520" alt="image" src="https://github.com/user-attachments/assets/e6ef0638-fcb1-4858-8c51-51647bd3330e" />

 Figure 3: sudo authentication and beginning of the Nmap command

## Step 4: Build the Nmap Scan Command
 
The full Nmap command is composed, targeting the entire local subnet (10.0.2.0/24). The flags used are:

•	-Pn — skip host discovery (ping) and treat all hosts as online

•	-sV — probe open ports to determine service/version information

•	10.0.2.0/24 — scan the full local /24 subnet

$ nmap -Pn -sV 10.0.2.0/24

<img width="781" height="520" alt="image" src="https://github.com/user-attachments/assets/3bb834e8-fc3c-44d4-9900-2ca73394b1bb" />

 Figure 4: Full Nmap scan command targeting the local subnet

## Step 5: Save Output and Run the Scan

An output flag is added so the results are written to a text file, and the scan is executed:

$ nmap -Pn -sV 10.0.2.0/24 -oN nmap_scan_results.txt

The scan begins, and Nmap prints its startup banner with the scan start time. Results will be written both to the terminal and to nmap_scan_results.txt for later review.

<img width="781" height="520" alt="image" src="https://github.com/user-attachments/assets/a4f876d0-6a18-49f3-b35e-ed969c034e1d" />

Figure 5: Nmap scan running, with output being logged to nmap_scan_results.txt

# 4. Observations

•	Nmap successfully identified as version 7.95 with support for common scanning engines (epoll, poll, select).

•	Required services (Apache2, SSH) were started successfully prior to scanning, ensuring detectable open ports.

•	The -sV flag enables service/version detection rather than a simple port-open/closed check.

•	Saving output with -oN creates a persistent, shareable record of the scan for documentation or later comparison.

# 5. Conclusion

This exercise demonstrated a basic but practical Nmap workflow on Kali Linux: confirming tool availability, preparing target services, constructing a service-detection scan across a subnet, and persisting the results to a file. This forms a foundational step in network reconnaissance and can be extended with additional flags (e.g., -A, -p-, -T4) for more detailed audits.
