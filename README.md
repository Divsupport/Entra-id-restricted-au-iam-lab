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

1) To create 2 users called Bob Jones and Greg Johnson on the Microsoft Entra admin center.

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

On this screen, I am configuring how Bob Jones's Hybrid Identity Administrator role behaves over time.

Before hitting assign, there are two key tasks to handle on this page:

- Fixing the Error (Enter Justification): The system shows a red warning because the Enter justification box is mandatory. For this lab, I will type a direct reason into the box, such as: "Assigning regional identity permissions for the New York branch deployment."
- I selected Active instead of Eligible
Understanding these two options is a fundamental concept in modern cloud identity management (Privileged Identity Management / PIM):

- Eligible Assignment: The user does not have the admin permissions during their regular routine. Instead, they are simply "allowed" to have them. If they need to do admin work, they must manually request activation, type a reason, and pass an extra MFA check. The permissions then automatically turn off after a few hours. This is the gold standard for security because it eliminates standing access.
- Active Assignment: The admin permissions are turned on immediately and stay on 24/7. The user can jump straight into admin tasks without waiting or going through an activation process.
  
Why I Picked Active for This Project I chose Active for Bob's profile to create a permanent, dedicated regional account for this lab environment. Because Bob is 

working strictly within the safe boundaries of the NY-Administrative-Unit, his permanent "Active" state is isolated from the rest of the company. This ensures he can immediately execute day-to-day management tasks for New York users without encountering the repetitive overhead of requesting access every single day.

<img src="Images/step 26.jpg"/> <br />

Bob Jones is now successfully registered, but his Scope column explicitly reads NY-Administrative-Unit instead of Directory. This means his management keys are entirely locked inside the New York container. He can fully manage the users and identity assets belonging to that specific branch, but he has absolutely no administrative power over any other department or region in the company, successfully achieving a true least-privilege deployment. 

- In cloud management, you don't want to spend your entire day assigning software licenses, setting folder permissions, or granting admin rights to users one by one. If you have 50 employees in New York, doing everything 50 separate times takes too long and invites mistakes. Instead, I will create a Security Group, drop all 50 New York employees inside it, and lock that entire group into your NY-Administrative-Unit. Now, Bob Jones can manage all 50 people instantly by controlling that single group container. It is called a Security group because its main job is managing safety boundaries and access controls for the network.
- With the administrative roles established, the next crucial step is creating the structural "backbone" for the New York workforce. Managing users one by one in an enterprise is highly inefficient and prone to mistakes. Creating a dedicated security group allows for streamlined, bulk management.
- On this configuration screen, I have filled out the essential properties for this new organizational asset:

<img src="Images/step 27.jpg"/> <br />

<img src="Images/step 28.jpg"/> <br />

- Click "New group": Once this menu fully loads, there will be a button at the top of the workspace labeled + New group. Clicking that will open up the creation panel.

<img src="Images/step 29.jpg"/> <br />

- Group Type (Security): I selected Security because this group’s primary purpose is to manage permissions and access control boundaries. It functions as a secure bucket to hold our local users so their identities can be governed collectively.
- To complete the setup of the NY-Staff-Group, I clicked on the Members link to explicitly populate the group. For this enterprise scenario, I added five group members consisting of regular New York branch employees, including Greg Johnson. By manually assigning these five members to this specific security group, I have established the target workforce container that Bob Jones will manage, allowing him to efficiently administer permissions, policies, and access controls for all five users simultaneously rather than updating their accounts individually.
- Group Name (NY-Staff-Group): I chose a clear, descriptive, and standardized naming convention so any IT administrator can immediately recognize that this group belongs specifically to the New York branch operations.
- Group Description: I added a professional definition: "Security group containing all regional employees located in the New York branch office, managed by the NY Hybrid Identity Administrator." This keeps the directory well-documented and auditable.
- Microsoft Entra Roles (No): I kept this toggle set to No. Enabling this feature creates a specialized, highly privileged group that can bypass standard security controls to assign massive tenant-wide admin roles. Because this group is strictly meant for standard, everyday employees (like Greg Johnson), turning this on would introduce an unnecessary security risk.
- Membership Type (Assigned): I chose Assigned over Dynamic user to keep membership strictly manual. This ensures that our newly appointed local admin, Bob Jones, has direct, hands-on control over explicitly adding or removing staff from his regional team, rather than letting automated cloud rules handle it.

