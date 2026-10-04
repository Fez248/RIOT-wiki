So, you've found a CVE on one of our client's firmware, you have read the description and it seems like something that could be exposed, something that could be exploitable, and something that will cause harm.

Basically, you've done your job.

First off all, congratulations!!

Second off all, maybe our client has already backported a security fix to that vulnerability and you are looking at a false positive.

When they patch a CVE with lets say, a Yocto patch, the code gets modified, but the version string doesn't.

So, instead of spending hours working first on an exploit (if it is not trivial to do so).

Then it is best for you to first check if that vulnerability has been fixed.

How to do it??

3 main ways:
### 1. Build & Source Code Verification: 

#### Package receipts
If you have access to the source code, Yocto layer metadata or build tree just check it there. Inspect Package Receipts / Metadata (.bbappend / Patches). Look for CVE patch directives in SRC_URI:
```bash
SRC_URI += "file://CVE-2022-xxxx.patch \
			file://CVE-2023-yyyy.patch"
```

#### Package Changelogs
Distributions like Debian, Ubuntu, and Red Hat append revision suffixes to package names rather than changing the upstream binary string:
```bash
# Debian / Ubuntu package query
dpkg -l | grep openssl
# Yields: 1.0.2u-1~deb10u3 (The 'u3' indicates Debian backported fixes)

# Read distribution changelog
apt-changelog openssl | grep -i CV
```

### 2. Static Binary Analysis (Reverse Engineering)

#### Search for CVE-Specific Unique Strings & Symbols
Patches frequently introduce new error messages, function symbols, or constant definitions.
```bash
# Extract readable strings from the binary
strings libcrypto.so.1.0.2 | grep -i "ERR_STR_NEW_PATH_FUNCTION"
```

#### Binary Diffing (Vimdiff, Bindiff, Ghidra, IDA Pro)
Compile two reference binaries from upstream: the unpatched version and a known fixed version.

Use a diffing tool to comapre your target binary against the unpatched reference.

Locate the specific function affected by the CVE and inspect the assembly logic:
- Example: If a CVE fixes an integer overflow, check wheter the assembly in your target binary contains the added boundary check (cmp, jge, or bounds-validation logic) prior to allocation or memory copy calls (malloc, memcpy).

### 3. Vendor Documentation & Artifacts
When analyzing third-party closed-source binaries (e.g., BSP blobs from Broadcom, NXP, or Qualcomm):
- Software Bill of Materials (SBOM):
	Request or generate SPDX / CycloneDX SBOMs. Formal SBOM declarations often list applied patch hashes or downstream patch identifiers alongside base versions.

- Security Advisories & Release Notes:
    Cross-reference the BSP/SDK release notes from the silicon vendor. Vendors frequently state: "Maintained OpenSSL 1.0.2u base; applied backported patches for CVE-XXXX-YYYY."



























