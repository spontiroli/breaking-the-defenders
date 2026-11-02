# ABSTRACT

**Breaking the defenders: measuring defense impairment at scale through msp telemetry**

The introduction of Defense Impairment as a standalone ATT&CK tactic reflects a significant shift in how modern adversaries operate. Rather than simply evading detection, attackers increasingly seek to degrade defenders' visibility by disabling or modifying security tools, abusing vulnerable drivers (BYOVD), tampering with logging, altering firewall configurations, and disrupting other defensive controls before achieving their objectives.

While recent public research has dissected EDR killers and defense impairment techniques used by individual ransomware groups, defenders still lack visibility into how widespread these behaviors are across real-world environments. Which techniques are becoming the norm? When during an intrusion do they occur? Are they consistently associated with ransomware, or are they becoming common across other intrusion types? Most importantly, what do these observations mean for organizations looking to operationalize the new ATT&CK tactic?

In this session, we present a telemetry-driven analysis of Defense Impairment techniques observed across our global MSP ecosystem, complemented by insights from MDR investigations. By mapping these observations to MITRE ATT&CK, we analyze the prevalence and evolution of Defense Impairment techniques, identify common sequences of attacker behavior, and explore which techniques most frequently precede high-impact actions such as ransomware deployment or credential theft. We also discuss how large-scale telemetry can help organizations move beyond simple ATT&CK coverage metrics toward evidence-based prioritization of detections, threat hunting, and defensive validation.

Attendees will leave with a practical understanding of how the new Defense Impairment tactic manifests in the wild, which techniques deserve the highest defensive priority, and how organizations can use ATT&CK not only to understand adversary behavior, but also to prioritize defenses against the techniques attackers use to reduce visibility and disrupt security operations.

# OUTLINE

1. Why Defense Impairment Matters

	- Brief overview of the evolution of ATT&CK Defense Evasion into the newly introduced Defense Impairment tactic.
	
	- Explain why this change reflects a shift in attacker behavior: rather than simply hiding, adversaries increasingly seek to actively reduce defenders' visibility and response capabilities.
	
	- Discuss recent public examples of EDR killers, BYOVD attacks, and security tool tampering to motivate the problem.
	
	- Define the key research question: How prevalent are Defense Impairment techniques in real-world attacks, and how should defenders operationalize this new ATT&CK tactic?

2. Dataset and Methodology

	- Describe the data source and analysis methodology.
	
	- Overview of anonymized telemetry collected across the Acronis MSP ecosystem.
	
	- Brief explanation of how telemetry is normalized and mapped to MITRE ATT&CK techniques.
	
	- Explain how MDR investigation outcomes are used to validate telemetry observations.
	
	- Discuss limitations and biases to ensure responsible interpretation.

3. Defense Impairment in the Wild

	- Most frequently observed Defense Impairment techniques.
	
	- Adoption trends over time.
	
	- EDR killers / BYOVD / service termination / Windows Event Log manipulation / firewall modification / security configuration changes
	
	- Which ATT&CK techniques are becoming increasingly common.
	
	- Differences across ransomware and non-ransomware activity.
	
	- Examples of ATT&CK Navigator visualizations highlighting observed technique prevalence.

4. What Happens Before Ransomware?

	- Move beyond individual techniques and examine attacker behavior.
	
	- Which Defense Impairment techniques commonly precede ransomware deployment.
	
	- Common sequences of ATT&CK techniques observed before encryption.
	
	- Which impairment techniques are associated with successful intrusions versus blocked attacks.
	
	- How often attackers attempt to impair defenses before executing encryption or credential theft.

5. Operationalizing the New ATT&CK Tactic

	- How organizations should prioritize Defense Impairment detections.
	
	- Common detection gaps observed across customer environments.
	
	- Using ATT&CK to measure defensive readiness beyond simple coverage percentages.

6. Key Takeaways and Future Work

	- Summarize the major findings.
	
	- Attendees should leave with an understanding of how Defense Impairment appears across real-world environments.
	
	- Data-driven insight into which ATT&CK techniques deserve the highest defensive priority.
	
	- Practical recommendations for operationalizing the new Defense Impairment tactic within detection engineering and threat hunting workflows.

# REFERENCES

## ATT&CK Evolution and Defense Impairment

### Defense Evasion Split: A Tale of Two Tactics
- **Date:** March 31, 2026
- **Description:** MITRE’s explanation of why the original Defense Evasion tactic had become too broad and why it was divided into Stealth and Defense Impairment. This is the foundational source for explaining the difference between hiding malicious activity and actively damaging defensive capabilities.
- **URL:** https://medium.com/mitre-attack/defense-evasion-split-5d533545fa32

