# Social Engineering Attacks

## CyberSecurity Project

RESEARCH REPORT
Social Engineering Attacks
(Submitted as part of the Summer Internship Program)


Submitted by
Name :-ABHAY SHARMA

Organization :- OASIS INFOBYTE

Date :-July 2026 

## Introduction

Social engineering is the practice of manipulating people, rather than exploiting software or hardware, into performing actions or divulging confidential information. The U.S. Cybersecurity and Infrastructure Security Agency (CISA) defines it as an attack in which the perpetrator uses human interaction to obtain or compromise information about an organization or its computer systems, often posing as a new employee, repair technician, or researcher to appear credible.

Rather than defeating firewalls or encryption, a social engineer defeats the person sitting behind them. Attackers exploit predictable psychological levers — authority, urgency, fear, curiosity, trust, and reciprocity — to short-circuit an individual's normal caution. Because these levers work on almost anyone regardless of technical sophistication, social engineering has become the dominant initial-access technique in modern cybercrime.
## Why It Is One of the Most Effective Attack Vectors
Independent industry research consistently shows that the human element, not a technical vulnerability, is the leading cause of security breaches:

* 60% of confirmed data breaches analyzed in the Verizon 2025 Data Breach Investigations Report involved a human element — a malicious click, a socially engineered phone call, or a misdelivered file.
  
* 57% of social engineering incidents in the same Verizon dataset were phishing, and 30% were pretexting, with pretexting tied to business email compromise nearly doubling in recent years.

* 16% of breaches in IBM's 2025 Cost of a Data Breach Report began with phishing — the single costliest initial access vector at an average of $4.8 million per breach.
 
* 859,532 complaints and $16.6 billion in losses were reported to the FBI's Internet Crime Complaint Center (IC3) in 2024, a 33% year-over-year increase, including $2.77 billion from business email compromise alone.

* The median time for a user to click a phishing link is about 21 seconds, with sensitive data submitted only 28 seconds later — faster than most automated defenses can react.
  
* These figures point to a consistent conclusion: technology alone cannot close the human gap. Even organizations with mature technical controls remain exposed because social engineering targets judgment, not infrastructure — and a single successfully deceived employee can be enough to compromise an entire network.
  
## Phishing
Phishing is a form of social engineering that uses email, text messages, phone calls, or fraudulent websites to impersonate a trustworthy entity and trick a victim into revealing credentials, financial data, or installing malware. CISA notes that attackers often exploit current events — natural disasters, epidemics, or major news stories — to lend urgency and credibility to their lures.
How It Works

A typical phishing attack follows a repeatable chain:

1.	Reconnaissance — the attacker identifies a target organization and, for more advanced variants, specific individuals within it (via LinkedIn, company websites, or data breaches).

2.	Lure creation — a message is crafted to impersonate a trusted sender (a bank, vendor, executive, or IT department) and to create urgency or fear.

3.	Delivery — the lure is sent via email, SMS, social media, or a phone call, often containing a malicious link, attachment, or request.

4.	Exploitation — the victim clicks a link to a spoofed login page, opens a weaponized attachment, or complies with a fraudulent instruction (e.g., a wire transfer).

5.	Follow-through — stolen credentials or footholds are used for account takeover, lateral movement, or further attacks against colleagues.

## Types of Phishing

•	**Spear Phishing** —
highly targeted messages built around research on a specific individual (their role, colleagues, or ongoing projects), making the lure far more convincing than a generic blast.

•	**Whaling** — spear phishing aimed at senior executives or other high-value targets, often impersonating a CEO or board member to authorize a large financial transaction (a hallmark of business email compromise).

•	**Vishing** (Voice Phishing) — phone-based social engineering, frequently impersonating IT support or a help desk to obtain credentials or trick staff into resetting multi-factor authentication.

•	Smishing (SMS Phishing) — text messages containing malicious links or phone numbers, exploiting the fact that mobile screens make it harder to inspect a URL before tapping it.
  
## Case Study: The 2020 Twitter (X) Account Hijacking

On July 15, 2020, attackers compromised approximately 130 high-profile Twitter accounts (including those of major public figures and companies) to run a Bitcoin scam. Twitter's own investigation found the intrusion began as a phone spear phishing (vishing) attack targeting a small number of employees, in which attackers convincingly impersonated internal IT staff and directed employees to a fake internal VPN login page to harvest their credentials.

Attackers first compromised lower-level employees who lacked access to account-management tools, then used the internal knowledge gained to socially engineer additional employees who did have that access. The New York State Department of Financial Services later confirmed that between January and July 2020, roughly one-third of significant cybersecurity incidents reported to it involved phishing or vishing, underscoring how routine this vector had become even before the Twitter incident.

The case illustrates two enduring lessons: remote and hybrid work increases exposure to phone-based impersonation (employees are less able to verify a caller through in-person cues), and access to internal tools should be tightly scoped so that compromising one account cannot cascade into full administrative control.
## Prevention Recommendations

6.	Deploy phishing-resistant multi-factor authentication (e.g., FIDO2 security keys) rather than SMS or push-based MFA, which can be bypassed through prompt-bombing or real-time relay (adversary-in-the-middle) attacks.

