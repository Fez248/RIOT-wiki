# Understanding Harmonised Standards

The Cyber Resilience Act outlines its essential cybersecurity requirements in broad, legally phrased terms (e.g., "protect data at rest," "ensure a secure default configuration"). A Harmonised Standard translates those broad legal requirements into highly specific, testable engineering specifications.

Currently, the European Commission has mandated three organizations (CEN, CENELEC, and ETSI) under Standardisation Request M/606 to write 41 of these standards.

The Legal Superpower: Presumption of Conformity
If a client builds their product according to a Harmonised Standard whose reference has been published in the Official Journal of the European Union (OJEU), the product is legally presumed to comply with the CRA requirements covered by that standard.
- Crucial for Class I Products: If a manufacturer of a Class I Important Product fully applies these standards, they are allowed to use Module A (Self-Assessment). If they don't follow the standards, they are legally forced to pay for a Notified Body audit (Module B+C).

How the Standards are Structured:
1. Horizontal Standards (Apply to everyone): Developed primarily by CEN-CENELEC (the EN 40000 series). These cover overarching processes. For example, EN 40000-1-2 dictates the exact risk management methodology you must use, and EN 40000-1-3 defines exactly how a vulnerability handling process must be structured (currently containing over 50 mandatory requirements).
2. Vertical Standards (Product-specific): Developed primarily by ETSI (the EN 304 6xx series). These are tailored to specific product categories. There will be one specific standard for network routers, another for operating systems, and another for smart home IoT devices.

### How to Follow Harmonised Standards

Even though final ratification and OJEU publication are expected between late 2026 and 2027, the drafts are currently public and stable enough to build your compliance pipelines around right now.
1. Identify the Scope: Determine which horizontal standards apply to your client's processes and which vertical standard applies to their specific product type.
2. Read the Drafts: Pull the current ETSI and CEN-CENELEC drafts (freely available during public enquiry phases).
3. Perform a Gap Analysis: Cross-reference your client's current development practices against the specific technical controls outlined in the standard.
4. Create a Matrix of Conformity: Inside the Annex VII Technical File, you will create a matrix. On the left side, list the CRA Annex I requirement. In the middle, list the specific clause of the Harmonised Standard (e.g., EN 40000-1-2 Clause 5.4). On the right side, link to the client's internal test report or design document proving they met that clause.