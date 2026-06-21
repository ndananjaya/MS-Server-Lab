<<<<<<< HEAD
# MS Server Lab Portfolio

This repository contains my hands-on Microsoft Server practical exercises.

## Active Directory Labs

| Lab | Description                              |
| --- | ---------------------------------------- |
| 01  | Install Active Directory Domain Services |
| 02  | Create Domain                            |
| 03  | Create Organizational Units              |
| 04  | Create Users                             |
| 05  | Create Groups                            |
| 06  | Configure Group Policies                 |
| 07  | Configure Shared Folders                 |

## Technologies Used

- Windows Server 2025
- Active Directory
- DNS
- Group Policy
- File Services
=======
## 🏢 Scenario: “TechWave Solutions Pvt Ltd” – AD DS Lab Project

## 🧾 Company Overview

TechWave Solutions is a mid-sized IT company with multiple departments and a growing workforce. They are upgrading their infrastructure and want a centralized Active Directory system for:

* User management
* Security policies
* File sharing
* Department-level access control
* Remote work support

---

# 🌐 Domain Setup Requirements

* **Domain Name:** `techwave.local`
* **NetBIOS Name:** TECHWAVE
* **Domain Controller:** `DC1`
* **IP Range:** `192.168.10.0/24`
* **Server Name:** `DC1.techwave.local`

---

# 🏢 Organizational Units (OU Structure)

techwave.local
│
├── HeadOffice
│   ├── IT_Department
│   ├── HR_Department
│   ├── Finance_Department
│   ├── Sales_Department
│   └── Management
│
├── BranchOffice
│   ├── Support_Team
│   └── Sales_Team
│
├── Groups
│
├── ServiceAccounts
│
└── Disabled_Accounts
```

---

# 👨‍💼 Users (Create sample accounts)

### IT Department

* it.admin1
* it.support1
* it.support2

### HR Department

* hr.manager1
* hr.officer1
* hr.officer2

### Finance Department

* finance.lead1
* finance.officer1
* finance.officer2

### Sales Department

* sales.exec1
* sales.exec2
* sales.exec3

### Management

* ceo.techwave
* cto.techwave

### Support Team (Branch)

* support1
* support2

---

# 👥 Groups (Security Groups)

 **security groups (not distribution groups)**:

* IT_Admins
* IT_Staff
* HR_Staff
* Finance_Staff
* Sales_Staff
* Management_Group
* Branch_Support

👉 All users must be added to appropriate groups (NOT direct permissions to users).

---

# 📁 Shared Folder Structure (File Server Requirement)

On a server (DC1 or a separate File Server), :

```
D:\CompanyShares
│
├── IT_Share
├── HR_Share
├── Finance_Share
├── Sales_Share
├── Management_Share
└── Public_Share
```

---

# 🔐 Folder Permission Rules

### General Rules

* Each department folder:

  * Only IT department group = Full Control
  * Domain Admins = Full Control
  * Others = No Access

---

### Specific Rules

#### IT_Share

* IT_Admins → Full Control
* IT_Staff → Modify
* Others → No Access

#### HR_Share

* HR_Staff → Full Control
* Management_Group → Read Only

#### Finance_Share

* Finance_Staff → Full Control
* Only CEO + CTO → Read access

#### Sales_Share

* Sales_Staff → Full Control
* Branch_Support → Read Only

#### Management_Share

* Only Management_Group → Full Control
* Domain Admins → Full Control

#### Public_Share

* All domain users → Read/Write

---

# 🧠 Group Policy Objects (GPOs)

Create and link GPOs at appropriate OUs.

## 1. Password Policy (Domain-wide)

* Minimum length: 10 characters
* Complexity enabled
* Max password age: 45 days
* Lockout after 5 attempts

---

## 2. Desktop Restriction Policy (All Users)

* Remove Control Panel access
* Disable CMD for non-IT users
* Prevent access to Registry Editor

---

## 3. IT Department GPO

* Allow CMD + PowerShell
* Allow Remote Desktop access
* Disable Windows Store

---

## 4. HR & Finance Security Policy

* Disable USB storage devices
* Prevent software installation
* Enable audit logging

---

## 5. Login Banner Policy

Display message:

> “This system is monitored. Unauthorized access is prohibited.”

---

## 6. Drive Mapping Policy

Automatically map drives:

* IT → `\\DC1\IT_Share`
* HR → `\\DC1\HR_Share`
* Finance → `\\DC1\Finance_Share`
* Sales → `\\DC1\Sales_Share`
* All users → `\\DC1\Public_Share`

---



---

>>>>>>> 8a2d03023985826dd295231fde15f742d6fc9608
