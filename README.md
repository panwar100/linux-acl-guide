# linux-acl-guide
# Linux ACL Management

This guide explains how to manage file and directory permissions using Access Control Lists (ACL) in Linux. It includes examples of basic file operations, ACL modifications, and recursive permission management.

# Table of Contents
1.[Commands Overview](#commands-overview)

2.[Viewing ACL Permissions](#viewing-acl-permission)

3.[Modifying ACL for user and group](#modifying-acl-for-user-and-group)
- [For a User](#for-a-user)
- [For a Group](#for-a-group)

4.[Modifying Other Permissions](#modifying-other-permissions)

5.[Adding Multiple ACL Rules](#adding-multiple-acl-rules)

6.[Setting Mask Permissions](#setting-mask-permission)

7.[Recursive Permissions for a Directory](#recursive-permission-for-a-directory)

8.[Removing ACL for a User](#removing-acl-for-a-user)

9.[Resetting All ACL Permissions](#resetting-all-acl-permission)

10.[Setting Default ACL for a Directory](#setting-default-acl-for-a-directory)

# 1.Commands Overview
1. **View ACL of a file**
    ```bash
    getfacl <file>
    ```

2. **Grant permissions**
    ```bash
    setfacl -m u:<user>:<permissions> <file>
    ```

3. **Remove permissions**
    ```bash
    setfacl -x u:<user> <file>
    ```

4. **Reset all ACLs**
    ```bash
    setfacl -b <file>
    ```

5. **Recursive ACL for directories**
    ```bash
    setfacl -Rm u:<user>:<permissions> <directory>
    ```

6. **Set default ACL for directories**
    ```bash
    setfacl -m d:u:<user>:<permissions> <directory>
    ```

## Examples
# 2.Viewing ACL Permissions
Displays the Access Control List (ACL) of the file f1.

![Screenshot from 2024-12-04 22-20-54](https://github.com/user-attachments/assets/4941b485-3956-4e5c-a73a-b9f2feb15286)

# 3.Modifying ACL For User and Group

## For a User:

![Screenshot from 2024-12-04 22-22-54](https://github.com/user-attachments/assets/779bcab5-e64c-49b9-844e-7325fa4cbd23)

Grants read-only (r) permission to user tom.

## For Group:

![Screenshot from 2024-12-04 22-29-21](https://github.com/user-attachments/assets/2e9839d5-bb1a-442b-acc2-177bdfd3ce28)


Grants read, write, execute (rwx) permissions to group A1.

# 4.Modifying other Permissions

![Screenshot from 2024-12-04 22-30-33](https://github.com/user-attachments/assets/0c3c42eb-1e39-452e-9743-f76f1992fd97)


Grants write-only (w) permission to others.

# 5.Adding Multiple ACL Rules

![Screenshot from 2024-12-04 22-34-48](https://github.com/user-attachments/assets/a7a116cc-92c7-4b1c-932f-c0cb8ea0176c)


Adds the following:
User varun gets rw (read, write) permissions.
Group B1 gets rx (read, execute) permissions.
User jack gets rwx (read, write, execute) permissions.

# 6.Setting Mask Permissions

![Screenshot from 2024-12-04 22-36-55](https://github.com/user-attachments/assets/f6c1cb54-f2c9-45d5-9a53-060477ba904a)

Sets the mask to read-only (r), which limits the effective permissions for group and other ACL entries.

# 7.Recursive Permissions for Directory

![Screenshot from 2024-12-04 22-45-58](https://github.com/user-attachments/assets/b81e33da-8ea0-4435-aa9a-c624eb39b188)

both have different permission but when we use -R recursive then

![Screenshot from 2024-12-04 22-49-51](https://github.com/user-attachments/assets/e656870a-4bed-4316-aa1e-169d2facbca6)

Recursively grants write permission to user tom for the directory abc and all its contents (like f2).

# 8.Removing ACL for a User

![Screenshot from 2024-12-04 22-54-10](https://github.com/user-attachments/assets/ae7023cb-5a0d-44f9-9ac1-33a0ead706a0)

Removes the ACL entry for user varun.

# 9.Resetting All ACL Permissions

![Screenshot from 2024-12-04 22-55-18](https://github.com/user-attachments/assets/76b3974f-78ee-4663-b908-f354cf585b7e)

Removes all ACL entries from file f1.

# 10.Setting Default ACL for a Directory

![Screenshot from 2024-12-04 23-01-30](https://github.com/user-attachments/assets/8434e5e1-7a03-4e59-a684-51f1c5c92ccb)

Sets a default ACL for user don with rwx permissions. Any new file created inside abc will inherit these default permissions.

## Notes

- Use `ls -l` to identify ACL-enabled files (`+` sign).

![Screenshot from 2024-12-04 23-02-52](https://github.com/user-attachments/assets/8df220b4-d5a0-4943-bc27-3bc20cda37d4)

- Use `mask` to limit the maximum effective permissions for ACL entries.

## Author
This guide was created to assist with Linux ACL management and improve understanding of permission settings.
