## Ref
- https://rootdse.org/posts/active-directory-basics-1/
- https://rootdse.org/posts/active-directory-basics-2/
- https://rootdse.org/posts/active-directory-basics-3/
- https://rootdse.org/posts/active-directory-basics-4/

## Sysvol
- The SYSVOL policies folder contains all the GPOs. And folder name for each GPO is same as that GPO’s GUID.
- Network Share
- Stores GPO Templates

Default location
```
%SYSTEMROOT%\SYSVOL\sysvol
```

Network location
```
\\<domain_name>\SYSVOL
```

## Exploit Cheat Sheet
- https://github.com/S1ckB0y1337/Active-Directory-Exploitation-Cheat-Sheet