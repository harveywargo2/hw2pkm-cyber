## Notable
Apple Code Signing is a fundamental macOS and iOS security technology that uses cryptography to certify two things about an application: its authenticity and its integrity.
- Authenticity (Who made it): It verifies that the app was created by a specific, identified developer whose identity has been validated by Apple (via the Apple Developer Program).
- Integrity (Has it been changed): It ensures that the app's code has not been altered or tampered with since the developer finished building and signing it

Signing
- Developer
- Identity & Integrity
- Digital Signature


Notarization
- Apple automated scanning
- Ticket granted by apple

  
Revocations
- CSSMERR_TP_CERT_REVOKED


The Flow:
For a modern macOS app to run without Gatekeeper warnings, the developer must:
1. Code Sign: Use their Developer ID Certificate and private key to sign the app.
2. Submit & Scan: Submit the signed app to the Apple Notary Service.
3. Notarize: The service automatically scans the app for malware. If clean, it issues a notarization ticket.
4. Staple: The developer staples this ticket to the app package.

  
TAOMM
- Status: revoked signature, no signature, signed by a developer certificate issued by Apple for distribution
- Is notarized: trusted by the Apple notary service
- Signing auths: