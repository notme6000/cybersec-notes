Linux controls access to files and directories through a simple but powerful permission model. Every file and folder has:

1. **An owner (user)**
2. **A group**
3. **Permissions** assigned to:

   * The owner
   * The group
   * Others (everyone else)

---

### Three Basic Permission Types

Each category (user, group, others) can have:

* **r — Read** → View file contents / list directory contents
* **w — Write** → Modify file / add or remove files in a directory
* **x — Execute** → Run a file as a program / enter a directory

---

### Example

When you run:

```bash
ls -l
```

You might see:

```
-rwxr-xr--
```

Breakdown:

* `-` → Regular file
* `rwx` → Owner can read, write, execute
* `r-x` → Group can read and execute
* `r--` → Others can only read

---

### Numeric (Octal) Representation

Permissions can also be written as numbers:

| Permission | Value |
| ---------- | ----- |
| r          | 4     |
| w          | 2     |
| x          | 1     |

Add them together:

* `7` = rwx (4+2+1)
* `5` = r-x (4+0+1)
* `4` = r--

Example:

```bash
chmod 755 file.sh
```

Means:

* Owner → 7 (rwx)
* Group → 5 (r-x)
* Others → 5 (r-x)

---

### Useful Commands

* `chmod` → Change permissions
* `chown` → Change owner
* `chgrp` → Change group

---

### Why It Matters

This system helps:

* Protect sensitive data
* Control who can run programs
* Secure multi-user systems


