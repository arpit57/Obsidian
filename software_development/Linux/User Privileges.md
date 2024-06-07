
#### Types of Users

1. **Root User**: The root user (UID 0) has full control over the system. The root user can perform any task without any restriction, including changing system files, installing software, and managing user accounts.
2. **Regular Users**: Regular users have limited privileges. They can access and modify their own files and directories but cannot perform administrative tasks unless granted specific permissions.
3. **System Users**: These are special-purpose accounts used by system services and daemons. They often have limited access and are not intended for interactive login.

#### Permissions

Each file and directory has three types of permissions for three different categories of users:

1. **Owner**: The user who owns the file.
2. **Group**: Users who are members of the group associated with the file.
3. **Others**: All other users.

Permissions include:

- **Read (r)**: Allows viewing the contents of a file or directory.
- **Write (w)**: Allows modifying the contents of a file or directory.
- **Execute (x)**: Allows executing a file or searching within a directory.

Permissions are displayed in a string like `-rwxr-xr--`, where:

- The first character indicates the file type (`-` for a regular file, `d` for a directory).
- The next three characters (`rwx`) represent the owner's permissions.
- The following three characters (`r-x`) represent the group's permissions.
- The last three characters (`r--`) represent others' permissions.

#### Changing Permissions

Permissions can be changed using the `chmod` command.

#### Changing Ownership

The owner and group of a file can be changed using the `chown` command.

### Sudo and Elevated Privileges

The `sudo` (superuser do) command allows a permitted user to execute a command as the superuser or another user, as specified by the security policy. It’s configured in the `/etc/sudoers` file.