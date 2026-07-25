# Pre-Security - 1. Intro to Cyber Security

## **1. Offensive Security**

#### **1 - What is Offensive Security?**

Offensive Security involves breaking into computer systems, exploiting software bugs, and finding loopholes in applications to gain unauthorized access. The goal is to understand hacker tactics and enhance our system defences.

Which of the following options better represents the process where you simulate a hacker's actions to find vulnerabilities in a system? Offensive Security

Using dirb is quite simple. Using the terminal, write the `dirb` command followed by the URL of the website you want to brute-force. Be sure to press `ENTER` in your keyboard to execute the command:

```bash
dirb http://fakebank.thm
```

the tool uses the default wordlist included with the tool, located at `/usr/share/dirb/wordlists/common.txt`. There's a copy of the `common.txt` file in your desktop as well, if you want to explore it.

![image.png](image.png)

## **2. Defensive Security**

**Task 1 - Introduction to Defensive Security**

Defensive security, **known as the blue team**, is used to prepare and proactively protect an organisation's IT infrastructure.  It is concerned with two main tasks:

1. Preventing intrusions from occurring
2. Detecting intrusions when they occur and responding properly

### 2 - Exploring the SOC

Some of the main areas of interest for a SOC are:

![image.png](image%201.png)

**Key Defender Principles**

- **Threat anticipation**: Review the systems you aim to protect and ask, "What if?" Imagine realistic paths an attacker may take to achieve their goal.
- **Attack awareness**: Attacks typically follow recognizable stages. Studying common attack chains and frameworks is incredibly useful for defenders.
- **Risk prioritization**: Not every part of your system carries equal risk. Defenders should identify high-value systems and targets.
- **Continuous adaptation**: Defense is not a one-time set up. Threats and attackers evolve, techniques change, and vulnerabilities emerge.

| **System or Infrastructure Component** | **What Could Go Wrong** | **Defenses You'll Use** |
| --- | --- | --- |
| Employee Devices | Someone clicks a bad link or downloads unsafe software | Antivirus to detect bad programsRegular software updates |
| Web Server | Attackers try to break into the website | Only allow safe trafficUse secure communication |
| Mail Server | Malicious or deceptive emails | Spam filtersScan attachments |
| Firewall | Strangers from the internet try to break in | Firewall rules that control accessBlock known troublemakers |
| The Outside Internet | External threats come from here | Restrict inbound trafficMonitor for suspicious activity |

**Key Terminology**

- **Blue Team**: A group of cyber security defenders tasked with protecting systems and responding to threats
- **Client Infrastructure**: The networks, servers, devices, and applications belonging to an organization that need protection
- **Visibility**: The ability to see and monitor activity across systems to spot potential issues
- **Threat**: A potential danger, such as a hacker or malware, that could harm systems or data
- **Prevention**: Stopping threats before they can cause harm by blocking, restricting, or reducing opportunities for attack
- **Detection**: The process of identifying threats or suspicious activity in networks and systems
- **Mitigation**: Actions taken to reduce or stop the impact of a threat once it's identified
- **Risk**: The likelihood and potential impact of a threat successfully harming an organization

**Core Offensive Security Terms**

- **Red Teaming**: A structured, authorized attack methodology that simulates a real adversary to test the effectiveness of defenses and find vulnerabilities within a defined scope
- **Penetration Test**: A structured security assessment where an authorized tester attempts to identify and exploit vulnerabilities within a defined scope to understand real-world risk
- **Vulnerability**: A weakness or flaw in a system, application, or configuration that an attacker could abuse
- **Exploit**: A technique or method used to take advantage of a vulnerability to achieve a specific outcome, such as accessing restricted functionality or data
- **Scope**: The boundaries of what is allowed to be tested during an engagement. Scope defines which systems, applications, and actions are permitted, and what is off-limits

**A Valuable Target**

- **Sensitive functionality**: Features that perform essential actions, such as modifying data, viewing restricted content, or triggering processes that should only be available to authorized users
- **User data**: Personal or private information belonging to users, such as names, email addresses, or account details, which attackers may steal, abuse, or sell
- **Administrative features**: High-privilege functionality that allows attackers to manage users, change settings, or gain full control of the application if accessed
- **Further attack opportunities**: Authenticated access can expose other vulnerabilities, allowing attackers to expand their access or move deeper into the application

**Key Terminology**

- **Scope**: The exact systems and actions allowed during a security test
- **Vulnerability**: A hidden weakness in a system that an attacker could use to break in
- **Exploit**: A method or technique that takes advantage of a vulnerability
- **Enumeration**: Collecting details about a system, users, and services to find weak points
- **Credentials**: Login details such as usernames and passwords that unlock access
- **Authentication**: The step that checks if someone or something is really who they claim to be when logging in
- **Dictionary attack**: Trying a predefined wordlist to guess a password or username

**Potential Career Opportunities**

- **Penetration Tester/Ethical Hacker**: Focuses on safely exploring vulnerabilities within a defined scope
- **Vulnerability Researcher**: Identify and validate undiscovered weaknesses in software and hardware
- **Red Team Operator**: Simulate real-world adversaries to test an organization's detection, response, and defensive capabilities

### 3 - Digital Forensics

**Digital Forensics:** Digital forensics is the application of traditional forensic science processes to digital devices. Digital forensics is used to preserve and analyse digital evidence to aide in the investigation of incidents, such as a breach.

### 4 - Incident Response

**Incident Response:** Incident Response is how organisations manage security events such as breaches, data leaks and cyber attacks. An incident response process is a defined set of stages to minimise damage, contain the threat and recover fast.

## **3. Cyber Career**

- **Security Analyst:** Monitors and evaluates networks to identify security risks and provide recommendations to improve an organisation’s defenses.
- **Security Engineer:** Designs and implements security solutions to prevent attacks, reduce vulnerabilities, and protect systems and data.
- **Incident Responder:** Handles security breaches by detecting, containing, and recovering from attacks through effective response plans and real-time actions.
- **Digital Forensics Examiner:** Investigates cyber incidents by collecting, analyzing, and preserving digital evidence to uncover the truth behind crimes or attacks.
- **Malware Analyst:** Examines and reverse-engineers suspicious software to understand malware behavior and identify potential threats.
- **Penetration Tester:** Performs ethical hacking to discover and exploit vulnerabilities in systems, helping organisations improve their security posture.
- **Red Teamer:** Simulates real-world cyberattacks to test an organisation’s ability to detect, respond to, and defend against advanced threats.