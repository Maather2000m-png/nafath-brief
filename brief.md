Version: NAFATH-V1


Track: Cybersecurity

## Overview
The Nafath mission proposes a single national SSO service where citizens log in once via a mobile app and website to access many government services. Software defines the login flow using OIDC and OAuth2 to separate authentication from API authorization. AI supports risk-based detection of suspicious logins but introduces fairness and security concerns. Mobile implements Android runtime permissions for camera and notifications. Networking benefits from DNS over HTTPS to protect lookup privacy. Cybersecurity requires phishing-resistant MFA like FIDO2. Data obligations under Oman PDPL govern consent, breach notification, and data minimization.

## Software
OAuth2 is authorization, answering whether an app may access a resource on behalf of a user via access tokens. OpenID Connect is authentication built on OAuth2, adding an ID token JWT that proves who logged in. For Nafath, OIDC should handle national login, while OAuth2 access tokens authorize calls to individual ministry APIs, preventing misuse of access tokens as identity proofs.
Resource: https://oauth.net/2/

## AI
A suspicious-login detector risks bias against certain locations, lack of transparency for citizens, and vulnerability to adversarial evasion. Under NIST AI RMF, govern and map risks like fairness and privacy, measure accuracy and false positives, and manage via human oversight and logging. Security requires protecting training data and monitoring model drift.
Resource: https://www.nist.gov/itl/ai-risk-management-framework

## Mobile
Android requires runtime consent for dangerous permissions. The Nafath app must request CAMERA only when scanning an ID and POST_NOTIFICATIONS for alerts, explaining why. Normal permissions like INTERNET are auto-granted. Users can deny or revoke anytime, so the app must degrade gracefully and re-request with rationale.
Resource: https://developer.android.com/privacy-and-security/permissions

## Networking
DNS over HTTPS encrypts DNS queries inside HTTPS, preventing eavesdroppers on Wi-Fi or ISPs from seeing which government domains are queried and blocking DNS tampering to fake login pages. It does not hide the destination IP after resolution, nor does it prevent the DoH resolver itself from seeing queries or protect against malware on the device.
Resource: https://www.cloudflare.com/learning/dns/dns-over-tls-vs-dns-over-https/

## Cybersecurity
Phishing-resistant means the credential is cryptographically bound to the real domain and cannot be replayed on a fake site. CISA recognizes only FIDO2/WebAuthn with non-exportable keys and PKI-based authentication as phishing-resistant. SMS OTP, email codes, TOTP codes, and push approvals are not phishing-resistant because they can be intercepted via AiTM proxies.
Resource: https://www.cisa.gov/sites/default/files/publications/fact-sheet-implementing-phishing-resistant-mfa-508c.pdf

## Data
Under Oman PDPL Royal Decree 6/2022, the authority must obtain explicit written consent, state purpose and retention, minimize collection, implement encryption and access controls, appoint a DPO, keep processing records, and report breaches within 72 hours to MTCIT. Citizens have rights to access, correction, erasure, and withdrawal of consent.
Resource: https://www.mtcit.gov.om/

## Misconception in My Track
One common wrong belief is that any MFA, such as SMS OTP or TOTP authenticator apps, counts as phishing-resistant. The correct version is that only FIDO2/WebAuthn and PIV/PIV-derived PKI authentication qualify as phishing-resistant because they use origin-bound cryptography. The CISA fact sheet proves this under the heading "Phishing-Resistant MFA" and the table "Phishing-Resistant Authenticator Types" which explicitly excludes SMS, voice, TOTP and push.

## Open Question
If Nafath adopts synced cloud passkeys, does the recovery via the cloud account password downgrade phishing resistance, and should device-bound keys be required for high-risk government transactions?