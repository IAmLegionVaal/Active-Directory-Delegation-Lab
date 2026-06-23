# Active Directory Delegation Lab

![Status](https://img.shields.io/badge/Project-Completed-success)
![Active Directory](https://img.shields.io/badge/Directory-Active%20Directory-0078D4)
![Least Privilege](https://img.shields.io/badge/Focus-Least%20Privilege-2F6FED)

A completed Active Directory lab in which I delegated limited administrative permissions at the OU level and validated that the delegated operator could perform only the intended tasks.

> **Status:** Completed and validated. This repository documents work already performed in a private lab. Real names, accounts, OUs, groups and domain details have been generalized.

## Objectives completed

- Created a dedicated OU for delegation testing
- Created or selected a limited administrative group
- Delegated specific user-management tasks
- Tested password reset and account-management permissions
- Confirmed that unrelated OUs remained protected
- Verified denied actions outside the delegated scope
- Reviewed permissions and audit evidence
- Documented least-privilege findings

## Implementation summary

1. Created a controlled OU containing test user objects.
2. Created a role-based group for delegated support staff.
3. Used the Delegation of Control Wizard to grant specific tasks.
4. Signed in or launched management tools with the delegated account.
5. Tested permitted actions such as resetting a password or updating selected attributes.
6. Tested prohibited actions inside and outside the delegated OU.
7. Reviewed the resulting access-control entries.
8. Removed broad permissions that were not required.
9. Documented the final scope and validation results.

## Validation commands

```powershell
Get-ADOrganizationalUnit -Filter *
Get-ADGroupMember "<delegated-group>"
(Get-Acl "AD:\OU=<test-ou>,DC=<domain>,DC=<suffix>").Access
```

## Outcome

The delegated operator successfully performed the approved support tasks within the selected OU but could not administer protected objects outside that scope. The lab confirmed that routine support responsibilities could be separated from full domain-administrator rights.

## Findings

- OU structure was a security boundary for delegated administration as well as an organizational tool.
- Delegating a narrow task to a group was easier to manage and revoke than assigning rights directly to individual technicians.
- Successful testing required both positive and negative cases: the operator had to complete approved tasks and fail at unauthorized ones.
- Permissions applied to the wrong OU or inherited too broadly could create unexpected administrative reach.
- The Delegation of Control Wizard simplified common tasks, but reviewing the resulting ACLs was still important for understanding the effective permissions.
- Full Domain Admin membership was unnecessary for many common helpdesk actions such as password resets and account unlocks.

## Skills demonstrated

- Active Directory delegation
- OU-based administration
- Access-control entry review
- Role-based security groups
- Least-privilege design
- Positive and negative permission testing
- Administrative scope validation
- Technical documentation

## Security notes

- No real privileged identity or domain information is included.
- All account and OU names are generalized.
- The lab was completed in a controlled non-production environment.

## Author

**Dewald Pretorius** — L2 IT Support Engineer