### ATT&CK v19: The Defense Evasion Split, ICS Sub-Techniques, New AI & Social Engineering Coverage, and Detection Strategies for Mobile
- **Date:** April 28, 2026
- **Description:** Official overview of ATT&CK v19. It documents the retirement of the Enterprise Defense Evasion tactic, the introduction of Stealth and Defense Impairment, the restructuring of T1562, and the addition of techniques such as Exploitation for Defense Impairment.
- **URL:** https://medium.com/mitre-attack/attack-v19-ff329cb65d66

### Defense Impairment, Tactic TA0112
- **Date:** Created April 14, 2026; last modified May 12, 2026
- **Description:** The authoritative ATT&CK definition of Defense Impairment. It covers adversary attempts to degrade, disable, or undermine security controls, monitoring infrastructure, and defensive tooling. This should be the principal definition cited in the presentation.
- **URL:** https://attack.mitre.org/tactics/TA0112/

### Detection of Defense Impairment, Detection Strategy DET0900
- **Date:** Created April 16, 2026; last modified July 31, 2026
- **Description:** An official ATT&CK detection strategy for exploitation used to impair defenses. It correlates suspicious interaction with security products to service crashes, driver unloads, unexpected restarts, tamper-state changes, and telemetry gaps. It supports the idea that the impairment attempt can be detected even if visibility disappears afterward.
- **URL:** https://attack.mitre.org/detectionstrategies/DET0900/

### Driver Load, Data Component DC0079
- **Date:** Created October 20, 2021; last modified October 13, 2026
- **Description:** Defines the telemetry associated with loading drivers in user or kernel mode. It is directly relevant to detecting BYOVD attacks and driver-based EDR killers, especially through sources such as Sysmon Event ID 6.
- **URL:** https://attack.mitre.org/datacomponents/DC0079/

### Defense Evasion Is Dead! What MITRE ATT&CK v19 Changed and How to Work With It
- **Date:** May 12, 2026
- **Description:** A practical third-party explanation of the ATT&CK v19 transition. It translates Stealth and Defense Impairment into operational language and discusses the remapping required for detections, threat intelligence, BAS content, purple-team exercises, and coverage matrices. Useful for explanation, but official MITRE sources should be cited for authoritative claims.
- **URL:** https://breachsimrange.io/blog/defense-evasion-is-dead/

## Detection Coverage and Measurement

### If I Have 100% ATT&CK Coverage, Why Didn’t I Detect That?
- **Date:** October 3, 2026
- **Description:** Argues that technique-level coverage percentages can create false confidence because detections often cover only particular procedures or implementations. It uses the CTID Windows case study to support moving from green ATT&CK heatmaps toward procedure-level and telemetry-aware measurement.
- **URL:** https://medium.com/@BlueTeamSteve/if-i-have-100-att-ck-coverage-why-didnt-i-detect-that-a6fda2101bb5

### Putting Detection Coverage to the Test: A Windows Security Case Study
- **Date:** September 29, 2026
- **Description:** CTID evaluated 144 Sigma analytics mapped to 84 ATT&CK techniques. Only 26 techniques had at least one implementation with meaningful coverage, and measured implementation coverage was approximately 26.8%. This is strong evidence for moving beyond ATT&CK coverage percentages.
- **URL:** https://ctid.mitre.org/blog/2026/09/29/windows-security-case-study/

### Beyond the Heatmap: A New Way to Measure Detection Coverage
- **Date:** September 10, 2026
- **Description:** Introduces the 2026 Summiting the Pyramid approach, including Implementation Coverage and Detection Quality. It explains how to measure which implementations of a technique can actually be detected and how robust and precise the underlying signals are.
- **URL:** https://ctid.mitre.org/blog/2026/09/10/summiting-the-pyramid-2026/

### Summiting the Pyramid v4.0.0

- **Date:** 2026; the page does not provide an exact publication day
- **Description:** The main methodology and resource site for engineering detections that are more difficult for adversaries to evade. It provides the Implementation Catalog, Detection Coverage Calculator, and guidance for assessing detection quality and implementation coverage.
- **URL:** https://center-for-threat-informed-defense.github.io/summiting-the-pyramid/

### MITRE ATT&CK Use Cases in 2026: A Security Team Guide
- **Date:** September 16, 2026
- **Description:** A broad vendor overview of ATT&CK use cases, including threat intelligence, detection engineering, red and purple teaming, BAS, gap assessment, SOC maturity, and vendor evaluation. It is useful as background, but it is commercial secondary material rather than primary research.
- **URL:** https://www.acalvio.com/blog/active-defense/important-use-cases-that-make-mitre-attck-compelling/

## Direct Defense Impairment Case Studies from TRU

### Cambodia-Focused Cluster Uses Multistage Infection Chain With Localized Lures
- **Date:** August 26, 2026
- **Description:** One of the strongest case studies for the presentation. The malware patches AMSI and ETW, adds Microsoft Defender exclusions, installs a vulnerable driver, and terminates processes belonging to Defender and other security products. It provides a clear example of BYOVD and security-control impairment occurring before later payload execution.
- **URL:** https://www.acronis.com/en/tru/posts/cambodia-focused-cluster-uses-multi-stage-infection-chain-with-localized-lures/

