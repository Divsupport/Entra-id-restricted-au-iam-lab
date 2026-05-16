# Entra-ID-Restricted-AU-IAM-lab

<h1>Microsoft Entra ID Restricted Administrative Unit (AU) IAM Lab</h1>

<h2>Description</h2>

This project demonstrates the implementation of a secure Identity and Access Management (IAM) governance model using Microsoft Entra ID Administrative Units (AUs), scoped Role-Based Access Control (RBAC), Security Groups, and Microsoft 365 delegated ownership.

The lab was designed to simulate a real-world enterprise environment where regional administrators require restricted administrative access without exposing the entire tenant to unnecessary privilege escalation risks.

In this project, I created a New York Administrative Unit, assigned a scoped Hybrid Identity Administrator role to a regional administrator, deployed Security and Microsoft 365 groups, and validated access boundaries between delegated administrators and group owners.

The project focuses heavily on:
- Least Privilege
- Scoped Administration
- Delegated Ownership
- Administrative Units
- RBAC
- Microsoft Entra ID Governance
- Identity Security Validation

<br />

<h2>Technologies and Services Used</h2>

- <b>Microsoft Entra ID</b>
- <b>Azure Portal</b>
- <b>Microsoft 365 Groups</b>
- <b>Administrative Units (AU)</b>
- <b>Security Groups</b>
- <b>RBAC</b>
- <b>Hybrid Identity Administrator Role</b>

<h2>Environment Used</h2>

- <b>Microsoft Entra ID Tenant</b>
- <b>Windows 11</b>
- <b>Microsoft Azure Portal</b>

<h2>Project Objectives</h2>

- Create a restricted Administrative Unit for New York users
- Assign scoped Hybrid Identity Administrator permissions
- Implement least privilege access controls
- Create Security Groups for regional workforce management
- Deploy Microsoft 365 collaboration groups with delegated ownership
- Validate permission boundaries between administrators and group owners
- Simulate enterprise IAM governance architecture

<h2>Architecture Overview</h2>

<p align="center">
Regional IAM Structure <br/>
<img src="images/01-architecture-overview.png" height="80%" width="80%" alt="Architecture Overview"/>
</p>

<h2>Project Walk-through</h2>

<p align="center">

















































<h2>Security Concepts Demonstrated</h2>

- Least Privilege Access
- Scoped Administrative Control
- Delegated Administration
- RBAC Enforcement
- Identity Governance
- Microsoft Entra ID Administrative Units
- Access Boundary Validation
- Group Ownership Isolation
- Separation of Duties

<h2>Key Validation Results</h2>

- Bob Jones successfully managed Security Group memberships inside the New York Administrative Unit
- Bob Jones was blocked from modifying Microsoft 365 collaboration groups
- Greg Johnson successfully managed the Microsoft 365 group he owned
- Greg Johnson could not manage Security Groups outside his ownership scope
- Administrative boundaries were successfully enforced through scoped RBAC assignments

<h2>Lessons Learned</h2>

This project reinforced the importance of restricting administrative access to only the resources required for a user's responsibilities.

The lab also demonstrated how Microsoft Entra ID Administrative Units can isolate regional management boundaries while still allowing centralized tenant oversight from higher-level administrators.

Through validation testing, the project confirmed that delegated ownership and scoped RBAC assignments can coexist securely without introducing unnecessary tenant-wide exposure.

<h2>Future Improvements</h2>

Future phases of this project will include:
- PowerShell automation
- Microsoft Graph API integration
- Automated user provisioning
- Automated group management
- Identity lifecycle automation
- Azure-based IAM workflows

<!--
 ```diff
- Scoped RBAC
+ Administrative Units
! Least Privilege
# Identity Governance
@@ Delegated Administration @@
```
-->