Why i picked no owner for this security Group?

- For this deployment, the group owner field was intentionally left blank. In Microsoft Entra ID, assigning a group owner delegates member management to a specific user without giving them a full IT admin role.
- However, leaving this blank is the best approach here because Bob Jones already has the Hybrid Identity Administrator role scoped directly to the NY-Administrative-Unit. Once this security group is placed inside that unit, Bob automatically gets full management power over it through his existing role. Assigning an explicit owner is redundant, and leaving it blank keeps the security model clean, professional, and entirely controlled by your established Administrative Unit framework.

<img src="Images/step 30.jpg"/> <br />

With the group configuration finalized and the five regional employees successfully added as members, I hit create and returned to the main All groups dashboard. As circled in red, the NY-Staff-Group now appears live in the directory.

This view confirms that our structural backbone is officially active, showcasing the exact settings selected for our deployment strategy: the group is registered correctly as a Security type, and its membership type is explicitly set to Assigned (manual mode) to preserve Bob Jones's direct administrative control. The group is now fully prepared to be linked to the NY-Administrative-Unit so our delegated regional management model can take effect.

<img src="Images/step 31.jpg"/> <br />

- To finalize the regional management boundary, I navigated back to the NY-Administrative-Unit, clicked on the Groups blade under the manage menu, and clicked + Add. On the flyout selection panel, I selected NY-Staff-Group from the available directory objects.
- By clicking the blue Select button at the bottom, this security group is officially placed inside the New York Administrative Unit container. This critical architectural step links the target workforce directly to Bob Jones's scoped administrative powers. Now, because the group resides within his assigned unit, Bob holds full regional authority to manage this group and its members, successfully completing the secure, decentralized identity governance model. 

<img src="Images/step 32.jpg"/> <br />
<img src="Images/step 33.jpg"/> <br />

To verify that the configuration was successful, I opened the overview page for the newly assigned NY-Staff-Group directly from within the administrative unit context. This dashboard serves as final confirmation that the group is fully operational and populated according to project specifications.
As highlighted by the red underlines and menu selections on this screen:

- Successful Member Enrollment: The User(s) metrics clearly display a count of 5, confirming that the five regional New York employees have been successfully added to this manual security container.
- Administrative Context: By navigating to the Members blade (circled on the left menu), an administrator can audit the exact identities of these five individuals.
- Validation of the Architecture: Because this group now has a "Total members" count of 5 and sits natively inside the NY-Administrative-Unit, the delegation loop is complete. Bob Jones, using his scoped Hybrid Identity Administrator role, now possesses full, isolated visibility and management authority over these five specific users via this unified group container.

To provide deep visibility and complete accountability within this infrastructure deployment, I clicked on the Members blade to verify the specific identities populated inside the NY-Staff-Group.
This dashboard displays the active roster of the 5 group members explicitly assigned to the New York branch container:

- Justin Blakeley
- mercylasson
- myriasanchez
- Robert Kim
- Sarah Lee

By documenting this roster, I can prove that all target users are correctly categorized with the User object type and hold standard Member user types. This clean list represents the exact workforce population that our local administrator, Bob Jones, can now actively oversee and manage. Because this group is nested within the NY-Administrative-Unit, Bob has full delegated authority over these specific individuals' identities, properties, and access rights without ever possessing global control over the rest of the enterprise tenant.

# Deploying the Departmental Marketing Group with Delegated Ownership

