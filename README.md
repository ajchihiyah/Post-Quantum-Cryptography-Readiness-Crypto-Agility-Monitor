# Post-Quantum-Cryptography-Readiness-Crypto-Agility-Monitor
A SOC analyst dashboard designed specifically for German banking compliance.

Post-Quantum Cryptography Readiness & Crypto-Agility Monitor for German Banks
The Problem: BaFin's 2026 Risks in Focus explicitly flags quantum computing as an emerging threat, warning of "harvest now, decrypt later" attacks on current encryption. The European Supervisory Authorities have added post-quantum cryptography (PQC) to their 2026 work programs. German banks hold decades of sensitive financial data; adversaries are already harvesting encrypted data to decrypt once quantum computers mature. Yet most institutions have no visibility into which systems, APIs, and data stores use vulnerable algorithms, nor a migration roadmap. 
Project Overview: Build a SOC analyst HTML frontend that:
 
Scans the bank's entire IT estate (on-prem, cloud, APIs, databases, file shares) to inventory cryptographic algorithms in use (RSA, ECC, AES-128, SHA-1, etc.)
 
Maps each asset against NIST PQC migration timelines and BSI TR-02102-1 recommendations
 
Prioritizes migration by risk: "This database contains 10 years of customer PII encrypted with RSA-2048 → PQC migration critical"
 
Monitors for new deployments using non-quantum-resistant algorithms (policy violation alerts)
 
Tracks crypto-agility progress: which systems can swap algorithms without code changes vs. hard-coded legacy systems
Frontend Features: Cryptographic inventory tree with algorithm badges, quantum vulnerability heatmap by business unit, PQC migration timeline with dependency graph, policy violation alert feed, and an executive "Quantum Readiness Score" for board reporting.
Why It Matters: This is a forward-looking, differentiated project. While every student builds phishing dashboards, very few tackle emerging regulatory frontiers. BaFin has announced it will issue supervisory expectations for PQC in 2026. German banks (especially those with long-term data retention like insurers and pension funds) are beginning to budget for this. A SOC analyst who can speak to both threat detection and cryptographic risk is rare and highly employable in Germany's conservative, compliance-heavy financial sector.
