## Ref
- https://themittenmac.com/threat-hunting-pids-within-apples-es-api/
- https://objective-see.org/blog/blog_0x4A.html

## Notable
Built from child up child, parent, grandparent
- process:
- parent:
	- The direct process that used the fork() system call to create the current process.
	- Typically launchHD
	- Direct Parent Process
- responsible parent:
	- The application or service that is ultimately accountable for launching the process.
- application services parent:
	- uses process serial numbers
	- deprecated service


Double Click Launch goes through launchd