# AWS IAM CLI Project

A hands-on guide for managing AWS Identity and Access Management (IAM) using the AWS Command Line Interface (CLI).
This project demonstrates creating, listing, attaching policies, and deleting users, groups, and policies through practical commands.

# 📌 Prerequisites

- AWS CLI installed → Install Guide

-Configured AWS credentials:

    aws configure

  
-IAM permissions to manage users, groups, and policies.

# 🎯 Why Use AWS CLI for IAM Management?

While the AWS Management Console provides a graphical interface, the AWS CLI offers several advantages:

Speed & Automation – Easily create, update, or delete multiple IAM users, groups, and policies with scripts.

Consistency – Commands ensure repeatable results, reducing human error compared to manual console work.

Auditing & Logging (usdit) –

Every CLI command can be logged with CloudTrail, providing a transparent audit trail.

Useful for compliance (e.g., SOC2, ISO, HIPAA) where actions must be traceable.

You can generate CSV/JSON outputs of users, policies, and roles for reporting.

Scalability – Manage hundreds of IAM entities with batch scripts instead of clicking through the console.

Integration – CLI commands can be embedded into CI/CD pipelines or automated scripts for user provisioning and access control.

Remote Management – Admins can securely manage IAM from local terminals without logging into the console.

# 👤 IAM User Management

1. List all IAM users



        aws iam list-users
Example output:

    USERS  arn:aws:iam::xxxxxxxxxxxx:user/Deborah
    USERS  arn:aws:iam::xxxxxxxxxxxx:user/James
    USERS  arn:aws:iam:xxxxxxxxxxxx:user/example

2. Create a new IAM user

        aws iam create-user --user-name example

3. Delete an IAM user

        aws iam delete-user --user-name example

4. List attached policies for a user

        aws iam list-attached-user-policies --user-name SecurityTeamAdmin


Example:

    arn:aws:iam::aws:policy/AdministratorAccess
    arn:aws:iam::aws:policy/IAMUserChangePassword
    arn:aws:iam::aws:policy/AWSAccountManagementFullAccess

# 👥 IAM Group Management

1. List IAM groups

        aws iam list-groups


Example output:

    GROUPS arn:aws:iam::xxxxxxxxxxxx:group/AdminGroup
    GROUPS arn:aws:iam::xxxxxxxxxxxx:group/CloudSecurityTeam
    GROUPS arn:aws:iam::xxxxxxxxxxxx:group/NetworkGroup

2. Create a new group

        aws iam create-group --group-name example

3. Delete a group

        aws iam delete-group --group-name example

# 🔑 Policies and Permissions

1. List attached group policies

        aws iam list-attached-group-policies --group-name CloudSecurityTeam

2. Attach a policy to a group


        aws iam attach-group-policy \
        --group-name example \
        --policy-arn arn:aws:iam::aws:policy/IAMReadOnlyAccess

3. Add user to a group

        aws iam add-user-to-group \
        --user-name example \
        --group-name example

# 🧹 Cleanup Example

To remove everything related to example:

    aws iam detach-group-policy --group-name example --policy-arn arn:aws:iam::aws:policy/IAMReadOnlyAccess
    aws iam remove-user-from-group --user-name example --group-name example
    aws iam delete-user --user-name example
    aws iam delete-group --group-name example

# 📷 Screenshots

This repo includes screenshots showing:

User creation & listing
<img width="1303" height="754" alt="Screen Shot 2025-09-30 at 9 20 12 PM" src="https://github.com/user-attachments/assets/64e96bcd-3cae-4beb-a245-5e04985df781" />

<img width="478" height="636" alt="Screen Shot 2025-09-30 at 9 21 14 PM" src="https://github.com/user-attachments/assets/afd0a84f-55fe-4893-8339-b717f1e56a88" />


Group creation & listing

<img width="1359" height="504" alt="Screen Shot 2025-09-30 at 9 44 20 PM" src="https://github.com/user-attachments/assets/5e338a1f-c694-480a-b36f-ac474e5adb89" />



Policies attached to users & groups


<img width="1166" height="96" alt="Screen Shot 2025-09-30 at 9 47 58 PM" src="https://github.com/user-attachments/assets/5bac0923-9aa1-4f53-bf7d-59ef835600a6" />



Adding/removing users from groups

<img width="1450" height="392" alt="Screen Shot 2025-09-30 at 9 48 43 PM" src="https://github.com/user-attachments/assets/a8ef654b-476b-42a0-a582-9c55810434f1" />



# 🚀 Conclusion

This project demonstrates how AWS IAM can be fully managed from the CLI, making it easier to automate, audit, and secure identity management across AWS environments.
