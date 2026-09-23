This file contains all the necessary steps to certify a product as CRA compliant.

# 1. Product Classification & Assessment Pathway Definition

The first step is determining the regulatory classification of the product with digital elements (PDE), as this dictates the entire compliance process.

1. Determine the Product Class: Categorize the product as Default, Important (Class I or Class II under Annex III), or Critical (Annex IV).

2. Select the Conformity Assessment Module (Annex VIII):
	- For Default products, select Module A (Internal Control / Self-Assessment).
	- For Important Class I products, select Module A if fully applying harmonized standards; otherwise, select Module B+C or Module H.
	- For Important Class II products, select Module B+C (EU-type examination) or Module H (Full quality assurance), or an applicable European cybersecurity certification.
	- For Critical products, select the mandated European cybersecurity certification scheme, falling back to Module B+C or Module H if unavailable.
# 2. Cybersecurity Risk Assessment & Secure Design (Annex I, Part I)

Manufacturers must ensure the product is designed, developed, and produced to ensure an appropriate level of cybersecurity based on the risks.
1. Conduct a Cybersecurity Risk Assessment: Document the specific threats, vulnerabilities, and required mitigation measures for the product's intended use and foreseeable misuse.
2. Implement Security by Default: Ensure the product is delivered with a secure default configuration, including mechanisms to turn off automatic updates if required.
3. Ensure Core Security Properties: Design the system to protect data at rest and in transit, ensure data minimization, and provide mechanisms for secure authentication, access control, and memory safety.
4. Define the Support Period: Determine and clearly document the specific support timeframe during which the product will receive vulnerability handling and security updates.
# 3. Development Pipelines, Testing, & Supply Chain Security

Establish the technical infrastructure required to monitor dependencies and validate the product's security prior to release.
- Implement Automated Security Scanning: Integrate Static Application Security Testing (SAST) and Dynamic Application Security Testing (DAST) into the CI/CD pipeline.
- Conduct Vulnerability Assessments & Penetration Testing: Perform rigorous pre-release security testing and retain the test reports as formal evidence.
- Generate a Software Bill of Materials (SBOM): Implement tooling to automatically generate an SBOM for every shipped version, identifying all components, versions, and origins.
- Secure the Supply Chain: Map the product architecture, including how software components interact and integrate into the overall processing environment.
# 4. Vulnerability Handling & Incident Reporting Framework (Article 14)

Compliance requires strict post-market operational procedures for detecting and reporting active threats.
1. Establish a Coordinated Vulnerability Disclosure (CVD) Policy: Create a public policy and establish a single point of contact (e.g., security@company.com) to receive vulnerability reports.
2. Implement the 24-Hour Early Warning Procedure: Define the internal governance for filing an early warning to ENISA and the national CSIRT within 24 hours of becoming aware of an actively exploited vulnerability or severe incident.
3. Establish the 72-Hour Notification Process: Create the framework to provide a detailed incident notification within 72 hours of awareness.
4. Prepare the 14-Day Final Reporting Protocol: Ensure a final report is submitted within 14 days after a corrective measure or fix is available, detailing the root cause and mitigation.
# 5. User Information & Instructions (Annex II / Article 10)

Develop the mandatory transparency documentation that must accompany the product.
1. Draft the Compliance Statement: Complete the Annex II template outlining manufacturer details, CVD contact points, and the intended purpose.
2. Provide Secure Commissioning Instructions: Document the necessary measures users must take during initial setup and throughout the product's lifetime to ensure secure use.
3. Detail Update Mechanisms: Explain how security-relevant updates can be installed and how users can disable automatic updates if applicable.
4. Define Secure Decommissioning: Provide clear instructions on how the product can be safely retired and how user data can be securely wiped.
# 6. Technical Documentation Compilation (Annex VII)

Assemble the internal technical file required for market surveillance authorities. This file must be maintained for 10 years or the duration of the support period, whichever is longer.
1. Compile the General Description: Gather product names, versions, supported hardware, intended use cases, and external/internal photographs or illustrations.
2. Document the Architecture & Design: Include architecture drawings, data flow maps, and records of critical security design decisions.
3. Consolidate Risk & Testing Evidence: Aggregate the risk assessment document, penetration test results, and all CI/CD security testing output.
4. List Applied Standards: Document the harmonized standards, common specifications, or certification schemes applied in full or in part.
5. Include the SBOM & CVD Policy: Attach the generated software bill of materials and the documented vulnerability handling procedures.
# 7. Conformity Assessment & EU Declaration

Execute the formal legal steps to authorize the product for the EU market.
1. Execute the Selected Conformity Module:
    - If using Module A, formally sign off on the self-assessment.
    - If using Module B+C or H, engage a Notified Body, submit the Annex VII Technical File, and undergo the formal audit.
2. Draw up the EU Declaration of Conformity: Draft the final legal declaration (Annex V) asserting that the product meets all CRA essential requirements.
3. Apply the CE Marking: Affix the CE marking visibly, legibly, and indelibly to the product, its packaging, or its accompanying documents.
4. Retain and Update: Ensure version control is applied to the Annex VII technical file and update it whenever a significant hardware or firmware change occurs.