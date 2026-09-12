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
In our simulated company, we have already created 3 security groups categorized by departments. Creating groups is the first step toward managing user identities, and can be used to assign roles and permissions to a group. This allows any roles assigned to the group to be inherited to any users assigned within that group, making permission auditing simpler. For this project, we will only be assigning roles at the user level.
<img width="1594" height="918" alt="Screenshot 2026-09-03 172857" src="https://github.com/user-attachments/assets/cbe64cb8-3af0-4d4c-9c6c-f1eeef7b9a7c" />

While creating our new groups, we will name it after the department title to make user management easier. This is also where we could assign baseline permissions to any users in that department, however we would still need to assign higher privileges at the account level. 

<img width="1591" height="920" alt="Screenshot 2026-09-03 173510" src="https://github.com/user-attachments/assets/9c895914-9815-4f81-8525-cbe46f547cd8" />

2. User Creation
The first part of the user management lifecycle is creating new users. In this project we will create new users using our domain name but it is also possible to invite external users for b2b collaboration. 

<img width="1598" height="927" alt="Screenshot 2026-09-03 174439" src="https://github.com/user-attachments/assets/1ed10df9-7ddb-4048-9b73-b84ff84caa79" />

<img width="1591" height="936" alt="Screenshot 2026-09-04 213928" src="https://github.com/user-attachments/assets/1a9e49d0-83e5-4cef-9708-ad63a97b165d" />

We also have the ability to assign a user to a group while creating the user, so we will select the group we created earlier. We also have the ability to assign a role to the user upon creation, however you can also assign roles later as we will do.

<img width="1592" height="936" alt="Screenshot 2026-09-04 214015" src="https://github.com/user-attachments/assets/aba73e2c-45fc-4f75-948c-d976529751d8" />

4. Role Assignment

Since our user in this scenario is a software developer, we should only give roles with permissions that are strictly needed for their job. For us this would include roles regarding application development as seen in the screenshot below. The purpose of role based access control is enforce least privilege, meaning that users get the bare minimum permissions they need. This is meant to limit the scope of damage that can be caused in the event of an account breach. This is the first major step in enforcing authorization and is one of the key components of IAM.

<img width="1592" height="921" alt="Screenshot 2026-09-04 214623" src="https://github.com/user-attachments/assets/2c1b2f50-4837-43ac-b9b5-dc6f711a07bb" />

5. Enforcing MFA
One of the steps we can take to mitigate the risk of authentication security is enabling MFA for users. By adding an extra layer of security, we can reduce the likelihood of an account compromise through a standard password. One of the better options is the Microsoft authenticator app.


6. Conditional Access



7. PIM



8. Role Change + Access Audit
When a user changes roles it is important to not only provide them with the privileges needed for their new job, but to also remove any old privileges that are no longer needed. This is an important step of the user management lifecycle that helps reduce the risk of excessive privileges as outlined earlier. In this example, when the employee moves from software development to finance, we need to first remove any old privileges related to application development. If we used group assigned roles, moving them to a different security group would automatically remove old roles while assigning new, however some users will have privileges above the baseline meaning they must be assigned at the user level. This is why access audits become important, to detect any outstanding privileges at the user level.


9. Offboarding
The last step of user management is offboarding. Once a user leaves, it is important to disable the user account to prevent logins while also removing all privileges given to the account either at the group or user level. It is also important to avoid deleting the account since the logs and compliance data related to it might be needed later. Different companies might have different ways of managing archived accounts, but you can also move the user to a new group meant for archived users.
