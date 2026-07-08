# OIBSIP
## CyberSecurity Project
RESEARCH REPORT
Common Network Security Threats
(Submitted as part of the Summer Internship Program)


Submitted by
Name :-ABHAY SHARMA
Organization :- OASIS INFOBYTE
Date :-July 2026


Introduction

Modern organizations depend on interconnected networks to run nearly every aspect of business, from financial transactions and customer communications to critical infrastructure and cloud services. This same connectivity that enables productivity and innovation also creates a vast attack surface that malicious actors continually probe and exploit. Network security threats such as denial-of-service attacks, man-in-the-middle interception, IP spoofing, and DNS poisoning can disrupt operations, steal sensitive data, damage brand reputation, and cause direct financial losses ranging from thousands to hundreds of millions of dollars. As threat actors increasingly leverage automation, botnets of compromised IoT devices, and weaknesses in foundational internet protocols (TCP/IP, DNS, and BGP), understanding how these attacks work — and how to defend against them — is essential for any network administrator, security engineer, or business leader responsible for protecting digital assets in today's threat landscape.

# 1. Denial-of-Service (DoS) and Distributed Denial-of-Service (DDoS) Attacks
   
**How It Works**

A denial-of-service attack occurs when an attacker floods a target system, service, or network with traffic or requests until it can no longer respond to legitimate users, effectively taking the resource offline. A distributed denial-of-service (DDoS) attack scales this technique across many machines — often a botnet of compromised, internet-connected devices — that simultaneously direct traffic at a single target, dramatically increasing volume and making the source of the attack harder to block.
CISA, the FBI, and the Multi-State Information Sharing and Analysis Center (MS-ISAC) categorize DDoS techniques into three types: volumetric attacks that consume available bandwidth, protocol attacks that exploit weaknesses in network protocols (e.g., SYN floods), and application-layer attacks that target vulnerabilities in specific running services (e.g., HTTP floods).

**Real-World Example**

On October 21, 2016, the Mirai botnet — built from compromised IoT devices such as routers, IP cameras, and DVRs still using default factory credentials — was used to launch a massive DDoS attack against Dyn, a managed DNS provider. The attack reached roughly 1 Tbps of traffic and knocked more than 50 major internet platforms offline or intermittently unreachable across the U.S. and Europe, including Twitter, Netflix, Amazon, PayPal, Reddit, Spotify, and GitHub, for several hours. Sony later reported a $2.7 million revenue loss tied directly to the outage of its PlayStation Network during the attack.

**Impact**

●	Extended service outages that block legitimate customers, employees, or partners from reaching a system

●	Direct financial losses from lost transactions, SLA penalties, and incident response costs

●	Reputational damage and erosion of customer trust, particularly for public-facing platforms

●	Secondary risk: DDoS traffic can be used as a smokescreen to distract security teams during a separate intrusion

**Mitigation Strategies**

1. Deploy DDoS protection services and CDNs — Use cloud-based scrubbing services, content delivery networks, and edge providers that can absorb and filter volumetric traffic before it reaches origin servers, as recommended in CISA's joint DDoS guidance.
2. Harden and segment infrastructure ahead of time — Conduct DDoS-specific risk assessments, apply rate limiting and web application firewall (WAF) rules, and maintain excess bandwidth/capacity headroom for critical services.
3. Build and rehearse a DDoS incident response plan — Predefine escalation paths with your ISP/CSP, maintain contact with a DDoS mitigation provider, and rehearse detection-to-recovery steps so response time is minimized during a live attack.

# 2. Man-in-the-Middle (MITM) Attacks
   
**How It Works**

In a man-in-the-middle attack, an adversary secretly positions themselves between two communicating parties — such as a user and a website, or two corporate email accounts — intercepting, and sometimes altering, the traffic while both sides believe they are communicating directly with each other. Common techniques include setting up rogue Wi-Fi access points, ARP or session spoofing on a local network, SSL stripping to downgrade an encrypted HTTPS connection to plaintext HTTP, and installing forged or unauthorized root certificates that let an attacker transparently decrypt supposedly secure traffic.

**Real-World Example**

In 2014–2015, Lenovo shipped consumer laptops preloaded with 'Superfish' adware that installed a self-signed root certificate on every device. That shared root certificate allowed the software — and anyone who extracted its private key — to transparently intercept and re-sign HTTPS traffic for any website a user visited, effectively enabling a man-in-the-middle attack on encrypted banking, email, and shopping sessions without any browser warning. The discovery forced Lenovo, Microsoft, and McAfee to coordinate emergency software updates to remove Superfish and its certificate from affected machines.

