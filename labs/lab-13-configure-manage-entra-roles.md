Lab 13: Configure and Manage Microsoft Entra Roles

Objective

Create a custom Microsoft Entra role with specific application management permissions, assign it to a test user, and verify that the assigned permissions work as expected.

Environment

* Tenant: Northstar Technology
* Platform: Microsoft Entra ID
* Role name: Application Registration Administrator
* Test application: Northstar-Test-App
* Assignment: Dedicated test user

1. Create a Custom Role

Navigate to Microsoft Entra ID → Roles and administrators → New custom role.

Configure the role with the following details:

* Role name: Application Registration Administrator
* Description: Allows management of basic properties and credentials for application registrations in the Northstar Technology tenant.
* Baseline permissions: Start from scratch

The custom role was configured with these permissions:

Permission	Purpose
microsoft.directory/applications/basic/update	Update basic application properties
microsoft.directory/applications/credentials/update	Manage application credentials

The selected permissions provide the ability to modify application properties and manage credentials without assigning a broader built-in administrative role.

2. Assign the Custom Role

After creating the role, assign it to a dedicated test user through the role’s assignment settings.

Verify that the test user appears in the assignment list.

3. Create a Test Application

Using the Global Administrator account, navigate to:

Microsoft Entra ID → Applications → App registrations → New registration

Register an application with the following configuration:

* Name: Northstar-Test-App
* Supported account types: Accounts in this organizational directory only
* Redirect URI: Leave blank

Select Register to create the application.

4. Test Basic Application Properties

Sign in to the Microsoft Entra admin center using the dedicated test user account.

Navigate to App registrations and open Northstar-Test-App.

Under Manage → Properties, verify that the Display name field is editable.

Change the display name temporarily and save the change.

The update was successful, confirming that the custom role allows the assigned user to modify basic application properties.

5. Test Application Credential Management

While signed in as the test user, open the application and navigate to:

Manage → Certificates & secrets → Client secrets

Select New client secret and create a temporary secret using the description Lab13-Test-Secret.

The portal successfully created the client secret, confirming that the assigned role allows the user to manage application credentials.

The secret value was not included in the documentation or screenshots.

6. Cleanup

After completing the permission tests:

* Deleted the temporary client secret.
* Restored the application’s original display name, Northstar-Test-App.
* Confirmed that the temporary credential was no longer needed.

Key Takeaways

* Custom Microsoft Entra roles allow administrators to assign specific permissions based on administrative responsibilities.
* Role permissions can be limited to selected tasks rather than granting broad administrative access.
* Role assignments should be verified using a separate test account.
* Testing actual operations helps confirm whether assigned permissions work as intended.
* Temporary credentials should be removed after testing and never exposed in public repositories.

This exercise demonstrated how custom role permissions can support least-privilege access for application registration management.
