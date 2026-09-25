<img width="1910" height="939" alt="image" src="https://github.com/user-attachments/assets/e9edcc10-ed5c-4083-8a86-d8cd2be5e076" />

# Post-Quantum Cryptography Readiness & Crypto-Agility Monitor

## Overview

A fully functional, interactive SOC analyst dashboard designed for German banks preparing for BaFin's 2026 Post-Quantum Cryptography (PQC) supervisory expectations. The monitor provides real-time visibility into cryptographic vulnerabilities across the entire IT estate, tracks migration progress against NIST and BSI TR-02102-1 timelines, and delivers board-ready quantum readiness scores.

---

## Problem Statement

BaFin's 2026 Risks in Focus explicitly flags quantum computing as an emerging threat, warning of **"harvest now, decrypt later"** attacks on current encryption. The European Supervisory Authorities have added PQC to their 2026 work programs. German banks hold decades of sensitive financial data; adversaries are already harvesting encrypted data to decrypt once quantum computers mature. Most institutions have no visibility into which systems, APIs, and data stores use vulnerable algorithms, nor a migration roadmap.

---

## Features

### 1. Executive Quantum Readiness Score
- **Animated ring gauge** (0-100) with gradient color coding
- **Four sub-dimensions** tracked:
  - Inventory Coverage (68%)
  - Crypto-Agility (23%)
  - PQC Migration Progress (18%)
  - Staff Training & Awareness (52%)
- **BaFin supervisory expectation banner** with critical system count
- Click KPI cards for detailed breakdown modals

### 2. Quantum Vulnerability Heatmap
- **16 business units** color-coded by risk level (Critical/High/Medium/Low)
- **Hover tooltips** show vulnerable asset counts, percentages, and descriptions
- **Click-to-drill** opens detailed modal with algorithm-specific breakdowns
- Includes: Retail Banking, Corporate Banking, Insurance, Pension Funds, Payments, etc.

### 3. Cryptographic Inventory
- **Tabbed view**: Assets, APIs, Databases
- **Live search** filters by system name, algorithm, PII type, or owner
- **Algorithm badge chips** (RSA-2048, ECC P-256, AES-128, SHA-1, TLS 1.2, ML-KEM) — click to filter
- **Expandable detail panel** per system showing:
  - System metadata (ID, environment, owner, last scan)
  - PII exposure level
  - Crypto-agility status
  - Migration status
- **Action buttons**: Mark for Migration, View Dependencies, Create JIRA Ticket

### 4. PQC Migration Timeline
- **NIST FIPS 203 + BSI TR-02102-1 aligned** roadmap from Q1 2026 to 2029
- **8 milestones** with status indicators (Done/Active/Pending)
- **Progress bars** per milestone
- **Dependency tracking** (e.g., "Vendor Support", "T24 v11+")
- Click to update progress and view detailed migration plans

### 5. Policy Violation Alert Feed
- **Live SOC feed** with severity-coded alerts (Critical/Warning/Info)
- **Working action buttons**: Investigate, Review, Dismiss, Resolve
- **Incident modals** with recommended actions and ticket creation
- **Auto-injection** of new random alerts every ~15 seconds
- **Animated resolve** transitions with real-time count updates

### 6. Crypto-Agility Matrix
- **Sortable table** by System, Agile status, or Migration Effort
- **12 systems** assessed for algorithm-swap capability
- **Color-coded effort levels**: Low (green), Medium (amber), High (red)
- **Click rows** for detailed migration strategy modals
- **Dynamic summary stats**: Agile count, Legacy count, Agility rate

---

## Technical Details

- **File**: `pqc_readiness_monitor.html` (67 KB, single file)
- **Dependencies**: None — fully self-contained HTML/CSS/JS
- **Browser Support**: Chrome, Firefox, Safari, Edge (modern versions)
- **Responsive**: Desktop-first with breakpoints at 1200px and 768px
- **No external libraries**: Pure vanilla JavaScript, no CDN calls

---

## Data Model

