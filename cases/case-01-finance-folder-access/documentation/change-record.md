# Change Record — NB-CHG-001

## Change Details

| Field          | Details                   |
| -------------- | ------------------------- |
| Related Ticket | `NB-INC-001`              |
| Change Type    | Access / Group Membership |
| Affected User  | `northbridge\sara.m`      |
| Security Group | `GG_Finance`              |
| Change         | Restore user membership   |
| Status         | Completed                 |

## Reason for Change

The Finance user's access to the Finance shared folder was denied because the user was not a member of the security group used by the existing Finance access-control model.

The technical investigation confirmed that `GG_Finance` already had the required Share and NTFS permissions.

[View Manu's technical findings](https://github.com/manunair16/northbridge-active-directory/blob/main/cases/case-01-finance-folder-access/documentation/technical-findings.md)

## Change Performed

The affected user was added to:

`GG_Finance`

[View change evidence](https://github.com/manunair16/northbridge-active-directory/blob/main/cases/case-01-finance-folder-access/evidence/remediation/05-user-added-to-group.png)

## Changes Not Performed

The following were intentionally left unchanged:

* Finance Share permissions
* Finance NTFS permissions
* User account configuration

This avoided introducing unnecessary permission changes.

## Validation

The user successfully accessed:

`\\SRV-DC01\Finance`

after the group membership was restored.

[View validation evidence](https://github.com/manunair16/northbridge-active-directory/blob/main/cases/case-01-finance-folder-access/evidence/remediation/06-user-access-regained.png)

## Security Consideration

Restoring the existing security-group membership maintains centralized access management.

Granting direct permissions to the individual user would have created an unnecessary exception to the existing access-control model.

## Change Outcome

**Successful**

The user's intended Finance access was restored and the original incident was resolved.

