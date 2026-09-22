Hello! I am continuing a project to build an automated IoT vulnerability tracking, triage, and remediation platform called RIOT, targeted at small and mid-sized hardware and IoT companies facing the EU Cyber Resilience Act (CRA) mandates. 

To bring you up to speed, here is the core context of our architecture and business model:

### 1. The Value Proposition & GTM Strategy
* **The Problem:** Small/mid-sized IoT/hardware companies lack security teams and cannot afford massive consultants. With the EU CRA enforced, they need to track, triage, and remediate vulnerabilities without slowing down their builds.
* **The Differentiator:** Traditional scanners dump 500+ uncontextualized alerts (including dead code and false positives) on developers. We solve the "reachability problem" and scanner noise.
* **Pricing Model:** Hybrid Audit + Retainer. Phase 1 Audit & Triage (€2,500–€3,500 one-time) and Phase 2 Continuous Risk Intelligence (€1,200–€1,800/month, which includes up to 3 hours of hands-on developer remediation guidance).

### 2. The Technical Architecture & Pipeline
* **Multi-Ecosystem Support:** Handles Yocto, Buildroot, custom self-compiled Linux distributions, and RTOS environments.
* **The Ephemeral Sandbox (Security):** Client firmware images (.img) are untrusted input. The FastAPI backend spins up a network-isolated, ephemeral Docker container, mounts the image read-only, and destroys it immediately post-extraction to prevent RCE.
* **Ingestion & Merging:** Inside the sandbox, `Binwalk` extracts the rootfs. Both `Syft` and `cve-bin-tool` generate separate SBOMs, which are then merged into a single master SBOM using `cyclonedx-cli`.
* **Vulnerability Scanning & Triage:** The master SBOM is scanned via stdin by `Grype` on the host. 
* **Advanced Intelligence:** 
  - **EPSS (Exploit Prediction Scoring System):** Daily cron job updates CVE exploitability probabilities from FIRST.org.
  - **Reachability Analysis:** Maps `systemd` services and configurations to flag whether a component is network-exposed (`is_network_exposed = TRUE`).
  - **VEX Automation:** Automatically flags unreachable/dead-code CVEs as `vex_status = 'not_affected'` and generates VEX compliance documents for auditors.
* **Database Schema:** PostgreSQL utilizing UUIDs, JSONB for raw SBOM storage, a `components` table with build context (`origin_context`, `recipe_or_module`), a `vulnerabilities` table with `epss_score`, `component_vulnerabilities` tracking VEX states and network exposure, and a `remediations` knowledge base table storing reusable patch files (`BYTEA`) and steps.

We are ready to continue developing, writing code, or refining our strategy. Let me know how you can help!
