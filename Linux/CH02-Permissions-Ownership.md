# CH-02: File Permissions & Ownership

## Overview
Every file and directory in Linux has a permission set that controls who can read, write, or execute it.

## The Three Permission Types
| Permission | Symbol | Meaning |
|------------|--------|---------|
| Read | r | View a file's contents / list directory contents |
| Write | w | Modify or delete the file / add-remove files in a directory |
| Execute | x | Run the file (script/program) or enter the directory |

## The Three Ownership Categories
- **Owner** — The user who created the file
- **Group** — A set of users sharing the same access
- **Others** — Every other user on the system

## Reading a Permission String
`ls -l file.txt` → `-rwxr-xr--`

| Category | Permissions |
|----------|-------------|
| Owner | rwx |
| Group | r-x |
| Others | r-- |

## Octal Notation
| Permission | Value |
|------------|-------|
| read (r) | 4 |
| write (w) | 2 |
| execute (x) | 1 |
| none | 0 |

Add the values per category to get a 3-digit number.

**Example:** `[rwx][r-x][r--]`
- Owner: 4+2+1 = **7**
- Group: 4+0+1 = **5**
- Others: 4+0+0 = **4**
- → `chmod 754 file.txt`

## chmod (change mode)
Changes the permissions on a file/directory.
- `chmod +x script.sh` → adds execute permission
- `chmod 755 script.sh` → sets exact permissions using octal notation

## chown (change owner)
Changes ownership of a file.
- `chown newuser file.txt` → changes owner only
- `chown newuser:newgroup file.txt` → changes owner and group together (usually needs `sudo`)

**chmod** controls *what* can be done with a file.
**chown** controls *who* it belongs to.

---

## Special Permission: SUID (Set User ID)

**Definition** — A special permission bit that makes a program run with the privileges of the file's **owner**, instead of the user executing it.

**Example:** If a program is owned by `root` and has SUID enabled, a regular user running it temporarily gains root privileges for that action.

### Summary
- Regular restricted results become privileged.
- SUID "suppresses" permission-denied and lets the program run with elevated rights.

### Identifying SUID
Permissions = read/write/execute, evaluated per category, plus a special `s` in the owner slot:
