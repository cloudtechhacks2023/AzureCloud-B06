## Class Notes: Basic Linux Commands and Installing WSL on Windows

### 1. `whoami` Command

- **Purpose:** The `whoami` command is used to display the currently logged-in user on the system. It simply returns the username that you are logged into the shell as.
  
- **Usage:**
  ```bash
  whoami
  ```

- **Example:**
  ```bash
  $ whoami
  john
  ```
  This means the user logged into the terminal is `john`.

- **Explanation:** This command is useful when you're working in a multi-user environment or if you're unsure which user account is currently active.

---

### 2. `pwd` Command

- **Purpose:** The `pwd` (print working directory) command displays the absolute path of the current directory you are in within the file system.

- **Usage:**
  ```bash
  pwd
  ```

- **Example:**
  ```bash
  $ pwd
  /home/john/projects
  ```

- **Explanation:** The command shows the directory path you're currently located in. This helps you track your position in the file system. The output is usually an absolute path, meaning it starts from the root (`/`).

---

### 3. `ls` Command

- **Purpose:** The `ls` command lists the contents (files and directories) of a directory. By default, it lists the contents of the current directory.

- **Basic Usage:**
  ```bash
  ls
  ```

- **Example:**
  ```bash
  $ ls
  Documents  Downloads  Pictures  Music
  ```

- **Explanation:** This command shows the files and directories within the current directory. You can also use flags to modify its behavior:
  - `-l` for a detailed listing (permissions, ownership, size, etc.)
  - `-a` to show hidden files (those that start with a dot `.`)
  - `-h` to display file sizes in human-readable format (e.g., KB, MB)
  - `-R` for recursive listing of all directories and subdirectories.

- **Examples of advanced usage:**
  ```bash
  ls -l
  ls -a
  ls -lh
  ```

---

### 4. `cd` Command

- **Purpose:** The `cd` (change directory) command is used to navigate between directories in the file system.

- **Basic Usage:**
  ```bash
  cd <directory-path>
  ```

- **Example:**
  ```bash
  $ cd /home/john/projects
  $ pwd
  /home/john/projects
  ```

- **Explanation:** 
  - To move into a directory, specify the full or relative path of the directory you want to go to.
  - If you want to go back to your home directory, simply type:
    ```bash
    cd ~
    ```
  - To go up one directory level (parent directory), use:
    ```bash
    cd ..
    ```
  - To move to the root directory (`/`), use:
    ```bash
    cd /
    ```

Certainly! Here's the revised section on installing WSL with a simplified approach:

---

### How to Install WSL on Windows

To install **Windows Subsystem for Linux (WSL)** on your Windows system, follow these simple steps:

#### 1. **Install WSL Using One Command**

- **Step 1:** Open **PowerShell** as Administrator.
  - Press `Win + X` and select **Windows PowerShell (Admin)**.

- **Step 2:** Run the following command to install WSL:
  ```powershell
  wsl --install
  ```

This single command will:
- Enable the necessary features for WSL.
- Install the default Linux distribution (usually **Ubuntu**).
- Set WSL 2 as the default version (if your system supports it).

#### 2. **Restart Your Computer**

After the installation completes, you might be prompted to restart your system. Go ahead and restart it to complete the installation.

#### 3. **Set Up Your Linux Distribution**

Once your system restarts, open your installed Linux distribution (e.g., **Ubuntu**) from the Start menu. The first time you run it, you will need to:
- Set your Linux username and password.

---

### Conclusion

By running `wsl --install`, you can quickly set up a Linux environment on your Windows machine with minimal steps. This command automatically installs WSL, enables required features, and sets up a default Linux distribution, making it the easiest way to get started with WSL.

Certainly! Here’s the updated version of the class notes with the additional part at the end:

# Try Ubuntu Online!

If you want to try out Ubuntu without installing WSL or making changes to your system, you can use an online Linux environment. Check out this interactive playground for Ubuntu:

[Ubuntu on KillerCoda Playground](https://killercoda.com/playgrounds/scenario/ubuntu)

This platform provides a web-based Ubuntu environment, allowing you to practice Linux commands and get familiar with the system without needing to install anything locally.

### **1. `mkdir`** (Make Directory)

The `mkdir` command is used to create new directories in the filesystem.

#### **Usage:**
```bash
mkdir [options] directory_name
```

#### **Common Options:**
- `-p`: Creates parent directories as needed. If the parent directories don’t exist, it creates them.
- `-v`: Verbose mode, displays a message for each directory created.

#### **Examples:**
- Create a single directory:
  ```bash
  mkdir my_directory
  ```

- Create multiple directories at once:
  ```bash
  mkdir dir1 dir2 dir3
  ```

- Create a directory with parent directories:
  ```bash
  mkdir -p /home/user/new_folder/sub_folder
  ```

---

### **2. `touch`** (Create a New File or Update Timestamps)

The `touch` command is used to create an empty file if it does not exist or update the timestamp of an existing file.

#### **Usage:**
```bash
touch [options] file_name
```

#### **Common Options:**
- `-c`: Do not create any files; only change timestamps of existing files.
- `-t`: Allows you to specify a custom timestamp.

#### **Examples:**
- Create an empty file:
  ```bash
  touch myfile.txt
  ```

- Update the timestamp of an existing file:
  ```bash
  touch myfile.txt
  ```

- Create multiple files at once:
  ```bash
  touch file1.txt file2.txt
  ```

---

### **3. `nano`** (Text Editor)

`nano` is a simple, command-line text editor used to edit files in the terminal.

#### **Usage:**
```bash
nano [options] file_name
```

#### **Common Commands Inside `nano`:**
- `CTRL + O`: Save the file.
- `CTRL + X`: Exit `nano`.
- `CTRL + K`: Cut selected text.
- `CTRL + U`: Paste the cut text.

#### **Examples:**
- Open a file for editing:
  ```bash
  nano myfile.txt
  ```

- Open a file in read-only mode:
  ```bash
  nano -v myfile.txt
  ```

---

### **4. `cat`** (Concatenate and Display File Contents)

The `cat` command is used to display the contents of a file or concatenate multiple files.

#### **Usage:**
```bash
cat [options] file_name
```

#### **Common Options:**
- `-n`: Number the lines of output.
- `-b`: Number non-blank lines only.
- `-E`: Display `$` at the end of each line.

#### **Examples:**
- Display the contents of a file:
  ```bash
  cat myfile.txt
  ```

- Concatenate multiple files:
  ```bash
  cat file1.txt file2.txt > combined.txt
  ```

- Display line numbers:
  ```bash
  cat -n myfile.txt
  ```

---

### **5. `cp`** (Copy Files or Directories)

The `cp` command is used to copy files and directories.

#### **Usage:**
```bash
cp [options] source destination
```

#### **Common Options:**
- `-r`: Copy directories recursively.
- `-i`: Prompt before overwriting.
- `-v`: Verbose mode, show what is being copied.

#### **Examples:**
- Copy a file:
  ```bash
  cp file1.txt file2.txt
  ```

- Copy a directory and its contents:
  ```bash
  cp -r dir1/ dir2/
  ```

- Copy and show details of the operation:
  ```bash
  cp -v file1.txt backup/
  ```

---

### **6. `mv`** (Move or Rename Files/Directories)

The `mv` command is used to move or rename files and directories.

#### **Usage:**
```bash
mv [options] source destination
```

#### **Common Options:**
- `-i`: Prompt before overwriting.
- `-v`: Verbose mode.

#### **Examples:**
- Rename a file:
  ```bash
  mv oldfile.txt newfile.txt
  ```

- Move a file to a different directory:
  ```bash
  mv file.txt /home/user/Documents/
  ```

- Move multiple files:
  ```bash
  mv file1.txt file2.txt /home/user/Documents/
  ```

---

### **7. `rm`** (Remove Files or Directories)

The `rm` command is used to remove (delete) files and directories.

#### **Usage:**
```bash
rm [options] file_name
```

#### **Common Options:**
- `-i`: Prompt before deleting.
- `-f`: Force deletion without prompts.
- `-v`: Verbose mode, show what is being deleted.

#### **Examples:**
- Remove a file:
  ```bash
  rm myfile.txt
  ```

- Forcefully remove a file without confirmation:
  ```bash
  rm -f myfile.txt
  ```

- Delete multiple files:
  ```bash
  rm file1.txt file2.txt file3.txt
  ```

---

### **8. `rm -r`** (Remove Directories Recursively)

The `rm -r` command is used to delete directories and their contents recursively.

#### **Usage:**
```bash
rm -r directory_name
```

#### **Common Options:**
- `-i`: Prompt before deleting each file and subdirectory.
- `-f`: Force deletion without prompts.

#### **Examples:**
- Remove a directory and its contents:
  ```bash
  rm -r mydirectory/
  ```

- Forcefully remove a directory:
  ```bash
  rm -rf mydirectory/
  ```

---

### **9. `grep`** (Search for Text in Files)

The `grep` command is used to search for a specified pattern (text string) within files.

#### **Usage:**
```bash
grep [options] pattern file_name
```

#### **Common Options:**
- `-i`: Ignore case when matching.
- `-r` or `-R`: Search recursively in directories.
- `-l`: Show only the filenames of files that contain the pattern.
- `-n`: Show line numbers along with matched lines.
- `-v`: Invert match (show lines that do not match the pattern).

#### **Examples:**
- Search for a string in a file:
  ```bash
  grep "search_term" myfile.txt
  ```

- Search recursively in a directory:
  ```bash
  grep -r "search_term" /path/to/dir/
  ```

- Ignore case while searching:
  ```bash
  grep -i "search_term" myfile.txt
  ```

---

### **10. `grep -i`** (Case-insensitive Search)

The `grep -i` command is used for searching patterns in files while ignoring case differences.

#### **Usage:**
```bash
grep -i "pattern" file_name
```

#### **Example:**
- Search case-insensitively for a term:
  ```bash
  grep -i "hello" myfile.txt
  ```

This will match "hello", "Hello", "HELLO", etc.

---

### **11. `cd ..`** (Change Directory Up One Level)

The `cd ..` command is used to navigate up one level in the directory tree.

#### **Usage:**
```bash
cd ..
```

#### **Examples:**
- Move up one level from the current directory:
  ```bash
  cd ..
  ```

- After navigating up, you can move into another directory:
  ```bash
  cd ..
  cd folder2/
  ```

---

### **Summary of Key Commands:**

| Command    | Description                                     | Example Usage                         |
|------------|-------------------------------------------------|---------------------------------------|
| `mkdir`    | Create directories                              | `mkdir mydir`                         |
| `touch`    | Create or update file timestamps                | `touch file.txt`                      |
| `nano`     | Open file in a text editor                      | `nano file.txt`                       |
| `cat`      | Display file contents                           | `cat file.txt`                        |
| `cp`       | Copy files or directories                       | `cp file1.txt backup/`                |
| `mv`       | Move or rename files or directories             | `mv file1.txt /home/user/`            |
| `rm`       | Remove files                                    | `rm file.txt`                         |
| `rm -r`    | Remove directories and contents recursively     | `rm -r folder`                        |
| `grep`     | Search for a string in files                    | `grep "pattern" file.txt`             |
| `grep -i`  | Case-insensitive search                         | `grep -i "pattern" file.txt`          |
| `cd ..`    | Change to the parent directory                  | `cd ..`                               |