**Impact**

●	Theft of login credentials, session cookies, and financial account details

●	Business email compromise (BEC) fraud, including altered invoices and redirected wire transfers

●	Loss of confidentiality for any data assumed to be protected by encryption

●	Erosion of trust in a vendor's software or a network's security when disclosed publicly

**Mitigation Strategies**

1. Enforce end-to-end encryption and HSTS — Require TLS for all sensitive traffic, enable HTTP Strict Transport Security (HSTS) so browsers refuse to downgrade to plaintext HTTP, and disable legacy/weak cipher suites.
2. Use certificate pinning and validate certificate authorities — Pin expected certificates or public keys in applications, and audit any software or device that installs its own root certificate authority.
3. Require secure network access controls — Mandate VPNs with multi-factor authentication for remote access, avoid transacting sensitive data over untrusted public Wi-Fi, and use network monitoring (IDS/SIEM) to flag anomalous ARP or routing behavior.

   
# 3. IP Spoofing

**How It Works**

IP spoofing is the practice of forging the source IP address field in packets so that traffic appears to originate from a trusted or different host than it actually does. Attackers use it to impersonate a trusted machine in order to bypass IP-based authentication, to hide their true location, or — in reflection/amplification DDoS attacks — to direct third-party servers' responses at a victim who never actually requested them.

**Real-World Example**

One of the earliest and most famous IP spoofing incidents occurred on December 25, 1994, when hacker Kevin Mitnick attacked the home computer of security researcher Tsutomu Shimomura. Mitnick forged a trusted host's source IP address and combined it with TCP sequence-number prediction — exploiting the fact that early TCP/IP stacks generated predictable sequence numbers — to complete a blind connection and plant a backdoor without ever seeing the return traffic himself. The intrusion was ultimately traced because a background packet capture recorded the activity that Mitnick's own log-clearing had missed, leading directly to his identification and arrest weeks later.

**Impact**

●	Bypassing of IP-based trust relationships and access controls between systems

●	Enabling of large-scale reflection/amplification DDoS attacks that abuse spoofed source addresses

●	Difficulty attributing an attack to its true origin, complicating investigation and response

●	Potential for unauthorized backdoor access to systems that trust source-IP identity alone

**Mitigation Strategies**

1. Deploy ingress and egress packet filtering (BCP 38 / RFC 2827) — Configure routers and ISUs to drop packets with source addresses that could not legitimately originate from a given network segment, preventing spoofed traffic from entering or leaving.
2. Use unpredictable sequence numbers and modern TCP stacks — Ensure operating systems and network devices use randomized initial sequence numbers and modern TCP/IP hardening to defeat sequence-prediction attacks.
3. Avoid IP-address-only trust models — Replace or supplement IP-based authentication with cryptographic authentication (e.g., mutual TLS, IPsec) so identity is not solely tied to a spoofable network address.

# 4. DNS Poisoning / Spoofing (Bonus Threat)

**How It Works**

DNS poisoning (also called DNS spoofing or cache poisoning) occurs when an attacker injects forged DNS responses into a resolver's cache or otherwise manipulates DNS resolution so that a legitimate domain name resolves to a malicious IP address. This can be achieved directly against a vulnerable DNS resolver, or indirectly by hijacking the underlying routing infrastructure — for example, through a Border Gateway Protocol (BGP) route hijack that redirects traffic destined for a legitimate DNS provider to an attacker-controlled server, which then returns poisoned DNS answers.

**Real-World Example**

On April 24, 2018, attackers executed a BGP route hijack against Amazon's Route 53 DNS service, announcing more specific IP prefixes that rerouted roughly two hours of traffic through a malicious server hosted at a Chicago data center. That server acted as a rogue DNS responder for the cryptocurrency wallet site MyEtherWallet.com, returning the IP address of a phishing site hosted in Russia. Victims who ignored a self-signed certificate warning had their private keys stolen, resulting in roughly $150,000 in Ether being drained from their wallets. Amazon confirmed Route 53 itself was never compromised — the attack instead exploited an upstream ISP's BGP announcements, illustrating how DNS and routing-layer trust can be abused together.

**Impact**

●	Silent redirection of users to phishing or malware-hosting sites while the real domain appears unaffected

