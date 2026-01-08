## Ref
- https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2021-36934


HiveNightMare-SeriousSAM
- https://github.com/GossiTheDog/HiveNightmare
- https://www.socinvestigation.com/exploiting-the-hive-nightmare-cve-2021-36934-detection-prevention/
- https://www.malwarebytes.com/blog/news/2021/07/hivenightmare-zero-day-lets-anyone-be-system-on-windows-10-and-11
- https://github.com/romarroca/SeriousSam/blob/main/serioussam.ps1

## Notable
Vulnerability Type Local Privilege Escalation (LPE)
- Core Cause: Overly Permissive Access Control Lists (ACLs) on key Windows Registry files, including the Security Account Manager (SAM) database.
- Affected Files: SAM, SECURITY, SYSTEM, DEFAULT, and SOFTWARE registry hive files located in %windir%\System32\config.
- Exploitation Method: A local, non-admin user can exploit the misconfigured ACLs to read these sensitive files from a Volume Shadow Copy (VSS), which are often created automatically by the Windows System Protection feature.
- Impact: Access to these files, especially the SAM file, allows an attacker to extract hashed user passwords (including local administrator and system accounts). These hashes can be used to authenticate with other services (Pass-the-Hash) or be cracked to gain plain-text passwords, leading to complete compromise of the local system and potential lateral movement on the network.
- Affected Systems: Various versions of Windows 10 (starting with version 1809) and related Windows Server versions released since October 2018 (though Microsoft updated the specific list of affected server versions over time).