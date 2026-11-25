# LockBit 3.0 -- Cyber Threat Intelligence Report

A defensive cyber threat intelligence research project examining LockBit
3.0 (LockBit Black), its ransomware-as-a-service model, attack
methodology, indicators of compromise (IOCs), and SOC detection and
investigation opportunities.

## Project objectives

-   Profile the LockBit 3.0 ransomware operation and its RaaS model.
-   Summarize publicly documented attack behaviors and map them to MITRE
    ATT&CK.
-   Collect and categorize file hashes, network indicators, host
    artifacts, and behavioral indicators.
-   Assess IOC confidence, limitations, and source context.
-   Identify practical SOC detection and investigation opportunities.

## Scope and methodology

This project uses public cybersecurity advisories and technical
analyses, including the FBI/CISA/MS-ISAC LockBit 3.0 advisory, RH-ISAC's
analysis of the leaked builder, VMware's technical analysis, Calif's
reverse engineering of a specific LockBit v3 build, and Proven Data's
report containing technical indicators. The February 2022 LockBit 2.0
advisory is used for historical comparison of selected indicators.

The collected indicators include file hashes, IP addresses, ransom-note
filenames, registry artifacts, command-line parameters, mutexes,
UAC-bypass techniques, and Group Policy-related artifacts. Indicators
are classified according to their source, technical context, and
relevance to specific LockBit versions. User-collected indicators are
retained but treated as unverified where the original
source-to-indicator mapping could not be independently established.

## Key findings

-   LockBit operates through a ransomware-as-a-service model in which
    affiliates may use different initial-access methods, tools,
    infrastructure, and lateral-movement techniques.
-   The September 2022 builder leak enabled the creation of unique and
    derivative builds, meaning file hashes and other sample-specific
    artifacts are not universal across LockBit 3.0 samples.
-   Reported technical indicators include file hashes, IP addresses,
    ransom-note filenames, mutexes, command-line parameters, registry
    artifacts, and other host-based behaviors.
-   Behaviors such as shadow-copy deletion, security-tool impairment,
    service stopping, log clearing, Group Policy changes, and mass file
    encryption can support behavior-based detection when correlated with
    identity, process, endpoint, and network telemetry.
-   IOC absence does not establish that an endpoint is clean.

## SOC detection and investigation

The project identifies detection opportunities involving suspicious
process and command-line activity, Windows event logs, Sysmon telemetry,
security-tool configuration changes, unusual outbound network activity,
and ransomware-like file activity. Investigation should consider the
initiating process, user account, affected host, timing, destination,
and surrounding events. Legitimate administrative activity and dual-use
tools must be assessed in context rather than treated as malicious based
on a single event.

## Limitations and confidence

This report is based on public sources and user-collected research. It
does not involve live malware execution, investigation of a victim
environment, or original malware sample acquisition. Public IOC lists
are incomplete and time-sensitive. Infrastructure may be reassigned,
shared, or taken down, and file hashes can vary across builds.
Ransom-note filenames and Windows utilities are not unique to LockBit.
Affiliate behavior also varies, and the leaked builder enables
additional derivative samples.

Some collected indicators remain unverified and should not be used as
standalone blocking rules. Builder hashes identify builder components
and should not automatically be treated as hashes of deployed ransomware
payloads. LockBit 2.0 indicators are included only for historical
comparison and are not automatically attributed to LockBit 3.0.
Confidence labels represent analytical judgements for this project, not vendor-assigned threat scores.

## Conclusion

This research examined LockBit 3.0 through public threat intelligence
sources, focusing on its RaaS model, attack methodology, technical
indicators, and SOC detection opportunities. It highlights how file
hashes, IP addresses, host-based artifacts, and attacker behaviors can
support threat identification and incident investigation. It also
demonstrates the importance of correlating multiple indicators with
endpoint, network, and system logs rather than relying on individual
IOCs. Overall, this project strengthened practical understanding of
ransomware threats, IOC analysis, MITRE ATT&CK mapping, and defensive
security practices relevant to SOC operations.

## Sources

-   FBI/CISA/MS-ISAC, [AA23-075A: #StopRansomware: LockBit
    3.0](https://www.ic3.gov/CSA/2023/230316.pdf)
-   RH-ISAC, [LockBit 3.0 Builder Code Leak Technical
    Analysis](https://rhisac.org/threat-intelligence/lockbit-3-0-builder-code-leak-technical-analysis/)
-   VMware, [LockBit 3.0 Ransomware
    Unlocked](https://blogs.vmware.com/security/2022/10/lockbit-3-0-also-known-as-lockbit-black.html)
-   Calif, [Dissecting LockBit v3
    ransomware](https://calif.io/research/lockbit-v3)
-   FBI/CISA/MS-ISAC, [LockBit 2.0
    advisory](https://www.ic3.gov/CSA/2022/220204.pdf) (used for
    historical comparison only)
-   Proven Data, [LockBit 3
    Ransomware](https://www.provendata.com/blog/lockbit3-ransomware)
    (technical analysis reporting hashes, IP addresses, and other
    indicators)

