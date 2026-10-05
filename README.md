# GreenZone

### Surveillance resilience, digital self-defence, and personal safety for an increasingly monitored world.

> **GreenZone is an open-source privacy and personal-safety platform designed to help ordinary people, journalists, activists, researchers, and other at-risk users preserve confidentiality, situational awareness, and control over their digital lives.**

GreenZone approaches privacy from a simple premise:

**Encryption protects information. It does not necessarily protect the person, their metadata, their movements, their relationships, or the inferences made about them.**

Modern surveillance systems increasingly combine many weak signals rather than relying on a single source of intelligence. Location history, cellular metadata, network identifiers, behavioural patterns, device telemetry, communications metadata, public records, social graphs, and algorithmic inference can collectively reveal considerably more than any individual data source.

GreenZone therefore explores a broader model of digital self-defence.

Instead of merely attempting to hide information, GreenZone aims to reduce the reliability of unnecessary surveillance and profiling while providing practical safety tools when a user enters a potentially hostile environment.

---

## Why GreenZone?

Privacy tools traditionally focus on protecting a particular layer:

- encrypted messaging protects message content;
- VPNs protect parts of network traffic;
- password managers protect credentials;
- secure storage protects files;
- anonymity networks obscure network origin;
- emergency applications provide location-based safety assistance.

These are important tools, but surveillance rarely operates at only one layer.

A sufficiently capable observer may correlate information from multiple independent systems. Even where individual observations are incomplete, statistical correlation can produce remarkably detailed profiles.

GreenZone is intended to operate across several of these layers simultaneously.

The project combines three broad ideas:

**Protection** — keeping sensitive information confidential.

**Awareness** — informing users when their environment or device behaviour changes in ways that may indicate increased surveillance risk.

**Uncertainty** — reducing the confidence with which unnecessary automated surveillance can convert observations into reliable conclusions about an individual.

The objective is not invisibility.

Perfect invisibility is generally unrealistic.

The objective is to make legitimate privacy considerably easier while making indiscriminate surveillance, profiling, and automated inference less reliable.

---

# Core concept

GreenZone is envisioned as a modular surveillance-resilience platform rather than a single-purpose privacy application.

Depending on platform capabilities and the user's threat model, GreenZone may eventually combine:

- encrypted local storage and secure data containers;
- protected remote backup and emergency data transfer;
- location-based risk zones and geofencing;
- detection of unusual cellular or network conditions;
- warnings associated with potentially suspicious base stations or network changes;
- emergency and panic signalling;
- trusted-contact mechanisms;
- border and jurisdiction awareness;
- secure temporary removal of particularly sensitive information;
- later restoration of protected information from trusted storage;
- device-separation and seizure indicators using paired Bluetooth or wearable devices;
- protection against unnecessary metadata correlation;
- surveillance-resilient communications;
- privacy-preserving traffic and behavioural obfuscation;
- safety information for journalists and other people operating in hostile environments.

Not every GreenZone installation will require every component.

The long-term goal is for users to select an appropriate **threat profile** rather than manually configure dozens of unrelated security technologies.

---

# Surveillance resilience

GreenZone distinguishes between **secrecy** and **observability**.

Encryption can make the contents of a message unreadable while still leaving observable facts such as:

`device A → service B → time C → location D`

Repeated observations can create patterns.

Patterns create correlations.

Correlations create assumptions.

At sufficient scale, assumptions become machine-generated intelligence.

GreenZone therefore investigates ways of defending not only the contents of communications but also the **inferences produced from surrounding signals**.

This includes two experimental concepts currently referred to within the project as **data poisoning** and **dual false SIGINT**.

---

## Data poisoning

In GreenZone terminology, *data poisoning* does **not** mean compromising external databases, modifying evidence, attacking machine-learning systems, or inserting information into systems belonging to other people.

It refers to defensive techniques intended to prevent passive mass-surveillance and profiling systems from treating every observable digital signal generated around a user as equally meaningful.

The underlying information-theoretical idea is straightforward:

> A surveillance system becomes less useful when the signal-to-noise ratio decreases.

Where appropriate and lawful, GreenZone may therefore introduce privacy-preserving ambiguity into telemetry or behavioural patterns that would otherwise permit unnecessary automated profiling.

The design principle is that such mechanisms should remain **local, reversible, non-destructive, and non-attributable to innocent third parties**.

GreenZone must never manufacture evidence against another person.

---

## Dual false SIGINT

GreenZone also explores a concept provisionally called **dual false SIGINT**.

Intelligence systems often gain confidence when independent sources agree.

For example:

```text
Source A ─────┐
              ├──► Correlation ───► High-confidence inference
Source B ─────┘
```

But independent sources that produce incompatible interpretations can reduce the confidence of an automated conclusion:

```text
Source A ─────► Observation X ───┐
                                ├──► Ambiguous / low-confidence inference
Source B ─────► Observation Y ───┘
```

GreenZone investigates whether deliberately maintaining uncertainty across observable signals can provide meaningful protection against indiscriminate automated surveillance.

The purpose is **not to defeat targeted investigations, impersonate other people, interfere with communications infrastructure, or fabricate evidence**.

It is to examine how individuals can preserve a reasonable sphere of privacy when automated systems attempt to infer activities from metadata that the user never intentionally disclosed.

The detailed implementation and safety boundaries of these techniques remain an active area of development.

---

# The Green Zone

The project's name comes from another part of the original concept.

GreenZone should be capable of helping a user answer a very immediate question:

**Where is the nearest place where I am safer?**

A Green Zone may eventually represent a location, jurisdiction, network, organisation, embassy, newsroom, trusted contact, legal resource, or other context associated with reduced risk.

For a journalist crossing a border, an activist attending a demonstration, a researcher travelling through a hostile jurisdiction, or an ordinary citizen suddenly confronted by an unsafe situation, digital security and physical safety can become the same problem.

GreenZone is therefore intended to combine **cybersecurity, privacy, and situational awareness** rather than treating them as unrelated disciplines.

---

# High-risk environments

Some users face threats that are fundamentally different from ordinary consumer cybersecurity.

A journalist carrying confidential source material through a border checkpoint may need to protect information without permanently destroying it.

A person travelling through an authoritarian jurisdiction may need to know when network behaviour suddenly changes.

An activist may need a trusted person to know that their phone has unexpectedly become separated from them.

A user may need sensitive information moved to protected storage before entering a particular geographical area and restored after leaving it.

GreenZone is being designed with such scenarios in mind.

Potential future mechanisms include encrypted streaming of protected data to remote storage, temporary removal of sensitive local information, remote restoration, geographical policy triggers, panic events, and paired-device monitoring.

These features require considerable care. False alarms, data loss, unsafe automation, and incorrect assumptions can themselves endanger users.

For that reason, safety-critical GreenZone components should favour transparent behaviour, explicit user control, recoverability, and extensive testing.

---

# Journalists and source protection

Journalism is one of the project's original use cases.

A confidential source may be compromised without anyone reading the journalist's messages.

Location correlation can show that two phones were repeatedly near one another.

Network metadata can reveal when communication occurred.

Cloud telemetry can reveal device activity.

Public information can fill remaining gaps.

Modern source protection must therefore consider **correlation risk**, not merely message encryption.

GreenZone aims to eventually provide a framework in which journalists can understand and reduce those risks without becoming telecommunications engineers or intelligence specialists.

This project is not exclusively for journalists, however.

Privacy is a civil right, not an occupational privilege.

---

# GreenZone and mass surveillance

GreenZone is partly motivated by the continuing expansion of automated surveillance capabilities in democratic as well as authoritarian states.

European debates surrounding communications monitoring, including successive proposals commonly described as **Chat Control**, illustrate a broader technical and political question:

> How can societies combat serious crime while preserving the confidentiality, security, and fundamental rights of hundreds of millions of people who are not suspected of any crime?

Reasonable people can disagree about where legislation should draw that boundary.

GreenZone approaches the problem technologically:

**Security mechanisms should not require citizens to surrender general-purpose control over their private communications and personal data.**

Strong child protection, effective criminal investigations, cybersecurity, freedom of expression, source protection, and communications privacy are not inherently mutually exclusive goals.

GreenZone is intended to contribute tools and research toward architectures in which those interests do not have to be treated as zero-sum.

---

# Threat model

GreenZone is primarily intended to reduce risks associated with:

- bulk collection and indiscriminate surveillance;
- automated metadata analysis;
- behavioural profiling;
- location correlation;
- passive network observation;
- hostile or deceptive network environments;
- device seizure or unexpected device separation;
- exposure of sensitive information while travelling;
- commercial surveillance and excessive tracking;
- correlation of otherwise unrelated digital identifiers.

GreenZone does **not** promise anonymity against every adversary.

A sufficiently capable targeted adversary with physical access to a device, endpoint compromise, zero-day exploits, extensive infrastructure visibility, or coercive powers may defeat many conventional security controls.

Any claim that an application can make a user completely invisible to such an adversary would be irresponsible.

GreenZone instead seeks to make surveillance **harder, less automatic, less reliable, more expensive, and more dependent on genuinely targeted investigative work**.

---

# Ethical boundaries

GreenZone exists to defend people, not attack them.

The project should never intentionally provide mechanisms whose purpose is to:

- frame or implicate innocent third parties;
- plant fabricated evidence;
- compromise external surveillance systems;
- interfere with emergency services;
- damage communications infrastructure;
- impersonate another person;
- gain unauthorised access to networks or devices;
- conceal attacks against other systems;
- facilitate stalking, harassment, exploitation, or violence.

