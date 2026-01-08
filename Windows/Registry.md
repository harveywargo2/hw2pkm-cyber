## Ref
- https://medium.com/@nikhil.aniill/windows-registry-for-cybersecurity-beginners-63eebffb4049
- https://www.avast.com/c-windows-registry
- https://academy.tcm-sec.com/p/practical-windows-forensics
- https://github.com/Defenders-Guide/TheDefendersGuide/blob/main/Windows/Windows%20Registry/The_Defenders_Guide_to_the_Windows_Registry.md

Tools
- https://kurtzimmermann.com/regcoolext_en.html


## Registry Structure

- Registry keys: containers that act like folders, with values or subkeys contained within them.
- Registry values: are similar to files (not containers).
- Hives: contain keys (directories) and values
- Keys: might contain subkeys and/or values
- Subkeys: no difference between key and subkey structure
- Values: store data

The main branches of the registry are called **hives**.
All the folders in the registry are called _keys_ except for these five hives.

  
The difference between HKEY_LOCAL_MACHINE and HKEY_CURRENT_USER is
- whether the referenced executable launches at startup for any user logging in
- or a specific user
- (current_user is copied to a stored “user hive” and loaded whenever that user ID logs in)


