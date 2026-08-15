# Incident Record — NB-INC-001

## Incident Details

| Field         | Details                           |
| ------------- | --------------------------------- |
| Ticket        | `NB-INC-001`                      |
| Category      | File Access                       |
| Priority      | Medium                            |
| Affected User | `northbridge\sara.m`              |
| Workstation   | `FIN-PC01`                        |
| Resource      | `\\SRV-DC01\Finance`              |
| Status        | Resolved                          |
| Case Role     | Documentation / Change Management |

## Incident Summary

A Finance user was able to authenticate to the Windows workstation but could not access the Finance shared folder.

The Helpdesk participant reproduced the issue and collected the initial evidence.

[View Hari's Helpdesk evidence](https://github.com/harikrishnan-rk/Northbridge-Active-Directory/tree/main/cases/case-01-finance-folder-access/evidence/helpdesk)

## Investigation

IT Support reviewed:

* User group membership
* `GG_Finance` membership
* Finance Share permissions
* Finance NTFS permissions

The investigation established that the affected user was not a member of `GG_Finance`.

[View Manu's technical findings](https://github.com/manunair16/northbridge-active-directory/blob/main/cases/case-01-finance-folder-access/documentation/technical-findings.md)

## Resolution

The user's membership in `GG_Finance` was restored.

The existing Share and NTFS permissions were left unchanged.

## Validation

Access to the Finance shared folder was successfully restored after the group membership change.

[View validation evidence](https://github.com/manunair16/northbridge-active-directory/blob/main/cases/case-01-finance-folder-access/evidence/remediation/06-user-access-regained.png)

## Closure

The original user-reported problem was resolved.

The resolution restored the intended access-control model without introducing unnecessary individual permissions.

**Final Status:** Resolved / Closed

