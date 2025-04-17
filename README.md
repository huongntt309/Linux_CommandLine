# Linux_CommandLine


### 🔐 **User & Permissions**

- `whoami` — Display the current user
- `id` — Show user and group information
    
    **Example output:**
    
    `uid=1000(labex) gid=1000(labex) groups=1000(labex),4(adm),27(sudo)...`
    
- `sudo` — Run commands as another user (default is root)



## 📁 Basic Files / Directories Operations

- `~` — Home directory
- `pwd` — Print working directory
- `echo` — Print text to the terminal
- `ls` — List files and directories in the current location
    - `ls -l` — Show a "long" listing format
    - `ls -a` — Show all files, including hidden ones
    - `ls -l testdir` — List contents of a specific directory
    - `ls -ld` — list the directory itself, rather than its contents
- `>` — Redirect output to a file
- Files starting with `.` are hidden. Example: `.zshrc`, `.bash_profile`
- `touch` — Create a file
- `mkdir` — Create a directory
    - `mkdir -p` — Create parent directories as needed
- `cp` — Copy files or directories
    - `cp -r` — Recursively copy directories
- `mv` — Move or rename files/directories
- `rm` — Remove files
    - `rm -i` — Prompt before each removal
    - `rm -f` — Force removal
- `rmdir` — Remove empty directories

### 📄 **File Content Viewing**

- `cat filename` — Display the contents of a file
    - `cat -n filename` — Display file contents with **line numbers**
- `head` — Show the **beginning** of a file
    - `head -n 1 filename` — Show the **first line** of the file
    - `head -c 1 filename` — Show the **first character** of the file
- `tail` — Show the **end** of a file
    - `tail -n 1 filename` — Show the **last line** of the file
    - `tail -c 1 filename` — Show the **last character** (often `\n`)



### 🔍 **File Comparison**

- `diff file1 file2` — Compare two files and display their differences
    
    **Example Output:**
    
    ```bash
    1c1
    < this is file1
    
    > this is file2
    
    ```
    
    - `<` shows content from **file1**
    - `>` shows content from **file2**
- `diff -r dir1 dir2` — Recursively compare the contents of two directories
    
    **Example Output:**
    
    ```sql
    Only in /home/labex/Desktop: code.desktop
    Only in /home/labex/Desktop: gedit.desktop
    Only in /home/labex/Desktop: gvim.desktop
    Only in /home/labex/Desktop: xfce4-terminal.desktop
    ```
    



## Permissions of Files
### 🔐 **Ownership**

- Use `ls -l` to view detailed info about files, including **permissions**, **owner**, and **group**.
    
    ```bash
    -rw-rw-r-- 1 labex labex 0 Jul 29 15:11 example.txt
    ```
    
    - `labex` (1st) → **Owner** of the file
    - `labex` (2nd) → **Group** of the file
- **Change ownership with `chown`**:
    - `sudo chown root:root example.txt` — Change owner and group to `root`
    - `sudo chown -R root:root new-dir` — Recursively change ownership of all files inside `new-dir`
- ✅ `R` = recursive (not `r`)

### 🔐  Permissions of Files

```bash
-rw-rw-r-- 1 labex labex 0 Jul 29 15:11 example.txt
```

- The first character:
    - → regular file
    - `d` → directory
    - `l` → symbolic link
- The next 9 characters are split into three sets of 3:
    - **Owner** permissions: `rw-`
    - **Group** permissions: `rw-`
    - **Others** permissions: `r--`
- What each character means:
    - `r` = read
    - `w` = write
    - `x` = execute
    - = no permission
- **Changing Permissions**
    - `ls -l` — View permissions
    - `chmod 700 file` — Set permissions with number (rwx)
    - `chmod -R 755 dir` — Set dir + subdir permissions (rwxr-xr-x)
    
    **Permission values:**
    
    - `r` = 4, `w` = 2, `x` = 1
    - `7` = rwx, `5` = r-x, `0` = 





### ✍️ **Symbolic Notation (chmod)**

- `chmod u+x script.sh` — Add execute permission for user (owner)
- `u/g/o/a` = user / group / others / all
- `+/-` = add / remove permission
- `r`, `w`, `x` = read, write, execute

## User Account Management
