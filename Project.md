1: Scenario - In this project, I will showcase a simulated environment for a company featuring multiple employees and departments. This company uses Entra ID for its cloud directory services including user authentication services as well as administrator privilege authorization. This project will use Entra ID to create users, groups, assign roles according to department and job responsibilities using least privilege, MFA, conditional access, and privileged identity management. I will also document the lifecycle of a user from onboarding to offboarding.
2: Business Problem - Since identity management is done manually, there are several created with this process with this process. The first is that we need to create a framework for the lifecycle management of users. Another is the possibility of outdated user access privileges. Since the granting and revoking of privileges is done by an administrator, it is possible that old privileges might be retained after a role change. One final problem is the security of individual accounts, specifically those with higher privileges.
3: Access Risks - Of the problems listed above, the greatest risk is account security. Since authentication acts as the first line of defense in our project, it is important that we configure strong security using the methods listed above.
4 Documentation
5
6: Recommendations - One of the major recommendations is the use of conditional access. While MFA is helpful as an added layer of security during authentication, it could also become an impediment. Since security and convenience are reversely proportional, the added layer of security could cause inconvenience and wasted time for end users. This is why conditional access is helpful, since you can set policies of when MFA should required, such as when signing in from a new device or when outside the standard geo-zone. 

Another recommendation is for frequent access and permission audits. It is a regular occurrence for employees to be promoted or switch roles, gaining new permissions while no longer needing old ones. For this reason it is normal for old and outdated permissions to be left on accounts, creating new vulnerabilities. It is important that audits be performed on a regular basis, for example weekly, to catch any outdated privileges 

7
1. Group Creation
In our simulated company, we have already created 3 security groups categorized by departments. Groups are helpful for organizing users while also assigning roles to the group itself, which is then inherited by any users placed within that group. The existing groups can be seen below:

<img width="1594" height="918" alt="Screenshot 2026-09-03 172857" src="https://github.com/user-attachments/assets/cbe64cb8-3af0-4d4c-9c6c-f1eeef7b9a7c" />

We will start by creating a new group, which we will name software development. While creating a new group, we will give it a name and owner while also designating it as a security group. We also have the option to add existing users to the group, but we will create a new user in the next step.

<img width="1591" height="920" alt="Screenshot 2026-09-03 173510" src="https://github.com/user-attachments/assets/9c895914-9815-4f81-8525-cbe46f547cd8" />

2. User Creation
Now that we've created a new group, we can create a new user to populate it. Once in the "Users" section, we will create a new user at the top. We also have the option to invite and external user to our directory for b2b purposes, but for this project we will focus on creating a new internal user.

<img width="1598" height="927" alt="Screenshot 2026-09-03 174439" src="https://github.com/user-attachments/assets/1ed10df9-7ddb-4048-9b73-b84ff84caa79" />

Once we start, we can give them a UPN using our existing domain while also setting their display name. Entra will automatically generate a password which should later be reset using the Self-Service Password Reset feature offered by Entra.

<img width="1591" height="936" alt="Screenshot 2026-09-04 213928" src="https://github.com/user-attachments/assets/1a9e49d0-83e5-4cef-9708-ad63a97b165d" />

We also have the ability to assign a user to a group while creating the user, so we will select the group we created earlier. We also have the ability to assign o role to the user upon creation, however you can also assign roles later as we will do.

<img width="1592" height="936" alt="Screenshot 2026-09-04 214015" src="https://github.com/user-attachments/assets/aba73e2c-45fc-4f75-948c-d976529751d8" />

4. Role Assignment

We can now select the new user and navigate to the assigned roles tab. From here we can select "Add assignments" at the top to give the user a role. Since our user in this scenario is a software developer, we should only give roles with permissions that are strictly needed for their job. For us this would include roles regarding application development as seen in the screenshot below. The purpose of role based access control is enforce least privilege, meaning that users get the bare minimum permissions they need. This is meant to limit the scope of damage that can be caused in the event of an account breach.

<img width="1592" height="921" alt="Screenshot 2026-09-04 214623" src="https://github.com/user-attachments/assets/2c1b2f50-4837-43ac-b9b5-dc6f711a07bb" />

5. Enforcing MFA



6. Conditional Access



7. PIM



8. Role Change + Access Audit



9. Offboarding