### Business Units (16)
| Unit | Total Assets | Vulnerable | Risk Level |
|------|-------------|------------|------------|
| Retail Banking | 420 | 312 | Critical |
| Corporate Banking | 280 | 198 | Critical |
| Insurance | 340 | 210 | Critical |
| Customer Portal | 220 | 156 | Critical |
| Pension Funds | 280 | 198 | Critical |
| ... | ... | ... | ... |

### Inventory Items (20 across Assets/APIs/Databases)
Each item includes: ID, name, type, algorithms[], risk level, crypto-agility flag, PII exposure, owner, environment, last scan date, migration status.

### Algorithms Tracked
- **RSA-2048** (vulnerable to Shor's algorithm)
- **ECC P-256** (vulnerable to Shor's algorithm)
- **AES-128** (Grover's algorithm reduces effective security to 64-bit)
- **SHA-1** (broken, deprecated)
- **TLS 1.2** (needs upgrade to 1.3)
- **ML-KEM** (NIST-approved PQC key encapsulation)

---

## Use Cases

### For SOC Analysts
- Monitor real-time policy violations and new vulnerable deployments
- Investigate incidents with recommended action workflows
- Track alert resolution metrics

### For CISOs / Risk Officers
- Present board-ready quantum readiness scores
- Prioritize migration by business unit risk heatmap
- Demonstrate compliance progress to BaFin

### For Architects / Engineers
- Identify crypto-agile vs. hard-coded legacy systems
- Plan migration sprints with dependency-aware timelines
- Assess effort levels for algorithm swaps

### For Compliance Teams
- Map systems against BSI TR-02102-1 recommendations
- Track BaFin 2026 supervisory expectation readiness
- Generate audit reports from inventory data

---

## Regulatory Context

| Authority | Document | Key Requirement |
|-----------|----------|-----------------|
| **BaFin** | Risks in Focus 2026 | PQC flagged as emerging threat; supervisory expectations Q4 2026 |
| **ESAs** | 2026 Work Program | PQC added to joint supervisory priorities |
| **NIST** | FIPS 203/204/205 | ML-KEM, ML-DSA, SLH-DSA standards finalized |
| **BSI** | TR-02102-1 | German cryptographic requirements; TLS 1.3 minimum |

---

## Installation

1. Download `pqc_readiness_monitor.html`
2. Open in any modern web browser (double-click or drag to browser)
3. No server, build step, or internet connection required

---

## Customization

To adapt for your bank:

1. **Edit `businessUnits` array** in the `<script>` section to match your org structure
2. **Edit `inventoryData` objects** to reflect your actual systems
3. **Update `timelineData`** to match your migration roadmap milestones
4. **Modify CSS variables** in `:root` for branding colors
5. **Add webhook URLs** in `createTicket()` and `markForMigration()` for real integrations

---

## Keyboard Shortcuts

| Key | Action |
|-----|--------|
| `Esc` | Close any open modal |
| `Ctrl+F` | Focus inventory search box |
| `1-3` | Switch inventory tabs (Assets/APIs/Databases) |

---

## Architecture Notes

The dashboard uses a **state-driven rendering pattern**:
- All data lives in JavaScript arrays (`businessUnits`, `inventoryData`, `alertsData`, etc.)
- Render functions regenerate DOM from state on every interaction
- No framework dependencies — pure DOM manipulation for zero overhead
- Modal system is reusable across all panels
- Live updates via `setInterval` with randomized alert injection

---

## Future Enhancements

- [ ] Connect to real CMDB/API for live asset inventory
- [ ] Integrate with JIRA/ServiceNow for ticket creation
- [ ] Add PDF export for board reports
- [ ] Implement WebSocket feed for real-time alert streaming
- [ ] Add NIST PQC algorithm performance benchmarking charts
- [ ] Multi-bank federation view for group-level compliance

---

## License

Built for educational and portfolio demonstration purposes. Adapt freely for your institution's PQC readiness program.

---

*Built for the German banking SOC analyst who needs to speak both threat detection and cryptographic risk.*
