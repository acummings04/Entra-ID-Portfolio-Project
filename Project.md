1: Scenario - In this project, I will showcase a simulated environment for a company featuring multiple employees and departments. This company uses Entra ID for its cloud directory services including user authentication services as well as administrator privilege authorization. This project will use Entra ID to create users, groups, assign roles according to department and job responsibilities using least privilege, set up MFA, conditional access, and privileged identity management. I will also document the lifecycle of a user from onboarding to offboarding.

2: Business Problem and Risks - Since identity management is done manually, there are several risks created with this process. The first is that we need to create a framework for the lifecycle management of users. One risk is the possibility of outdated or excessive user access privileges. Since the granting and revoking of privileges is done by an administrator, it is possible that old privileges might be retained after a role change. This is a high risk that can increase the scope of damage that can be caused by an attacker in the case of an account compromise. By limiting user privileges and access to resources, we can reduce the possible damage that can be done. Another risk is the security of individual accounts, specifically those with higher privileges. Since admins are responsible for setting and enforcing authentication policies, it is important to choose strong policies that protect user accounts without impacting productivity. Since authentication acts as the first line of defense in IAM, it is critical that this risk is addressed with proper policies that are enforced on highly privileged users. The goal of this project is to use Entra ID to solve the problems of user management and authorization as well as secure authentication practices.

4 Documentation

6: Recommendations - One of the major recommendations is the use of conditional access. While MFA is helpful as an added layer of security during authentication, it could also become an impediment. Since security and convenience are inversely proportional, the added layer of security could cause inconvenience and wasted time for end users. This is why conditional access is helpful, since you can set policies of when MFA should required, such as when signing in from a new device or when outside the standard geo-zone. 

Another recommendation is for frequent access and permission audits. It is a regular occurrence for employees to be promoted or switch roles, gaining new permissions while no longer needing old ones. For this reason it is normal for old and outdated permissions to be left on accounts, creating new vulnerabilities. It is important that audits be performed on a regular basis, for example weekly, to catch any outdated privileges 

7: Differences in a production environment - Although this project helps discuss and remediate some business problems, it does not represent a full IAM solution. Most companies have additional resources and applications that that they must manage user access for. Although this project discusses a solution for user management, it does not cover application management.

Another challenge in a production environment is the introduction of new policies. When introducing new policies such as conditional access, there is always a chance that something can go wrong. Although this project gives experience on how to set up and enforce authentication policies, it does not match the nuance of a real environment. Other factors need to be considered such as when a policy is implemented as well as on what scale. For example, it is helpful to test a conditional access policy on an experiment groups to ensure it does not cause any unexpected issues.

Need for automated access reviews - Although this project helps define the importance of access reviews while conducting one for a single account, this project does not match the number of users in a real environment. For this reason, access reviews can be more complex and time consuming than shown in this project. This is why... 

maybe lacking authentication

1. Group Creation
In our simulated company, we have already created 2 security groups categorized by departments. Creating groups is the first step toward managing user identities, and can be used to assign roles and permissions to a group. This allows any roles assigned to the group to be inherited to any users assigned within that group, making permission auditing simpler. For this project, we will only be assigning roles at the user level.
<img width="1594" height="936" alt="Screenshot 2026-09-27 170543" src="https://github.com/user-attachments/assets/cbe494d0-540d-473a-8d17-14ab0b32be01" />

While creating our new groups, we will name it after the department title to make user management easier. This is also where we can assign baseline permissions to any users in that department, allowing users within that security group to inherit those permissions. 

<img width="1598" height="937" alt="Screenshot 2026-09-27 170619" src="https://github.com/user-attachments/assets/f08acdc9-df77-457a-814d-ae2082ce42a6" />

2. User Creation
The first part of the user management lifecycle is creating new users. In this project we will create new users using our given domain but it is also possible to invite external users for b2b collaboration. 

<img width="1597" height="938" alt="Screenshot 2026-09-27 170759" src="https://github.com/user-attachments/assets/3b05749d-4177-4cae-b0f5-d85666a1c9e1" />

This is also where we can give properties to an identity for easier management.
<img width="1595" height="939" alt="Screenshot 2026-09-27 170840" src="https://github.com/user-attachments/assets/247e60a7-767f-4ef4-9c6a-495ed316db0c" />

We also have the ability to assign a user to a group while creating the user, so we will select the group we created earlier. We also have the ability to assign a role to the user upon creation, however you can also update or assign new roles later.

<img width="1594" height="936" alt="Screenshot 2026-09-27 171233" src="https://github.com/user-attachments/assets/360e6086-57e8-4145-860f-b42cb0957f35" />

4. Role Assignment

Since our user in this scenario is a billing administrator, we should only give roles with permissions that are strictly needed for their job. For us this would include roles regarding billing as seen in the screenshot below. The purpose of role based access control is enforce least privilege, meaning that users get the bare minimum permissions they need. This is meant to limit the scope of damage that can be caused in the event of an account breach. This is the first major step in enforcing authorization and is one of the key components of IAM.

