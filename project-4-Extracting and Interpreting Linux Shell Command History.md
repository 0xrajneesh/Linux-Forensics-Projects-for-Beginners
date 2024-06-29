# Project: Extracting and Interpreting Linux Shell Command History

## Introduction
Shell command history can provide valuable insights during forensic investigations by revealing the actions performed by users on a Linux system. This project will guide you through the process of extracting and interpreting Linux shell command history from various shell environments. You will learn how to analyze these command histories to uncover potential security incidents and user activities.

## Objective
The objective of this project is to provide hands-on experience in extracting and interpreting shell command history on Linux systems. By the end of this project, you will be able to effectively use forensic tools to analyze shell command history and gather relevant evidence.

## Lab Setup and Tools
To complete this project, you will need access to a Linux operating system. You can use a physical machine, set up a virtual machine using software like VirtualBox or VMware, or use a cloud-based Linux instance.

### Pre-requisites
- Basic understanding of Linux OS and command-line interface
- Administrative privileges on the Linux machine

### Tools Installation
For this project, we will use the following tools:
1. **Grep**: A command-line utility for searching plain-text data.
2. **Auditd**: A userspace component to collect audit data.
3. **Last**: A command-line tool to display login history.

#### Installing Auditd
1. Install Auditd using the package manager:
    ```bash
    sudo apt-get install auditd
    ```

## Exercises

### Exercise 1: Extracting Bash Shell Command History
**Objective**: Learn how to extract and analyze command history from the Bash shell.

**Steps**:
1. Open a terminal.
2. Navigate to a user's home directory:
    ```bash
    cd /home/username
    ```
3. Display the contents of the `.bash_history` file:
    ```bash
    cat .bash_history
    ```
4. Use `grep` to search for specific commands or keywords:
    ```bash
    grep "sudo" .bash_history
    ```

**Expected Output**: You should be able to see the history of commands executed by the user in the Bash shell and identify specific actions taken.

### Exercise 2: Extracting Zsh Shell Command History
**Objective**: Learn how to extract and analyze command history from the Zsh shell.

**Steps**:
1. Open a terminal.
2. Navigate to a user's home directory:
    ```bash
    cd /home/username
    ```
3. Display the contents of the `.zsh_history` file:
    ```bash
    cat .zsh_history
    ```
4. Use `grep` to search for specific commands or keywords:
    ```bash
    grep "sudo" .zsh_history
    ```

**Expected Output**: You should be able to see the history of commands executed by the user in the Zsh shell and identify specific actions taken.

### Exercise 3: Analyzing Shell Command History with Auditd
**Objective**: Use Auditd to track and analyze shell commands executed by users.

**Steps**:
1. Ensure the `auditd` service is running:
    ```bash
    sudo service auditd start
    ```
2. Add an audit rule to track all executed commands:
    ```bash
    sudo auditctl -a always,exit -F arch=b64 -S execve -k exec_commands
    ```
3. Generate some user activity by executing various commands in the shell.
4. Use `ausearch` to query the audit logs for executed commands:
    ```bash
    sudo ausearch -k exec_commands
    ```

**Expected Output**: You should be able to track and analyze shell commands executed by users using Auditd.

### Exercise 4: Correlating Command History with Login Records
**Objective**: Correlate shell command history with login records to understand user sessions.

**Steps**:
1. Use the `last` command to display the login history:
    ```bash
    last
    ```
2. Note the login times and user accounts.
3. Compare the login records with the timestamps in the shell command history files (e.g., `.bash_history`).
4. Identify the commands executed during specific user sessions.

**Expected Output**: You should be able to correlate shell command history with login records to understand user sessions and actions.

### Exercise 5: Investigating Suspicious Commands
**Objective**: Identify and investigate suspicious commands executed by users.

**Steps**:
1. Extract the shell command history for the user as described in Exercises 1 and 2.
2. Use `grep` to search for potentially malicious commands or keywords (e.g., `wget`, `curl`, `nc`, `rm`):
    ```bash
    grep -E "wget|curl|nc|rm" .bash_history
    ```
3. Review the output to identify any suspicious commands.
4. Investigate the context and potential impact of the identified commands.

**Expected Output**: You should be able to identify and investigate suspicious commands executed by users, providing insights into potential security incidents.

---

With these exercises, you will gain practical experience in extracting and interpreting Linux shell command history. This will enhance your skills in digital forensics and help you effectively investigate user actions by uncovering valuable evidence from shell command histories.
