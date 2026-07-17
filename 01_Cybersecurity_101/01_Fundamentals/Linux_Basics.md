# Linux Fundamentals: Core Concepts & Commands

A consolidated, organized reference guide for essential Linux commands, filesystem navigation, permissions, process management, and system maintenance.

---

## 📂 Filesystem Navigation & Interaction

### Essential Commands
* `whoami`: Displays the username of the current logged-in session.
* `ls`: Lists the contents of the current directory.
  * Use the `-h` flag (e.g., `ls -lh`) to display file sizes in a **human-readable** format.
* `cd`: Changes the current working directory to a specified path.
* `touch`: Creates a new, empty file (e.g., `touch newnote`).
* `mkdir`: Creates a new, empty directory (e.g., `mkdir myfolder`).
* `mv`: Moves or renames files and directories (e.g., `mv myfile myfolder/`).
* `rm`: Deletes a file.
  * Use `rm -r` to recursively delete a directory and all of its contents.
* `file`: Analyzes and determines the file type of a given file (e.g., identifying a file as `ASCII text`).
* `cat`: Displays the full content of a file in the terminal.

### Directory Navigation Shortcuts
* `cd ..` : Moves up one directory level.
* `cd ~` : Moves directly to the current logged-in user's home directory.
* `cd -` : Toggles back to the previous working directory you were just in.

### Important System Directories
* `/root`: The dedicated home directory of the system administrator (root user).
* `/var/log`: The standard location where system, service, and application logs are stored.
* `/tmp`: A volatile, temporary directory where files are wiped upon reboot, functioning similarly to a computer's RAM.

---

## 🔐 Permissions & Access Control

### User Management
* `su`: Switches the current terminal session to another user account (e.g., `su user2`).

### Understanding File Permissions (`chmod`)
Permissions are broken down into three classes: **User/Owner (u)**, **Group (g)**, and **Others (o)**. They are calculated using octal values:

| Permission | Octal Value | Description |
| :--- | :--- | :--- |
| **r** (Read) | `4` | Allows viewing the file contents or listing a directory. |
| **w** (Write) | `2` | Allows modifying or deleting the file/directory contents. |
| **x** (Execute) | `1` | Allows running a file as a program or entering a directory. |

* **Common Examples:**
  * `chmod 755 filename` $\rightarrow$ Owner: `rwx` (7), Group: `r-x` (5), Others: `r-x` (5).
  * `chmod 644 filename` $\rightarrow$ Owner: `rw-` (6), Group: `r--` (4), Others: `r--` (4).
  * `chmod +x script.sh` $\rightarrow$ Adds execute permissions for all classes.

---

## ⚙️ Command Line Operations & Utilities

### Input/Output Operators
* **Redirection (`>`)**: Overwrites the existing contents of a target file with new text output.
  ```bash
  echo password123 > passwords
* **Append (`>>`)**: Appends new text output to the end of a file without deleting its current contents.
  ```Bash
  echo tryhackme >> passwords
* **Backgrounding (`&`)**: Appending an ampersand to the end of any command runs that process immediately in the background.

### Searching & Networking
* **`grep`**: Searches through files or terminal outputs for specific text patterns.
  ```Bash
  grep "THM" access.log
* **`wget`**: Downloads files directly from web or network servers using a specific URL.
  ```Bash
  wget http://MACHINE_IP:8000/.flag.txt

### System Documentation
* **`man`**: Opens the built-in manual page for any given command. Use the Down arrow key to scroll down through the documentation.

---

## 🛠️ System Administration, Processes & Automation
### Text Editing
* **`nano`**: A straightforward, terminal-based text editor used to modify files directly inside the command line (e.g., nano task3).

### Process & Service Control
* **Process IDs (PID)**: Every active process on the system is assigned a unique, sequential numerical ID. If the previous process ID was 300, the next launched process will receive 301.

* **Process Termination**: The SIGTERM signal is sent to a process to request it to cleanly and safely shut down.

* **`fg`**: Brings a backgrounded process (bg or &) back into the active foreground.

* **`systemctl`**: Manages systemd services and background daemons.

```Bash
# Stop a running service
systemctl stop myservice

# Configure a service to start automatically during system boot-up
systemctl enable myservice
```

### Automation & Forensic Logging
* **Crontab**: Schedules automated tasks. Using the @reboot string ensures a specific command or script executes immediately upon system boot.

* **Log Analysis**: Server logs tracking user traffic contain forensic details crucial for security auditing, including remote visitor IP addresses (e.g., 10.9.232.111) and requested server resources (e.g., catsanddogs.jpg).
  
