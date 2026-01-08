## Ref
- https://developers.google.com/admin-sdk/reports/v1/appendix/activity/admin-event-names
- https://cloud.google.com/logging/docs/audit/gsuite-audit-logging
- https://developers.google.com/admin-sdk/reports/v1/appendix/activity/admin-event-names
- https://www.techrepublic.com/article/how-to-manage-multiple-domains-in-g-suite/#:~:text=1.-,Sign%20in%20as%20a%20G%20Suite%20administrator.,Domain%20Alias%20(Figure%20C).&text=Choose%20Add%20Another%20Domain%20when,your%20organization's%20G%20Suite%20setup
- https://developers.google.com/admin-sdk/reports/v1/appendix/activity/admin-delegated-admin-settings
- https://developers.google.com/admin-sdk/reports/v1/guides/manage-audit-admin

PreBuilt Admin Roles
- https://support.google.com/a/answer/2405986?hl=en

Admin Log Fields
- https://support.google.com/a/answer/4579579?hl=en

Event Name List
- https://developers.google.com/admin-sdk/reports/v1/appendix/activity/admin-event-names\

Pre-Built Admin
- https://support.google.com/a/answer/2405986?hl=en

Admin Log Sample
- https://support.google.com/a/answer/4579579

Super Admin Example
- https://developers.google.com/admin-sdk/directory/v1/guides/manage-roles


## Log Example
```
{
"kind": "admin\#directory\#roles",
"etag": "\"sxH3n22L0-77khHtQ7tiK6I21Yo/DywA6_jaJCYw-f0lFs2-g17UWe8\"",
"items": 
[
	{
	"kind": "admin\#directory\#role",
	"etag": ... ,
	"roleId": "3894208461012993",
	"roleName": "_SEED_ADMIN_ROLE",
	"roleDescription": "Google Workspace Administrator Seed Role",
	"rolePrivileges": 
	[
		{
		"privilegeName": "SUPER_ADMIN",
		"serviceId": "01ci93xb3tmzyin"
		},
		{
		"privilegeName": "ROOT_APP_ADMIN",
		"serviceId": "00haapch16h1ysv"
		},
		{
		"privilegeName": "ADMIN_APIS_ALL",
		"serviceId": "00haapch16h1ysv"
		},
		...
	],
	"isSystemRole": true,
	"isSuperAdminRole": true
	},
	{
	"kind": "admin\#directory\#role",
	"etag": "\"sxH3n22L0-77khHtQ7tiK6I21Yo/bTXiZXfuK1NGr_f4paosCWXuHmw\"",
	"roleId": "3894208461012994",
	"roleName": "_GROUPS_ADMIN_ROLE",
	"roleDescription": "Groups Administrator",
	"rolePrivileges": 
		[
		{"privilegeName": "CHANGE_USER_GROUP_MEMBERSHIP",
		"serviceId": "01ci93xb3tmzyin"
		},
		{
		"privilegeName": "USERS_RETRIEVE",
		"serviceId": "00haapch16h1ysv"
		},
		{
		"privilegeName": "GROUPS_ALL",
		"serviceId": "00haapch16h1ysv"
		},
		{
		"privilegeName": "ADMIN_DASHBOARD",
		"serviceId": "01ci93xb3tmzyin"
		},
		{
		"privilegeName": "ORGANIZATION_UNITS_RETRIEVE",
		"serviceId": "00haapch16h1ysv"
		}
		],
	"isSystemRole": true
	},
...
]
}
```

## Notable

Common Key Fields and General
- type = Admin Activity Category Group like ('DELEGATED_ADMIN_SETTINGS', 'DOMAIN_SETTINGS')
- applicationName = api that was called
- eventName = Log Name per Admin Activity Category Group
- privilegeName = Name of Privileges assigned
- actorEmail = Email address of the user who performed the action
- ipAddress = IP Address of the user making or performing the change
- userEmail = who received the assignment

Instead of an email address, you might see
- License Manager
- Service Account
- Anonymous

_SEED_ADMIN_ROLE -> Super Admin
SUPER_ADMIN = GoogleWorkspace Privilege