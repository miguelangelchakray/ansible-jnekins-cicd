# New OS User role

This role is used to creat new admin user accounts on all components, add them to the admin group (to provide passwordless sudo) and upload the public keys.

## Structure

* defaults/main.yaml
  There are no defaults set for this role, variables are pulled from the Enviroment Inventory.

* tasks/main.yaml
  Creates admin users, groups and uploads ssh public keys to the relevant user.

* templates/01-os-admins.j2
  Sets the admin group to have passwordless sudo for all members.

## Variables

The entire role relys one just one variable/array, which is located in the Enviroment Inventory file.

* admin_users
  - An array that includes admin user names and the groups they need to be a member of.

**The task to upload the public keys uses the same array as for creating the users, and checks the folder 'secrets/wso2_ssh/users' for a key matching the username.**
