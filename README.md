# GreenZone

*Surveillance resilience, digital self-defence, network integrity, consensual forensics, and personal safety.*

> **GreenZone is a security, privacy, and personal-safety platform in the design stage, intended to help individuals, journalists, lawyers, researchers, activists, organisations, and other at-risk users preserve confidentiality, reduce unnecessary surveillance exposure, detect unexpected technical conditions, and retain meaningful control over their digital lives.**

GreenZone begins with a simple observation:

**Encryption protects information. It does not necessarily protect the person, their metadata, their location, their relationships, their devices, or the inferences made about them.**

Modern surveillance rarely depends upon one decisive source of information.

Location history, cellular metadata, IP traffic, device identifiers, telemetry, cloud services, behavioural patterns, communications metadata, public records, cameras, biometrics, social graphs, endpoint compromise, and automated analysis may individually reveal little.

Combined, they can reveal considerably more.

GreenZone is therefore designed around a broader concept:

> **Protect the information.  
> Protect the endpoint.  
> Protect the path.  
> Reduce correlation.  
> Preserve evidence of boundary violations.**

The objective is not invisibility.

Perfect invisibility is unrealistic.

The objective is to make lawful privacy easier while making indiscriminate surveillance, unnecessary profiling, metadata correlation, and silent endpoint compromise substantially more difficult, expensive, detectable, and accountable.

---

## Project status

**GreenZone is currently a design-stage project. The capabilities described in this README are planned features or research directions, not a list of implemented protections.**

The repository currently contains project documentation and its license. It does not yet provide a working GreenZone application, supported installation procedure, or production-ready security controls. Build and installation instructions will be added alongside working, tested components.