●	Theft of credentials, private keys, and financial assets, particularly in cryptocurrency and banking contexts

●	Long attack windows before detection, since DNS/BGP anomalies are not always immediately visible to victims

●	Cache poisoning can affect every user of a shared resolver, multiplying the blast radius of a single attack

**Mitigation Strategies**

1. Implement DNSSEC — Deploy Domain Name System Security Extensions to cryptographically sign DNS records so resolvers can detect and reject forged or tampered responses.
2. Adopt HSTS and validate TLS certificates strictly — Configure HSTS so browsers refuse insecure connections, and train users/systems to treat self-signed or unexpected certificate warnings as a hard stop rather than something to click through.
3. Monitor and secure BGP routing — Use Resource Public Key Infrastructure (RPKI) and route-origin validation, along with BGP monitoring services, to detect and reject illegitimate route announcements before they can redirect DNS traffic.

# Comparison Table: Threats at a Glance

The table below summarizes each threat covered in this report across four dimensions relevant to prioritizing defenses.

## Comparison of Common Network Security Threats

| Threat | Primary Attack Vector | Who Is at Risk | Difficulty to Execute | Ease of Mitigation |
|--------|-----------------------|----------------|-----------------------|--------------------|
| **DoS / DDoS** | Traffic/request flooding of network, transport, or application layers (often via botnets) | Any internet-facing service; especially e-commerce, gaming, financial, and DNS/CDN providers | Low–Medium (booter/stresser services are cheap and require little skill) | Medium (requires scale, provider cooperation, and ongoing investment) |
| **Man-in-the-Middle (MITM)** | Interception of traffic between two parties via rogue Wi-Fi, ARP spoofing, or forged certificates | Users on public/unsecured Wi-Fi, remote workers, financial and email transactions | Medium (needs network position or social engineering) | Medium–High (TLS, HSTS, and certificate pinning are well established) |
| **IP Spoofing** | Forged source IP addresses to impersonate trusted hosts or hide attacker origin | Trust-based network services, reflection/amplification DDoS victims, session-based applications | Medium (protocol knowledge required; harder on modern stacks) | High (ingress/egress filtering and BCP 38 are mature, standard controls) |
| **DNS Poisoning / Spoofing** | Injection of forged DNS responses or route hijacks (e.g., BGP) to redirect DNS resolution | Any organization relying on DNS; especially financial services and cryptocurrency platforms | Medium–High (cache poisoning is difficult on modern resolvers; BGP hijacks require network access) | Medium (DNSSEC, DoH/DoT, and RPKI exist but adoption is still incomplete) |

# Conclusion: Key Takeaways for Network Administrators

1. Defense in depth beats any single control. No single tool stops every threat covered here — DDoS scrubbing, TLS/HSTS, ingress filtering, and DNSSEC each address a different layer of the stack. Administrators should layer protocol-level hardening, network-level filtering, and application-level monitoring rather than relying on one defense.
2. Foundational internet protocols remain a soft target. TCP/IP, DNS, and BGP were designed for connectivity, not security, and each still carries exploitable trust assumptions decades later. Investing in modern protections like DNSSEC, RPKI, and BCP 38 filtering closes gaps that attackers continue to exploit.
3. Preparation and monitoring shorten every incident. In nearly every case study above, the difference between a contained incident and a costly breach was how quickly the anomaly was detected and how well-rehearsed the response plan was. Maintain monitoring (IDS/SIEM), pre-negotiated relationships with ISPs/mitigation providers, and a tested incident response plan before an attack occurs.

# References

* Cybersecurity and Infrastructure Security Agency (CISA). Understanding and Responding to Distributed Denial-of-Service Attacks.
* Cybersecurity and Infrastructure Security Agency (CISA). Understanding Denial-of-Service Attacks.
* MITRE ATT&CK. Network Denial of Service (T1498) and Network Sniffing (T1040).
* National Institute of Standards and Technology (NIST). Special Publication 800-81-2: Secure Domain Name System (DNS) Deployment Guide.
* SANS Institute Reading Room. Papers on Man-in-the-Middle Attacks and IP Spoofing.
* The Register. Audacious BGP seizure of Route 53 IP addresses followed by crypto-cyber-heist (MyEtherWallet DNS hijack, 2018).
* CoverLink Insurance. Cyber Case Study: The Mirai DDoS Attack on Dyn.
* StrongDM. Man-in-the-Middle (MITM) Attack: Definition, Examples & More (Lenovo Superfish incident).
