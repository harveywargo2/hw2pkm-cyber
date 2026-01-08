## Ref

Eval ISOs
- https://www.microsoft.com/en-us/evalcenter

Lab Set Up
- https://academy.tcm-sec.com/p/practical-ethical-hacking-the-complete-course
- https://www.youtube.com/watch?v=xftEuVQ7kY0
- https://rootdse.org/posts/active-directory-lab-setup-forest/
- https://rootdse.org/posts/active-directory-lab-setup-add-data/

Lab Guides
- https://medium.com/@gwenilorac/empowering-your-learning-journey-building-an-active-directory-home-lab-807c436a7f04
- https://rootdse.org/posts/active-directory-lab-setup-forest/
- https://rootdse.org/posts/active-directory-lab-setup-add-data/

Azure AD Lab
- https://kamran-bilgrami.medium.com/ethical-hacking-lessons-building-free-active-directory-lab-in-azure-6c67a7eddd7f

## Pre Setup
- Get ISO's
	- put dummy data in the windows eval
	- bypass windows keys
- Get VMWare or other virtual software
- Specs
	- 2 cores
	- 8 gb (can be lowered after initial install)
	- server 2022 iso
	- 60 gb disk

## Server Install
- Create from ISO on Fusion
	- uncheck easy setup
- Quick Enter On VM Start
	- if you miss you get net error
- Win Server Desktop Experience
- New Drive 0
	- Apply
- Windows Server Installs
- set admin password
- install VMWare tools
	- setup64.exe
	- complete install
- rename computer
	- search name
	- rename computer

## Set Up DC
- Set Up Domain Controller
	- Manage (add roles & features)
	- role based
	- Add ADDS
	- restart auto
	- promote server to domain controller
- Deployment Config (Promote to DC)
	- add new forest
	- use .local
	- netbios will populate
	- install from prereqs
	- Reboot
- Set Up Certificate services
	- Manage (add Roles & features)
	- role based
	- AD Cert Services
	- Certification Authority
- Configure Cert Services
	- cert authority