The project is intended to operate on a non-commercial basis, without advertising or user profiling. The choice of software license is under review; the current MIT grant and third-party terms are explained in [Licensing](#licensing).

The architecture, terminology, APIs, threat models, legal-policy framework, platform capabilities, and individual modules remain subject to significant change.

Initial releases should be considered experimental.

GreenZone must not initially be relied upon as the sole protection for:

- life-critical communications;
- confidential journalistic sources;
- attorney-client material;
- evidence;
- irreplaceable data;
- emergency communications;
- or systems whose compromise could cause serious harm.

The project will progressively introduce formal threat models, security documentation, reproducible testing, forensic validation, independent review, and platform-specific capability documentation. A roadmap entry does not establish that a feature is available, effective, or safe for a particular threat model.

## Contents

- [Why GreenZone?](#why-greenzone)
- [Core principles](#core-principles)
- [Architecture](#architecture)
- [Planned platforms](#planned-platforms)
- [Cryptography](#cryptography)
- [Surveillance resilience](#surveillance-resilience)
- [GreenZone Gateway](#greenzone-gateway)
- [Path Integrity & Transition Control](#path-integrity--transition-control)
- [GreenZone Connection Advisor](#greenzone-connection-advisor)
- [GreenZone Secure Workspace](#greenzone-secure-workspace)
- [Protected mobility and personal safety](#protected-mobility-and-personal-safety)
- [Mobile Verification Toolkit integration](#mobile-verification-toolkit-integration)
- [GreenZone Evidence Provenance](#greenzone-evidence-provenance)
- [Professional Mode](#professional-mode)
- [EU-wide legal architecture](#eu-wide-legal-architecture)
- [Offline GreenZone Wiki](#offline-greenzone-wiki)
- [Threat model](#threat-model)
- [Build and supply-chain security](#build-and-supply-chain-security)
- [Privacy by default](#privacy-by-default)
- [Ethical boundaries](#ethical-boundaries)
- [Roadmap](#roadmap)
- [Contributing](#contributing)
- [Licensing](#licensing)

---

## Why GreenZone?

Traditional privacy and security products usually protect one layer.

An encrypted messenger protects message contents.

A VPN protects part of the network path.

A password manager protects credentials.

Full-disk encryption protects data at rest.

An anonymity network obscures network origin.

An antivirus product looks for known malicious behaviour.

A firewall decides whether connections are permitted.

A forensic toolkit searches for traces of compromise.

These are all useful.

But an adversary does not have to attack the strongest layer.

A system protected by excellent cryptography may still disclose information through:

- endpoint malware;
- operating-system telemetry;
- application telemetry;
- browser identifiers;
- DNS;
- route changes;
- unexpected tunnels;
- cloud synchronisation;
- notification previews;
- screen capture;
- clipboard history;
- crash dumps;
- page files;
- smart displays;
- cameras;
- cellular registration;
- location correlation;
- or human behaviour.

GreenZone therefore treats privacy as a **system property** rather than a feature.

---

## Core principles

GreenZone combines five broad security goals.

### 1. Confidentiality

Keep sensitive information confidential through strong, well-studied cryptography, compartmentalisation, independent keys, protected storage, and secure communications.

### 2. Unlinkability

Reduce unnecessary correlation between identities, devices, network contexts, applications, locations, and behaviours.

### 3. Situational awareness

Detect changes in the technical environment that may indicate increased risk.

### 4. Path integrity

Verify that communications actually travel through the security path required by policy rather than silently falling back to an unexpected interface, tunnel, resolver, gateway, or network.

### 5. Legal and forensic provenance

Preserve cryptographically verifiable evidence about security boundaries and integrity events so that unexpected access can later be investigated and, where relevant, legally challenged.

---

## Architecture

GreenZone is intended to become an ecosystem rather than one monolithic application.

```text
GreenZone
├── Core: policy, keys, storage, events, platform capabilities
├── Endpoint protection
│   ├── Desktop and mobile
│   ├── Secure Workspace and Secure Presentation Path
│   └── Protected mobility and personal safety
├── Network protection
│   ├── Gateway and segmentation
│   ├── Path Integrity Monitor
│   └── Connection Advisor
├── Forensics and integrity
│   ├── Optional MVT workflows
│   ├── Evidence Provenance
│   └── Professional Mode policies
└── Offline Wiki: security guidance and jurisdiction packs
```

Planned architectural components include:

- **GreenZone Core**
- **GreenZone Desktop**
- **GreenZone Mobile**
- **GreenZone Protected Mobility and Safety**
- **GreenZone Secure Workspace**
- **GreenZone Secure Presentation Path**
- **GreenZone Gateway**
- **GreenZone Path Integrity Monitor**
- **GreenZone Professional Mode**
- **GreenZone Evidence Provenance**
- **GreenZone Connection Advisor**
- **GreenZone Mobile Verification / MVT integration**
- **GreenZone Offline Wiki**

Not every installation will require every component.

---

## GreenZone Core

The portable security core is planned around **ISO C++23**.

The project intends to avoid unnecessary compiler-specific behaviour while validating the core against multiple independent toolchains, including GCC, Clang/LLVM, Apple Clang, and where appropriate MSVC.

Multiple toolchains can expose portability defects and enable independent checks. Compiler diversity alone does not establish that a compiler or build is trustworthy.

The core is expected to provide common implementations for:

- cryptographic policy;
- key management abstractions;
- secure storage;
- policy evaluation;
- threat profiles;
- event classification;
- protected contexts;
- protocol handling;
- integrity measurements;
- secure serialisation;
- forensic event structures;
- platform capability negotiation.

Platform-specific privileged operations will remain outside the portable core.

---

## Planned platforms

GreenZone is intended to support all major personal-computing platforms:

- Windows
- macOS
- Linux
- Android
- iOS

These are target platforms, not a claim of current support. Planned support does not imply identical capabilities.

Operating systems expose very different networking, cryptographic, biometric, sandboxing, background-execution, display-protection, and hardware-security facilities.

GreenZone will therefore use a capability model:

```text
GreenZone asks:

"What can this platform protect safely?"

rather than:

"How can every platform be forced to behave identically?"
```

Platform differences will be documented explicitly.

---

## Cryptography

GreenZone will not invent proprietary cryptographic algorithms.

Security through obscurity is not considered an acceptable foundation.

Instead, GreenZone will use established and independently analysed cryptographic primitives while supporting **cryptographic agility** so algorithms can be replaced as standards and threat models evolve.

GreenZone is particularly interested in layered protection using independent keys and independent security boundaries.

For example:

```text
sensitive object
      │
      ▼
per-object encryption
      │
      ▼
encrypted GreenZone vault
      │
      ▼
encrypted transport
      │
      ▼
remote encrypted storage
```

The important property is not simply:

```text
encrypt(encrypt(encrypt(data)))
```

but rather:

- independent keys;
- domain separation;
- compartmentalisation;
- limited key lifetime;
- hardware-backed protection where available;
- minimal plaintext exposure;
- protected memory handling;
- cryptographic agility;
- recoverability.

Future versions may support hybrid classical/post-quantum key establishment where appropriate.

GreenZone does **not** claim that strong encryption alone defeats a compromised endpoint.

If an attacker controls the system while plaintext or keys are available, attacking the endpoint is frequently easier than attacking the cryptography.

---

## Surveillance resilience

GreenZone distinguishes between **secrecy** and **observability**.

A message may be encrypted while still revealing:

```text
device A
    │
service B
    │
time C
    │
location D
    │
communication pattern E
```

Repeated observations produce patterns.

Patterns produce correlations.

Correlations produce hypotheses.

At sufficient scale, hypotheses become machine-generated intelligence.

GreenZone therefore investigates ways to defend not only information itself but also against unnecessary **cross-domain correlation**.

---

## Correlation resistance

An early internal GreenZone concept was described as **dual false SIGINT**.

The public architecture uses a more precise concept:

### Cross-Domain Correlation Resistance

Intelligence and profiling systems gain confidence when independent observations converge.

```text
Source A ─────┐
              ├──► correlation ───► high-confidence inference
Source B ─────┘
```

GreenZone seeks to reduce unnecessary correlation by creating separation between contexts where technically and legally appropriate.

```text
Context A ────► identifier A ───┐
                                │
Context B ────► identifier B ───┼──► difficult to correlate
                                │
Context C ────► identifier C ───┘
```

Preferred mechanisms include:

- compartmentalised identities;
- short-lived identifiers;
- independent network contexts;
- local processing;
- traffic normalisation;
- batching;
- padding;
- metadata minimisation;
- controlled cover traffic;
- independent routing contexts;
- separation of applications and security domains.

The objective is not to impersonate another person.

The objective is to reduce unnecessary correlation. Effectiveness must be measured against explicit adversary models; context separation does not guarantee unlinkability.

---

## Privacy-preserving data poisoning

GreenZone may investigate carefully bounded forms of **privacy-preserving data poisoning**.

In GreenZone terminology, this does **not** mean:

- corrupting external databases;
- modifying government systems;
- falsifying evidence;
- attacking machine-learning systems;
- impersonating third parties;
- attributing activity to innocent people;
- or contaminating systems belonging to other organisations.

The design objective is much narrower:

> Reduce the confidence of passive profiling systems without creating false accusations or harming third parties.

Candidate techniques must satisfy strict requirements:

```text
Does it reduce unnecessary correlation?
              │
              ▼
Does it harm another person?
      │               │
     NO              YES
      │               │
      ▼               ▼
continue            reject
      │
      ▼
Does it fabricate material evidence?
      │               │
     NO              YES
      │               │
      ▼               ▼
candidate           reject
```

GreenZone must never manufacture evidence against another person.

These are experimental research directions. Cover traffic or unusual identifiers can also increase fingerprintability, network load, or suspicion. Any proposal must be evaluated for those effects before it becomes an optional user-facing feature.

---

## GreenZone Gateway

The endpoint cannot protect an organisation by itself.

Human beings click links.

People bring unmanaged devices to work.

Software changes its network behaviour.

Applications silently introduce new telemetry.

Operating systems discover alternative routes.

Smart devices communicate without telling anyone.

GreenZone Gateway exists to establish an organisation-wide minimum security baseline even when individual users are not security experts.

```text
                         INTERNET
                            │
                    ┌───────▼───────┐
                    │   GreenZone   │
                    │    Gateway    │
                    └───────┬───────┘
                            │
       ┌────────────┬───────┼────────┬────────────┐
       │            │       │        │            │
    Lawyers       Staff   Servers   Guest        IoT
       │            │       │        │            │
     VLAN          VLAN    VLAN      VLAN         VLAN
```

The Gateway should enforce both:

**North-south security**

```text
organisation ↔ Internet
```

and, where deployed as the inter-zone router:

**East-west security**

```text
endpoint ↔ endpoint
endpoint ↔ server
IoT      ↔ workstation
guest    ↔ internal systems
```

Network segmentation should allow organisations to enforce policies such as:

```text
Guest → Internal network       DENY
IoT → Workstations             DENY
Staff → Privileged endpoints   DENY by default
Managed → Server               policy controlled
Professional → Protected zone  explicitly authorised
```

The Gateway should protect users who never learn how GreenZone works.

---

## Inspect behaviour, not confidential content

GreenZone Gateway should avoid becoming another surveillance system.

The planned architecture should therefore favour:

- connection metadata;
- route state;
- endpoint integrity assertions;
- process-to-flow attribution;
- DNS state;
- transport metadata;
- policy context;
- cryptographic device identity.

It should **not** require routine interception of confidential application payloads.

In particular, GreenZone should avoid deploying organisation-wide TLS interception simply because doing so is technically possible.

A privacy system should not solve surveillance by building its own surveillance infrastructure. Connection metadata can itself be sensitive: collection should be purpose-limited, access-controlled, retained briefly, and visible to the people affected.

A gateway can enforce only the paths and observation points it controls. Same-segment traffic, an independent cellular connection, or an unmanaged tunnel may require endpoint controls or a different network layout. Encrypted DNS, encrypted client-hello information, VPNs, and application multiplexing can limit attribution; missing evidence must be reported as uncertainty.

---

## Path Integrity & Transition Control

Modern systems may have many possible paths to the Internet:

- Ethernet;
- Wi-Fi;
- cellular;
- VPN;
- IPv4;
- IPv6;
- overlay networks;
- virtual adapters;
- transition tunnels;
- container networks;
- hypervisors;
- application proxies.

GreenZone therefore includes a planned **Path Integrity Monitor** spanning endpoint and gateway observation where available.

Its central question is:

> **Did traffic travel through the path required by security policy?**

The monitor distinguishes four evidence planes:

```text
PROCESS PLANE
What application requested communication?
        │
        ▼
RESOLUTION PLANE
How was the destination resolved?
        │
        ▼
ROUTING PLANE
Which interface / gateway / tunnel was selected?
        │
        ▼
PACKET PLANE
What traffic actually crossed the observation point?
```

GreenZone must distinguish:

- configured capability;
- available route;
- selected route;
- and observed traffic.

An available IPv6 interface does not prove that IPv6 was used.

A DNS `AAAA` response does not prove that IPv6 was used.

A configured tunnel does not prove that packets crossed it.

Security decisions should therefore rely upon observed state rather than speculative inference whenever possible. If an interface, process, or packet cannot be observed, GreenZone should report that gap rather than imply that it has verified the entire path.

---

## Transition tunnels

Enterprise deployments may explicitly restrict unapproved transition and encapsulation mechanisms such as:

- 6to4 / 6in4;
- IPv6-over-IPv4 Protocol 41;
- Teredo;
- ISATAP;
- IP-HTTPS;
- GRE;
- IP-in-IP;
- other unauthorised overlays.

These technologies are not automatically malicious.

The relevant question is:

> **Was this communications path authorised for this endpoint and security profile?**

A managed GreenZone network may therefore operate according to:

```text
Native IPv4              policy controlled
Native IPv6              policy controlled
Approved GreenZone path  allowed
Unapproved tunnel        deny / investigate
Unknown overlay          quarantine / investigate
```

---

## No silent fail-open

High-security GreenZone profiles should support explicit fail-closed behaviour.

If policy specifies:

```text
REQUIRE GreenZone protected path
```

then loss of that path should mean:

```text
NETWORK ACCESS DENIED
```

rather than:

```text
fallback to ordinary Internet connection
```

Normal dual-stack behaviour such as IPv4/IPv6 Happy Eyeballs selection is not itself considered suspicious.

A security event occurs when the **observed path violates the applicable policy**. Each profile must explain how fail-closed behaviour affects emergency alerts and other connectivity, including any explicit, visible user override; there must be no silent bypass.

---

## GreenZone Connection Advisor

GreenZone should help users understand network decisions without turning an AI model into the firewall.

The architecture therefore separates deterministic evidence gathering from explanation.

```text
system evidence
      │
      ▼
policy engine
      │
      ▼
risk classification
      │
      ▼
human-readable explanation
```

An AI component may explain:

- why a connection is unusual;
- which evidence was observed;
- what changed;
- what policy applies;
- what the consequences of allowing or blocking may be.

The model should not invent network evidence.

The decision engine must remain inspectable and reproducible. AI explanations should be optional, work locally where practical, and have no authority to silently override deterministic security policy. Sensitive connection or forensic data must not be sent to an external model without informed user choice.

---

## GreenZone Secure Workspace

Sensitive work may require stronger isolation than ordinary application-level security.

GreenZone Secure Workspace is intended to provide protected execution contexts with controls for:

- process isolation;
- secure temporary storage;
- clipboard restrictions;
- protected notifications;
- search-index exclusions;
- crash-dump protection;
- protected recent-file handling;
- restricted cloud synchronisation;
- protected communication profiles;
- protected network paths;
- compartmentalised identities.

The long-term architecture may explore stronger virtualised isolation where operating-system capabilities make that appropriate.

---

## Secure Presentation Path

Protecting encrypted files is insufficient if plaintext is subsequently exposed on screen.

GreenZone should evaluate available operating-system mechanisms to reduce capture through ordinary screenshot and recording interfaces. Search indexing, previews, crash dumps, and history or recall features require their own controls and validation.

Examples of platform capabilities include mechanisms such as:

- Windows display-capture exclusion;
- Android secure-window functionality;
- equivalent platform-supported protections where available.

GreenZone must clearly distinguish:

```text
ordinary screenshot API        potentially protectable
screen-recording API            potentially protectable
OS history / Recall             potentially protectable
kernel-level compromise         not guaranteed
hostile firmware                not guaranteed
external camera                 cannot be prevented
```

These are candidate protection surfaces, not validated GreenZone capabilities. Availability and effectiveness depend on the operating system, application, privileges, capture method, and device configuration.

No screenshot-protection mechanism should be marketed as protection against a fully compromised kernel or external recording device.

---

## Ambient devices and smart displays

A workstation may be well protected while the display attached to it is not.

Smart televisions, smart monitors, streaming devices, voice assistants, printers, conference equipment, and other ambient systems may contain:

- microphones;
- cameras;
- telemetry;
- automatic content recognition;
- cloud services;
- advertising identifiers;
- vendor analytics;
- remote-management components.

GreenZone therefore treats ambient devices as part of the threat model.

Devices may be classified as:

```text
Tier 1
Controlled endpoints
Windows / Linux / macOS / Android / iOS

Tier 2
Semi-controlled endpoints
Android TV / Google TV and similar systems

Tier 3
Untrusted ambient devices
Smart TVs
Smart monitors
IoT equipment
Vendor appliances
```

Where software installation is impractical, GreenZone Gateway may provide network-level isolation and policy enforcement.

---

## Protected mobility and personal safety

The original GreenZone concept includes practical support for people travelling, handling confidential material, or facing unexpected device separation. Planned capabilities include:

- encrypted local containers and protected remote backups;
- authenticated, encrypted transfer of selected material to trusted storage;
- user-controlled temporary removal and later restoration of sensitive local data;
- travel and border profiles, location risk zones, and geofenced policy prompts;
- paired-device or wearable signals that may indicate separation or loss;
- explicit emergency actions and opt-in trusted-contact notifications;
- network-change awareness and cellular indicators where platform APIs permit;
- offline access to trusted organisations, consular information, and legal resources.

Backup verification, recovery-key handling, explicit confirmation for destructive actions, and tested restoration must precede any feature that removes local information. Deleting a file does not establish secure erasure from flash storage, cloud replicas, snapshots, or earlier backups.

Location and Bluetooth signals can be absent, inaccurate, spoofed, or delayed. Separation is not proof of seizure, and a network change is not proof of an interception device. GreenZone should explain these uncertainties and avoid unsupported accusations.

Emergency actions need clear cancellation and recovery paths. Notifications and transfers may fail without connectivity; a trusted contact must opt in, and an automated alert must not imply that help has been dispatched. Data collected for safety features should stay local unless sharing is explicitly chosen.

---

## Mobile Verification Toolkit integration
GreenZone intends to provide an optional integration with the [**Mobile Verification Toolkit (MVT)**](https://docs.mvt.re/en/latest/), maintained by Amnesty International Security Lab and contributors.

MVT supports consensual forensic analysis of Android and iOS devices to identify traces of compromise. GreenZone would guide supported workflows and preserve their outputs; this is not a claim that GreenZone currently includes or runs MVT.

Potential GreenZone integration includes:

- guided device acquisition;
- invoking supported MVT workflows;
- importing public indicators of compromise;
- preserving MVT output;
- correlating results with GreenZone integrity events;
- producing timelines;
- integrating results into incident-response workflows;
- preserving forensic provenance.

The MVT License requires the **Data Owner** to provide explicit, informed consent free from coercion, including an understanding of privacy implications and data retention and disposal. The Data Owner is defined by legitimate use of the device and may differ from its legal owner; possession or employer ownership alone does not establish that consent.

GreenZone must also preserve an important limitation:

> **A negative MVT result does not prove that a device is uncompromised.**

Advanced spyware evolves continuously, and recent compromises may not match publicly available indicators.

Findings need contextual, expert interpretation. Public indicators can be incomplete, and an apparent match may need further investigation. Acquisition and analysis can alter device state, so preservation requirements should be considered before starting a workflow.

MVT and modifications to its covered code remain governed by [MVT License 1.1](https://license.mvt.re/1.1/), including its notice and source-distribution requirements. Its consent condition also applies to a Larger Work as defined by that license. Any future integration must review these terms for the particular release and architecture. Optional installation or a separate executable is an architectural choice, not an automatic exemption from license conditions. See [Licensing](#licensing).

Forensic exports and indicators also need provenance, access controls, retention limits, and their own license review where applicable.

---

## GreenZone Evidence Provenance

GreenZone cannot guarantee that unlawfully or improperly obtained material will automatically be excluded by a court.

Different legal systems apply different evidentiary rules.

Instead, GreenZone Evidence Provenance is intended to help preserve independent technical evidence about the existence and integrity of protected contexts.

A protected context may produce a signed manifest containing information such as:

```text
GreenZone release
binary hashes
policy version
device integrity state
protected-context identifier
security configuration
timestamp
nonce
```

The manifest can be cryptographically committed:

```text
manifest
   │
   ▼
cryptographic hash
   │
   ▼
digital signature
   │
   ├── protected local record
   │
   └── privacy-preserving external timestamp
```

An external timestamp service should not need to know:

- the client;
- the lawyer;
- the journalist;
- the case;
- the document;
- or the contents.

It should receive only the commitment and the minimum information required by the timestamp protocol. A timestamp can support a claim that committed data existed no later than a particular time; it does not verify the truth of that data, the absence of compromise, or the legality of an event. Timing and network metadata may still reveal information and must be included in the privacy assessment.

---

## Tamper-evident integrity history

GreenZone should avoid creating invasive user-activity logs.

Instead of recording everything a user does, it should be capable of recording security-boundary state changes such as:

```text
protected boundary valid
protected boundary valid
unexpected privileged access
integrity state changed
protected boundary restored
```

Events may be cryptographically chained:

```text
E0
 │
 ▼
H(E0) + E1
 │
 ▼
H(previous) + E2
 │
 ▼
H(previous) + E3
```

Periodic external commitments can help expose later rewriting relative to a trusted commitment. Hash chains and signatures alone do not detect events that were never logged, prove that a sensor was truthful, or prevent a compromised endpoint from suppressing events or stealing signing keys. Evidence exports must state those limits and identify the observation points, key custody, clock assumptions, and possible gaps.

---

## Professional Mode

Some users operate under legal or professional confidentiality requirements.

GreenZone Professional Mode is intended for environments such as:

- lawyers;
- journalists;
- medical professionals;
- researchers;
- human-rights organisations;
- confidential corporate work;
- protected sources;
- sensitive negotiations.

Professional Mode may associate a protected workspace with a policy without revealing its confidential content.

For example:

```text
PROTECTED CONTEXT
Type: Professional
Policy: High confidentiality
External connectivity: Restricted
Capture protection: Required
Evidence provenance: Enabled
```

GreenZone should enforce technical boundaries.

It should not attempt to replace a lawyer's interpretation of the law.

---

## EU-wide legal architecture

GreenZone is being designed for use across the European Union rather than being tied exclusively to Swedish law.

The legal architecture therefore follows a layered model:

```text
European Union baseline
        │
        ├── fundamental rights
        ├── privacy
        ├── data protection
        ├── communications confidentiality
        ├── cybersecurity
        ├── product security
        └── applicable EU regulation
                │
                ▼
Member-state legal overlays
        │
        ├── Sweden
        ├── Denmark
        ├── Germany
        ├── France
        ├── Netherlands
        └── other jurisdictions
```

The proposed policy model separates applicable EU rules from national rules and local procedures. Any conclusion about primacy, scope, exceptions, or a conflict of laws requires jurisdiction-specific legal review.

National criminal procedure, intelligence law, professional secrecy, telecommunications law, evidentiary rules, and surveillance authorities nevertheless differ considerably.

GreenZone therefore should never assume:

```text
one legal rule == all EU countries
```

Jurisdiction-specific policy packs are expected to become part of the project. Each legal entry should identify its official sources, jurisdiction, effective dates, last review date, responsible reviewer, and uncertainty or pending changes. A signed pack establishes origin and integrity, not legal correctness. Offline material can become outdated.

---

## Offline GreenZone Wiki

Technology cannot solve every privacy problem.

A person may use flawless cryptography and still compromise themselves through:

- travel behaviour;
- device handling;
- an exposed screen;
- public cameras;
- insecure charging;
- cellular registration;
- social engineering;
- poor operational security;
- revealing metadata;
- physical observation.

GreenZone plans to include an **offline security and privacy knowledge base** as a core component.

The Wiki should be usable without Internet access so that users can consult it where connectivity is unavailable, unsafe, censored, monitored, or intentionally disabled. Reading installed content should not require an account, send reading-history telemetry, or load remote resources.

Content should be versioned and signed.

Optional updates may be downloaded when the user chooses.

The Wiki may contain jurisdiction-specific sections, with an EU baseline and member-state packs. Guidance should cite primary sources, distinguish verified facts from assumptions, state its limitations, and display when it was last reviewed. Expired guidance must remain identifiable when the device is offline.

---

## Wiki topics

Planned topics include:

### Airports, borders, and travel

- risks associated with cellular registration;
- the benefits, limits, and practical consequences of powering down or disabling radios in a specific threat scenario, including emergency access and device-specific behaviour;
- border-search preparation;
- temporary travel devices;
- eSIM/SIM considerations;
- device separation;
- secure backups;
- minimising confidential local data;
- safe charging;
- hostile Wi-Fi;
- Bluetooth exposure;
- location metadata.

### Cameras and biometric surveillance

- how real-time facial-recognition systems work;
- applicable legal frameworks;
- understanding camera-rich environments;
- reducing unnecessary biometric exposure through lawful practices;
- device and photograph metadata;
- image-sharing risks;
- organisational travel policy.

For example, Sweden's [SFS 2026:806](https://www.riksdagen.se/sv/dokument-och-lagar/dokument/svensk-forfattningssamling/lag-2026806-om-anvandning-av-ai-system-for_sfs-2026-806/) addresses police and Security Service use of real-time facial recognition and other remote biometric identification in public places, subject to statutory conditions. An account of a legal power must remain distinct from evidence that a particular system is deployed at a particular location.

The GreenZone Wiki should explain such legislation without pretending that software alone can prevent observation by a physical camera.

### Journalism and source protection

- meeting-source threat models;
- metadata correlation;
- device separation;
- secure communications;
- location exposure;
- document handling;
- photographing documents safely;
- emergency procedures;
- source-compartmentalisation principles.

### Lawyer-client confidentiality

- protected workspaces;
- travel with privileged information;
- cloud-service risks;
- metadata;
- communications;
- device seizure;
- integrity evidence;
- incident response.

### Spyware

- warning signs;
- what advanced spyware can and cannot do;
- when to preserve rather than modify a device;
- when MVT is appropriate;
- why absence of public indicators does not prove safety;
- obtaining professional forensic help.

### Public Wi-Fi and hostile networks

- captive portals;
- rogue access points;
- certificate warnings;
- DNS manipulation;
- VPN limitations;
- network compartmentalisation.

### Physical OPSEC

- shoulder surfing;
- cameras;
- microphones;
- smart displays;
- USB devices;
- charging equipment;
- unattended devices;
- secure storage.

The Wiki should favour practical, lawful, evidence-based guidance. It must not present unverified claims about a particular airport, cell site, camera, or intelligence operation as established facts, or promise reliable defeat of facial recognition.

---

## The Green Zone

The project's original name comes from a physical-safety concept.

GreenZone should eventually help answer:

> **Where is the nearest place, network, jurisdiction, or person that reduces my current risk?**

A Green Zone may represent:

- a trusted physical location;
- an embassy or consular resource;
- a newsroom;
- a trusted organisation;
- a legal resource;
- a trusted network;
- an approved communications environment;
- a known safe contact;
- a protected jurisdictional context.

For someone crossing a border, reporting from a conflict, attending a demonstration, protecting a confidential source, or travelling through a hostile environment, cybersecurity and physical safety can become the same problem.

A listed resource or location is not a guarantee of safety, access, protection, or suitability. Entries need sources, review dates, jurisdictional context, and a way to report outdated information. Consulting offline resources should not require disclosing a live location to a central service.

---

## Threat model

GreenZone is primarily intended to reduce risks associated with:

- commercial surveillance;
- bulk data collection;
- indiscriminate monitoring;
- behavioural profiling;
- metadata analysis;
- location correlation;
- device fingerprinting;
- passive network observation;
- hostile networks;
- unexpected routing;
- unauthorised tunnels;
- application telemetry;
- spyware indicators;
- smart-device telemetry;
- device seizure;
- sensitive travel;
- source identification;
- cross-domain correlation.

The threat model includes adversaries ranging from commercial trackers and opportunistic attackers to highly capable organisations.

---

## State-capable adversaries

A sufficiently capable targeted adversary may possess:

- zero-day exploits;
- zero-click exploitation;
- kernel-level access;
- credential extraction;
- microphone/camera access;
- filesystem acquisition;
- plaintext capture;
- traffic correlation;
- commercial spyware;
- supply-chain intelligence;
- telecommunications visibility;
- provider cooperation;
- physical access.

GreenZone does **not** claim to make a person invisible to such an adversary.

If an attacker completely controls an endpoint, many conventional privacy controls can be defeated.

GreenZone instead seeks to:

- remove easy surveillance paths;
- reduce unnecessary metadata;
- compartmentalise information;
- increase attacker cost;
- expose unexpected state changes;
- create independently verifiable integrity evidence;
- and reduce the usefulness of mass correlation.

---

## MVT and endpoint compromise

Sophisticated spyware demonstrates an important principle:

```text
Why break the cipher
when plaintext can be stolen
before encryption
or after decryption?
```

GreenZone therefore treats endpoint integrity as equally important as encryption.

The strongest cipher in the world cannot protect plaintext displayed to a fully compromised operating system.

---

## Public review as a security principle

GreenZone assumes that adversaries can read the source code.

That is intentional.

A security feature whose protection collapses when its implementation becomes public is not suitable as a GreenZone foundation.

Secrets should exist in:

- keys;
- ephemeral session state;
- protected user material;
- local configuration where appropriate;

not in hidden algorithms.

---

## Build and supply-chain security

Compilers and build infrastructure are themselves part of the threat model.

GreenZone therefore intends to adopt:

- reproducible builds;
- signed source tags;
- signed release artifacts;
- software bills of materials;
- dependency pinning;
- static analysis;
- sanitizers;
- continuous fuzzing;
- compiler diversity;
- independent release builders;
- release provenance;
- automated dependency auditing;
- strict code review.

Where practical, the project may explore diverse compilation techniques inspired by research into the classic compiler-trust problem.

Independent tooling and builders should make build assumptions visible. Reproducibility and signatures establish specific properties of a build; they do not by themselves establish that the source, compiler, dependencies, or resulting software are safe.

---

## Signed binaries

Official GreenZone releases should be signed using the appropriate platform mechanisms.

Potential infrastructure includes:

- Windows code signing;
- macOS signing and notarisation;
- Apple platform signing;
- Android signing;
- Linux package signing;
- signed update metadata.

A valid digital signature links an artifact to the corresponding signing key, subject to correct verification and key trust.

It does **not** prove that software is harmless.

GreenZone will therefore treat signature validation as one evidence source rather than an absolute trust decision.

---

## Privacy by default

GreenZone must not become the surveillance system it was created to resist.

The project therefore follows several design principles.

### Local first

Sensitive analysis should happen locally whenever technically practical.

### Minimal telemetry

GreenZone should collect as little central telemetry as possible.

### No advertising model

GreenZone should never depend upon profiling or advertising users.

### No unnecessary accounts

A GreenZone account should not be required for functionality that can safely operate without one.

### No hidden cloud dependency

Security-critical functionality should continue to operate locally wherever possible.

### Explainable decisions

Users should be able to understand why GreenZone blocked, warned, isolated, or changed something.

### Fail safely

Security failures should not silently downgrade protection.

### Recoverability

Protection mechanisms must avoid unnecessarily destroying the user's own information.

### Human safety first

Technically correct behaviour can still create physical danger.

Physical safety takes priority over elegant engineering.

---

## Ethical boundaries

GreenZone exists to protect people.

It is not intended to:

- frame innocent third parties;
- fabricate incriminating evidence;
- compromise external systems;
- corrupt databases;
- impersonate other users;
- interfere with emergency services;
- jam communications;
- damage communications infrastructure;
- access systems without authorisation;
- facilitate stalking;
- facilitate harassment;
- conceal attacks on third parties;
- obstruct legitimate emergency response.

Privacy-preserving ambiguity must remain fundamentally different from harmful deception.

---

## Criminal misuse

Any strong privacy technology can be misused.

Encryption, operating systems, networks, cars, telephones, and ordinary web browsers can all be used by people committing crimes.

GreenZone therefore cannot rely upon an assumption that every user is benevolent.

The project's responsibility is to establish security boundaries that defend privacy without intentionally creating mechanisms designed to:

- fabricate evidence;
- implicate innocent people;
- attack investigators;
- interfere with infrastructure;
- or compromise third-party systems.

The fact that privacy can be abused does not eliminate its legitimate importance to journalists, lawyers, researchers, victims, ordinary citizens, and civil society.

---

## GreenZone and surveillance law

GreenZone is partly motivated by the expansion of automated surveillance capabilities in both democratic and authoritarian states.

European debates around communications monitoring, biometric surveillance, spyware, bulk metadata, law-enforcement access, and proposals often collectively discussed under terms such as **Chat Control** demonstrate a wider question:

> **How can societies investigate serious crime while preserving confidentiality, cybersecurity, source protection, professional secrecy, freedom of expression, and fundamental rights for people who are not suspected of crimes?**

GreenZone does not attempt to answer that political question for everyone.

It attempts to build technology that keeps meaningful privacy technically possible.

---

## Legal provenance is not legal advice

GreenZone Evidence Provenance may help establish facts relevant to:

- incident investigation;
- forensic reconstruction;
- professional secrecy;
- security-policy compliance;
- regulatory review;
- oversight;
- litigation.

It cannot determine whether evidence will be admissible or excluded.

That decision belongs to applicable law and the relevant legal institutions.

GreenZone does not provide legal advice.

---

## Roadmap

The roadmap is provisional.

### Phase 1 — Foundation

- C++23 core;
- threat profiles;
- architecture documentation;
- secure configuration;
- cryptographic abstraction;
- protected storage;
- build system;
- CI;
- signed releases;
- threat model;
- legal-safety model.

### Phase 2 — Endpoint security

- Windows;
- Linux;
- macOS;
- Android;
- iOS;
- process/network observation;
- protected contexts;
- secure presentation features;
- key-management integration.

### Phase 3 — GreenZone Gateway

- network segmentation;
- path-integrity monitoring;
- DNS visibility;
- route monitoring;
- tunnel/transition policy;
- process-to-flow correlation;
- device identity;
- fail-closed policy;
- IoT isolation;
- organisational profiles.

### Phase 4 — Mobile and hostile-environment awareness

- network-change detection;
- cellular/environment indicators where platform APIs permit;
- travel mode;
- border mode;
- device-separation events;
- wearable integration;
- geofenced policy;
- encrypted backup, temporary local-data protection, and tested restoration;
- explicit emergency actions and opt-in alerts;
- trusted contacts.

### Phase 5 — Consensual mobile forensics

- MVT integration;
- Android and iOS forensic workflows;
- IOC management;
- protected forensic output;
- incident timelines;
- expert-mode interpretation.

### Phase 6 — Evidence provenance

- protected-context manifests;
- cryptographic commitments;
- tamper-evident event histories;
- external timestamp witnesses;
- exportable forensic reports.

### Phase 7 — Correlation resistance

- metadata minimisation;
- independent contexts;
- identifier management;
- traffic normalisation;
- privacy-preserving cover traffic;
- cross-domain correlation research.

### Phase 8 — Offline Wiki

- travel OPSEC;
- mobile security;
- border guidance;
- biometric-surveillance awareness;
- spyware guidance;
- journalism;
- legal confidentiality;
- physical security;
- jurisdiction-specific policy packs.

### Phase 9 — Ecosystem

- APIs;
- third-party integrations;
- research modules;
- auditing tools;
- institutional deployments;
- community threat intelligence.

---

## Research project as much as software

GreenZone intersects with:

- cybersecurity;
- cryptography;
- networking;
- telecommunications;
- operating systems;
- digital forensics;
- information theory;
- machine learning;
- intelligence analysis;
- privacy engineering;
- law;
- journalism;
- professional secrecy;
- human-computer interaction;
- ethics.

Some of the most important GreenZone questions do not yet have clean engineering answers.

One central research question is:

> **What does meaningful personal privacy look like when surveillance itself becomes distributed, probabilistic, biometric, and algorithmic?**

---

## Contributing

GreenZone welcomes responsible contributions from:

- software developers;
- security researchers;
- cryptographers;
- network engineers;
- mobile-security researchers;
- lawyers;
- journalists;
- academics;
- privacy engineers;
- digital-forensics specialists;
- designers;
- accessibility specialists;
- telecommunications researchers;
- human-rights organisations.

Useful contributions include:

- code review;
- threat-model analysis;
- cryptographic review;
- protocol design;
- fuzzing;
- reproducible builds;
- platform security;
- legal research;
- jurisdictional research;
- forensic methodology;
- documentation;
- accessibility;
- false-positive analysis;
- adversarial review.

Security-sensitive contributions should be handled responsibly.

A formal vulnerability-disclosure policy and private reporting route are planned. Once available, use the repository's published security policy for sensitive findings; public issues should not contain private user data, device extractions, credentials, or confidential forensic evidence.

---

## Contribution model

Because GreenZone will include security-critical code, inclusion in the upstream repository requires review.

Contributors are encouraged to:

1. fork the repository;
2. develop changes independently;
3. document the associated threat model;
4. include appropriate tests or validation for the change;
5. submit changes for review.

Security claims should be treated as hypotheses until they have been reviewed and tested.

---

## Licensing

### Current terms

The repository currently carries the **MIT License**. See [LICENSE](LICENSE) for the complete terms.

Copyright © 2026 Iman Mirbioki.

GreenZone is intended as a non-commercial, public-interest project. That project policy does **not** restrict permissions already granted by MIT, which permits commercial use, distribution, and sale subject to its terms. This README does not adopt a replacement license or withdraw existing grants.

### License review

A future licensing model is under review. Two different goals must be distinguished:

- **Keeping improvements open:** a copyleft license such as [GNU AGPL-3.0](https://www.gnu.org/licenses/agpl-3.0.html) is a candidate. It allows commercial use and includes source-sharing obligations, including for users interacting over a network with modified versions covered by its network clause.
- **Prohibiting downstream commercial use:** a license such as [PolyForm Noncommercial 1.0.0](https://polyformproject.org/licenses/noncommercial/1.0.0) is a candidate for review. A commercial-use prohibition would make the affected code source-available rather than open source under the [Open Source Definition](https://opensource.org/osd).

Neither candidate has been adopted. Any change must define intended professional uses, respect contributor rights and existing MIT grants, and check dependency compatibility. A future restriction cannot simply retract permissions already granted for earlier MIT-licensed copies.

### Third-party components and documentation

GreenZone's license does not replace third-party terms. In particular, the planned [MVT integration](#mobile-verification-toolkit-integration) must preserve MVT's license and requirements. No automatic compatibility between MVT and AGPL, PolyForm, or any other proposed GreenZone license is claimed.

Reused wiki text, indicators, datasets, images, and other materials require appropriate permissions and attribution. The documentation licensing model will be specified before distributing third-party content packs.

---

## Final thought

For most of computing history, security engineering concentrated on keeping secrets secret.

That remains essential.

But modern surveillance systems increasingly do not need to know exactly what happened.

They need enough independent observations to calculate what probably happened.

And modern attackers often do not need to break the encryption.

They attack everything around it.

GreenZone is an attempt to build tools for that world.

**Encrypt the information.  
Protect the endpoint.  
Protect the path.  
Question the inference.  
Preserve the evidence.**

Welcome to GreenZone.
