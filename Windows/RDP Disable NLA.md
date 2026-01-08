## Ref
- https://media.kasperskycontenthub.com/wp-content/uploads/sites/43/2022/06/23093553/Common-TTPs-of-the-modern-ransomware_low-res.pdf
- https://www.cisa.gov/sites/default/files/2024-11/aa23-136a-joint-csa-stopransomware-bianlian-ransomware-group.pdf
- https://thedfirreport.com/2024/08/26/blacksuit-ransomware/
- https://fixingitpro.com/2011/07/06/disabling-rdp-network-level-authentication-nla-remotely-via-the-registry/

## Notable
To disable Network Level Authentication (NLA) for Remote Desktop Protocol (RDP) through the registry,

you need to modify the SecurityLayer and UserAuthentication values within the HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Terminal Server\WinStations\RDP-Tcp registry key.

Setting both values to 0 disables NLA. Disabling NLA can weaken security and make your system more vulnerable to attacks.

It is generally recommended to keep NLA enabled unless there is a specific reason, like compatibility issues, to disable it.

Find the SecurityLayer value and change its data to 0

Find the UserAuthentication value and change its data to 0