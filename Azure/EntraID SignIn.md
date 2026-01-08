## Ref
- https://techcommunity.microsoft.com/t5/microsoft-sentinel-blog/non-interactive-logins-minimizing-the-blind-spot/ba-p/2287932
- https://isroot.nl/2022/03/23/parsing-interactive-and-non-interactive-sign-in-logs-with-microsoft-sentinel/
- https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-sign-ins
- https://login.microsoftonline.com/error
- https://learn.microsoft.com/en-us/azure/active-directory/develop/reference-aadsts-error-codes
- https://learn.microsoft.com/en-us/azure/active-directory/reports-monitoring/concept-sign-ins

## Types of Sign Ins
- Interactive user sign-ins
- Non-interactive user sign-ins
- Service principal sign-ins
- Managed identity sign-ins

Interactive sign-in request
- Happens when user authenticates with a username and password and optionally a multi-factor authentication token.
- Another way of saying this is that an interactive sign-in happens if a user logs in by using a keyboard **interactively**.

Non-interactive sign-in request
- Happens when a user authenticates with a saved or cached credential from a previously authenticated session.
- For example: a browser session that was previously authenticated interactively and is now authenticated because of the cached credential.
- In this case the user is already authenticated and does not have to provide a username and password interactively.

## Error Codes
- 50001 : InvalidResource The resource is disabled or doesn't exist. Check your app's code to ensure that you have specified the exact resource URL for the resource you're trying to access.
- 50034 : UserAccountNotFound - To sign into this application, the account must be added to the directory.
- 50055 : InvalidPasswordExpiredPassword The password is expired. The user's password is expired, and therefore their login or session was ended.
- 50056 : Invalid or null password: password doesn't exist in the directory for this user. The user should be asked to enter their password again.
- 50057 : UserDisabled The user account is disabled. The user object in Active Directory backing this account has been disabled.
- 50126 : InvalidUserNameOrPassword Error validating credentials due to invalid username or password.
- 50131 : ConditionalAccessFailed - Indicates various Conditional Access errors such as bad Windows device state, request blocked due to suspicious activity, access policy, or security policy decisions.
- 50135 : PasswordChangeCompromisedPassword - Password change is required due to account risk.
- 50173 : FreshTokenNeeded - The provided grant has expired due to it being revoked, and a fresh auth token is needed. Either an admin or a user revoked the tokens for this user, causing subsequent token refreshes to fail and require re authentication. Have the user sign in again.
- 51004 : UserAccountNotInDirectory - The user account doesn’t exist in the directory.
- 53003 : BlockedByConditionalAccess - Access has been blocked by Conditional Access policies. The access policy does not allow token issuance.
- 120000 : PasswordChangeIncorrectCurrentPassword
- 120002 : PasswordChangeInvalidNewPasswordWeak
- 120020 : PasswordChangeFailure