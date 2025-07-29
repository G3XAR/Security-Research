# PoC: Stored XSS Vulnerability in Slink (v1.4.9 – v1.6.3)

## Vulnerability Type
Stored Cross-Site Scripting (XSS)

## Estimated CVSS Score
~5.4 (context-dependent)

## Affected Versions
Confirmed in v1.4.9, v1.5.1, and v1.6.3. Likely present in earlier versions.

## Description
A stored Cross-Site Scripting (XSS) vulnerability has been identified in Slink, a self-hosted image sharing platform.  
The application fails to properly sanitize uploaded SVG files, allowing attackers to embed arbitrary JavaScript code.  
When a user views the image, the script executes in the context of their browser.

Although Slink is typically deployed in private or restricted environments, its flexibility also allows it to be exposed to broader networks—either intentionally or accidentally.  
If an attacker gains access to the internal network, or if the platform is deployed in a public-facing setup, this vulnerability could be exploited.

## Impact
- Affects both authenticated and unauthenticated users.  
- Potential consequences: session hijacking, phishing attacks, drive-by script execution, redirection to malicious sites.  
- Attack surface includes unauthenticated visitors viewing SVG images.

## Steps to Reproduce
1. Create a malicious SVG file with embedded JavaScript.  
2. Log in to Slink and upload the SVG via the image upload interface.  
3. Share the direct link.  
4. The embedded script executes automatically when the image is opened—no login required.

*Tested on PC and mobile devices.*

---