Privacy-preserving ambiguity must remain fundamentally different from deception that causes harm to someone else.

That distinction is central to GreenZone.

---

# Design principles

### Privacy by default

A privacy system should not itself become a surveillance system.

Collection of GreenZone telemetry should therefore be minimised whenever technically possible.

### Local first

Sensitive decisions should preferably occur on the user's own device rather than requiring centralised processing.

### No unnecessary trust

GreenZone should assume that infrastructure can fail, services can disappear, networks can become hostile, and credentials can eventually be compromised.

### Open source

Security should not depend on secrecy surrounding the implementation.

GreenZone's code should be inspectable, auditable, criticised, tested, forked, and improved.

### Explainability

When GreenZone takes an important action or issues a warning, users should be able to understand why.

### Recoverability

Security software that accidentally destroys the user's own information is not secure.

Emergency protection mechanisms should therefore be designed with recovery in mind.

### Modular architecture

Different users face different adversaries.

GreenZone should allow protection mechanisms to be combined according to threat model rather than assuming that everyone faces the same risks.

### Human safety first

A technically correct action can still be dangerous in the real world.

Physical safety takes priority over elegant cryptography.

---

# Project status

**GreenZone is currently in early development.**

The architecture, terminology, threat model, interfaces, and individual modules are expected to change substantially.

Initial releases should be considered experimental.

Do not depend on GreenZone as the sole protection for life-critical communications, confidential sources, legal evidence, or irreplaceable information until the relevant components have undergone appropriate review and testing.

The repository will gradually gain technical documentation describing individual modules, supported platforms, threat models, protocol designs, testing methodology, and research behind experimental surveillance-resilience techniques.

---

# Roadmap

The project is expected to evolve in stages:

**Phase 1 — Foundation**

Core architecture, configuration, threat profiles, cryptographic storage, documentation, and platform abstraction.

**Phase 2 — Situational awareness**

Network-change monitoring, location risk zones, geofencing, suspicious-environment warnings, and emergency functions.

**Phase 3 — Protected mobility**

Secure remote storage, temporary protection of sensitive local information, controlled restoration, border/travel modes, and trusted-device integration.

**Phase 4 — Surveillance resilience**

Metadata protection, correlation resistance, privacy-preserving obfuscation, experimental data-poisoning mechanisms, and research into contradictory-signal techniques.

**Phase 5 — Ecosystem**

Auditing tools, third-party modules, research integrations, additional operating systems, APIs, and community-maintained threat intelligence.

This roadmap is provisional and will evolve with the project.

---

# Research project as much as software

Some GreenZone components involve problems for which there are no clean engineering answers.

The project touches cryptography, networking, mobile security, information theory, telecommunications, machine learning, privacy engineering, digital forensics, journalism, intelligence analysis, human-computer interaction, law, and ethics.

That makes GreenZone partly an application and partly an experiment:

**What does meaningful personal privacy look like when surveillance itself is distributed, probabilistic, and algorithmic?**

Contributions challenging GreenZone's assumptions are therefore just as valuable as contributions implementing them.

---

# Contributing

GreenZone welcomes responsible contributions from developers, security researchers, privacy engineers, journalists, lawyers, academics, designers, telecommunications specialists, and anyone interested in improving digital autonomy.

Particularly useful contributions include:

- threat-model analysis;
- cryptographic review;
- networking research;
- mobile-platform security;
- accessibility;
- documentation;
- legal and jurisdictional research;
- reproducible testing;
- false-positive analysis;
- privacy-preserving architecture;
- adversarial review of proposed features.

Please treat security-sensitive design discussions responsibly.

If you discover a vulnerability that could place users at risk, avoid publishing exploit details until a responsible disclosure process is available.

---

# A note on legality

Privacy technology is legal in many jurisdictions, but particular functionality and particular uses may not be.

Telecommunications, cryptography, radio systems, location information, data protection, border searches, obstruction laws, and surveillance regulation vary between jurisdictions.

Users are responsible for understanding the laws applicable to them.

GreenZone does not provide legal advice.

The project nevertheless begins from a clear principle:

> **The existence of surveillance technology does not eliminate the individual's right to privacy.**

---

# License

GreenZone is released under the **MIT License**.

Copyright © 2026 Iman Mirbioki.

See `LICENSE` for the complete license text.

---

# Final thought

For most of computing history, security engineering has concentrated on keeping secrets secret.

That problem remains important.

But the next privacy problem is different.

Machines increasingly do not need to know exactly what happened.

They only need enough correlated observations to calculate what *probably* happened.

GreenZone is an attempt to build tools for that world.

**Encrypt the information.  
Protect the person.  
Question the inference.**

Welcome to GreenZone.
