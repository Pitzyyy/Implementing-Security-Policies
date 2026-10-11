# Implementing Security Policies

## Description

A comprehensive practical exercise demonstrating the implementation of core domain security controls using Active Directory Group Policy Objects (GPOs) and system security administrative tools. This activity covers three essential administrative operations: Password Policy Configuration (enforcing domain-wide password length, complexity, and age requirements), User Rights Assignments (managing delegated privileges and system access rights), and Fine-Grained Password Policies (applying tailored password and lockout settings to specific groups or users using Password Settings Objects).

## Environment Used

- Windows Server 2022 (Domain Controller)
- Windows 10 Enterprise (Domain-Joined Client Workstation)
- VMware Workstation

## Lab walk-through

## Password Policy Configuration

<p align="center">
Launch Group Policy Management on the Domain Controller and inspect the Default Domain Policy linked to the domain.
  <img src="./assets/images/1.png" alt="Create new user"
       style="width:80%;height:80%;display:block;margin:0 auto;" />
</p>

<p align="center">
Open the Default Domain Policy in the Group Policy Management Editor to access Computer Configuration and User Configuration settings.
  <img src="./assets/images/2.png" alt="Create new user"
       style="width:80%;height:80%;display:block;margin:0 auto;" />
</p>

<p align="center">
Navigate to Computer Configuration > Policies > Windows Settings > <br> Security Settings > Account Policies > Password Policy to review default security settings.
  <img src="./assets/images/3.png" alt="Create new user"
       style="width:80%;height:80%;display:block;margin:0 auto;" />
</p>

<p align="center">
Modify the Password Policy settings to enforce a 12-character minimum password length, <br> retain a 4-password history, set maximum password age to 60 days, and keep complexity requirements enabled.
  <img src="./assets/images/4.png" alt="Create new user"
       style="width:80%;height:80%;display:block;margin:0 auto;" />
</p>

<p align="center">
Navigate to Account Lockout Policy under Account Policies >to review account lockout threshold and duration options.
  <img src="./assets/images/5.png" alt="Create new user"
       style="width:80%;height:80%;display:block;margin:0 auto;" />
</p>

<p align="center">
Configure Account Lockout Policy settings: set Account lockout threshold to 5 invalid logon attempts,  <br> Account lockout duration to 30 minutes, and Reset account lockout counter after 30 minutes.
  <img src="./assets/images/6.png" alt="Create new user"
       style="width:80%;height:80%;display:block;margin:0 auto;" />
</p>

<p align="center">
Verify the Account Lockout Policy enforcement on the Windows 10 client machine after <br> exceeding 5 invalid password attempts, confirming the targeted user account (Charles Leclerc) is locked out.
  <img src="./assets/images/7.png" alt="Create new user"
       style="width:80%;height:80%;display:block;margin:0 auto;" />
</p>


## User Rights Assignment

<p align="center">
Create a new Group Policy Object named "User Rights Assignment" in Group Policy Management.
  <img src="./assets/images/8.png" alt="Create new user"
       style="width:80%;height:80%;display:block;margin:0 auto;" />
</p>

<p align="center">
Navigate to Computer Configuration > Policies > Windows Settings > Security Settings > <br> Local Policies > User Rights Assignment to access logon and access control policy settings.
  <img src="./assets/images/9.png" alt="Create new user"
       style="width:80%;height:80%;display:block;margin:0 auto;" />
</p>

<p align="center">
Open the "Deny log on locally" policy properties window and add the target user/group
  <img src="./assets/images/10.png" alt="Create new user"
       style="width:80%;height:80%;display:block;margin:0 auto;" />
</p>

<p align="center">
Confirm that the HR Department group is added to the "Deny log on locally" security policy settings list.
  <img src="./assets/images/11.png" alt="Create new user"
       style="width:80%;height:80%;display:block;margin:0 auto;" />
</p>

<p align="center">
Configure the "Allow log on through Remote Desktop Services" policy setting <br> to grant explicit remote desktop logon rights to the IT Department group.
  <img src="./assets/images/12.png" alt="Create new user"
       style="width:80%;height:80%;display:block;margin:0 auto;" />
</p>

<p align="center">
Attempt interactive local login on the Windows 10 workstation using an HR user account and verify <br> the system blocks login with "The sign-in method you're trying to use isn't allowed" message.
  <img src="./assets/images/13.png" alt="Create new user"
       style="width:80%;height:80%;display:block;margin:0 auto;" />
</p>

<p align="center">
Initiate a Remote Desktop Connection from the client machine targeting the Domain Controller hostname.
  <img src="./assets/images/14.png" alt="Create new user"
       style="width:80%;height:80%;display:block;margin:0 auto;" />
</p>

<p align="center">
Test remote desktop connectivity for unauthorized users and verify remote connection access is restricted according to policy.
  <img src="./assets/images/15.png" alt="Create new user"
       style="width:80%;height:80%;display:block;margin:0 auto;" />
</p>


## Fine-Grained Password Policies

<p align="center">
Launch the Active Directory Administrative Center (ADAC) on the Domain Controller.
  <img src="./assets/images/16.png" alt="Create new user"
       style="width:80%;height:80%;display:block;margin:0 auto;" />
</p>

<p align="center">
Navigate to System > Password Settings Container in Active Directory Administrative Center to manage Fine-Grained Password Policies.
  <img src="./assets/images/17.png" alt="Create new user"
       style="width:80%;height:80%;display:block;margin:0 auto;" />
</p>

<p align="center">
Configure a new Password Settings Object (PSO) named "AdminPasswordPolicy" setting precedence to 1, minimum password length to 15 characters, and history to 7 passwords.
  <img src="./assets/images/18.png" alt="Create new user"
       style="width:80%;height:80%;display:block;margin:0 auto;" />
</p>

<p align="center">
Apply the AdminPasswordPolicy directly to the IT Department security group under the "Directly Applies To" section.
  <img src="./assets/images/19.png" alt="Create new user"
       style="width:80%;height:80%;display:block;margin:0 auto;" />
</p>

<p align="center">
Create a secondary Password Settings Object named "UserPasswordPolicy" with precedence 2, minimum password <br> length of 20 characters, history of 5 passwords, and directly apply it to the HR Department group.
  <img src="./assets/images/20.png" alt="Create new user"
       style="width:80%;height:80%;display:block;margin:0 auto;" />
</p>

<p align="center">
Verify the newly created Password Settings Objects (AdminPasswordPolicy and UserPasswordPolicy)<br>with their assigned precedence levels inside the Password Settings Container.
  <img src="./assets/images/21.png" alt="Create new user"
       style="width:80%;height:80%;display:block;margin:0 auto;" />
</p>







