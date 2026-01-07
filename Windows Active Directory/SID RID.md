## Ref
- https://rootdse.org/posts/active-directory-basics-1/
- https://rootdse.org/posts/active-directory-basics-2
- https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/understand-security-identifiers

SID Components
- https://learn.microsoft.com/en-us/windows/win32/secauthz/sid-components

SID Structure
- https://learn.microsoft.com/en-us/windows/win32/api/winnt/ns-winnt-sid

Well Known SIDS
- https://learn.microsoft.com/en-us/windows/win32/secauthz/well-known-sids
- https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/understand-security-identifiers#well-known-sids-all-versions-of-windows

## Notable
RID
- RID (Relative identifier) is a part of an Active Directory object’s Security Identifier (SID) that uniquely identifies an account or group within a domain
- assigned to active directory objects at the time of creation
- last part of a SID

SID
- Every domain has a unique SID (Security Identifier) with which it is identified
- SIDs are used to uniquely identify security principals like user accounts, computer accounts or processes
- unique within their scope (domain or local), and they are never reused
- (SID)-(Revision Level)-(Identifier-Authority)-(Sub-Authority1)-(Sub-Authority2)...-(RID)
- S ids it as a SID