### From Emerging Threat to Top-Tier Ransomware-as-a-Service: The Evolution of INC Ransomware
- **Date:** June 17, 2026
- **Description:** A strong ransomware example with an explicit Defense Impairment section. It documents INC actors using PsKill and a custom BYOVD process terminator to kill EDR processes before the impact stage. This directly supports the argument that impairment activity can precede ransomware deployment.
- **URL:** https://www.acronis.com/en/tru/posts/from-emerging-threat-to-top-tier-ransomware-as-a-service-the-evolution-of-inc-ransomware/

### LockBit Strikes With New 5.0 Version, Targeting Windows, Linux and ESXI Systems
- **Date:** February 12, 2026
- **Description:** Documents ETW patching, DLL unhooking, process hollowing, event-log clearing, self-deletion, and other anti-forensic behavior in LockBit 5.0. Important sequencing caveat: the analyzed sample performs ETW patching and log clearing after encryption, so this supports impairment and evidence destruction but not necessarily the claim that impairment always precedes ransomware impact.
- **URL:** https://www.acronis.com/en/tru/posts/lockbit-strikes-with-new-50-version-targeting-windows-linux-and-esxi-systems/

## Supporting Stealth and Evasion Case Studies from TRU

These examples help distinguish Stealth from Defense Impairment. They show why ATT&CK v19 separated behaviors that hide from security controls from behaviors that damage or disable them.

### Mustang Panda Targets India’s Government and Energy Sectors With ZOHOMURK and MINIRECON
- **Date:** June 28, 2026
- **Description:** Covers DLL sideloading, hidden payloads, cloud-service abuse, persistence, remote execution, and exfiltration through Zoho WorkDrive. It is primarily a Stealth and trusted-service-abuse example rather than a direct Defense Impairment case.
- **URL:** https://www.acronis.com/en/tru/posts/mustang-panda-targets-indias-government-and-energy-sectors/

### Same Packet, Different Magic: Mustang Panda Hits India’s Banking Sector and Korea Geopolitics
- **Date:** April 21, 2026
- **Description:** Describes a LOTUSLITE campaign using DLL sideloading through a legitimate Microsoft-signed executable. It illustrates how adversaries execute under a trusted process to avoid suspicion, making it a useful Stealth example and contrast to active security-control disruption.
- **URL:** https://www.acronis.com/en/tru/posts/same-packet-different-magic-mustang-panda-hits-indias-banking-sector-and-korea-geopolitics/

### CRESCENTHARVEST: Iranian Protestors and Dissidents Targeted in Cyberespionage Campaign
- **Date:** February 17, 2026
- **Description:** Covers a remote-access and information-stealing campaign delivered through DLL sideloading with a signed Google executable. It includes command execution, keylogging, credential-related browser-data access, and exfiltration. It is more relevant to Stealth and credential theft than direct impairment.
- **URL:** https://www.acronis.com/en/tru/posts/crescentharvest-iranian-protestors-and-dissidents-targeted-in-cyberespionage-campaign/

### PATCHCORD: New Malware Cluster Targets Afghan Telecom and South Asian Critical Infrastructure
- **Date:** August 13, 2026
- **Description:** Describes custom backdoors targeting telecom and critical infrastructure. One PATCHCORD variant checks for debuggers, sandboxes, Sysmon, Wireshark, Process Hacker, Burp Suite, and other analysis tools, then delays execution when they are detected. This is primarily anti-analysis and Stealth, but it provides a useful contrast with tools that terminate those products.
- **URL:** https://www.acronis.com/en/tru/posts/patchcord-new-malware-cluster-targets-afghan-telecom-and-south-asian-critical-infrastructure/

### Behind Khmer Shadow: Targeted Espionage Against Cambodian Government Entities
- **Date:** June 10, 2026
- **Description:** Documents NIGHTFORGE and Havoc Demon activity using DLL sideloading, in-memory execution, NTDLL unhooking, and direct system calls to bypass user-mode monitoring. It is a strong example of Stealth and monitoring bypass, but not of disabling the security product itself.
- **URL:** https://www.acronis.com/en/tru/posts/behind-khmer-shadow-targeted-espionage-against-cambodian-government-entities/

### Red Heron Exploits Gitea N-Day Flaw in Multinational Campaign, Exposing New Linux Rootkit
- **Date:** September 13, 2026
- **Description:** Covers rapid exploitation of Gitea, credential collection, lateral movement, persistent access, and the SIXZUT Linux rootkit. The rootkit hides files, processes, and network connections, providing a Linux example of attackers reducing the reliability of host-level visibility. It is primarily Stealth, although the resulting visibility loss is relevant to the presentation’s “blind afterward” argument.
- **URL:** https://www.acronis.com/en/tru/posts/red-heron-exploits-gitea-n-day-flaw-in-multinational-campaign-exposing-new-linux-rootkit/
