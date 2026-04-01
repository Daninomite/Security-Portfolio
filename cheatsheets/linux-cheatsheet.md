# Linux Commands Cheat Sheet
**By Daninomite**

---

## File & Directory Navigation

| Command | Description | Examples |
|---|---|---|
| `ls` | Lists files and folders in the current directory | `ls` → current folder, `ls /root` → /root folder |
| `ls -l` | Long format showing permissions, owner, size, and date | `ls -l` → detailed list, `ls -l /etc` → detailed /etc list |
| `ls -a` | Lists all files including hidden ones (starting with a dot) | `ls -a` → shows .ssh and .bashrc |
| `ls -la` | Combines long format with hidden files | `ls -la` → full detailed list including hidden files |
| `cd` | Change directory — moves you into a different folder | `cd /root`, `cd ..`, `cd ~`, `cd my-project` |
| `pwd` | Print Working Directory — shows your current location | `pwd` → outputs something like /root/my-project |

---

## File & Directory Management

| Command | Description | Examples |
|---|---|---|
| `mkdir` | Make Directory — creates a new folder | `mkdir projects`, `mkdir -p a/b/c` → nested folders |
| `rmdir` | Remove Directory — deletes an empty folder | `rmdir oldfolder` |
| `rm` | Remove — deletes a file permanently (no recycle bin!) | `rm file.txt`, `rm -i file.txt` → confirms before deleting |
| `rm -r` | Remove Recursively — deletes a folder and everything inside | `rm -r myfolder`, `rm -rf myfolder` → force delete |
| `cp` | Copy — copies a file or folder | `cp file.txt backup.txt`, `cp -r myfolder/ myfolder_copy/` |
| `mv` | Move — moves or renames a file or folder | `mv file.txt newname.txt`, `mv file.txt /root/projects/` |

---

## Viewing File Contents

| Command | Description | Examples |
|---|---|---|
| `cat` | Prints the full contents of a file to the screen | `cat README.md`, `cat file1 file2` |
| `less` | Views a file one screen at a time (Q to quit, Space to scroll) | `less bigfile.txt` |
| `head` | Shows the first 10 lines of a file by default | `head file.txt`, `head -n 20 file.txt` → first 20 lines |
| `tail` | Shows the last 10 lines of a file by default | `tail file.txt`, `tail -f log.txt` → live follow a log |

---

## Searching & Counting

| Command | Description | Examples |
|---|---|---|
| `grep` | Searches for a pattern or word inside a file | `grep "error" log.txt`, `grep -i "error"` → case-insensitive |
| `wc` | Word Count — counts lines, words, and characters | `wc file.txt`, `wc -l file.txt` → line count only |

---

## Permissions & Ownership

| Command | Description | Examples |
|---|---|---|
| `chmod` | Change Mode — changes who can read, write, or execute a file | `chmod 755 script.sh`, `chmod +x script.sh` |
| `chown` | Change Owner — changes who owns a file or folder | `chown john file.txt`, `chown -R john myfolder/` |

### Permission Numbers Quick Reference

| Number | Meaning |
|---|---|
| `4` | Read |
| `2` | Write |
| `1` | Execute |
| `7` | Read + Write + Execute (4+2+1) |
| `6` | Read + Write (4+2) |
| `5` | Read + Execute (4+1) |

---

## User Management

| Command | Description | Examples |
|---|---|---|
| `useradd` | Creates a new user account | `useradd john`, `useradd -m john` → with home directory |
| `usermod` | Modifies an existing user account | `usermod -aG sudo john`, `usermod -l newname oldname` |
| `userdel` | Deletes a user account | `userdel john`, `userdel -r john` → removes home directory too |

---

## Group Management

| Command | Description | Examples |
|---|---|---|
| `groupadd` | Creates a new group | `groupadd developers` |
| `groupmod` | Modifies an existing group | `groupmod -n devs developers` → renames group |
| `groupdel` | Deletes a group | `groupdel developers` |

---

## Superuser / Admin

| Command | Description | Examples |
|---|---|---|
| `sudo` | Superuser Do — runs a command as administrator/root | `sudo rm /etc/somefile`, `sudo -i` → switch to root |

> **Note:** On real Linux servers you will use sudo constantly for administrative tasks.

---

## Processes

| Command | Description | Examples |
|---|---|---|
| `ps` | Process Status — shows currently running processes | `ps`, `ps aux` → all processes on the system |
| `top` | Live dashboard of running processes, CPU, and memory | `top` → press Q to quit |
| `kill` | Stops a running process using its process ID (PID) | `kill 1234`, `kill -9 1234` → force kill |

**How to find a PID:**
```bash
ps aux | grep firefox
```

---

## Text Editors

### nano — Beginner Friendly
```bash
nano file.txt
```

| Shortcut | Action |
|---|---|
| `Ctrl + O` | Save the file |
| `Ctrl + X` | Exit nano |
| `Ctrl + K` | Cut a line |
| `Ctrl + U` | Paste a line |
| `Ctrl + W` | Search |

### vim — Advanced
```bash
vim file.txt
```

| Command | Action |
|---|---|
| `I` | Enter insert mode |
| `Esc` | Exit insert mode |
| `:w` | Save the file |
| `:q` | Quit |
| `:wq` | Save and quit |
| `:q!` | Quit without saving |

---

## Bonus Useful Commands

| Command | Description | Examples |
|---|---|---|
| `echo` | Prints text to the screen or into a file | `echo "hello"`, `echo "hello" >> file.txt` |
| `touch` | Creates an empty file or updates a file's timestamp | `touch newfile.txt` |
| `clear` | Clears the terminal screen | `clear` |
| `history` | Shows a list of previously run commands | `history`, `history | grep git` |
| `man` | Manual — shows full documentation for any command | `man ls`, `man grep` |

---

## Git Commands

| Command | Description | Examples |
|---|---|---|
| `git clone` | Downloads a repository from GitHub | `git clone https://github.com/username/repo.git` |
| `git status` | Shows which files have been changed | `git status` |
| `git add` | Stages files for the next commit | `git add file.txt`, `git add .` |
| `git commit` | Saves a snapshot of your staged changes | `git commit -m "added new feature"` |
| `git push` | Uploads your commits to GitHub | `git push origin main` |
| `git pull` | Downloads latest changes from GitHub | `git pull origin main` |
| `git log` | Shows the history of commits | `git log`, `git log --oneline` |

---

*Keep practicing — you've got this!* 💪