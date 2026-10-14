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

## Cybersecurity

## Data

## Misconception in My Track

## Open Question