7.	Run continuous, realistic security-awareness training and simulated phishing campaigns; organizations using ongoing simulation-based training have measured phishing susceptibility fall dramatically over 12 months.

8.	Establish out-of-band verification for sensitive requests, such as password resets, wire transfers, or VPN/IT support calls — never authenticate a request using contact information supplied within the suspicious message itself.

9.	Harden email and web gateways with DMARC/DKIM/SPF enforcement, attachment sandboxing, and URL rewriting/inspection to catch look-alike domains before a user ever sees the message.

## Pretexting

Pretexting is a social engineering technique in which an attacker fabricates a plausible scenario, or "pretext," to justify why a target should share information or perform an action they would not normally undertake for a stranger. Where phishing typically relies on a single deceptive message, pretexting is a sustained performance — the attacker adopts a false identity or role and builds a believable narrative around it.

## How an Attacker Builds a False Scenario

10.	Research the target — attackers gather names, job titles, internal jargon, org charts, and recent events (a merger, a new IT rollout, a helpdesk process change) from social media, public filings, or previous social-engineering calls.

11.	Construct a credible identity — the attacker impersonates a role the target is inclined to trust or obey: IT support, a new hire, an auditor, a vendor, or a senior executive.

12.	Introduce urgency or authority — the pretext is framed as time-sensitive ("your account will be locked") or backed by apparent authority ("the CFO needs this today") to discourage the target from pausing to verify.

13.	Request the specific action — a password reset, an MFA code, a wire transfer, or physical access — framed as routine and low-risk given the fabricated context.

14.	Escalate using information already gathered — details obtained from an earlier, lower-privilege victim are used to sound legitimate to the next, higher-privilege target.
## Case Study: Pretext-Driven Help Desk Compromise (Scattered Spider / Twitter 2020)

The Twitter 2020 breach described above is also a textbook pretexting case: attackers did not merely send a phishing link, they impersonated Twitter's internal IT department over the phone and built a false scenario around a plausible VPN problem, since VPN issues were common at the time due to remote work.

A closely related and well-documented modern pattern is used by the threat group tracked as Scattered Spider, which CISA describes as conducting layered social engineering over multiple calls to corporate help desks: first learning the exact steps required to reset a password, then calling back to convince help desk staff to reset a targeted employee's password or transfer their MFA enrollment to an attacker-controlled device.

These cases show that pretexting succeeds by exploiting institutional trust in job roles and internal processes — the victim is not fooled by a fake website, but by a convincingly ordinary-sounding request from someone who appears to belong.

## Prevention Measures

15.	Enforce strict identity-verification protocols for any request involving credential resets, MFA changes, or financial transactions — including callback verification to a number on file, not one provided by the caller.

16.	Train help desk and support staff specifically, since they are disproportionately targeted; require multi-step identity checks (e.g., manager confirmation) before any privileged account action.

17.	Limit the amount of internal process detail exposed publicly (org charts, IT ticketing workflows, employee directories) that an attacker could use to build a convincing pretext.

## Baiting

Baiting lures a victim with the promise of something desirable — a free item, an interesting file, or a good deal — in order to get them to compromise their own security. Unlike phishing, which usually asks for information directly, baiting relies on the victim taking an action (plugging in a device, downloading a file) that they believe benefits them.

## Physical Baiting

The classic form is the USB drop attack: an attacker leaves an infected USB drive in a parking lot, lobby, or cafeteria, often labeled to provoke curiosity ("Payroll 2026") or a sense of obligation (a drive attached to a physical key). A target who finds the device plugs it in — out of curiosity or a wish to identify its owner — and unknowingly executes malware or a keystroke-injection payload.

## Digital Baiting

Digital baiting takes the same psychological approach online: fake software downloads, cracked movie or game files, "free" ebooks, or browser pop-ups offering prizes, all bundled with malware. A newer variant, sometimes called ClickFix, tricks users into pasting attacker-supplied commands into their own terminal under the guise of fixing a CAPTCHA or browser error, achieving the same self-inflicted compromise without any file download at all.
 
## Case Study: USB Baiting Experiments and Real-World Incidents

In a widely cited controlled study, Google security researcher Elie Bursztein and colleagues from the University of Illinois dropped 297 USB drives around the University of Illinois Urbana-Champaign campus. 290 of the drives were picked up, and at least 48% were plugged into a computer — with drives bearing labels designed to invoke curiosity or an appeal to altruism (a drive attached to a physical key) proving the most effective lures.

The technique has also been used operationally: a documented 2008 incident describes an infected USB drive left in the parking lot of a U.S. military facility in the Middle East, which, once plugged into a laptop, spread a worm across both classified and unclassified defense networks and reportedly took roughly 14 months to fully remediate.

Together, these cases demonstrate that baiting works regardless of a target's general security awareness — the Bursztein study found no meaningful difference in susceptibility between security-savvy participants and the general population, suggesting that curiosity and helpfulness are difficult impulses to train away entirely.

## Prevention Measures

18.	Disable AutoRun/AutoPlay and restrict or block unauthorized USB and removable media at the endpoint level using device-control software.