<img width="1598" height="938" alt="Screenshot 2026-09-27 173420" src="https://github.com/user-attachments/assets/ae8143fd-95ac-43c8-b391-90501cfa2ef3" />

5. Enforcing MFA
One of the steps we can take to mitigate the risk of authentication security is enabling MFA for users. By adding an extra layer of security, we can reduce the likelihood of an account compromise through a standard password. One of the better options is the Microsoft authenticator app. To do this for specific users, we can use the per-user MFA option. To set this up we can check any accounts that we want to enable MFA for and configure any settings before enabling MFA.
<img width="1596" height="932" alt="Screenshot 2026-09-20 152855" src="https://github.com/user-attachments/assets/ee1c6725-f01d-4f46-bfb9-133a888328fe" />

Now when we attempt to sign in with this user's account, we will get a prompt to download and use the Microsoft authenticator app, which is the standard default and recommended method. Although this method of enforcing MFA is helpful in providing an extra layer of security, conditional access is more efficient.
<img width="1594" height="904" alt="Screenshot 2026-09-20 153749" src="https://github.com/user-attachments/assets/461f4b33-449e-4765-b6f7-9ac7bb8387ad" />


7. Conditional Access
Conditional access offers greater control compared to per-user MFA since it allows assignment to users or groups, as well as granular control over what conditions require MFA for specific resources.

We can start by creating a conditional access policy limited to the Finance group we created earlier. This way, only users within this security group will be included in this policy.
<img width="1597" height="942" alt="Screenshot 2026-09-28 204241" src="https://github.com/user-attachments/assets/7c1fae1e-5624-47b4-b266-a56ac4b9b973" />

Next we can decide which resources and applications will require MFA, as opposed to per-user MFA being enforced across the board. In this example, we will require MFA for Office.<img width="1598" height="940" alt="Screenshot 2026-09-28 204304" src="https://github.com/user-attachments/assets/b0c9e976-b892-4c38-89a4-d54dbaa2ade8" />

We can also decide which conditions will require MFA, specifically locations and networks. If a company wanted to create a policy requiring remote workers to use MFA while employees on premises did not, we can choose to include all network locations before excluding, or whitelisting the on premises location.
<img width="1594" height="940" alt="Screenshot 2026-09-28 205451" src="https://github.com/user-attachments/assets/ff9f0bd6-22c1-4477-9b4c-4ae71e9652be" />

We can also choose to whitelist specific devices from this policy through filters, although we will not configure this section in order to enforce this policy across all devices.
<img width="1598" height="943" alt="Screenshot 2026-09-28 205528" src="https://github.com/user-attachments/assets/5947648d-9165-47d5-b9d2-c8fcd6ef49a5" />

Here is where we can choose which action will grant access. In this case we will set up an MFA policy as shown below.
<img width="1594" height="940" alt="Screenshot 2026-09-28 205619" src="https://github.com/user-attachments/assets/a9552938-3107-4630-bfe3-070520718396" />

One additional feature that we can configure is the frequency of the MFA requirement. We can set the policy to only need MFA every 24 hours, enhancing security without creating too much of an inconvenience for workers. 
<img width="1596" height="941" alt="Screenshot 2026-09-28 210945" src="https://github.com/user-attachments/assets/9cfc60ae-a57b-4ff0-9f2e-04ad0d883c59" />

Below is an image of the finalized policy. The major difference between per-user MFA and conditional access is the granularity, specifically the scope of resources affected, easier group enforcement, location restrictions, and frequency.
<img width="1599" height="940" alt="Screenshot 2026-09-28 211043" src="https://github.com/user-attachments/assets/d97a8595-6b78-4d2e-a6dd-ec3e1e56845e" />


9. PIM



10. Role Change + Access Audit
When a user changes roles it is important to not only provide them with the privileges needed for their new job, but to also remove any old privileges that are no longer needed. This is an important step of the user management lifecycle that helps reduce the risk of excessive privileges as outlined earlier. In this example, when the employee moves from the finance department to IT, we need to first remove any old privileges related to application development. Since we used group assigned roles, moving our user to a different security group will automatically remove old roles while assigning new ones. One problem however, is that some users will need privileges above the baseline meaning they must be assigned at the user level. Roles assigned at the user level can easily be forgotten and maintained during role changes, which is why access audits become important for detecting any outstanding privileges.


11. Offboarding
The last step of user management is offboarding. Once a user leaves, it is important to disable the user account to prevent logins while also removing all privileges given to the account either at the group or user level. It is also important to avoid deleting the account since the logs and compliance data related to it might be needed later. Different companies might have different ways of managing archived accounts, but you can also move the user to a new group meant for archived users.
