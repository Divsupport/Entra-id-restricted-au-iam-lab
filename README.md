<h1 align="center">🔐 Microsoft Entra ID Restricted Administrative Unit (AU) IAM Lab</h1>

<h3 align="center">
Built by <span style="color:#0078D4;">Divine Oguamanam</span>
</h3>

---

<h2>📖 Description</h2>

This project demonstrates the implementation of a secure Identity and Access Management (IAM) governance model using Microsoft Entra ID Administrative Units (AUs), scoped Role-Based Access Control (RBAC), Security Groups, and Microsoft 365 delegated ownership.

The lab simulates a real-world enterprise environment where regional administrators require restricted administrative access without exposing the entire tenant to unnecessary privilege escalation risks.

In this project, I created a New York Administrative Unit, assigned a scoped Hybrid Identity Administrator role to a regional administrator, deployed Security and Microsoft 365 groups, and validated administrative boundaries between delegated administrators and group owners.

<h3>🔑 Key Focus Areas</h3>

- Least Privilege
- Scoped Administration
- Delegated Ownership
- Administrative Units
- RBAC
- Microsoft Entra ID Governance
- Identity Security Validation

<br />

<h2>🛠️ Technologies and Services Used</h2>

- <b>Microsoft Entra ID</b>
- <b>Azure Portal</b>
- <b>Microsoft 365 Groups</b>
- <b>Administrative Units (AU)</b>
- <b>Security Groups</b>
- <b>RBAC</b>
- <b>Hybrid Identity Administrator Role</b>

---

<h2>💻 Environment Used</h2>

- <b>Microsoft Entra ID Tenant</b>
- <b>Windows 11</b>
- <b>Microsoft Azure Portal</b>

---

<h2>🎯 Project Objectives</h2>

- Create a restricted Administrative Unit for New York users
- Assign scoped Hybrid Identity Administrator permissions
- Implement least privilege access controls
- Create Security Groups for regional workforce management
- Deploy Microsoft 365 collaboration groups with delegated ownership
- Validate permission boundaries between administrators and group owners
- Simulate enterprise IAM governance architecture

---

<h2>🏗️ Architecture Overview</h2>

<p align="center">
Regional IAM Structure <br/>
<img src="images/step1.png" height="80%" width="80%" alt="Architecture Overview"/>
</p>

---

<h2>🚀 Project Walk-through</h2>

<p align="center">

So I will be working on this project or lab on the Entra ID space on the Entra.microsoft.com  or Portal.azure.com so my first plan is:

1) Create 2 users called Bob Jones and Greg Johnson on the Microsoft Entra admin center.

👤 Overview of the Microsoft Entra admin center: <br/><br/>
<img src="Images/step 1.jpg"/>
<br />
<br />













































---

<h2>🔒 Security Concepts Demonstrated</h2>

- Least Privilege Access
- Scoped Administrative Control
- Delegated Administration
- RBAC Enforcement
- Identity Governance
- Microsoft Entra ID Administrative Units
- Access Boundary Validation
- Group Ownership Isolation
- Separation of Duties

---

<h2>📊 Key Validation Results</h2>

✅ Bob Jones successfully managed Security Group memberships inside the New York Administrative Unit

✅ Bob Jones was blocked from modifying Microsoft 365 collaboration groups

✅ Greg Johnson successfully managed the Microsoft 365 group he owned

✅ Greg Johnson could not manage Security Groups outside his ownership scope

✅ Administrative boundaries were successfully enforced through scoped RBAC assignments

---

<h2>📚 Lessons Learned</h2>

This project reinforced the importance of restricting administrative access to only the resources required for a user's responsibilities.

The lab also demonstrated how Microsoft Entra ID Administrative Units isolate regional management boundaries while still allowing centralized tenant oversight from higher-level administrators.

Through validation testing, the project confirmed that delegated ownership and scoped RBAC assignments coexist securely without introducing unnecessary tenant-wide exposure.

---

<h2>🚧 Future Improvements</h2>

Future phases of this project will include:

- PowerShell automation
- Microsoft Graph API integration
- Automated user provisioning
- Automated group management
- Identity lifecycle automation
- Azure-based IAM workflows

---

<h2>🤝 Connect With Me</h2>

<p align="left">
<a href="https://linkedin.com/in/divine-oguamanam-a21765337" target="blank">
<img align="center" src="https://cdn.jsdelivr.net/npm/simple-icons@v3/icons/linkedin.svg" height="30" width="40" />
</a>

<a href="https://twitter.com/syskko" target="blank">
<img align="center" src="https://cdn.jsdelivr.net/npm/simple-icons@v3/icons/twitter.svg" height="30" width="40" />
</a>
</p>

