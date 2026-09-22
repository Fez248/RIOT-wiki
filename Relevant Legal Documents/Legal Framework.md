# Introduction

One of the most important parts of Ferrita, from now one called in this document RIOT as the internal name, it is the fact of being a real problem since moment zero.

Other companies need to create a sense of urgency to promote and sell their services. This has always been one of the most difficult problems when building a startup. The need to justify, the need to make a company or a user need the services that the startup offers.

Nevertheless, in our case it is much easier. As the sense of urgency is real, and more importantly, driven by the European Union in the form of a legal framework, the [CRA](https://digital-strategy.ec.europa.eu/es/policies/cyber-resilience-act). 

In a sentence, this new law defines and imposes the measures all enterprises need to follow and take into account in order to be able to sell **products with digital elements in the  EU**.

However, companies, specially small and mid-sized ones in Spain/Barcelona Area have **NO IDEA** of how to secure their devices. They do not have qualified personal and specially, willingness to spend their precious engineering hours in that. But, they need, or they risk getting fined really big.

That is where we enter, we need to offer a service that makes all this process easy and much cheaper than contracting a full cybersecurity expert in-house.

To do so, we **MUST** know how does CRA work and exactly what do we need to do.

It is recommended to read at least the appendixes and their respectable articles in the official document [[CRA_OJ_L_202402847_EN_TXT.pdf]]. If that is not an option here I layout the essential of everything there is needed to be known.

# Annexes

Annexes are divided by categories depending on which part of the process they talk about. There are some related to engineering, others related to product categorization and lastly some related to legal release. Do not get confused, it is our job to assist our clients through each one of them, so we must know all of them well, not only engineering.

## Development and Engineering (Annex I & VII) 
### Annex I
Annex I lays down the essential cybersecurity requirements relating to the properties of products with digital elements.
```text
The original document talks about "products with digital elements" as a way to refer to all the profucts falling inside the CRA framework. For simplicity in this document they are going to be called just products.
``` 
#### General rule
Products shall be designed, developed and produced with a level of cybersecurity based on the risks. Meaning, a device that serves as a critical part of a government pipeline needs a bigger cybersecurity assessment than an ads screen not connected to the internet.

#### Specific rules
Each product must follow these set of rules:
1. Be made available on the market without known **exploitable** vulnerabilities:
	Special consideration to the word "exploitable", if, for example, a library contains a known vulnerability but, there is no way to exploit it, it can be legally put in the market. 
	
	Take for instance, the vulnerable function of the library is never used and not reachable, then, it is "probably" okay to put that product on the market if an adequate VEX document has been made. 
	
	I say "probably" due to the fact that I am not a lawyer, but I believe it to be correct.

2. Be made available on the market with a secure by default configuration 
	Means that the product must arrive on its most safest and most hardened state. For example, a router with now password on the admin panel or a well-known password is not a save by default configuration.
	
	**Exception**: There can be an exception where if the manufacturer and the business user agree (a business user is another enterprise, never and end individual user).
	
	Example: A business user running software in a strictly air-gapped network (not connected to any other network, not even the internet) may explicitly agree in writing to turn off automatic updates or customize default configurations to avoid breaking operational workflows.

3. Ensure that vulnerabilities can be addressed through security updates
	Be able to update the device, including where applicable:
	- Automatic security updates  installed within an appropiate timeframe enabled as a default setting
	- A clear easy-to-use opt-out mechanism with notifications of available updates to users and the option to temporarily postpone them

4.  Ensure protection from unauthrosied access 
	Ensure protection by appropiate control mechanisms and report on possible unauthorised access. Some measures to do so, but not limited, are: 
	- Authentication
	- Identity management systems
	- Access maangement systems

5. Protect the confidentiality of data 
	All data stored, transmitted or otherwise processed must be secured, such as by encrypting relevant data at rest, or in transit by state of the art mechanisms, and by using other technical means.

6.  Protect the integrity of data
	All data stored, transmited or otherwise processed must be protected against any manipulation or modification not authorised by the user, and report on corruptions. Here it is included as data not only personal data, but also commands, programs and configurations.

7. Data minimisation
	Process only data relevant and limited to what is necessary in relation to the intended purpose of the product.

8. Protect the availability
	Protect availability of essential and basic function, also after an incident, including through resilience and mitigation measures against denial-of-service attacks.

9. Minimise negative impact

10.  Limit attack surfaces
	Be designed, developed and producted to limit attack surfaces, including external interfaces.

11. Explotation mitigations mechanisms and techinques
	Be designed, developed and produced to reduce the impact of an incident. For example, running a web server inside a containerized environment (ex, Docker) so in case it gets compromised it does not affect the system behind of it.

12. Provide security related information
	Provide information by recording and monitoring relevant internal acitivty, including the access to or modifiation of data, services or functions, with an opt-out mechanism for the user.


Every manufacturer of these products must follow thse set of rules:
1. Identify and document vulnerabilities and components
	Identify and document vulnerabilities and components contained in products with digital elements, including by drawing up a software bill of materials (SBOM) in a commonly used and machine-readable format covering at the very least the top-level dependencies of the products.

2. Address and remediate vulnerabilities without delay
	In relation to the risks posed to products, address and remediate vulnerabilities without delay, including by providing security updates: where technically feasible, new security updates shall be provided separately form funcitonallity updates.

3.  Recurrent tests
	Requires ongoing, recurring security audits (scans, pentests, code reviews) throughout the product support period, not just a one-time pre-launch test.

4. Share and publicly disclose information about updates
	When releasing a security patch, publicly disclose the flaw (description, severity, affected versions/products, and clear fix instructions).
	
	The enterprise may briefly delay public disclosure only if publishing immediately creates a higher risk than the benefit, giving users time to apply the patch first.

5. Vulnerability disclosure
	Publish and actively run a formal Coordinated Vulnerability Disclosure policy setting clear rules on how security researchers and users report flaws and how the enterprise handles them.

6. Contact point for vulnerability reporting
	Provide a dedicated, accessible contact address (e.g., security@ or security.txt) to make reporting bugs in the product or integrated 3rd-party dependencies fast and friction-free.

7. Provide secure update mechanisms
	Build reliable and secure delivery channels to push updates promptly. Where applicable, security patches must install automatically by default (with a clear opt-out for users).

8. Dissemination & Free Security Patches
	Deliver security updates without delay and free of charge (unless custom-negotiated in writting with a B2B client for a tailor-made product).
	
	Accompany every updates with clear, actionable advisory notices explaining what was fixed and what action the user needs to take.

### Annex VII
Annex VII lays down the minimum information the technical documentation of such products must contain.

#### Specific rules
1. A general description of the product, including:
	-  Its intended purpose.
	* Versions of software affecting compliance with essential cybersecurity requirements:
		This means, for every **shipped** update, not for every commit or internal build, for every version that its delivered to the market there should be the following documentation associated:
		-  Internal build (hash of the last commit)
		-  Internal version ID
		-  Security Scope (If the change affects to security or not, ex: changing a colour does not)
		-  Compliance Status (yes or no)
		-  Related Tests in case if affects security, how has the cybersecurity of the product been tested for that specific build, specially regarding the new changes
	-  If the product is a hardware product, include photographs or illustrations showing external features, marking and internal layout.
	-  User information and instructions as set out in [Annex II](#Annex%20II)

2. A description of the desidn, development and production of the product and vulnerability handling processes, including:
	-  Necessary information on the design and development of the product, including, where applicable, drawings and schemes and  a description of the system architecture explaining how software components intecrate with each other.
	-  Neceessary information and specifications of the vulnerability handling processes including:
		- SBOM
		-  Coordinated vulnerability disclosure policy
		-  Evidence of the provision of a contact address for the reporting of the vulnerrabilities
		-  A description of the technical solutions chosen for the secure distribution of updates
	-  Necessary information and specifications of the production and monitoring processes of the product and the validation of those processes.
	    -  Secure CI/CD & Build Pipelines: Proof that source code repositories, build systems, and factory flashing tools are protected against unauthorized modifications (preventing supply chain attacks).
	    -  Quality & Validation Steps: Documentation of internal audits, security regression testing, and code review rules used before code reaches production.
	    -  Post-Market Monitoring: Processes used to continuously monitor third-party components for newly disclosed CVEs (e.g., automated dependency scanners running against your SBOM).

3. Cybersecurity risk assessment. Document the threat modeling and risk assessment carried out for the product across its entire lifecycle (design, build, delivery )
	-  Threat Model: A list of plausible threats and attack vectors relevant to your product's deployment context (e.g., unauthorized access, data interception, physical tampering, supply chain compromise).

	-  Applicability Mapping to Annex I, Part I: Explicitly document how each essential security requirement in Annex I applies to your product (e.g., explaining how password policies, data encryption at rest/in transit, or secure boot satisfy specific risks). If a specific Annex I requirement does not apply to your product, you must explicitly justify why (e.g., "Requirement X on wireless security is non-applicable because the product possesses no wireless interfaces").

4. Determination of the support period. Information about the technical and commercial justification used to determine the support end date. It should be taken into account information like: expected physical lifespan of the hardware, software component lifecycle limits, industry standards for similar products, and user expectations.

5. State which officail standards or technical specifications were used to prove compliance.
	-  Harmonised Standards / Common Specifications / EU Certification Schemes: List any official standards published in the EU Official Journal that you followed (e.g., EN standards derived from IEC 62443 or ETSI EN 303 645).

	-  Partial Application: If you only applied specific clauses of a standard, you must explicitly list which sections were used and which were omitted.

	-  Alternative Solutions / Custom Implementation: If no official harmonized standards were used (or were only partially applied), you must document the alternative technical specifications or engineering frameworks used to meet the Annex I requirements.

6.  Reports of the tests carried out to verify the conformity of the product.
	Product Security Verification: Test execution logs, static/dynamic analysis (SAST/DAST) reports, penetration test summaries, and fuzzing results for the product binary/hardware.
	
	Vulnerability Handling Verification: Evidence showing that your vulnerability intake, patch management, SBOM generation, and update delivery systems function as claimed.

6.  A  copy of the EU declaration of conformity. [[EU_Declaration_Of_Conformity_Template]]
7.  The SBOM
### Annex II