To demonstrate a decentralized, department-led collaboration model within the regional architecture, I first created Greg Johnson as a standard directory user, intentionally leaving all global administrative roles unassigned. With Greg's standard account established, I proceeded to build a new Microsoft 365 group named NY-Marketing-Group to serve as a collaboration hub for the local marketing team. During the creation process, I bypassed the traditional role-based assignment framework and explicitly added Greg Johnson as the Group Owner.
By designating Greg as the owner of this Microsoft 365 group, he is granted the direct capability to manage the group's internal roster, add or remove marketing members, and oversee their shared tools without requiring an elevated IT directory role. This specific configuration allows the group to be placed safely under the NY-Administrative-Unit umbrella for regional visibility, while ensuring that daily departmental administration is successfully offloaded to Greg himself, perfectly showcasing a real-world blend of centralized structural oversight and localized data ownership.

<img src="Images/step 34.jpg"/> <br />

I clicked the Create button to officially make Greg Johnson's new account. After his profile was live, I went into the NY-Administrative-Unit and added him as a member.

<img src="Images/step 35.jpg"/> <br />

Now the Greg johnson is on the NY AU so i will now create a Microsoft 365 group Marketing Group and make Greg the owner of the group.

<img src="Images/step 36.jpg"/> <br />

I configured a new Microsoft 365 group named NY-Marketing-Group directly within the New York Administrative Unit interface to serve as the regional team's communication hub. I assigned Greg Johnson as the group owner to delegate roster management, added three initial team members, and kept Entra roles disabled to maintain standard security practices. Clicking Create finalized this setup, successfully blending regional structural boundaries with localized departmental data ownership.

<img src="Images/step 37.jpg"/> <br />

The Groups menu of the NY-Administrative-Unit confirms that the NY-Marketing-Group is now active and properly placed within the regional container. This view displays our two distinct group strategies working side-by-side: the 

NY-Staff-Group operating as a standard Security group for general infrastructure control, and the newly added NY-Marketing-Group running as a Microsoft 365 group for team collaboration. Because this new group is positioned inside the unit and has its ownership delegated to Greg Johnson, the regional setup successfully supports both secure administrative boundaries and local department management.

<img src="Images/step 38.jpg"/> <br />

Opening the NY-Marketing-Group dashboard confirms the group profile is fully built and functioning as intended. The overview blade displays our custom description identifying it as a collaboration hub managed by Greg Johnson, and the basic information field notes a total of three active user members. This screen verifies that the object properties are complete, the type is correctly set to Microsoft 365, and the group stands ready for daily department operations.

# Validation and Testing 

To prove that the regional administration framework works correctly, I initiated a validation phase to test the actual permissions of our scoped users. This testing process ensures that the access boundaries configured within the Microsoft Entra tenant actively enforce the principle of least privilege in a live environment. By logging into separate sessions as Bob Jones and Greg Johnson, I can verify that their administrative capabilities strictly match their assigned organizational roles.

<img src="Images/step 39.jpg"/> <br />

I will log into the Azure Portal using Bob Jones's credentials through the windows incognito.

<img src="Images/step 40.jpg"/> <br />

It will require you to set a new password 

<img src="Images/step 41.jpg"/> <br />

It will prompt you to install the MS Authenticator

<img src="Images/step 42.jpg"/> <br />

I will use the QR code on the ms authenticator app on my phone to synchronized to bob credentials on my device.

<img src="Images/step 43.jpg"/> <br />

<img src="Images/step 44.jpg"/> <br />

I have successfully logged in using Bob Jones's credentials, which can be verified by his user principal name highlighted in the top-right corner of the portal. To begin validating his scoped administrative permissions, I am clicking on the Microsoft Entra ID service icon from the dashboard to enter the identity management console.

<img src="Images/step 45.jpg"/> <br />

<img src="Images/step 46.jpg"/> <br />

Once inside the Microsoft Entra ID dashboard, I navigated to the left-hand sidebar menu, clicked on Administrative units, and selected the NY-Administrative-Unit. This opens the specific management container where Bob's regional permissions are active, allowing me to view the users and groups assigned to his care.

