# Case 01 — Finance Folder Access Issue

## 📌 Overview

A Finance user reported that they could log in to `FIN-PC01` but could not access the Finance shared folder.

This case was completed collaboratively by [Mr. Hari Krishnan R K](https://github.com/harikrishnan-rk), [Mr. Manu P Nair](https://github.com/manunair16), and [Mr. Varun M Nair](https://github.com/varunmnair95).

Each participant worked in an independent NorthBridge lab environment.

## 👤 My Role

**Documentation / Change Management**

My responsibility was to maintain the case record, document the technical findings and change, verify the supporting evidence, and confirm that the case was properly validated before closure.

## 🎫 Incident

The reported problem was:

> Finance user could log in to `FIN-PC01` but could not access `\\SRV-DC01\Finance`.

The Helpdesk investigation confirmed the reported access failure.

**Helpdesk evidence:**
[Hari — Finance access denied](https://github.com/harikrishnan-rk/Northbridge-Active-Directory/blob/main/cases/case-01-finance-folder-access/evidence/helpdesk/02-finance-access-denied.png)

## 🔎 Technical Findings

IT Support investigated the user's Active Directory group membership and the Finance permission configuration.

The investigation found that the affected user was not a member of `GG_Finance`.

**Investigation evidence:**

* [Manu — User group membership](https://github.com/manunair16/northbridge-active-directory/blob/main/cases/case-01-finance-folder-access/evidence/investigation/01-user-membership.png)
* [Manu — GG_Finance membership](https://github.com/manunair16/northbridge-active-directory/blob/main/cases/case-01-finance-folder-access/evidence/investigation/02-groups-members.png)

The existing Finance permissions were already assigned to `GG_Finance`.

**Permission evidence:**

* [Manu — Share permissions](https://github.com/manunair16/northbridge-active-directory/blob/main/cases/case-01-finance-folder-access/evidence/permissions/03-share-permission.png)
* [Manu — NTFS permissions](https://github.com/manunair16/northbridge-active-directory/blob/main/cases/case-01-finance-folder-access/evidence/permissions/04-ntfs-share-permission.png)

## 🛠️ Change

The affected Finance user was added back to:

`GG_Finance`

The existing Share and NTFS permissions were not changed.

**Change evidence:**
[Manu — User added to GG_Finance](https://github.com/manunair16/northbridge-active-directory/blob/main/cases/case-01-finance-folder-access/evidence/remediation/05-user-added-to-group.png)

## ✅ Validation

After the group membership was restored, access to the Finance shared folder was successfully tested.

**Validation evidence:**
[Manu — Finance access restored](https://github.com/manunair16/northbridge-active-directory/blob/main/cases/case-01-finance-folder-access/evidence/remediation/06-user-access-regained.png)

## 📋 Closure

The reported access problem was resolved by restoring the user's expected Finance security-group membership.

No unnecessary Share or NTFS permission changes were made.

The case can therefore be closed.

## 💡 Lesson Learned

Access changes should follow the existing authorization model. Restoring the expected security-group membership was preferable to creating direct permissions for the individual user.

## 🤝 Collaboration

* [Mr. Hari Krishnan R K](https://github.com/harikrishnan-rk)
* [Mr. Manu P Nair](https://github.com/manunair16)
* [Mr. Varun M Nair](https://github.com/varunmnair95)

Each participant maintained their own evidence and documentation.
