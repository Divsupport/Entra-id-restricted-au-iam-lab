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

This image is the Microsoft Entra admin portal, and you can see me as a global admin as Divine Oguamanam, and my domain is syskko.onmicrosoft.com. The global admin have total access to every single setting, from reading every email to deleting the entire company directory. And there are the only ones who can assign roles to other people, manage billing/licenses, and reset passwords for other administrators. 

<img src="Images/step 2.jpg"/> <br />

<img src="Images/step 3.jpg"/> <br />

Before running large automation scripts, it is best practice to manually create test users within the GUI portal. This ensures that the tenant domain configuration, licensing environment, and basic identity parameters are functioning correctly. 

 <br />

 <img src="Images/step 4.jpg"/> <br />

 
- I navigated to the Microsoft Azure Portal (portal.azure.com) -> Microsoft Entra ID -> Users -> Create new user. 
- User Principal Name (UPN): Set to Bobjones@syskko.onmicrosoft.com. This serves as the user's primary cloud login identity and email routing prefix.
- Mail Nickname: Automatically derived from the UPN prefix (Bobjones) to handle mail routing alias properties.
- Display Name: Set to Bobjones for clear directory identification across Microsoft 365 services (Teams, Outlook). 
- Password Management: A strong, custom temporary password was manually assigned, and the account status was explicitly toggled to Account enabled ($true) to allow immediate authentication testing post-creation.

I will go to Next: Properties

<img src="Images/step 5.jpg"/> <br />

After establishing the core identity parameters (UPN and Display Name), the next phase involves enriching the user profile with organizational metadata. This metadata is critical for Role-Based Access Control (RBAC), auditing, and dynamic group assignments.To align with corporate identity hierarchies, Bob Jones's profile is configured with a high-level engineering title, establishing him as the primary administrator of the cloud tenant environment.

 <br />

<img src="Images/step 6.jpg"/> <br />

<img src="Images/step 7.jpg"/> <br />


For this phase of the lab, I navigated to the Assignments tab to configure the necessary permissions matching Bob Jones's engineering profile. To avoid over-provisioning the account with global access, I clicked + Add role and selected the Hybrid Identity Administrator role instead of Global Administrator. This specific role gives Bob the required technical capability to manage corporate authentication policies, directory sync features, and identity infrastructure configurations without granting unnecessary control over non-identity systems like company billing, SharePoint data, or Exchange email routing.


<img src="Images/step 8.jpg"/> <br />

This is the summary of the user creation so i click on create and it will create Bob as a user.

 <br />

<img src="Images/step 9.jpg"/> <br />

<img src="Images/step 10.jpg"/> <br />

After creating the account, I opened Bob Jones's Overview page in Microsoft Entra ID to make sure everything worked correctly. This page shows the real-world status of the user. 

- Account is Active: The page shows Account status: Enabled, which means Bob can log in right away.
- Unique ID Created: Entra ID gave him a unique Object ID (771256e2...). The system uses this long number to identify Bob behind the scenes, ensuring his account never gets mixed up with anyone else.
- Role is Attached: It shows Assigned roles: 1. This proves that his Hybrid Identity Administrator role successfully attached to his account when it was made.

<img src="Images/step 11.jpg"/> <br />

During my security audit of Bob Jones's profile, i went to assigned roles and i noticed his role Scope was set to Directory. For this project, Bob is strictly supposed to be a regional administrator for New York. Leaving his scope as "Directory" is a major security risk because it gives him administrative power over the entire company instead of just his assigned region.
To fix this security flaw and enforce the Principle of Least Privilege, I executed the following steps:

- Stripping the Global Power: On this Assigned roles screen, I clicked the Remove button next to his role. This completely took away his tenant-wide "Directory" powers, turning him back into a regular user.
- Applying Regional Scope: Instead of assigning roles directly to his user profile, I navigated out of this menu and opened the NY-Administrative-Unit that I created for the project.
- Assigning the Scoped Role: Inside the New York AU settings, I went to Roles and administrators, selected the admin role, and assigned it to Bob Jones there. 

<img src="Images/step 12.jpg"/> <br />
<img src="Images/step 13.jpg"/> <br />
<img src="Images/step 14.jpg"/> <br />
<img src="Images/step 15.jpg"/> <br />

To limit Bob Jones's administrative power strictly to New York, I navigated to Administrative units and started creating the management boundary for this project.

- Name Configuration: I named the unit NY-Administrative-Unit to clearly state its regional purpose.
- The Critical Choice (Restricted Management Administrative Unit): I selected No for the "Restricted management administrative unit" option.

Choosing No is the standard approach for a regional office setup. It means that while Bob Jones will be given the Hybrid Identity Administrator role scoped inside this specific New York unit to manage local users, higher-level tenant administrators (like the main Global Admin) can still see, manage, and help troubleshoot these New York accounts if needed. This keeps the New York team managed locally by Bob, without locking out central IT support.

<img src="Images/step 16.jpg"/> <br />

I chose not to assign any roles and skipped directly to the next step.
Leaving this blank is a deliberate security decision for this project. Assigning a role at this stage applies it globally across the entire tenant directory. To ensure Bob Jones's administrative privileges are strictly confined to the New York branch, his role will be assigned directly inside the completed NY-Administrative-Unit container later, rather than during this initial creation wizard.

<img src="Images/step 17.jpg"/> <br />

Now create 

<img src="Images/step 18.jpg"/> <br />

Now the New York Adminstrative unit have been created.

<img src="Images/step 19.jpg"/> <br />

Now that the NY-Administrative-Unit is created, I need to add Bob Jones here so his admin powers only work inside this specific New York box.
Here is exactly what I will do on this screen:

<img src="Images/step 20.jpg"/> <br />


- First, I will stay on this Users tab and click + Add member. I will search for Bob Jones and add him to the unit. This places his account inside the New York management boundary.

<img src="Images/step 21.jpg"/> <br />

<img src="Images/step 22.jpg"/> <br />

- Next, I will look at the left-hand menu and click on Roles and administrators. Inside that menu, I will find the Hybrid Identity Administrator role on the search bar and click on it.

<img src="Images/step 23.jpg"/> <br />

<img src="Images/step 24.jpg"/> <br />

- I will click "+ Add assignments": I will click the button circled in red to start the assignment process.
- Select Bob Jones: In the pane that pops up, I will search for and select Bob Jones as the user.
- Because this assignment is being built inside the NY-Administrative-Unit container, the system will automatically restrict his Hybrid Identity Administrator powers.

 <img src="Images/step 25.jpg"/> <br />










































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

