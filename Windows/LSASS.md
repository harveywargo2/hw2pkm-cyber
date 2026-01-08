## Ref
- https://en.wikipedia.org/wiki/Local_Security_Authority_Subsystem_Service
- https://strontic.github.io/xcyclopedia/library/lsass.exe-03C70933698C6E3E466076DD9C3FAA18.html
- https://www.microsoft.com/en-us/security/blog/2022/10/05/detecting-and-preventing-lsass-credential-dumping-attacks/
- https://learn.microsoft.com/en-us/windows-server/security/windows-authentication/credentials-processes-in-windows-authentication

How it Works
- https://learn.microsoft.com/en-us/windows-server/security/windows-authentication/credentials-processes-in-windows-authentication

## Notable
Key Functions of LSASS
- User Authentication: LSASS verifies users logging on to a Windows computer or server by validating their credentials (like username and password).
- Security Policy Enforcement: It enforces local security policies, such as password complexity and account lockout rules.
- Access Token Creation: After successful authentication, it creates access tokens that determine the user's privileges and what resources they can access.
- Credential Management: For the purpose of enabling single sign-on (SSO) and other services, LSASS handles and stores various forms of user credential material (like password hashes and Kerberos tickets) in its memory.

Because LSASS holds sensitive credential data in memory, it is a high-value target for attackers.
- Credential Dumping: Adversaries who gain elevated privileges (like administrative access) on a system often target the LSASS process memory to "dump" or extract stored credentials, which they can then use to move laterally across a network and escalate their privileges. Tools like Mimikatz are known for this.
- System Integrity: LSASS is a critical system file. If the lsass.exe process is forcibly terminated, the system will often lose access to accounts and may automatically restart as a security measure.