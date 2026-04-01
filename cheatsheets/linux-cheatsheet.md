=====================================
   LINUX COMMANDS CHEAT SHEET
   By Daninomite
=====================================

-------------------------------------
FILE & DIRECTORY NAVIGATION
-------------------------------------

COMMAND: ls
DESCRIPTION: Lists files and folders in the current directory.
EXAMPLES:
  ls                  → shows files in current folder
  ls /root            → shows files in the /root folder

COMMAND: ls -l
DESCRIPTION: Lists files in long format showing permissions, owner, size, and date.
EXAMPLES:
  ls -l               → detailed list of current folder
  ls -l /etc          → detailed list of /etc folder

COMMAND: ls -a
DESCRIPTION: Lists all files including hidden ones (files starting with a dot).
EXAMPLES:
  ls -a               → shows hidden files like .ssh and .bashrc
  ls -la              → combines long format with hidden files

COMMAND: cd
DESCRIPTION: Change directory — moves you into a different folder.
EXAMPLES:
  cd /root            → go to root home directory
  cd ..               → go up one level
  cd ~                → go to home directory
  cd my-project       → go into a folder called my-project

COMMAND: pwd
DESCRIPTION: Print Working Directory — shows your current location in the file system.
EXAMPLES:
  pwd                 → outputs something like /root/my-project

-------------------------------------
FILE & DIRECTORY MANAGEMENT
-------------------------------------

COMMAND: mkdir
DESCRIPTION: Make Directory — creates a new folder.
EXAMPLES:
  mkdir projects      → creates a folder called projects
  mkdir -p a/b/c      → creates nested folders in one command

COMMAND: rmdir
DESCRIPTION: Remove Directory — deletes an empty folder.
EXAMPLES:
  rmdir oldfolder     → removes oldfolder if it is empty

COMMAND: rm
DESCRIPTION: Remove — deletes a file permanently (no trash/recycle bin).
EXAMPLES:
  rm file.txt         → deletes file.txt
  rm -i file.txt      → asks for confirmation before deleting

COMMAND: rm -r
DESCRIPTION: Remove Recursively — deletes a folder and everything inside it.
EXAMPLES:
  rm -r myfolder      → deletes myfolder and all its contents
  rm -rf myfolder     → force deletes with no confirmation (be careful!)

COMMAND: cp
DESCRIPTION: Copy — copies a file or folder from one place to another.
EXAMPLES:
  cp file.txt backup.txt          → copies file.txt to backup.txt
  cp -r myfolder/ myfolder_copy/  → copies an entire folder

COMMAND: mv
DESCRIPTION: Move — moves or renames a file or folder.
EXAMPLES:
  mv file.txt newname.txt         → renames file.txt to newname.txt
  mv file.txt /root/projects/     → moves file.txt into projects folder

-------------------------------------
VIEWING FILE CONTENTS
-------------------------------------

COMMAND: cat
DESCRIPTION: Concatenate — prints the full contents of a file to the screen.
EXAMPLES:
  cat README.md       → displays everything in README.md
  cat file1 file2     → displays both files one after another

COMMAND: less
DESCRIPTION: Views a file one screen at a time. Press Q to quit, space to scroll down.
EXAMPLES:
  less bigfile.txt    → opens bigfile.txt in a scrollable viewer

COMMAND: head
DESCRIPTION: Shows the first 10 lines of a file by default.
EXAMPLES:
  head file.txt       → shows first 10 lines
  head -n 20 file.txt → shows first 20 lines

COMMAND: tail
DESCRIPTION: Shows the last 10 lines of a file by default.
EXAMPLES:
  tail file.txt       → shows last 10 lines
  tail -n 5 file.txt  → shows last 5 lines
  tail -f log.txt     → live-follows a file as it updates (useful for logs)

-------------------------------------
SEARCHING & COUNTING
-------------------------------------

COMMAND: grep
DESCRIPTION: Searches for a pattern or word inside a file.
EXAMPLES:
  grep "error" log.txt          → finds all lines containing "error"
  grep -i "error" log.txt       → same but case-insensitive
  grep -r "TODO" ./             → searches all files in current folder

COMMAND: wc
DESCRIPTION: Word Count — counts lines, words, and characters in a file.
EXAMPLES:
  wc file.txt         → shows line count, word count, character count
  wc -l file.txt      → shows only the number of lines

-------------------------------------
PERMISSIONS & OWNERSHIP
-------------------------------------

COMMAND: chmod
DESCRIPTION: Change Mode — changes who can read, write, or execute a file.
EXAMPLES:
  chmod 755 script.sh → owner can do everything, others can read/execute
  chmod +x script.sh  → makes a file executable
  chmod 600 file.txt  → only owner can read and write

PERMISSION NUMBERS QUICK REFERENCE:
  4 = read
  2 = write
  1 = execute
  7 = read + write + execute (4+2+1)
  6 = read + write (4+2)
  5 = read + execute (4+1)

COMMAND: chown
DESCRIPTION: Change Owner — changes who owns a file or folder.
EXAMPLES:
  chown john file.txt           → gives ownership to user john
  chown john:staff file.txt     → sets owner to john and group to staff
  chown -R john myfolder/       → changes ownership of folder and all contents

-------------------------------------
USER MANAGEMENT
-------------------------------------

COMMAND: useradd
DESCRIPTION: Creates a new user account.
EXAMPLES:
  useradd john                  → creates a user called john
  useradd -m john               → creates john with a home directory

COMMAND: usermod
DESCRIPTION: Modifies an existing user account.
EXAMPLES:
  usermod -aG sudo john         → adds john to the sudo group
  usermod -l newname oldname    → renames a user

COMMAND: userdel
DESCRIPTION: Deletes a user account.
EXAMPLES:
  userdel john                  → removes user john
  userdel -r john               → removes john and their home directory

-------------------------------------
GROUP MANAGEMENT
-------------------------------------

COMMAND: groupadd
DESCRIPTION: Creates a new group.
EXAMPLES:
  groupadd developers           → creates a group called developers

COMMAND: groupmod
DESCRIPTION: Modifies an existing group.
EXAMPLES:
  groupmod -n devs developers   → renames developers group to devs

COMMAND: groupdel
DESCRIPTION: Deletes a group.
EXAMPLES:
  groupdel developers           → removes the developers group

-------------------------------------
SUPERUSER / ADMIN
-------------------------------------

COMMAND: sudo
DESCRIPTION: Superuser Do — runs a command as an administrator/root user.
EXAMPLES:
  sudo apk update               → runs apk update as root
  sudo rm /etc/somefile         → deletes a protected file as root
  sudo -i                       → switches fully into root user mode

NOTE: In iSH you are already root so sudo is not needed, but on real
Linux servers you will use this constantly.

-------------------------------------
PROCESSES
-------------------------------------

COMMAND: ps
DESCRIPTION: Process Status — shows currently running processes.
EXAMPLES:
  ps                  → shows processes in current session
  ps aux              → shows all running processes on the system

COMMAND: top
DESCRIPTION: Live dashboard of running processes, CPU, and memory usage.
EXAMPLES:
  top                 → opens live process viewer (press Q to quit)

COMMAND: kill
DESCRIPTION: Stops/terminates a running process using its process ID (PID).
EXAMPLES:
  kill 1234           → sends stop signal to process 1234
  kill -9 1234        → force kills process 1234 immediately

HOW TO FIND A PID:
  ps aux | grep firefox         → find the PID of firefox

-------------------------------------
TEXT EDITORS
-------------------------------------

COMMAND: nano
DESCRIPTION: A simple beginner-friendly terminal text editor.
EXAMPLES:
  nano file.txt       → opens file.txt in nano
  nano newfile.txt    → creates and opens a new file

NANO SHORTCUTS:
  Ctrl + O            → save the file
  Ctrl + X            → exit nano
  Ctrl + K            → cut a line
  Ctrl + U            → paste a line
  Ctrl + W            → search

COMMAND: vi / vim
DESCRIPTION: A powerful but more complex text editor. vim is the improved version.
EXAMPLES:
  vi file.txt         → opens file in vi
  vim file.txt        → opens file in vim

VIM BASICS:
  Press I             → enter insert mode (now you can type)
  Press Esc           → exit insert mode
  Type :w             → save the file
  Type :q             → quit
  Type :wq            → save and quit
  Type :q!            → quit without saving

NOTE: vim has a steep learning curve but is very powerful once learned.
      nano is recommended for beginners.

-------------------------------------
BONUS USEFUL COMMANDS
-------------------------------------

COMMAND: echo
DESCRIPTION: Prints text to the screen or into a file.
EXAMPLES:
  echo "hello"                  → prints hello
  echo "hello" >> file.txt      → appends hello to file.txt

COMMAND: touch
DESCRIPTION: Creates an empty file or updates a file's timestamp.
EXAMPLES:
  touch newfile.txt             → creates an empty file called newfile.txt

COMMAND: clear
DESCRIPTION: Clears the terminal screen.
EXAMPLES:
  clear                         → wipes the screen clean

COMMAND: history
DESCRIPTION: Shows a list of previously run commands.
EXAMPLES:
  history                       → shows all recent commands
  history | grep git            → searches history for git commands

COMMAND: man
DESCRIPTION: Manual — shows the full documentation for any command.
EXAMPLES:
  man ls                        → shows the manual for ls
  man grep                      → shows the manual for grep

NOTE: man may not be available in iSH by default. Use --help instead:
  ls --help
  grep --help

-------------------------------------
GIT COMMANDS (BONUS)
-------------------------------------

COMMAND: git clone
DESCRIPTION: Downloads a repository from GitHub to your local machine.
EXAMPLES:
  git clone git@github.com:username/repo.git

COMMAND: git status
DESCRIPTION: Shows which files have been changed or are ready to commit.
EXAMPLES:
  git status

COMMAND: git add
DESCRIPTION: Stages files to be included in the next commit.
EXAMPLES:
  git add file.txt              → stages one file
  git add .                     → stages all changed files

COMMAND: git commit
DESCRIPTION: Saves a snapshot of your staged changes with a message.
EXAMPLES:
  git commit -m "added new feature"

COMMAND: git push
DESCRIPTION: Uploads your commits to GitHub.
EXAMPLES:
  git push origin main

COMMAND: git pull
DESCRIPTION: Downloads and merges the latest changes from GitHub.
EXAMPLES:
  git pull origin main

COMMAND: git log
DESCRIPTION: Shows the history of commits.
EXAMPLES:
  git log                       → full commit history
  git log --oneline             → compact one-line history

=====================================
   END OF CHEAT SHEET
   Keep practicing — you've got this!
=====================================
