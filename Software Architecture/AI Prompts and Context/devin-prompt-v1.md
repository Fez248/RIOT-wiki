***

### 2. Updated Devin Mega-Prompt

*This prompt now explicitly instructs Devin to use the `docker` Python library to orchestrate an ephemeral sandbox for Module 2.*

```text
You are a Senior Backend Engineer and Embedded Cybersecurity Expert. Your task is to implement the complete `RIOT-backend` repository, an automated IoT vulnerability tracking, triage, and remediation platform. 

The system ingests untrusted firmware images across multiple ecosystems. To prevent RCE, the extraction pipeline must run inside an ephemeral, network-isolated Docker container. The pipeline orchestrates Binwalk to extract the filesystem, runs both Syft and cve-bin-tool to generate separate SBOMs, merges them using cyclonedx-cli, runs Grype vulnerability scans via stdin on the host, and manages a PostgreSQL knowledge base. It features a Vulnerability Triage Engine with Reachability Analysis, EPSS scores, and an API to generate VEX compliance documents.

Please implement the full project step-by-step. Provide complete, production-ready Python code with no placeholders. 

### 1. Technology Stack
* Backend: Python 3.10+
* API Framework: FastAPI
* Database: PostgreSQL (using psycopg2 or SQLAlchemy)
* Containerization: Docker SDK for Python (`docker`)
* Subprocess Tools (Host): Grype
* Subprocess Tools (Sandbox): Binwalk, Syft, cve-bin-tool, cyclonedx-cli

### 2. Database Schema (Source of Truth)
[Insert the exact same SQL schema from the previous prompt here]

### 3. Required Modules to Implement

**Module 1: Database Setup (`database.py`)**
* Implement a connection pool to PostgreSQL.
* Function to initialize the schema.

**Module 2: Ephemeral Sandbox & Ingestion Engine (`parser.py` & `sandbox/Dockerfile`)**
* Create a `Dockerfile` that installs `binwalk`, `syft`, `cve-bin-tool`, and `cyclonedx-cli`.
* Use the Python `docker` library to dynamically spin up this container.
* Mount the untrusted `.img` into the container as read-only.
* Execute a shell script inside the container that runs Binwalk, runs Syft and cve-bin-tool, and merges them with cyclonedx-cli.
* Retrieve the `merged_sbom.json` from the container into the host backend, then force-remove (`--rm`) the container.
* Extract basic metadata from the merged SBOM to populate the `components` table.
* Implement the Reachability Analyzer: scan the safe SBOM or explicitly extracted config files for `systemd` or `init.d` scripts to flag `is_network_exposed = TRUE`.

**Module 3: Continuous Monitoring Engine (`cve_monitor.py`)**
* Daily cron logic to run `grype db update`.
* Feed the merged `firmware_images.raw_sbom` into Grype via stdin (`grype sbom:- -o json`).
* UPSERT results into `vulnerabilities` and `component_vulnerabilities`.
* Auto-triage logic: If `is_network_exposed` is FALSE, automatically set `vex_status = 'not_affected'` and `vex_justification = 'vulnerable_code_not_in_execute_path'`.

**Module 4: EPSS Threat Intel Integration (`epss_updater.py`)**
* Script to fetch the latest EPSS CSV data from FIRST.org API.
* Parse the CSV and batch update the `epss_score` column.

**Module 5: VEX Generator API (`vex_api.py`)**
* FastAPI endpoint: `GET /api/v1/vex/{image_id}`.
* Query `component_vulnerabilities` where `vex_status` != 'affected'.
* Return a JSON structure representing a VEX document mapping the CVEs and justifications.

### 4. Execution Constraints
* Output the project structure as a tree first.
* Use your sandbox environment to build the Dockerfile, spin up local PostgreSQL, and test the pipeline with dummy data. If a tool fails to install in the Docker build after 3 attempts, mock the script output and proceed.

"Here is the complete architectural specification for the RIOT backend. please download the official IoTGoat release image directly inside your sandbox environment using `wget`. You can fetch the latest release image from the official GitHub repository (`[https://github.com/OWASP/IoTGoat](https://github.com/OWASP/IoTGoat)`), extract it if necessary, and use it to test your ingestion and sandbox extraction pipeline."Please implement the entire repository as specified, and then write an integration test script that passes this iimage file through your newly created Docker sandbox and ingestion pipeline to verify it successfully generates the master SBOM and populates PostgreSQL."
