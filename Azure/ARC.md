## References
- https://learn.microsoft.com/en-us/azure/azure-arc/servers/agent-overview
- https://learn.microsoft.com/en-us/azure/azure-arc/servers/learn/quick-enable-hybrid-vm
- https://learn.microsoft.com/en-us/azure/azure-arc/servers/security-overview

Perms & RBAC
- https://learn.microsoft.com/en-us/azure/azure-arc/servers/security-machine-configuration
- https://learn.microsoft.com/en-us/azure/azure-arc/servers/security-identity-authorization

Arc CLI Commands
- https://learn.microsoft.com/en-us/cli/azure/service-page/arc?view=azure-cli-latest
- https://learn.microsoft.com/en-us/cli/azure/connectedmachine?view=azure-cli-latest

Logging
- https://kaidojarvemets.com/automating-arc-enabled-server-log-collection-with-azure-run-command/
- https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/scenarios/hybrid/arc-enabled-servers/eslz-management-and-monitoring-arc-server


## Service Names
- himds.exe: chronizes metadata with Azure and hosts a local REST API for extensions and applications to access the metadata and request Microsoft Entra managed identity tokens
- gc_arc_service.exe || gc_service.exe prior to version 1.36: audits and enforces Azure guest configuration policies on the machine.
- gc_extension_service.exe || gc_service.exe prior to version 1.36: installs, updates, and manages extensions on the machine.
- NT SERVICE\himds: Unprivileged account used to run the Hybrid Instance Metadata Service

## Machine Config
The Machine Configuration (formerly Guest Configuration) service can use up to 5% of the CPU to evaluate policies. The Extension service can use up to 5% of the CPU on Windows machines and 30% of the CPU on Linux machines to install, upgrade, run, and delete extensions. Some extensions might apply more restrictive CPU limits once installed.

## Extension Manager
- The extension manager is responsible for installing, configuring, upgrading, and removing additional software on your machine.
- Out of the box, Azure Arc doesn’t know how to do things like monitor or patch your machine. Instead, when you choose to use those features, the extension manager downloads and enables those capabilities.
- The extension manager runs as Local System on Windows and root on Linux because the software it installs may require full system access.
- You can limit which extensions the extension manager is allowed to install or disable it entirely if you don’t intend to use extensions.
  

## RBAC
Azure Connected Machine Resource Administrator, Contributor, and Owner don't grant access to use SSH or WAC via the Azure Arc Connectivity Platform.

Roles that allow remote access include:
- Virtual Machine Local User Login (SSH with local credentials)
- Virtual Machine User Login (SSH with Microsoft Entra ID, standard user access)
- Virtual Machine Administrator Login (SSH with Microsoft Entra ID, full admin access)
- Windows Admin Center Administrator Login (WAC with Microsoft Entra ID authentication)

There are two built-in roles in Azure that you can use to control access to an Azure Arc-enabled server:
- Azure Connected Machine Onboarding,
	- intended for accounts used to connect new machines to Azure Arc.
	- This role allows accounts to see and create new Arc servers but disallows extension management.
- Azure Connected Machine Resource Administrator
	- intended for accounts that will manage servers once they’re connected. This role allows accounts to read, create, and delete Arc servers, VM extensions, licenses, and private link scopes.
- Generic RBAC roles in Azure also apply to Azure Arc-enabled servers, including Reader, Contributor, and Owner.
	- Users and applications granted or administrator role access to the resource can make changes to the resource, including deploying or deleting extensions on the machine.
	- Extensions can include arbitrary scripts that run in a privileged context, so consider any contributor on the Azure resource to be an indirect administrator of the server