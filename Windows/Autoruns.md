## Ref
- https://www.cyborgsecurity.com/cyborg-labs/hunting-for-persistence-registry-run-keys-startup-folder/#:~:text=Persistence%2C%20especially%20amongst%20threat%20hunters%2C%20doesn%E2%80%99t%20often%20get,top%20hunts%20that%20hunt%20teams%20should%20focus%20on
- https://medium.com/@domdalcerro/run-key-persistence-threat-package-part-1-introduction-56e63140013b
- https://www.linkedin.com/pulse/windows-persistence-registry-run-keysstartup-folder-mangipudi
- https://alican-kiraz1.medium.com/threat-hunting-for-windows-registry-27778993e21b
- https://resources.infosecinstitute.com/topics/malware-analysis/common-malware-persistence-mechanisms/

## Notable
The registry run keys perform the same action, but can be located in four different locations:
- HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Run
- HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run
- HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\RunOnce
- HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\RunOnce

  

Then there is `Run` and `RunOnce`
- the only difference is that `RunOnce` will automatically delete the entry upon successful execution.