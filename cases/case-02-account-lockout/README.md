# 🔐 Case 02 — Account Lockout

## 📌 Scenario

Kevin Thomas, an Operations Executive, reported that he could not sign in to `OPS-PC01` because his NorthBridge domain account was locked.

The issue was intentionally simulated in the isolated NorthBridge Active Directory lab.

---

## 🎫 Incident Details

| Item              | Details             |
| ----------------- | ------------------- |
| Ticket            | `NB-INC-002`        |
| User              | Kevin Thomas        |
| Department        | Operations          |
| Client            | `OPS-PC01`          |
| Domain Controller | `SRV-DC01`          |
| Domain            | `northbridge.local` |
| Issue             | Account Lockout     |
| Status            | Resolved            |

---

## 👥 Participants

| Participant                                                 | Role             | Repository                                                                           |
| ----------------------------------------------------------- | ---------------- | ------------------------------------------------------------------------------------ |
| [Mr. Hari Krishnan R K](https://github.com/harikrishnan-rk) | 🛠️ IT Support   | [Hari's Repository](https://github.com/harikrishnan-rk/Northbridge-Active-Directory) |
| [Mr. Manu P Nair](https://github.com/manunair16)            | 📝 Documentation | [Manu's Repository](https://github.com/manunair16/northbridge-active-directory)      |
| [Mr. Varun M Nair](https://github.com/varunmnair95)         | 🧑‍💻 Helpdesk   | [Varun's Repository](https://github.com/varunmnair95/northbridge-active-directory)   |

---

## 🧑‍💻 My Role — Helpdesk

My responsibility was to reproduce the reported issue, perform basic endpoint and connectivity checks, collect initial evidence, and escalate the incident for Active Directory investigation.

---

## 🔎 Initial Investigation

### 1. Reproduced the login failure

The account-lockout message was reproduced on `OPS-PC01`.

📸 Evidence:

`evidence/helpdesk/01-account-locked.png`

### 2. Confirmed the workstation

The workstation identity was confirmed using:

```cmd
hostname
```

📸 Evidence:

`evidence/helpdesk/02-workstation.png`

### 3. Checked Domain Controller connectivity

DNS resolution and basic connectivity to `SRV-DC01` were checked using:

```cmd
nslookup SRV-DC01
ping SRV-DC01
```

📸 Evidence:

`evidence/helpdesk/03-domain-connectivity.png`

---

## 🧠 Helpdesk Finding

Kevin's account was confirmed to be locked.

Basic connectivity from `OPS-PC01` to `SRV-DC01` was available, so the incident was escalated for Active Directory investigation.

The account was not unlocked during Helpdesk triage.

---

## 🔗 Investigation & Resolution

The Active Directory investigation and remediation were performed by:

🛠️ **[Hari — IT Support](https://github.com/harikrishnan-rk/Northbridge-Active-Directory/tree/main/cases/case-02-account-lockout)**

The final documentation and validation were completed by:

📝 **[Manu — Documentation](https://github.com/manunair16/northbridge-active-directory/tree/main/cases/case-02-account-lockout)**

---

## 💡 Lessons Learned

* 🔎 Reproduce the reported problem before changing anything.
* 🌐 Basic connectivity checks help eliminate simple client-side causes.
* 🔐 An account lockout should be investigated rather than immediately unlocked.
* 📤 A good Helpdesk escalation provides evidence and useful findings to the next support level.

---

## 🤝 Collaboration

This case was completed collaboratively by:

* [Mr. Hari Krishnan R K](https://github.com/harikrishnan-rk)
* [Mr. Manu P Nair](https://github.com/manunair16)
* [Mr. Varun M Nair](https://github.com/varunmnair95)

Each participant maintained their own implementation and evidence in an independent NorthBridge Active Directory lab.
