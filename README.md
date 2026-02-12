# 🔐 Microsoft Entra ID — User Lifecycle & Access Governance (Manual)

<img width="1536" height="1024" alt="ChatGPT Image Feb 11, 2026 at 11_58_42 PM" src="https://github.com/user-attachments/assets/034e90e7-ec05-4325-a698-51534b3c937a" />

**Platform:** Microsoft Entra ID  
**Scope:** Cloud-only (No Active Directory, No Automation)  
**Focus:** Identity Lifecycle, Group-Based Access, Governance  
**Level:** Beginner → Solid IAM Fundamentals  

---

## 📘 Project Overview

This project demonstrates **manual identity lifecycle management** using Microsoft Entra ID.  
The lab intentionally avoids automation and scripting to highlight **core IAM decision-making**, **access control**, and **governance workflows** commonly handled by IAM analysts.

The environment simulates a real organization managing users through **Joiner, Mover, and Leaver (JML)** scenarios using **cloud-native Entra controls**.

---

## 🎯 Objectives

This lab validates the ability to:

- Create and manage cloud-only identities
- Control access using Entra security groups
- Perform Joiner → Mover → Leaver transitions manually
- Review and revoke access cleanly
- Validate actions using Entra audit and sign-in logs

---

## 🏗️ Environment

- Microsoft Entra ID tenant
- Cloud-only users (no hybrid identity)
- Security groups (assigned membership)
- My Apps portal for access visibility
- Entra audit and sign-in logs

---

## 👤 Identity Lifecycle Implementation

### Joiner (User Onboarding)

Three cloud-only users were created to represent different business roles:

| User | Role |
|-----|-----|
| Felipe-HR | Human Resources user |
| Felipe-IT | IT administrative user |
| Felipe-Temp | Temporary contractor |

Each identity was provisioned directly in Entra ID and managed without automation to reflect hands-on IAM operations.

![Image 2-11-26 at 23 20](https://github.com/user-attachments/assets/6971be81-3b07-456e-a7e4-2e7973c805ab)

---

## 👥 Group-Based Access Control

Access was governed entirely through **Entra security groups**, aligning with least-privilege and role-based access principles.

### Security Groups Implemented

| Group | Purpose |
|-----|-----|
| ENT-All-Users | Baseline access for all identities |
| ENT-HR-Users | HR-specific access |
| ENT-IT-Admins | IT administrative access |

![Image 2-11-26 at 23 23](https://github.com/user-attachments/assets/56c2b48c-902c-49f0-a729-56a9b3c3b5ce)

![Image 2-11-26 at 23 25](https://github.com/user-attachments/assets/b1c77b53-0cc2-427f-9d3e-1c154439bb60)

![Image 2-11-26 at 23 26](https://github.com/user-attachments/assets/5835d949-aac0-4c18-b437-c8844b9ab137)

![Image 2-11-26 at 23 28](https://github.com/user-attachments/assets/87c83b5f-37a9-4f86-b82b-52914e7011c0)

Users were assigned to groups based on their role, ensuring access decisions were **centralized, auditable, and easy to adjust**.

---

## 🔑 Application Access Visibility

Rather than configuring custom SSO integrations, access visibility was validated through the **Microsoft My Apps portal**.

The My Apps portal dynamically reflected group-based access assignments, confirming that:

- Users only saw applications they were entitled to
- Access changed automatically when group membership changed
- No direct application assignment to users was required

This mirrors how end users typically experience access in enterprise environments.

![Image 2-11-26 at 23 40](https://github.com/user-attachments/assets/220f1bbd-baae-413a-8d40-a1e393b34bb6)

![Image 2-11-26 at 23 41](https://github.com/user-attachments/assets/8bb0c2a8-d798-4f11-b433-5312f42df053)

---

## 🔄 Mover Scenario (Role Change)

A role transition was simulated where **Felipe-HR** moved from Human Resources to IT.

- HR group membership was removed
- IT administrative group membership was granted
- Access visibility was revalidated through My Apps

This demonstrated how **role changes are handled cleanly through group membership updates**, without modifying the user object itself.

![Image 2-11-26 at 23 44](https://github.com/user-attachments/assets/b237020f-8a44-4a11-a28c-2e947b3b67e9)

![Image 2-11-26 at 23 44](https://github.com/user-attachments/assets/3407ceb3-5181-4d88-b390-b2dd09868e84)

![Image 2-11-26 at 23 46](https://github.com/user-attachments/assets/903a6216-af45-4efa-b333-62b554a6e159)

---

## 🚪 Leaver Scenario (Offboarding)

The contractor account (**Felipe-Temp**) was offboarded to demonstrate secure access removal.

Actions taken:

- User sign-in was blocked
- Group memberships were removed
- Access visibility was revoked immediately

This reflects standard IAM offboarding practices designed to reduce lingering access risk.

![Image 2-11-26 at 23 50](https://github.com/user-attachments/assets/7a1e6abc-7d28-4b26-bd27-bf2eacf344f2)

![Image 2-11-26 at 23 51](https://github.com/user-attachments/assets/83ef1724-b921-492d-939b-2c1ac3812265)

---

## 🧾 Audit & Governance Evidence

All lifecycle actions were validated using native Entra monitoring tools.

### Audit Logs Reviewed

- User creation events
- Group membership additions and removals
- User disable (block sign-in) events

![Image 2-12-26 at 00 07](https://github.com/user-attachments/assets/b7686bb5-ef31-47e9-810f-d3ded0d1344b)

### Sign-In Logs (Optional Validation)

- Successful sign-in prior to offboarding
- Blocked access after user disable

These logs provide **tamper-proof evidence** of identity and access changes, supporting compliance and security investigations.

![Image 2-12-26 at 00 07](https://github.com/user-attachments/assets/9ea4e7f1-6d64-4eee-b88a-bf13065fda81)

---

## 🧠 Key Takeaways

- Manual IAM processes remain critical even in cloud-native environments
- Group-based access simplifies governance and role transitions
- Joiner, Mover, and Leaver workflows can be enforced without automation
- Audit and sign-in logs are essential for accountability and compliance
- My Apps provides clear end-user access visibility without additional configuration
