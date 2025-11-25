Linux Least Privilege Hardening Project

A hands-on Linux security project demonstrating how to enforce the Principle of Least Privilege (PoLP) on a Ubuntu system. This includes user creation, group management, privilege restriction, sudo rights removal, permission verification, and failed privilege escalation demonstration.

This project shows practical hardening techniques used in SOC, IR, and system administration environments.

Project Overview

This lab walks through:

Creating standard users

Creating organizational groups

Assigning users to groups

Removing default privileges

Restricting sudo access

Validating least privilege enforcement

Demonstrating permission denials

Cleaning up users securely

The result is a hardened Linux setup where users have only the minimum privileges required — a core security control used across enterprise environments.

📂 Steps Performed

1. Create a new user
sudo adduser expuser

![User Creation](/mnt/data/VirtualBox_Security lS privlege #1.png)

2. Create new groups (developers, support)
sudo groupadd developers
sudo groupadd support


![Group Creation](/mnt/data/VirtualBox_Security lS privlege #2.png)

(If a group already exists, Linux will notify you.)

3. Add the user to a specific group
sudo usermod -aG developers expuser


![Group Assignment](/mnt/data/VirtualBox_Security lS privlege #3.png)

4. Verify group membership
groups expuser


![Verify Group Membership](/mnt/data/VirtualBox_Security lS privlege #4.png)

5. Remove unnecessary group memberships
sudo deluser expuser users


This forces the user into an even stricter permission model.

![Group Removal](/mnt/data/VirtualBox_Security lS privlege #5.png)

6. Verify sudo privileges
sudo -l -U expuser


This confirms the user cannot perform privileged actions.

Output confirms:

User expuser is not allowed to run sudo...


![Sudo Denial](/mnt/data/VirtualBox_Security lS privlege #6.png)

7. Attempt a restricted command

Logged in as the limited user:

sudo deluser test12


Output:

expuser is not in the sudoers file.


This is the perfect demonstration of least privilege enforced.

![Failed Privilege Escalation](/mnt/data/VirtualBox_Security lS privlege #7.png)

Final Verification

![Final Verification](/mnt/data/VirtualBox_Security lS privlege #8.png)

📸 Screenshots Included

The repo includes screenshots showing:

User creation

Group creation

Group assignment

Privilege verification

Sudo denial

Permission enforcement

Failed escalation attempt


🔱 MITRE ATT&CK Mapping
Relevant Mitigations

M1053 – User Account Management
Properly configured account roles reduce unauthorized access and attack surface.

M1026 – Privileged Account Management
Removing administrative rights blocks common privilege escalation paths.

M1022 – Restrict File and Directory Permissions
Least privilege limits access to protected system areas, reducing lateral movement.

Techniques This Hardening Helps Defend Against

T1068 – Privilege Escalation
Limits an attacker’s ability to elevate permissions.

T1078 – Valid Accounts
Even if an account is compromised, privilege is restricted.

T1548 – Abuse Elevation Control Mechanisms
Removal of sudo access prevents attempts to misuse elevation tools.

 Conclusion

This project reinforces how enforcing least privilege:

Reduces attack surface

Limits damage from compromised accounts

Controls user capabilities

Protects sensitive system areas

         and

Ensures operational security

