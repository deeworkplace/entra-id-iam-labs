# Lab 14: Administrative Units and Delegated Administration

## Objective

Create a Microsoft Entra Administrative Unit (AU), add a user to its administrative scope, and assign a scoped administrative role to demonstrate delegated administration.

This lab explores how Administrative Units help organizations delegate user management responsibilities without granting administrators access to manage the entire tenant.

## Environment

- Platform: Microsoft Entra ID
- Portal: https://entra.microsoft.com
- License: Microsoft Entra ID P2 trial
- Administrative Unit: IT Department
- Administrative Role: User Administrator
- Managed User: Adele Vance
- Delegated Administrator: Chris Green

## 1. Review Administrative Units

Navigated to Microsoft Entra ID > Roles & admins > Admin units.

Administrative Units provide a way to organize directory objects into administrative boundaries. Administrators can receive permissions scoped to a specific AU instead of having unrestricted access across the tenant.

Screenshot:

![Administrative Units overview](../screenshots/lab-14-admin-units-overview.jpg)

## 2. Create the IT Department Administrative Unit

Created a new Administrative Unit with the following settings:

- Name: IT Department
- Description: Administrative unit for delegated IT administration and user management.
- Restricted management administrative unit: No

The Administrative Unit was created successfully.

Screenshots:

![Create IT Department Administrative Unit](../screenshots/lab-14-create-it-department-au.jpg)

![IT Department Administrative Unit created](../screenshots/lab-14-it-department-au-created.jpg)

## 3. Review Administrative Unit Settings

Opened the IT Department Administrative Unit and reviewed its management sections:

- Properties
- Users
- Groups
- Roles

These sections provide access to the objects and administrative role assignments associated with the Administrative Unit.

Screenshot:

![IT Department Administrative Unit](../screenshots/lab-14-it-department-au-overview.jpg)

## 4. Add a User to the Administrative Unit

Created a test user named Adele Vance and added the account to the IT Department Administrative Unit.

Verified that Adele Vance appeared in the AU Users list.

This places the user within the Administrative Unit's administrative scope.

Screenshot:

![Adele Vance added to IT Department AU](../screenshots/lab-14-it-department-au-user-added.jpg)

## 5. Review Group Membership

Opened the Groups section of the IT Department Administrative Unit.

No groups were assigned to the AU during this lab.

Administrative Unit membership is separate from group membership. Adding a group to an AU does not automatically add every member of that group as an individual AU member.

Screenshot:

![IT Department AU groups](../screenshots/lab-14-it-department-au-groups-empty.jpg)

## 6. Review Available Administrative Roles

Opened the Roles section and reviewed the available administrative roles.

Selected User Administrator for the delegated administration exercise.

The User Administrator role provides permissions for managing users, subject to the assigned administrative scope.

Screenshot:

![Available administrative roles](../screenshots/lab-14-it-department-au-available-roles.jpg)

## 7. Assign the User Administrator Role

Started a new role assignment and selected the IT Department Administrative Unit as the assignment scope.

Selected Chris Green as the delegated administrator.

Configured the assignment as Active and entered the following justification:

"Assigning the User Administrator role to a test account within the IT Department Administrative Unit to demonstrate scoped delegated administration and user management."

Completed the assignment and verified that Chris Green appeared under the active User Administrator assignments.

Screenshots:

![User Administrator assignment settings](../screenshots/lab-14-user-administrator-assignment-settings.jpg)

![User Administrator assignment justification](../screenshots/lab-14-user-administrator-assignment-justification.jpg)

![User Administrator role assigned](../screenshots/lab-14-user-administrator-role-assigned.jpg)

## 8. Test Delegated Administration

Signed in to the Microsoft Entra admin center using the Chris Green test account.

Navigated to Microsoft Entra ID > Users > All users.

Chris Green was able to access the user directory.

Opened Adele Vance's profile and confirmed that the account details and available management actions were visible, including the Reset password option.

This demonstrated that the delegated administrator could access the user assigned to the IT Department Administrative Unit.

Screenshot:

![Chris Green accessing the user directory](../screenshots/lab-14-chris-green-user-directory-access.jpg)

![Chris Green viewing Adele Vance's profile](../screenshots/lab-14-chris-green-adele-vance-management.jpg)

## 9. Compare Access to a Global Administrator Account

While signed in as Chris Green, opened the Global Administrator account's profile.

The profile was visible, but the Edit properties option was unavailable. The Reset password option was displayed.

No changes were made to the Global Administrator account.

This provided an additional example of how the delegated administrator's available management actions differed from those of a tenant-wide Global Administrator.

Screenshot:

![Chris Green viewing Global Administrator profile](../screenshots/lab-14-chris-green-global-admin-restricted-access.jpg)

## 10. Results and Key Takeaways

The lab demonstrated the following:

- Created an Administrative Unit named IT Department.
- Added Adele Vance as a member of the Administrative Unit.
- Reviewed the AU's Users, Groups, and Roles sections.
- Assigned the User Administrator role to Chris Green with the IT Department AU as the selected scope.
- Verified the active role assignment.
- Signed in as Chris Green and accessed the user directory.
- Opened Adele Vance's profile and reviewed the available management actions.
- Compared the available actions on a Global Administrator account.

### Key Concepts

**Administrative Unit (AU):** A container used to define an administrative boundary for selected directory objects.

**Scoped Role Assignment:** An administrative role assignment limited to a specific Administrative Unit rather than the entire tenant.

**User Administrator:** A Microsoft Entra role that provides permissions to manage users within the scope of the assignment.

**Delegated Administration:** The practice of assigning administrative responsibilities to other users without granting them unrestricted tenant-wide privileges.

### Observations

Administrative Units help organizations separate administrative responsibilities by department, location, or another organizational structure.

Assigning a role at the AU scope provides more control over which directory objects an administrator can manage. This supports the principle of least privilege by limiting administrative access to the responsibilities assigned.

The test confirmed that Chris Green could access Adele Vance's profile and view available management actions. The comparison with the Global Administrator account also showed differences in available actions.

A complete test of access denial for a user outside the AU was not performed in this exercise.

## Conclusion

This lab demonstrated how Microsoft Entra Administrative Units and scoped role assignments can be used to delegate user management responsibilities.

The exercise provided practical experience creating an AU, adding users, assigning the User Administrator role, and reviewing the permissions available to a delegated administrator.
