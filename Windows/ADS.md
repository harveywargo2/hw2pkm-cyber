## Ref
- https://www.malwarebytes.com/blog/101/2015/07/introduction-to-alternate-data-streams
- https://gist.github.com/chriselgee/bf41951d0b51d0ef9d2504a36921cd13
- https://blog.netwrix.com/2022/12/16/alternate_data_stream/
- https://blog.ironmansoftware.com/daily-powershell/powershell-alternate-data-streams/
- https://www.youtube.com/watch?v=qBrFW3gpjpM

Sysinternals Streams
- https://learn.microsoft.com/en-us/sysinternals/downloads/streams

## Notable
- Alternate Data Streams (ADS) are a file attribute only found on the NTFS file system
- In this system a file is built up from a couple of attributes, one of them is _$Data_, aka the data attribute
- Looking at the regular data stream of a text file there is no mystery.
- It simply contains the text inside the text file. But that is only the primary data stream


Find All Streams

```
Get-Item .\file.txt -Stream *

```

View Stream

```
Get-Content .\file.txt:Zone.Identifier

```

  
Add Stream

```
Set-Content .\file.txt:Dank.Memes -Value "All your base"

```

  
Unblock-File

```
Unblock-File .\file.txt

```

  
In cmd.exe, you can:
- `dir /R` to see all ADS in a directory
- `echo Hidden text > file1.txt:hidden` to add text as an ADS
- `more < file1.txt:hidden` to see the hidden text
- `type nc.exe > file1.txt:nc.exe` to hide an executable in a text file