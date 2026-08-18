# 🌐 Case 03 — DNS Service Failure

## 📌 Scenario

NorthBridge reported a DNS resolution problem affecting `MGT-PC01`.

The workstation could communicate with the domain controller, but DNS queries for `northbridge.local` were timing out.

The issue was escalated for server-side investigation.

---

## 🎫 Incident Details

| Item              | Details                |
| ----------------- | ---------------------- |
| Ticket            | `NB-INC-003`           |
| Client            | `MGT-PC01`             |
| Domain Controller | `SRV-DC01`             |
| Domain            | `northbridge.local`    |
| DNS Server        | `SRV-DC01`             |
| DNS Server IP     | `192.168.29.10`        |
| Issue             | DNS Resolution Failure |
| Status            | Resolved               |

---

## 👥 Participants

| Participant                                                 | Role             | Repository                                                                           |
| ----------------------------------------------------------- | ---------------- | ------------------------------------------------------------------------------------ |
| [Mr. Hari Krishnan R K](https://github.com/harikrishnan-rk) | 📝 Documentation | [Hari's Repository](https://github.com/harikrishnan-rk/Northbridge-Active-Directory) |
| [Mr. Manu P Nair](https://github.com/manunair16)            | 🧑‍💻 Helpdesk   | [Manu's Repository](https://github.com/manunair16/northbridge-active-directory)      |
| [Mr. Varun M Nair](https://github.com/varunmnair95)         | 🛠️ IT Support   | [Varun's Repository](https://github.com/varunmnair95/northbridge-active-directory)   |

---

## 🛠️ My Role — IT Support

My responsibility was to investigate the server-side cause of the DNS resolution failure, identify the root cause, restore the affected service, and validate the resolution.

---

## 🔎 Server-Side Investigation

### 1. Checked DNS Server service

The DNS Server service on `SRV-DC01` was checked using:

```powershell
Get-Service -Name DNS
```

The service was found to be stopped.

📸 Evidence: [DNS Service Stopped](https://github.com/varunmnair95/northbridge-active-directory/blob/main/cases/case-03-dns-service-failure/evidence/01-dns-service-investigation.png)

### 2. Checked DNS Server role

DNS Server was reviewed through Server Manager to confirm that the DNS role was still present on `SRV-DC01`.

📸 Evidence: [DNS Server Manager](https://github.com/varunmnair95/northbridge-active-directory/blob/main/cases/case-03-dns-service-failure/evidence/02-dns-manager-investigation.png)

### 3. Confirmed service state

The DNS Server service status and configuration were checked again.

The service was confirmed as stopped while its startup type remained `Automatic`.

📸 Evidence: [DNS Service Confirmed Stopped](https://github.com/varunmnair95/northbridge-active-directory/blob/main/cases/case-03-dns-service-failure/evidence/03-dns-manager-investigation.png)

---

## 🧠 Root Cause

The **DNS Server service on `SRV-DC01` was stopped**.

The DNS role remained installed and the server itself was reachable.

The client-side evidence and server-side investigation supported the conclusion that the DNS service was the cause of the resolution failure.

---

## 🛠️ Resolution

The DNS Server service was started using:

```powershell
Start-Service -Name DNS
```

The service was then checked again using:

```powershell
Get-Service -Name DNS
```

The service was confirmed as `Running`.

📸 Evidence: [DNS Service Restored](https://github.com/varunmnair95/northbridge-active-directory/blob/main/cases/case-03-dns-service-failure/evidence/04-dns-service-restored.png)

---

## ✅ Validation

After restoring the DNS Server service:

1. The service was confirmed as `Running`.
2. DNS resolution was tested again from `MGT-PC01`.
3. `northbridge.local` successfully resolved.
4. The DNS server address was returned.

This confirmed that the original DNS resolution problem had been resolved.

---

## 🔗 Investigation & Evidence

The initial client-side investigation was performed by:

🧑‍💻 **[Manu — Helpdesk](https://github.com/manunair16/northbridge-active-directory/tree/main/cases/case-03-dns-service-failure)**

The client-side evidence established that:

* DNS queries were failing.
* `SRV-DC01` remained reachable.

This provided the basis for the server-side investigation.

---

## 💡 Lessons Learned

* 🌐 DNS is a critical dependency for Active Directory.
* 🔎 A reachable server does not necessarily mean its DNS service is functioning.
* 🛠️ Server-side service status should be checked when DNS queries fail.
* ⚙️ The DNS role can remain installed while the DNS Server service is stopped.
* ✅ Service restoration should always be followed by client-side validation.

---

## 🤝 Collaboration

This case was completed collaboratively by:

* [Mr. Hari Krishnan R K](https://github.com/harikrishnan-rk)
* [Mr. Manu P Nair](https://github.com/manunair16)
* [Mr. Varun M Nair](https://github.com/varunmnair95)

Manu performed the initial client-side investigation and validation.

I performed the server-side investigation and DNS service restoration.

Hari handled documentation and coordination. [Hari Documentation](https://github.com/harikrishnan-rk/northbridge-active-directory/tree/main/cases/case-03-dns-service-failure)

Each participant maintained their own implementation and evidence in an independent NorthBridge Active Directory lab.