<img src="Images/step 47.jpg"/> <br />

Now that I am inside the NY-Administrative-Unit dashboard, I need to look at the groups that Bob Jones has the authority to manage. From the left-hand navigation menu under the Manage section, I am clicking on Groups to open the list containing both our regional security group and the marketing collaboration group. 

<img src="Images/step 48.jpg"/> <br />

From the list of available groups inside the unit, I am clicking directly on the NY-Staff-Group. Since this is a standard Security group located within Bob's administrative boundary, opening it will allow me to test if his Hybrid Identity Administrator role grants him the power to manage its membership.

<img src="Images/step 49.jpg"/> <br />

Inside the NY-Staff-Group panel, I am clicking on Members from the left-hand menu and then selecting the Add members button at the top. To test Bob's scoped admin powers, I will search for a user who isn't in the group yet and add them. This action should process successfully, proving that Bob's role allows him to manage standard security group rosters within his designated Administrative Unit. 

<img src="Images/step 50.jpg"/> <br />

To test my permissions, I clicked Add members and searched for an employee named brunocapson. The system located the user account successfully under the search box. I am now clicking the checkbox next to his name and selecting the blue Select button at the bottom of the blade to add him to the NY-Staff-Group. 

<img src="Images/step 51.jpg"/> <br />

The direct members list updates immediately to show brunocapson as a newly added user, raising the group count to six total members. This successful update proves that Bob Jones can actively manage security group memberships within his assigned administrative container.
Now, I need to test his restrictions. To do this, I will navigate back to the NY-Administrative-Unit group menu and open the NY-Marketing-Group to see if his admin role is blocked from changing a Microsoft 365 group roster.

<img src="Images/step 52.jpg"/> <br />

Inside the NY-Marketing-Group, I am navigating to the Members section on the left menu, just like I did before.
Once the members page opens, I will look closely at the Add members button at the top. Because this is a Microsoft 365 group and Bob is only an administrative unit manager, the system should prevent him from adding people. The button will be grayed out when clicked.

This successfully completes Bob's validation test, proving that his administrative powers are strictly confined to infrastructure security groups and blocked from touching collaborative team groups.

To begin the second half of the validation phase, I opened a fresh InPrivate browser window and logged in using Greg Johnson's credentials. Greg holds no global directory roles within the company tenant, which means his access relies entirely on direct object ownership. From the main dashboard, I am clicking on the Microsoft Entra ID service icon to navigate to the identity portal and verify his localized management permissions.

<img src="Images/step 53.jpg"/> <br />

<img src="Images/step 54.jpg"/> <br />

Once inside the Microsoft Entra ID overview page, I bypassed the Administrative Units section entirely since Greg is not a directory administrator. Instead, I navigated to the left-hand sidebar menu under the Manage section and clicked directly on Groups. This opens the central directory group list, where I can test Greg's ability to manage his specific team. 

<img src="Images/step 55.jpg"/> <br />

<img src="Images/step 56.jpg"/> <br />

<img src="Images/step 57.jpg"/> <br />

Inside the Members blade of the NY-Marketing-Group, the Add members command button at the top of the workspace is fully illuminated, active, and clickable for me. I clicked the button, searched for an unassigned user account called sarah lee within the tenant directory, and successfully committed the selection.
The direct members roster updated instantly to incorporate the new employee. This successful operation validates that explicit object ownership over a Microsoft 365 group completely bypasses the need for global or regional directory roles, enabling delegated business leaders to manage their own team boundaries directly.

<img src="Images/step 58.jpg"/> <br />

To finish my testing, I went back to the main groups list and opened the NY-Staff-Group. When I clicked on Members, the Add members button was completely grayed out and did not work.
This is exactly what should happen and It proves that Greg has zero power over groups he does not own. This test confirms that this security boundaries work perfectly, keeping a department leader's controls strictly inside their own team space.

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