19.	Establish a clear policy instructing employees to hand any found or unexpected device to IT/security rather than plugging it in, and reinforce this through awareness campaigns.

20.	Restrict software installation and downloads to approved sources, and use application allow-listing and web filtering to block known malicious download sites and file types.

## Quid Pro Quo (Bonus)

Quid pro quo ("something for something") is a social engineering variant in which the attacker offers a service or benefit in exchange for information or access. A common example is an attacker cold-calling employees claiming to be from IT support offering to fix a (nonexistent) problem, and asking the employee to disable antivirus software or provide their login credentials so the "fix" can proceed. Another variant offers a free gift, gift card, or prize survey in exchange for personal or corporate information.

Quid pro quo differs from baiting in that the exchange is framed as a two-way transaction initiated by the attacker's offer of help, rather than a passive lure the victim happens to discover.

## Prevention
•	Never provide credentials, disable security software, or grant remote access based on an unsolicited call or offer, regardless of how helpful it appears.

•	Verify any offer of IT support through the organization's official service-desk channel before acting.

•	Educate staff that legitimate IT support will never ask them to disclose a password or one-time passcode.

# Comparison Table

The table below summarizes each attack type's primary target, the psychological lever it exploits, and the most effective countermeasure.

## Comparison of Common Social Engineering Attacks

| Attack Type | Primary Target | Psychological Lever Exploited | Best Countermeasure |
|-------------|----------------|-------------------------------|---------------------|
| **Phishing** | Employees via email, SMS, voice calls (broad or targeted) | Urgency, authority, fear of consequences | Email security gateway, phishing-resistant MFA, and a strong user reporting culture |
| **Pretexting** | Specific individuals (Help Desk, Finance, HR) | Trust, authority, and obligation to help a "colleague" | Enforce strict identity verification procedures for sensitive requests |
| **Baiting** | Anyone who finds or downloads the lure | Curiosity, greed, or desire for free/interesting content | Disable AutoRun, implement endpoint security controls, and enforce USB/device usage policies |
| **Quid Pro Quo** | Employees expecting a service in return | Reciprocity and desire for a "good deal" or free technical assistance | Verify the identity of callers before granting remote access or sharing sensitive information |

## Organizational Recommendations: Employee Security Awareness Checklist

A structured, recurring training program is the most effective organizational defense against social engineering, since technical controls alone cannot prevent a human from being persuaded. The following five-point checklist provides a baseline program:

21.	Conduct recurring, scenario-based training covering phishing, vishing, smishing, pretexting, and baiting — not a single annual slideshow, but short, frequent modules reinforced with simulated phishing and vishing exercises.

22.	Establish a clear, low-friction reporting channel (e.g., a "Report Phishing" email button) and publicly reinforce that reporting a suspicious message or call is always the right call, with no blame for false positives.

23.	Mandate identity-verification procedures for any sensitive request — password resets, MFA changes, wire transfers, or physical access — especially for help desk and finance staff, who are frequently targeted.

24.	Enforce technical baseline controls that reduce the impact of a successful deception: phishing-resistant MFA, least-privilege access, USB/device restrictions, and email authentication (DMARC/DKIM/SPF).

25.	Measure and iterate: track phishing simulation click-rates and reporting-rates over time, and use the results to target additional training at the highest-risk teams (e.g., help desk, HR, finance, and executives).

## References

1. Verizon. 2025 Data Breach Investigations Report. 
  
  https://www.verizon.com/business/resources/reports/dbir/

2. IBM Security. Cost of a Data Breach Report 2025. 

https://www.ibm.com/reports/data-breach

3. Federal Bureau of Investigation, Internet Crime Complaint Center (IC3). 2024 Internet Crime Report. 

https://www.ic3.gov/

4. Cybersecurity and Infrastructure Security Agency (CISA). Avoiding Social Engineering and Phishing Attacks. 

https://www.cisa.gov/news-events/news/avoiding-social-engineering-and-phishing-attacks

5. Twitter, Inc. An update on our security incident (July 2020). 
  
  https://blog.x.com/en_us/topics/company/2020/an-update-on-our-security-incident

6. New York State Department of Financial Services. Twitter Investigation Report (October 2020). 

https://www.dfs.ny.gov/Twitter_Report

7. CISA. Scattered Spider Cybersecurity Advisory (AA23-320A). 

https://www.cisa.gov/news-events/cybersecurity-advisories/aa23-320a

8. Bursztein, Elie. Concerns about USB security are real: 48% of people do plug in USB drives found in parking lots. 
  
  https://elie.net/blog/security/concerns-about-usb-security-are-real-48-percent-of-people-do-plug-in-usb-drives-found-in-parking-lots

9. ManageEngine. USB Drop Attack — DataSecurity Plus. 

https://www.manageengine.com/data-security/security-threats/usb-drop-attack.html

10. RSA / EMC (as reported by Computer Weekly and Zoho Workplace). RSA discloses phishing-attack data breach details (2011). 
  
  https://www.computerweekly.com/news/1280095593/RSA-discloses-phishing-attack-data-breach-details
