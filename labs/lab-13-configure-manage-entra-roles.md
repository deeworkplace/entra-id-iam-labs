# Lab 13: Configure and Manage Microsoft Entra Roles

## Objective

Create a custom Microsoft Entra role, assign it to a test user, and verify that the assigned permissions allow application property and credential management.

## 1. Create a Custom Role

Navigate to Microsoft Entra ID → Roles and administrators → New custom role.

Configure the following:

- Role Name: Application Registration Administrator
- Description: Allows management of basic properties and credentials for application registrations in the Northstar Technology tenant.
- Baseline Permissions: Start from scratch

![Custom Role Entry](../screenshots/lab-13-custom-role-entry.jpg)

![Custom Role Basics](../screenshots/lab-13-custom-role-basics.jpg)

Add the following permissions:

| Permission | Description |
|---|---|
| `microsoft.directory/applications/basic/update` | Update basic application properties. |
| `microsoft.directory/applications/credentials/update` | Manage application credentials. |

![Custom Role Permissions](../screenshots/lab-13-custom-role-permissions.jpg)

Review the selected permissions before creating the custom role.

![Custom Role Review](../screenshots/lab-13-custom-role-review.jpg)

## 2. Assign the Custom Role

Open the newly created role and select Add assignments.

Assign the Application Registration Administrator role to a dedicated test user. Verify that the account appears in the assignment list.

![Custom Role Created](../screenshots/lab-13-custom-role-created.jpg)

![Custom Role Assignment](../screenshots/lab-13-custom-role-assignment.png)

![Assignment Verification](../screenshots/lab-13-custom-role-assignment-verification.png)

## 3. Create a Test Application

Using the Global Administrator account, navigate to:

Microsoft Entra ID → Applications → App registrations → New registration

Register an application with these settings:

- Name: Northstar-Test-App
- Supported Account Types: Accounts in this organizational directory only
- Redirect URI: Leave blank

Select Register to create the application.

![Test Application Created](../screenshots/lab-13-test-application-created.png)

## 4. Verify Basic Application Property Permissions

Sign in to the Microsoft Entra admin center using the dedicated test user account.

Open App registrations → Northstar-Test-App → Manage → Properties.

Verify that the Display name field is editable. Temporarily change the display name and select Save.

The update completed successfully, confirming that the assigned custom role permits changes to basic application properties.

![Basic Properties Permission Test](../screenshots/lab-13-custom-role-basic-properties-test.png)

## 5. Verify Application Credential Permissions

While signed in as the test user, navigate to:

Northstar-Test-App → Manage → Certificates & secrets → Client secrets

Select New client secret and create a temporary secret with the description Lab13-Test-Secret.

The portal successfully created the client secret, confirming that the assigned custom role permits application credential management.

The secret value was not included in the documentation or screenshots.

![Credential Permission Test](../screenshots/lab-13-custom-role-credentials-test.png)

## 6. Cleanup

After completing the permission tests:

- Deleted the temporary client secret.
- Restored the application's original display name, Northstar-Test-App.
- Confirmed that the temporary credential was no longer needed.

## Key Takeaways

- Custom Microsoft Entra roles provide granular control over administrative permissions.
- Specific permissions can be assigned without granting broader administrative privileges.
- Testing with a separate account helps verify that role assignments work as intended.
- Application property and credential management permissions can be tested independently.
- Temporary credentials should be removed after testing and must never be exposed in public repositories.
